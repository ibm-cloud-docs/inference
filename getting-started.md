---

copyright:
  years: 2024, 2026
lastupdated: "2026-10-13"

keywords: instructlab, ai, inference, chat completions

subcollection: inference

content-type: tutorial

services: {{site.data.keyword.subcollection}}
account-plan: paid
completion-time: 15m

---

{{site.data.keyword.attribute-definition-list}}


# Getting started with {{site.data.keyword.instructlab_full_notm}}
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-services="{{site.data.keyword.subcollection}}"}
{: toc-completion-time="15m"}

Ready to start using AI in your applications? In this tutorial, you'll learn how to inference with foundation models and generate AI-powered responses. In just 15 minutes, you'll be chatting with a large language model and integrating conversational AI into your workflows.
{: shortdesc}

{{site.data.keyword.instructlab_full}} is a business-ready, private, and secure generative AI solution powered by Red Hat OpenShift AI. This tutorial focuses on getting you started with inference for interacting with foundation models, the fastest way to start using AI.


## What you'll accomplish
{: #objectives}

In this tutorial, you'll do the following tasks:

* Set up your {{site.data.keyword.cloud_notm}} account and project.
* Authenticate to the inference API.
* Generate your first chat completion with a foundation model.
* Learn about next steps for customizing models with your own data.

## Before you begin
{: #prereqs}

Make sure you have the following:

* A Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* [A {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).

* The Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access](/docs/inference?topic=inference-iam&interface=ui).

## Get your project ID and API endpoint
{: #get-project-id}
{: step}

Your project ID is required for all API requests.

1. Go to [{{site.data.keyword.instructlab_short}} projects](https://cloud.ibm.com/instructlab/projects){: external}.

1. Open your project.

1. Copy your project ID and save it for the next steps.

### API endpoint
{: #gs-api-endpoint}

All API requests use the following base URL format:


```text
https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference
```
{: codeblock}



Replace `<project_id>` with your project ID.

## Authenticate to the API
{: #authenticate}
{: step}

Before you can interact with foundation models, you need to authenticate your API requests. You can use either a bearer token or an {{site.data.keyword.cloud_notm}} API key. This tutorial shows how to use a service ID with an API key for programmatic access. For more information on using a bearer token, see [Authenticating by using a bearer token](/docs/inference?topic=inference-inf-auth&interface=ui#inf-auth-token).

### Creating a service ID and an API key
{: #create-service-id}

A service ID manages access for applications and automated workflows. When you create a service ID directly within your project, the Writer service access role is automatically assigned so that you can create chat completions.

1. Go to the [{{site.data.keyword.instructlab_short}} projects](https://cloud.ibm.com/instructlab/projects){: external} page, and select your project.
1. In the **Using the API** section, click **Create API key**.
1. Click **Next**, and select **This project only** to restrict access to the current project.
1. Click **Create**.
1. Copy the API key and store it securely. The API key value cannot be displayed again after you close the dialog.

You can now use that API key to authenticate your requests. In the next step, you'll use this key in the `Authorization: Bearer` header of your API calls.

## Explore available models
{: #explore-models}
{: step}

Different foundation models have different strengths, so it's important to review the models that are available in your project.

Make the following API call to list all the available models. Replace `<project_id>` with your project ID and `<api_key>` with your service ID API key:



```bash
curl -L 'https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/models' \
  -H 'Accept: application/json' \
  -H "Authorization: Bearer <api_key>"
```
{: codeblock}
{: curl}

```python
from openai import OpenAI
client = OpenAI(
  api_key="<api_key>",
  base_url="https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference",
)

models = client.models.list()
print(models)
```
{: codeblock}
{: python}



The response shows you all the models you can use, along with information about their capabilities. You can experiment with different models to find the one that best fits your use case.

## Generate your first chat completion
{: #generate-completion}
{: step}

Now, send a message to the model and receive an AI-generated response.

Make the following API call, replacing `<project_id>` with your project ID and `<api_key>` with your service ID API key:



```bash
curl https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <api_key>" \
  -d '{
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
  api_key="<api_key>",
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




You should receive a response from the model introducing itself.

### Understanding the request
{: #understand-request}

Let's break down what you just did:

model
:   You specified `granite-4-0-h-small`, one of the available foundation models. Different models have different capabilities and performance characteristics.

messages
:   You provided two messages. One was a developer message that set the system prompt and instructed the model on how to behave. The user message included your actual question for the model to answer.

API endpoint
:   The request went to your project's inference endpoint, which handles routing to the appropriate model.

You can customize the model's behavior by adjusting the system prompt, adding more messages, or using different models for different use cases.
{: tip}

## Next steps
{: #next-steps}

Now that you've successfully started using inference, here's what you can do next:

### Continue with inference
{: #continue-inference}

* [Learn more about inference](/docs/inference?topic=inference-inf-chat-completions&interface=ui) to discover advanced features like streaming responses, adjusting model parameters, and managing conversation history.

* Explore the [OpenAI Chat Completion API](https://developers.openai.com/api/reference/resources/chat){: external} documentation for complete API reference.

* Integrate inference into your applications using the Python SDK or other programming languages.
