---

copyright:
  years: 2024, 2026
lastupdated: "2026-05-05"

keywords: instructlab, ai, inferencing, chat completions

subcollection: instructlab

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

Ready to start using AI in your applications? In this tutorial, you'll learn how to use inferencing to interact with foundation models and generate AI-powered responses. In just 15 minutes, you'll be chatting with a large language model and integrating conversational AI into your workflows.
{: shortdesc}

{{site.data.keyword.instructlab_full}} is a business-ready, private, and secure generative AI solution powered by Red Hat OpenShift AI. Red Hat AI on {{site.data.keyword.cloud_notm}} provides two core capabilities: inferencing for interacting with foundation models and model alignment (InstructLab) for customizing models to your specific needs. This tutorial focuses on getting you started with inferencing, the fastest way to start using AI.

## What you'll accomplish
{: #objectives}

In this tutorial, you'll do the following tasks:

* Set up your {{site.data.keyword.cloud_notm}} account and project
* Authenticate to the inferencing API
* Generate your first chat completion with a foundation model
* Learn about next steps for customizing models with your own data

## Before you begin
{: #prereqs}

Make sure you have the following:

* A Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* [A {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).

* The Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access for InstructLab](/docs/inference?topic=inference-iam&interface=ui).

## Get your project ID and API endpoint
{: #get-project-id}
{: step}

Your project ID is required for all API requests. 

1. Go to [{{site.data.keyword.instructlab_short}} projects](https://cloud.ibm.com/instructlab/projects){: external}.

1. Open your project.

1. Click **Details**.

1. Copy your project ID and save it for the next steps.

### API endpoint
{: #gs-api-endpoint}

All API requests use the following base URL format:


```text
https://us-east.rhai.ibm.com/v1/projects/{project_id}/inference
```
{: codeblock}



Replace `{project_id}` with your project ID. 

## Authenticate to the API
{: #authenticate}
{: step}

Before you can interact with foundation models, you need to authenticate your API requests. You can use either a bearer token or an {{site.data.keyword.cloud_notm}} API key. This tutorial shows how to use a service ID with an API key for programmatic access. For more information on using a bearer token, see [Authenticating by using a bearer token](/docs/inference?topic=inference-inference&interface=api#inf-chat-token). 

### Create a service ID and assign access
{: #create-service-id}

A service ID is a useful way to control and distribute access to {{site.data.keyword.instructlab_short}} projects. Create the service ID, then assign it access to your project. 

1. In the {{site.data.keyword.cloud_notm}} console, go to **Manage** > **Access (IAM)** > **[Service IDs](/iam/serviceids){: external}** and click **Create**.

2. Enter a name and description for your service ID, then click **Create**.

3. From the service ID page, click **Assign access**.

4. Select **{{site.data.keyword.instructlab_short}}** as the service.

5. Within **Resources**, select **Specific resources** and choose your project. By doing so, you limit access to a specific project. 

6. Within **Roles and actions**, select the appropriate service access role:
   - Select **Writer** if you need to create chat completions.
   - Select **Reader** if you only need to read chat completions or view model information.

   Platform access roles are not required for API access.

7. (Optional) Add conditions such as time-based access to further scope the service ID access.

8. Review the access summary and click **Assign**.

### Create an API key
{: #create-api-key}

Now that your service ID has access to your {{site.data.keyword.instructlab_short}} project, create a service ID API key to use in your API calls. 

1. From the service ID page, click **API keys**.

2. Click **Create** and enter a name for your API key. 

3. For leaked key handling, select **Disable the leaked key** to automatically disable the key if it's detected as leaked.

4. Set an expiration date for the key. Regular key rotation is recommended for security.

5. Click **Create**.

6. Copy the API key and save it in a secure location. The key cannot be viewed again.

You can now use that API key to authenticate your requests. In the next step, you'll use this key in the `Authorization: Bearer` header of your API calls.

## Explore available models
{: #explore-models}
{: step}

Different foundation models have different strengths, so it's important to review the models that are available in your project.

Make the following API call to list all the available models. Replace `{project_id}` with your project ID and `{api_key}` with your service ID API key:



```bash
curl -L 'https://us-east.rhai.ibm.com/v1/projects/{project_id}/inference/models' \
  -H 'Accept: application/json' \
  -H "Authorization: Bearer {api_key}"
```
{: codeblock}
{: curl}

```python
from openai import OpenAI
client = OpenAI(
  api_key="{api_key}",
  base_url="https://us-east.rhai.ibm.com/v1/projects/{project_id}/inference",
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

Make the following API call, replacing `{project_id}` with your project ID and `{api_key}` with your service ID API key:



```bash
curl https://us-east.rhai.ibm.com/v1/projects/{project_id}/inference/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer {api_key}" \
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
  api_key="{api_key}",
  base_url="https://us-east.rhai.ibm.com/v1/projects/{project_id}/inference",
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
:   The request went to your project's inferencing endpoint, which handles routing to the appropriate model.

You can customize the model's behavior by adjusting the system prompt, adding more messages, or using different models for different use cases.
{: tip}

## Next steps
{: #next-steps}

You've successfully started using inferencing with Red Hat AI on {{site.data.keyword.cloud_notm}}. Here's what you can do next:

### Continue with inferencing
{: #continue-inferencing}

* [Learn more about inferencing](/docs/inference?topic=inference-inference) to discover advanced features like streaming responses, adjusting model parameters, and managing conversation history.

* Explore the [OpenAI Chat Completion API](https://platform.openai.com/docs/api-reference/chat){: external} and [OGX API](https://ogx-ai.github.io/docs/api/openai-chat-completion-v-1-chat-completions-post){: external} documentation for complete API reference.

* Integrate inferencing into your applications using the Python SDK or other programming languages.

### Customize models with your data
{: #customize-models}

Ready to go beyond general-purpose models? You can customize foundation models with your organization's specific knowledge and skills through model alignment:

1. [Prepare a taxonomy](/docs/inference?topic=inference-taxonomy-prep) containing your business knowledge and skills.

1. [Generate synthetic data](/docs/inference?topic=inference-data-generate) from your taxonomy.

1. [Train a custom model](/docs/inference?topic=inference-model-train) aligned with your specific needs.


By doing so, you can fine-tune models so they understand your business context, terminology, and requirements, which goes beyond what the general-purpose models can provide. 
