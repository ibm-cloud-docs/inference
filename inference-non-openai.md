---

copyright:
  years: 2025, 2026
lastupdated: "2026-07-31"

keywords: litellm, openai, api translation, proxy

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}


# Setting up a model gateway with LiteLLM proxy
{: #model-gateway}

You can use LiteLLM proxy to set up a model gateway in front of {{site.data.keyword.instructlab_short}}. A model gateway gives you a single entry point for managing API requests to your models, so you can route traffic to the model that best fits your needs, fall back to another model if one is unavailable, or connect tools that don't natively support the OpenAI-compatible API.
{: shortdesc}

[LiteLLM proxy](https://docs.litellm.ai/docs/simple_proxy){: external} is an open source LLM gateway. It runs as a local proxy server that sits between your clients and {{site.data.keyword.instructlab_short}}, and supports load balancing, model fallback, and API format translation. When you configure LiteLLM proxy, all requests are forwarded to {{site.data.keyword.instructlab_short}} by using the OpenAI-compatible format that the service expects.

## Before you begin
{: #inference-non-openai-prereqs}

Before you can set up a model gateway with LiteLLM proxy, make sure that you complete the following steps:

* Create a Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* Create [a {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project){: external}.

* Find your project ID. Go to [{{site.data.keyword.instructlab_short}} projects](/instructlab/projects){: external} and open the project.

* Make sure that you have the Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access](/docs/inference?topic=inference-iam&interface=ui).

* Create a [service ID API key](/docs/inference?topic=inference-getting-started&interface=api#create-service-id) to authenticate your requests. For other authentication options, see [authenticating to the API](/docs/inference?topic=inference-inference&interface=api#inf-chat-auth).

* Install `uv`, a Python package manager. For example, on macOS you can install it with Homebrew:

    ```sh
    brew install uv
    ```
    {: pre}

## Installing and configuring LiteLLM proxy
{: #inference-non-openai-litellm}

Install LiteLLM proxy, create a directory to store your configuration file, and create the configuration file to list the models you want to use. Complete the following steps:

1. Install LiteLLM proxy.

    ```sh
    uv tool install 'litellm[proxy]'
    ```
    {: pre}

1. Create a directory to store your configuration file.

    ```sh
    mkdir litellm-proxy && cd litellm-proxy
    ```
    {: pre}

1. In that directory, create a file named `config.yaml`. In the file, list each {{site.data.keyword.instructlab_short}} model that you want to make available through the proxy. Use the `custom_openai/` prefix in the `model` field and set `drop_params: true` so that unsupported parameters do not cause errors. 

    Replace `<project_id>` and `<api_key>` with your project ID and API key.

    ```yaml
    model_list:
      - model_name: granite-4-0-h-small
        litellm_params:
          model: custom_openai/granite-4-0-h-small
          api_base: https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference
          api_key: <api_key>
          drop_params: true

      - model_name: llama-3-3-70b-instruct
        litellm_params:
          model: custom_openai/llama-3-3-70b-instruct
          api_base: https://us-east.rhai.ibm.com/v1/projects/<project_id>/inference
          api_key: <api_key>
          drop_params: true
    ```
    {: codeblock}



    Add or remove model entries as needed. For a full list of available models, see the model catalog in the [{{site.data.keyword.instructlab_short}} service](/inference/overview){: external}.

    The `POST /v1/chat/completions` endpoint is used for all requests. The `custom_openai` provider prefix instructs LiteLLM to treat the target as a generic OpenAI-compatible API, which is what {{site.data.keyword.instructlab_short}} provides.
    {: note}

## Starting LiteLLM proxy
{: #inference-non-openai-start}

Start LiteLLM proxy by using your configuration file. Use the `--host` option to restrict connections to localhost only, which prevents external access to the proxy.

```sh
litellm --config config.yaml --host 127.0.0.1
```
{: pre}

When the proxy starts successfully, you see output similar to the following.

```text
LiteLLM: Proxy initialized with Config, Set models:
    granite-4-0-h-small
    llama-3-3-70b-instruct
INFO:     Uvicorn running on http://127.0.0.1:4000 (Press CTRL+C to quit)
```
{: screen}

The proxy is now running at `http://localhost:4000` and is ready to accept requests.

## Connecting your client to LiteLLM proxy
{: #inference-non-openai-connect}

Configure your AI client to point to the local LiteLLM proxy instead of its default API endpoint. The configuration steps depend on your specific client, but typically involve setting two values:

* API base URL: `http://localhost:4000`
* API key: any non-empty string (LiteLLM does not validate this value; authentication is handled by the credentials in your `config.yaml`)

For example, to verify that the proxy is working before connecting your client, you can send a test request with curl.

```sh
curl -sX POST http://localhost:4000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer no-key" \
  -d '{
    "model": "granite-4-0-h-small",
    "messages": [
      { "role": "user", "content": "Hello!" }
    ]
  }'
```
{: pre}

Refer to your client's documentation for instructions on setting a custom API endpoint.
