---

copyright:
  years: 2025, 2026
lastupdated: "2026-10-13"

keywords: instructlab, ai, inference, authentication, bearer token, api key

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}


# Authenticating to the API
{: #inf-auth}

Before you can make API calls to the {{site.data.keyword.instructlab_short}} service, you need to authenticate your requests. You can authenticate by using either a bearer token or an {{site.data.keyword.cloud_notm}} API key.
{: shortdesc}

## Before you begin
{: #inf-auth-prereqs}

* Create a Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. For more information or to upgrade your account, see [Account types](/docs/account?topic=account-accounts#compare).

* Create [a {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).

* Make sure that you have the Writer role or greater on the {{site.data.keyword.instructlab_short}} service. For more information, see [Managing IAM access](/docs/inference?topic=inference-iam&interface=ui).

## Authenticating by using a bearer token
{: #inf-auth-token}

Bearer tokens ensure secure access to your project's inference capabilities and are generated from your {{site.data.keyword.cloud_notm}} API key. Bearer tokens expire after a set period, so they must be refreshed periodically.

The following example shows how to retrieve a bearer token.

```bash
curl -X POST "https://iam.cloud.ibm.com/identity/token" --header "Content-Type: application/x-www-form-urlencoded" --header "Accept: application/json" --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" --data-urlencode "apikey=$<IBM_CLOUD_API_KEY>"
```
{: pre}

The bearer token is the `access_token` in the response. These tokens have an expiration date and must be periodically refreshed.

```bash
{"access_token":"xxxxx","refresh_token":"not_supported","token_type":"Bearer","expires_in":3600,"expiration":1770058324,"scope":"ibm openid"}
```
{: screen}

## Authenticating by using an API key
{: #inf-auth-apikey}

You can authenticate with an API key by using either a service ID API key or a user API key.

Using a [service ID](/docs/iam?topic=iam-serviceids&interface=ui) is the recommended method to manage and delegate access permissions. After you create a service ID, [create a service ID API key](/docs/iam?topic=iam-serviceidapikeys&interface=ui) to authenticate your requests. For details on creating a service ID and an API key within your project, see [Getting started with {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-getting-started#authenticate).

When you create the service ID in IAM, assign the Writer service access role to create chat completions. Assign the Reader service access role if you need only to view model information or read chat completions. Platform access roles are not required for API access.
{: tip}

Alternatively, you can authenticate by using a personal user API key. For more information, see [Managing user API keys](/docs/iam?topic=iam-userapikey&interface=ui).
