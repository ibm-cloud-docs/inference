---

copyright:
  years: 2025, 2026
lastupdated: "2026-10-05"

keywords: ai, embeddings, text embeddings, rag, retrieval-augmented generation, vector store, cosine similarity, chat completions

subcollection: inference

content-type: tutorial

services: {{site.data.keyword.subcollection}}
account-plan: paid
completion-time: 30m

---

{{site.data.keyword.attribute-definition-list}}

# Improving chat completions with vector embeddings and RAG
{: #embeddings-rag}
{: toc-content-type="tutorial"}
{: toc-services="{{site.data.keyword.subcollection}}"}
{: toc-completion-time="30m"}

Learn how to use vector embeddings from the {{site.data.keyword.instructlab_full_notm}} API to build a retrieval-augmented generation (RAG) pipeline that gives a chat model accurate, grounded answers from your own knowledge base.
{: shortdesc}

Large language models are powerful, but they have no knowledge of facts outside their training data. When you need a model to reason over a specific knowledge base — such as a product catalog, customer history, or domain corpus — you need a way to surface the right information at query time. This tutorial demonstrates the full RAG loop: embed a knowledge base, store it in a vector index, and inject the most relevant facts into a chat completion request so the model's answer is grounded in your data.

For more information about embeddings use cases, such as search, clustering, and classification, see [Embeddings use cases](https://developers.openai.com/api/docs/guides/embeddings#use-cases){: external}.
{: tip}

## Objectives
{: #embeddings-rag-objectives}

In this tutorial, you complete the following tasks:

* Authenticate to the {{site.data.keyword.instructlab_short}} API.
* Embed a knowledge base using the `granite-embedding-278m-multilingual` model.
* Store embeddings in an in-memory vector index and search it with cosine similarity.
* Query the `gpt-oss-120b` chat model both without and with retrieved context to see the improvement in accuracy firsthand.

The application you build has the following architecture:

1. Each fact in your knowledge base is converted to an embedding vector and added to a `MemoryStore`.
2. A user question is embedded using the same model.
3. Cosine similarity ranks the stored vectors against the question vector, and the top 3 facts are retrieved.
4. Those facts are injected into the system prompt sent to the chat model.
5. The model returns a grounded answer.

## Before you begin
{: #embeddings-rag-prereqs}

Make sure you have the following:

* A Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* [A {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).

* The Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access](/docs/inference?topic=inference-iam&interface=ui).

* [Python 3.9 or later](https://www.python.org/downloads/){: external} installed on your workstation.

* The `openai` Python package. Install it by running the following command:

   ```sh
   pip install openai
   ```
   {: pre}

## Set up API authentication
{: #embeddings-rag-auth}
{: step}

Before you can call the {{site.data.keyword.instructlab_short}} API, you need to authenticate your requests using a service ID and API key. If you already completed [the getting started tutorial](/docs/inference?topic=inference-getting-started), you can reuse the service ID and API key you created there and skip to [Get your project ID and endpoint](#embeddings-rag-project-id).

### Create a service ID and assign access
{: #embeddings-rag-create-service-id}

A service ID is a useful way to control and distribute access to {{site.data.keyword.instructlab_short}} projects. Create the service ID, then assign it access to your project.

1. In the {{site.data.keyword.cloud_notm}} console, go to **Manage** > **Access (IAM)** > **[Service IDs](/iam/serviceids){: external}** and click **Create**.

1. Enter a name and description for your service ID, then click **Create**.

1. From the service ID page, click **Assign access**.

1. Select **{{site.data.keyword.instructlab_short}}** as the service.

1. Within **Resources**, select **Specific resources** and choose your project.

1. Within **Roles and actions**, select **Writer** as the service access role.

   Platform access roles are not required for API access.
   {: note}

1. Review the access summary and click **Assign**.

### Create an API key
{: #embeddings-rag-create-api-key}

Now that your service ID has access to your project, create a service ID API key.

1. From the service ID page, click **API keys**.

1. Click **Create** and enter a name for your API key.

1. For leaked key handling, select **Disable the leaked key** to automatically disable the key if it's detected as leaked.

1. Set an expiration date for the key. Regular key rotation is recommended for security.

1. Click **Create**.

1. Copy the API key and save it in a secure location. The key cannot be viewed again.

## Get your project ID and API endpoint
{: #embeddings-rag-project-id}
{: step}

Your project ID is required for all API requests.

1. Go to [{{site.data.keyword.instructlab_short}} projects](https://cloud.ibm.com/instructlab/projects){: external}.

1. Open your project.

1. Copy your project ID and save it for the next steps.

The base URL for all API requests in this tutorial takes the following form:


```text
https://us-east.rhai.ibm.com/v1/projects/<project_id>
```
{: codeblock}


Replace `<project_id>` with the project ID you copied.

## Set environment variables
{: #embeddings-rag-env}
{: step}

Set your endpoint and store your API key in a variable:


```sh
export ENDPOINT="https://us-east.rhai.ibm.com/v1/projects/<project_id>"
export API_KEY="<your-api-key>"
```
{: pre}


Replace `<project_id>` with your project ID and `<your-api-key>` with the API key you created earlier.

Never hardcode credentials in source files. Use environment variables or a secrets manager such as [{{site.data.keyword.secrets-manager_full_notm}}](/docs/secrets-manager?topic=secrets-manager-getting-started){: external}.
{: important}

## Generate a bearer token
{: #embeddings-rag-token}
{: step}

The API requires an IAM bearer token. Exchange your API key for an IAM bearer token by running the following command:


```sh
export AUTH=$(curl -s -X POST "https://iam.cloud.ibm.com/identity/token" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=$API_KEY" \
  | python3 -c "import sys,json; print(json.load(sys.stdin)['access_token'])")
```
{: pre}


Verify the token was issued successfully. A valid token starts with `eyJ`:

```sh
echo $AUTH | cut -c1-4
```
{: pre}

IAM tokens expire after 1 hour. Re-run the token exchange command if you receive a 401 error when running the script.
{: note}


## Build the vector store
{: #embeddings-rag-store}
{: step}

The vector store is an in-memory index that holds text alongside its embedding vector. The following Python implementation uses cosine similarity to find the entries most semantically similar to a query vector.

Create a file named `store.py` and add the following code:

```python
import math


def cosine_similarity(a: list[float], b: list[float]) -> float:
    """Return the cosine similarity between two vectors."""
    dot = sum(x * y for x, y in zip(a, b))
    mag_a = math.sqrt(sum(x * x for x in a))
    mag_b = math.sqrt(sum(x * x for x in b))
    if mag_a == 0 or mag_b == 0:
        return 0.0
    return dot / (mag_a * mag_b)


class MemoryStore:
    """In-memory vector store with cosine similarity search."""

    def __init__(self) -> None:
        self._entries: list[dict] = []

    def add(self, text: str, vector: list[float]) -> None:
        """Store a text/vector pair."""
        self._entries.append({"text": text, "vector": vector})

    def search(self, query: list[float], top_k: int) -> list[dict]:
        """Return the top_k entries most similar to the query vector."""
        scored = [
            {"text": e["text"], "score": cosine_similarity(query, e["vector"])}
            for e in self._entries
        ]
        scored.sort(key=lambda x: x["score"], reverse=True)
        return scored[:top_k]
```
{: codeblock}

Cosine similarity measures the angle between two vectors, not their magnitude. This makes it well-suited for comparing text embeddings because it captures semantic direction regardless of text length.
{: tip}

## Create the API client
{: #embeddings-rag-client}
{: step}

The API client wraps two {{site.data.keyword.instructlab_short}} endpoints: the embeddings endpoint and the chat completions endpoint. This implementation uses the `openai` package, which provides a Python client for any OpenAI-compatible API.

Create a file named `client.py` and add the following code:

```python
import os

from openai import OpenAI


def _client() -> OpenAI:
    """Return an OpenAI client pointed at the InstructLab endpoint."""
    return OpenAI(
        api_key=os.environ["AUTH"],
        base_url=f"{os.environ['ENDPOINT']}/inference/v1",
    )


def embed_text(text: str) -> list[float]:
    """Call the embeddings endpoint and return the vector for the given text."""
    response = _client().embeddings.create(
        model="granite-embedding-278m-multilingual",
        input=text,
        encoding_format="float",
    )
    return response.data[0].embedding


def chat_complete(system_prompt: str, user_message: str, prefix: str = "") -> None:
    """Call the chat completions endpoint with streaming and print tokens as they arrive."""
    messages = []
    if system_prompt:
        messages.append({"role": "system", "content": system_prompt})
    messages.append({"role": "user", "content": user_message})

    stream = _client().chat.completions.create(
        model="gpt-oss-120b",
        messages=messages,
        stream=True,
    )

    print(prefix, end="", flush=True)
    for chunk in stream:
        content = chunk.choices[0].delta.content if chunk.choices else None
        if content:
            print(content.replace("\n", f"\n{prefix}"), end="", flush=True)
    print()
```
{: codeblock}

The `_client()` helper constructs an `OpenAI` instance pointed at the {{site.data.keyword.instructlab_short}} API using your `ENDPOINT` and `AUTH` environment variables. The `embed_text` function calls the embeddings endpoint with `encoding_format="float"` to ensure the response is returned as a plain float list. The `chat_complete` function calls the chat completions endpoint with streaming enabled, so tokens are printed to the terminal as they arrive.

## Seed the memory store and run the demo
{: #embeddings-rag-main}
{: step}

With the vector store and API client in place, you can now write the main script that ties everything together: it seeds the store, answers each question without memory, then answers with RAG and prints both responses side-by-side for comparison.

Create a file named `main.py` and add the following code:

```python
import os
import sys

from client import chat_complete, embed_text
from store import MemoryStore

# knowledge is the set of facts to embed into the vector store.
# This example uses IBM Cloud support FAQs as the knowledge base.
KNOWLEDGE = [
    "To reset your IBM Cloud account password, go to the IBM Cloud login page and click 'Forgot password' to receive a reset email.",
    "IBM Cloud Pay-As-You-Go accounts are charged monthly based on resource usage, with no upfront commitment required.",
    "IBM Cloud resource groups are used to organize account resources and manage access with IAM policies.",
    "You can monitor IBM Cloud service health and view planned maintenance on the IBM Cloud Status page at cloud.ibm.com/status.",
    "IBM Cloud Lite accounts are free and include a selection of always-free services, but do not support all paid features.",
    "To create an IBM Cloud API key, go to Manage > Access (IAM) > API keys in the IBM Cloud console.",
    "IBM Cloud support plans range from Basic (included with all accounts) to Advanced and Premium tiers with faster response times.",
    "IBM Cloud Object Storage stores data as objects across multiple regions for high availability and durability.",
]

QUESTIONS = [
    "How do I reset my IBM Cloud password?",
    "What is the difference between a Lite account and a Pay-As-You-Go account?",
]

TOP_K = 3


def build_system_prompt(entries: list[dict]) -> str:
    facts = "\n".join(f"{i + 1}. {e['text']}" for i, e in enumerate(entries))
    return (
        "You are a helpful assistant with access to the following verified facts.\n"
        "Use these facts to answer the user's question accurately and concisely.\n\n"
        f"Relevant facts:\n{facts}\n"
    )


def main() -> None:
    if not os.environ.get("ENDPOINT") or not os.environ.get("AUTH"):
        print("ERROR: ENDPOINT and AUTH environment variables must be set.", file=sys.stderr)
        sys.exit(1)

    # Seed the vector store.
    print("Embedding knowledge base...")
    store = MemoryStore()
    for i, fact in enumerate(KNOWLEDGE):
        print(f"  [{i + 1}/{len(KNOWLEDGE)}] {fact[:60]}")
        store.add(fact, embed_text(fact))
    print(f"\nMemory store ready with {len(KNOWLEDGE)} entries.\n")

    # Run each question without memory, then with RAG.
    for question in QUESTIONS:
        print(f"Question: {question}\n")

        print("  WITHOUT memory:")
        chat_complete("", question, prefix="    ")

        print("\n  WITH memory (RAG):")
        query_vec = embed_text(question)
        relevant = store.search(query_vec, TOP_K)

        print("  Retrieved facts:")
        for i, entry in enumerate(relevant):
            print(f"    {i + 1}. {entry['text']}")

        print()
        chat_complete(build_system_prompt(relevant), question, prefix="    ")
        print("\n" + "─" * 70)


if __name__ == "__main__":
    main()
```
{: codeblock}

Run the Python script:

```sh
python main.py
```
{: pre}

The output shows each question answered twice. The first response comes from the model's general training knowledge alone. The second response is grounded in the facts retrieved from your vector store:

```text
Question: How do I reset my IBM Cloud password?

  WITHOUT memory:
    To reset your password, visit the account login page and look for a
    'Forgot password' or 'Reset password' option ...

  WITH memory (RAG):
  Retrieved facts:
    1. To reset your IBM Cloud account password, go to the IBM Cloud login
       page and click 'Forgot password' to receive a reset email.
    2. To create an IBM Cloud API key, go to Manage > Access (IAM) > API keys
       in the IBM Cloud console.
    3. IBM Cloud support plans range from Basic to Advanced and Premium tiers.

    To reset your IBM Cloud account password, go to the IBM Cloud login page
    and click 'Forgot password'. You will receive an email with instructions
    to set a new password.
```
{: screen}

The RAG response is more specific and directly cites the retrieved facts because those facts were injected into the system prompt before the chat model was called.

## Next steps
{: #embeddings-rag-next-steps}

Now that you've built a complete RAG pipeline, here are some ways to extend it:

* **Bring your own knowledge base** — Replace the `KNOWLEDGE` list in `main.py` with any list of strings: product documentation, support tickets, internal wikis, or domain-specific data.
* **Persist the vector store** — Serialize the store's entries to disk (for example, as JSON) so you don't re-embed on every run.
* **Tune retrieval** — Adjust `TOP_K` in `main.py` to retrieve more or fewer facts per query and observe the effect on response quality.
* **Explore other inference capabilities** — See the [Running inference](/docs/inference?topic=inference-inference) topic to learn about additional models and parameters available through the {{site.data.keyword.instructlab_short}} API.
