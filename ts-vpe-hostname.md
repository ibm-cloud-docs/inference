---

copyright:
  years: 2026
lastupdated: "2026-10-30"

keywords: vpe, virtual private endpoint, hostname, dig, endpoint gateway, private endpoint, resolve

subcollection: inference

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Why doesn't the private hostname resolve to my endpoint gateway?
{: #troubleshoot-vpe-hostname}
{: troubleshoot}
{: support}

You run the `dig` command against the {{site.data.keyword.instructlab_short}} private hostname, but the address it returns does not match the reserved IP address of your endpoint gateway.
{: shortdesc}

The `dig` command returns no address, returns a public IP address, or returns an address that does not match the reserved IP address of your endpoint gateway.
{: tsSymptoms}

The hostname resolves to the endpoint gateway only from within a VPC that has an endpoint gateway for {{site.data.keyword.instructlab_short}}. The issue is caused by one of the following conditions:

- You ran the `dig` command from outside the VPC, for example, from your local workstation.
- The endpoint gateway is in a different VPC than the resource you are running the command from.
- The endpoint gateway is in a different region than the `us-east` region.
- No endpoint gateway for {{site.data.keyword.instructlab_short}} exists in the VPC.
{: tsCauses}

Complete the following steps:

1. Make sure that you run the `dig` command from a resource inside the VPC, such as a virtual server instance, not from your local workstation or another network.
1. Confirm that the endpoint gateway is in the same VPC as the resource you are running the command from.
1. Confirm that the endpoint gateway is in the `us-east` region.
1. If no endpoint gateway for {{site.data.keyword.instructlab_short}} exists in the VPC, create one. For more information, see [Configuring an endpoint gateway](/docs/inference?topic=inference-vpe-connection#vpe-setup).
{: tsResolve}
