---

copyright:
  years: 2026
lastupdated: "2026-11-11"

keywords: vpe, virtual private endpoint, requests time out, connection refused, security group, network ACL, endpoint gateway

subcollection: inference

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Why do my requests to the private endpoint time out or get refused?
{: #troubleshoot-vpe-requests}
{: troubleshoot}
{: support}

Requests that you send to the {{site.data.keyword.instructlab_short}} private endpoint time out or are refused with a connection error.
{: shortdesc}

Requests to the private hostname either hang and eventually time out, or they return a connection refused error immediately.
{: tsSymptoms}

Security groups or network access control lists (ACLs) are blocking traffic between your workload and the reserved IP address of the endpoint gateway.
{: tsCauses}

Make sure that the security groups and network ACLs for the resources in your VPC allow traffic between your workload and the reserved IP address of the endpoint gateway. For more information, see [Configuring ACLs and security groups for use with endpoint gateways](/docs/vpc?topic=vpc-configure-acls-sgs-endpoint-gateways).
{: tsResolve}
