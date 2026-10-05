---

copyright:
  years: 2025, 2026
lastupdated: "2026-10-05"

keywords: instructlab, ai, inference, models, list models

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}


# Listing models
{: #inf-list-models}

Discover which foundation models are accessible in your project and understand their capabilities, so you can use the best model for your specific use case and optimize for factors like response quality, speed, or cost.
{: shortdesc}

## Before you begin
{: #inf-list-models-prereqs-ui}
{: ui}

* Create a Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* Create [a {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).

* Make sure that you have the Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access](/docs/inference?topic=inference-iam&interface=ui).

## Before you begin
{: #inf-list-models-prereqs-api}
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

   

   Replace `<project_id>` with your project ID. To find it, go to [{{site.data.keyword.instructlab_short}} projects](/instructlab/projects) and open your project.

## Listing models by using the console
{: #inf-list-models-ui}
{: ui}

The console provides an interactive playground where you can experiment with different models, test prompts, and refine your AI interactions before integrating them into your applications.

The playground does not support embeddings. Use the API to [create embeddings](/docs/inference?topic=inference-inf-create-embeddings).
{: note}

1. In the console, open the [{{site.data.keyword.instructlab_short}} service](/inference/overview){: external}.
1. Click **Model catalog** to explore the available models.

## Listing models by using the API
{: #inf-list-models-api}
{: api}

The following example shows how to list models. For a complete list of the available parameters, see [OpenAI List Models](https://developers.openai.com/api/reference/resources/models/methods/list){: external}.



```bash
curl -L 'https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/models' \
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

models = client.models.list()
print(models)
```
{: codeblock}
{: python}



If `supports_embeddings` is `true` in the model response, the model can be used to create embeddings.
{: note}

## Getting a model by ID by using the API
{: #inf-get-model}
{: api}

Retrieving detailed information about a specific model helps you understand its characteristics, capabilities, and limitations before using it in your application.

The following example shows how to get a model by ID. For a complete list of the available parameters, see [Retrieve Model](https://developers.openai.com/api/reference/resources/models/methods/retrieve){: external}.



```bash
curl -L 'https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference/models/<model>' \
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

model = client.models.retrieve("<model>")  # for example, "granite-4-0-h-small"
print(model)
```
{: codeblock}
{: python}




If `supports_embeddings` is `true` in the model response, the model can be used to create embeddings.
{: note}
