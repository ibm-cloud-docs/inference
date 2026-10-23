---

copyright:
  years: 2025, 2026
lastupdated: "2026-10-23"

keywords: instructlab, ai, inference, chat completions, chatting

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}


# Working with chat completions
{: #inf-chat-completions}

Chat completions are the core of inference. They allow you to send messages to a foundation model and receive AI-generated responses. This is how you build conversational experiences, get answers to questions, generate content, or process natural language inputs. You can control the conversation flow by providing system prompts that define the model's behavior and maintain message history for context-aware interactions.
{: shortdesc}

The following APIs are supported for chat completions:

Chat completions `/v1/chat/completions`
:   Create - [OpenAI documentation](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/create){: external}
:   Get - [OpenAI documentation](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/retrieve){: external}
:   List - [OpenAI documentation](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/list){: external}
:   Delete - [OpenAI documentation](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/delete){: external}

## Before you begin
{: #inf-chat-completions-prereqs-api}
{: api}

* Create a Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* Create [a {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).

* Make sure that you have the Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access](/docs/inference?topic=inference-iam&interface=ui).

* [Authenticate to the API](/docs/inference?topic=inference-inf-auth).

* Get your API endpoint. All API requests use the following base URL format:

   
   ```text
   https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference
   ```
   {: codeblock}

   

   Replace `<project_id>` with your project ID. To find it, go to [{{site.data.keyword.instructlab_short}} projects](/inference/projects) and open your project.

## Before you begin
{: #inf-chat-completions-prereqs-ui}
{: ui}

* Create a Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* Create [a {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).

* Make sure that you have the Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access](/docs/inference?topic=inference-iam&interface=ui).

## Working with chat completions by using the console
{: #inf-chat-completions-ui}
{: ui}

The console provides an interactive playground where you can experiment with different models, test prompts, and refine your AI interactions before integrating them into your applications.

The playground does not support embeddings. Use the API to [create embeddings](/docs/inference?topic=inference-inf-create-embeddings).
{: note}

1. In the console, open the [{{site.data.keyword.instructlab_short}} service](/inference/overview){: external} and click the name of your project to open it.

1. From the project page, click **Playground** to open the inference playground.

1. Begin your chat session. You can customize your chat session with the following options:

Model selection
:   You can choose from a list of foundation models.

System prompt
:   The system prompt instructs the model on how to conduct the dialog.

Inference settings
:   Adjust the **Randomness**, **Repetition**, and **Response limits**.

Chat history
:   You can filter the chat history by **Model** or **Date range**.


## Generating a chat completion by using the API
{: #inf-chat-generate}
{: api}

The following example shows how to generate a chat completion. For a complete list of the available parameters, see [OpenAI Chat Completion](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/create){: external}.



```bash
curl https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/chat/completions -H "Content-Type: application/json" -H "Authorization: Bearer <bearer_token>" -d '{
 "model": "granite-4-0-h-small",
 "messages": [
   {
     "role": "developer",
     "content": "You are a helpful assistant"
   },
   {
     "role": "user",
     "content": "Hello! Tell me about yourself"
   }
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

completion = client.chat.completions.create(
  model="granite-4-0-h-small",
  messages=[
    {"role": "developer", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Hello! Tell me about yourself"}
  ]
)

print(completion.choices[0].message)
```
{: codeblock}
{: python}




## Getting a chat completion by ID by using the API
{: #inf-chat-get-completion}
{: api}

Retrieving a specific chat completion by ID is useful for auditing, debugging, or analyzing past interactions.

The following example shows how to get a chat completion by its ID. For a complete list of the available parameters, see [Get Chat Completion](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/retrieve){: external}.



```bash
curl -L 'https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/chat/completions/<completion_id>' \
-H 'Accept: application/json' -H "Authorization: Bearer <bearer_token>"
```
{: codeblock}
{: curl}

```python
from openai import OpenAI
client = OpenAI(
  api_key="<bearer_token>",
  base_url="https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference",
)

completion = client.chat.completions.retrieve(completion_id="<completion_id>")
print(completion)
```
{: codeblock}
{: python}



## Listing chat completions by using the API
{: #inf-chat-list}
{: api}

Listing chat completions provides an overview of all your inference activity, so you can monitor usage patterns, track costs, and analyze how your application is interacting with foundation models. This is particularly valuable for understanding user behavior, identifying popular use cases, and optimizing your AI integration strategy.

The following example shows how to list chat completions. For a complete list of the available parameters, see [List Chat Completions](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/list){: external}.



```sh
curl -L 'https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/chat/completions' \
-H 'Accept: application/json' -H "Authorization: Bearer <bearer_token>"
```
{: codeblock}
{: curl}

```python
from openai import OpenAI
client = OpenAI(
  api_key="<bearer_token>",
  base_url="https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference",
)

completions = client.chat.completions.list()
print(completions)
```
{: codeblock}
{: python}



## Deleting a chat completion by using the API
{: #inf-chat-delete}
{: api}

Deleting chat completions helps you clean up test data and comply with privacy requirements.

The following example shows how to delete a chat completion. For a complete list of the available parameters, see [Delete chat completion](https://developers.openai.com/api/reference/resources/chat/subresources/completions/methods/delete){: external}.



```bash
curl -X DELETE https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/chat/completions/<completion_id> \
-H "Content-Type: application/json" -H "Authorization: Bearer <bearer_token>"
```
{: codeblock}
{: curl}

```python
from openai import OpenAI
client = OpenAI(
  api_key="<bearer_token>",
  base_url="https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference",
)

client.chat.completions.delete("<completion_id>")
```
{: codeblock}
{: python}
