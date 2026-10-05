---

copyright:
  years: 2026
lastupdated: "2026-10-05"

keywords: instructlab, ai, inference, embeddings, vectors

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}



# Creating embeddings
{: #inf-create-embeddings}

Embeddings convert text into numerical vectors that capture semantic meaning, enabling AI models to compare and retrieve semantically similar content. For a tutorial that shows how embeddings can improve chat completion responses by providing a model with relevant context from your own knowledge base, see [Improving chat completions with vector embeddings and RAG](/docs/inference?topic=inference-embeddings-rag). For a complete list of the available parameters, see [OpenAI Create embeddings](https://developers.openai.com/api/reference/resources/embeddings/methods/create){: external}.
{: shortdesc}

## Before you begin
{: #inf-create-embeddings-prereqs}

* Create a Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* Create [a {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).

* Make sure that you have the Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access](/docs/inference?topic=inference-iam&interface=ui).

* [Authenticate to the API](/docs/inference?topic=inference-inf-auth).

* Get your API endpoint. All API requests use the following base URL format:

   
   ```text
   https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference
   ```
   {: codeblock}

   

   Replace `<project_id>` with your project ID. To find it, go to [{{site.data.keyword.instructlab_short}} projects](/instructlab/projects) and open your project.

To check whether a model supports embeddings, [list the models](/docs/inference?topic=inference-inf-list-models) or [get a model by ID](/docs/inference?topic=inference-inf-list-models#inf-get-model) and verify that `supports_embeddings` is set to `true`.
{: tip}

## Input formats and limits
{: #embeddings-inputs-limits}

The embeddings API supports the following input formats for the `input` parameter:

String
:   A single text string to turn into an embedding vector.

Array of strings
:   An array of text strings, where each string is turned into a separate embedding vector.

Array of numbers
:   An array of integers representing tokens, which is converted to an embedding vector.

Array of arrays of numbers
:   An array of token arrays, where each token array is turned into a separate embedding vector.

When you submit input for embeddings, the following limits and behaviors apply:

Input token limits
:   Each embedding model defines its maximum input token limit based on its context window size.

Array input evaluation
:   If you submit an array of multiple inputs, the input token limit is applied to each text individually.

Exceeding the limits
:   If any single text input in the array exceeds the model's token limit, the API rejects the entire request and returns an `HTTP 400 Bad Request` error.

## Output dimensions
{: #embeddings-outputs}

The output of an embeddings request is a high-dimensional vector. Consider the following characteristics of output vectors:

Representation quality
:   A larger output vector size can represent more detail and capture more granular semantic meaning. However, larger vectors require more memory for storage and search, which can increase resource usage.

Configuring vector size
:   The size of the output vector is model-dependent. Although the embeddings API supports a `dimensions` parameter to configure the output vector size, this parameter is used only if the selected model is compatible with configuring dimension sizes.

## Creating embeddings
{: #inf-create-embeddings-api}

Use the embeddings API to convert one or more text inputs into vector representations. The following examples show how to create embeddings with the API by using cURL or the OpenAI Python client.



```bash
curl https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/embeddings \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <bearer_token>" \
  -d '{
    "model": "granite-embedding-278m-multilingual",
    "input": [
      "Manage your projects from the IBM Cloud console.",
      "Use the API to automate workflows and integrate AI into your applications.",
      "IBM Cloud offers a range of AI and machine learning services for enterprise applications."
    ]
  }'
```
{: codeblock}
{: curl}

```python
from openai import OpenAI
client = OpenAI(
  api_key="<bearer_token>",
  base_url="https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference",
)

response = client.embeddings.create(
  model="granite-embedding-278m-multilingual",
    input=[
        "Manage your projects from the IBM Cloud console.",
        "Use the API to automate workflows and integrate AI into your applications.",
        "IBM Cloud offers a range of AI and machine learning services for enterprise applications."
    ]
)

print(response.data[0].embedding)
```
{: codeblock}
{: python}



