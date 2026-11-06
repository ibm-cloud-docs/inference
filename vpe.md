---

copyright:
  years: 2026
lastupdated: "2026-11-06"

keywords: ai, vpe, virtual private endpoint, private endpoint, endpoint gateway, VPC, private network

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}


# Using virtual private endpoints for VPC to privately connect to {{site.data.keyword.instructlab_short}}
{: #vpe-connection}

Send inference requests from your Virtual Private Cloud (VPC) to {{site.data.keyword.instructlab_short}} over the {{site.data.keyword.cloud_notm}} private network, so that your request traffic does not cross the public internet.
{: shortdesc}

{{site.data.keyword.cloud}} Virtual Private Endpoints (VPE) for VPC enable you to connect to {{site.data.keyword.instructlab_short}} from your VPC network by using a reserved IP address that is allocated from a subnet in your VPC. The IP address is bound to an endpoint gateway. The endpoint gateway is a virtualized function that scales horizontally, is redundant and highly available, and spans all availability zones of your VPC. Virtual server instances and other workloads in your VPC then call {{site.data.keyword.instructlab_short}} through a private hostname. For more information about endpoint gateways, see [About virtual private endpoint gateways](/docs/vpc?topic=vpc-about-vpe).

## Before you begin
{: #vpe-prereqs}

Before you set up a virtual private endpoint for {{site.data.keyword.instructlab_short}}, make sure that you have the following items.

* A Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account. Trial accounts are not supported. To upgrade your account, see [Upgrading your account](/docs/account?topic=account-upgrading-account).

* [A {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project).
* [The Writer role or greater](/docs/inference?topic=inference-iam&interface=ui) on the {{site.data.keyword.instructlab_short}} service.
* A VPC in the Washington DC (`us-east`) region. For more information, see [Getting started with VPC](/docs/vpc?topic=vpc-getting-started).
* A [plan for your virtual private endpoints](/docs/vpc?topic=vpc-vpe-planning-considerations), including the subnets and reserved IP addresses that you want to use.
* A way to [authenticate your requests](/docs/inference?topic=inference-inf-auth). Authentication is the same as for the public endpoint.
* Ensure that [correct access controls](/docs/vpc?topic=vpc-configure-acls-sgs-endpoint-gateways) are set for your virtual private endpoint.
* Understand how to [view details](/docs/vpc?topic=vpc-vpe-viewing-details-of-an-endpoint-gateway) about a virtual private endpoint.

## Private endpoint hostname and CRN
{: #vpe-endpoint-details}

When you use the private endpoint, send your API requests to the private hostname instead of the public hostname. The private hostname is not reachable from the public internet. It resolves to the reserved IP address of your endpoint gateway only from within a VPC that has an endpoint gateway for {{site.data.keyword.instructlab_short}}.

If you create the endpoint gateway by using the CLI or API, you must specify the [Cloud Resource Name (CRN)](/docs/account?topic=account-crn) of the {{site.data.keyword.instructlab_short}} endpoint. The following table lists the private hostname and CRN for the supported region.



| Region | Private hostname | CRN |
|--------|------------------|---------------------------|
| `us-east` | `private.us-east.rhai.ibm.com` | `crn:v1:bluemix:public:instructlab:us-east:::endpoint:private.us-east.rhai.ibm.com` |
{: caption="Region, private hostname, and CRN for connecting to {{site.data.keyword.instructlab_short}} over the private network" caption-side="bottom"}



## Configuring an endpoint gateway
{: #vpe-setup}

Create an endpoint gateway for {{site.data.keyword.instructlab_short}} in the VPC that runs the workloads that call the service.

You must create the endpoint gateway before you call the private hostname from your VPC. Without an endpoint gateway, requests from your VPC do not use the virtual private endpoint path.
{: important}

1. [Create an endpoint gateway](/docs/vpc?topic=vpc-ordering-endpoint-gateway) in your `us-east` VPC. For the target service, select **{{site.data.keyword.instructlab_short}}**. If you create the endpoint gateway by using the CLI or API, specify the CRN from the previous table.

1. [Bind a reserved IP address](/docs/vpc?topic=vpc-bind-unbind-reserved-ip) to the endpoint gateway.

1. View the details of the endpoint gateway to confirm that it is available. For more information, see [Viewing details of an endpoint gateway](/docs/vpc?topic=vpc-vpe-viewing-details-of-an-endpoint-gateway).

After the endpoint gateway is available, workloads in the VPC can call {{site.data.keyword.instructlab_short}} through the private hostname.

## Verifying the private connection
{: #vpe-verify}

To confirm that your VPC reaches {{site.data.keyword.instructlab_short}} over the private network, complete the following steps from a virtual server instance in the VPC.

1. Resolve the private hostname.

   

   ```sh
   dig private.us-east.rhai.ibm.com
   ```
   {: pre}

   

   The hostname must resolve to the reserved IP address of your endpoint gateway. If it resolves to a different address, see [Why doesn't the private hostname resolve to my endpoint gateway?](/docs/inference?topic=inference-troubleshoot-vpe-hostname).

1. Send a request to the private endpoint. For example, list the models in your project. Replace `<project_id>` with your project ID and `<bearer_token>` with a valid bearer token. For more information, see [Authenticating to the API](/docs/inference?topic=inference-inf-auth).

   

   ```sh
   curl -L 'https://private.us-east.rhai.ibm.com/v1/projects/<project_id>/inference/models' \
   -H 'Accept: application/json' -H "Authorization: Bearer <bearer_token>"
   ```
   {: pre}

   

   A successful request returns the list of models that are available in your project.

## Using the private endpoint
{: #vpe-using}

The private endpoint serves the same API as the public endpoint. The request paths, request bodies, and authentication are the same. Only the hostname is different. To use the private endpoint with your applications, replace the public hostname with the private hostname in your base URL.



```text
https://private.us-east.rhai.ibm.com/v1/projects/<project_id>/inference
```
{: codeblock}



The following example shows how to set the private base URL when you use the OpenAI Python client.



```python
from openai import OpenAI
client = OpenAI(
  api_key="<bearer_token>",
  base_url="https://private.us-east.rhai.ibm.com/v1/projects/<project_id>/inference",
)

models = client.models.list()
print(models)
```
{: codeblock}



For more examples of working with the API, see [Working with chat completions](/docs/inference?topic=inference-inf-chat-completions) and [Creating embeddings](/docs/inference?topic=inference-inf-create-embeddings).

## Troubleshooting the private connection
{: #vpe-troubleshooting}

If your requests to the private endpoint fail, see the following troubleshooting topics.

- [Why doesn't the private hostname resolve to my endpoint gateway?](/docs/inference?topic=inference-troubleshoot-vpe-hostname)
- [Why do my requests to the private endpoint time out or get refused?](/docs/inference?topic=inference-troubleshoot-vpe-requests)
