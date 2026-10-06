---

copyright:
  years: 2025, 2026
lastupdated: "2026-10-05"

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

There are two ways to authenticate with an API key: You can [create a service ID](/docs/iam?topic=iam-serviceids&interface=ui), which is the recommended way to distribute access and controls. If you create a service ID, you need to [create a service ID API key](/docs/iam?topic=iam-serviceidapikeys&interface=ui) as well, which you use to authenticate. [Getting started with {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-getting-started#authenticate) explains how to create a service ID and an API key to authenticate programmatically.

You can also authenticate by using a user API key, as opposed to a service ID API key. For more information, see [Managing user API keys](/docs/iam?topic=iam-userapikey&interface=ui).
