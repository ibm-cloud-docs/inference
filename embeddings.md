---

copyright:
  years: 2025, 2026
lastupdated: "2026-08-04"

keywords: ai, embeddings, text embeddings

subcollection: inference

content-type: tutorial

services: {{site.data.keyword.subcollection}}
account-plan: paid
completion-time: 15m

---

{{site.data.keyword.attribute-definition-list}}

# Creating text embeddings with {{site.data.keyword.instructlab_short}}
{: #embeddings}
{: toc-content-type="tutorial"}
{: toc-services="{{site.data.keyword.subcollection}}"}
{: toc-completion-time="15m"}

Learn how to use the {{site.data.keyword.instructlab_full_notm}} API to generate text embeddings. In this tutorial, you'll create embeddings that represent three text inputs in just 15 minutes.
{: shortdesc}

Text embeddings are numerical representations of text that capture semantic meaning. You can use them to power search, clustering, classification, and retrieval-augmented generation (RAG) workflows.

## Objectives
{: #embeddings-objectives}

In this tutorial, you'll complete the following tasks:

* Authenticate to the API by using a service ID and API key.
* Export your API key as an environment variable.
* Call the embeddings API to generate vector representations of three text inputs.

## Before you begin
{: #embeddings-prereqs}

Make sure you have the following:

* A Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* [A {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).

* The Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access](/docs/inference?topic=inference-iam&interface=ui).

## Set up API authentication
{: #embeddings-auth}
{: step}

Before you can call the embeddings API, you need to authenticate your requests using a service ID and API key. If you already completed [the getting started tutorial](/docs/inference?topic=inference-getting-started), you can reuse the service ID and API key you created there and skip to [Export your API key](#embeddings-export-key).

### Create a service ID and assign access
{: #embeddings-create-service-id}

A service ID is a useful way to control and distribute access to {{site.data.keyword.instructlab_short}} projects. Create the service ID, then assign it access to your project.

1. In the {{site.data.keyword.cloud_notm}} console, go to **Manage** > **Access (IAM)** > **[Service IDs](/iam/serviceids){: external}** and click **Create**.

1. Enter a name and description for your service ID, then click **Create**.

1. From the service ID page, click **Assign access**.

1. Select **{{site.data.keyword.instructlab_short}}** as the service.

1. Within **Resources**, select **Specific resources** and choose your project. By doing so, you limit access to a specific project.

1. Within **Roles and actions**, select **Writer** as the service access role.

   Platform access roles are not required for API access.

1. (Optional) Add conditions such as time-based access to further scope the service ID access.

1. Review the access summary and click **Assign**.

### Create an API key
{: #embeddings-create-api-key}

Now that your service ID has access to your {{site.data.keyword.instructlab_short}} project, create a service ID API key to use in your API calls.

1. From the service ID page, click **API keys**.

1. Click **Create** and enter a name for your API key.

1. For leaked key handling, select **Disable the leaked key** to automatically disable the key if it's detected as leaked.

1. Set an expiration date for the key. Regular key rotation is recommended for security.

1. Click **Create**.

1. Copy the API key and save it in a secure location. The key cannot be viewed again.

## Export your API key
{: #embeddings-export-key}
{: step}

Save your API key as an environment variable so you can reference it in the next step without hardcoding it in your command.

Run the following command on macOS or Linux, replacing `<your_api_key>` with the API key you created:

```sh
export IBM_CLOUD_API_KEY="<your_api_key>"
```
{: pre}

## Create text embeddings
{: #embeddings-create}
{: step}

Now you're ready to call the embeddings API. The following command sends three text inputs to the `granite-embedding-278m-multilingual` model and returns a vector representation for each one.

Replace `<project_id>` with your project ID. You can find your project ID in the {{site.data.keyword.instructlab_short}} [projects page](https://cloud.ibm.com/instructlab/projects){: external}.



```sh
curl https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/v1/embeddings \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $IBM_CLOUD_API_KEY" \
  -d '{
    "model": "granite-embedding-278m-multilingual",
    "input": [
      "Manage your projects from the IBM Cloud console.",
      "Use the API to automate workflows and integrate AI into your applications.",
      "IBM Cloud offers a range of AI and machine learning services for enterprise applications."
    ]
  }'
```
{: pre}



The API returns a JSON response containing an embedding array for each input. Each embedding is a list of floating-point numbers that encodes the semantic content of the corresponding text.

## Next steps
{: #embeddings-next-steps}

Now that you've generated your first text embeddings, here are some ways to continue:

* Explore the [Running inference](/docs/inference?topic=inference-inference) topic to learn about other inference capabilities, including chat completions.

* Integrate embeddings into a retrieval-augmented generation (RAG) pipeline to ground model responses in your own data.

* Try different input texts and compare the resulting vectors to understand how semantic similarity is captured.
