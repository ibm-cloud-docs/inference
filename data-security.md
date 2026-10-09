---

copyright:
  years: 2025, 2026
lastupdated: "2026-10-09"

keywords: data, secure, encrypt, cos, bucket, storage

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}

# Securing your data in {{site.data.keyword.short_name}}
{: #mng-data}

To ensure that you can securely manage your data when you use {{site.data.keyword.instructlab_short}}, it is important to know exactly what data is stored and encrypted and how you can delete any stored data.
{: shortdesc}

## How your data is stored and encrypted in {{site.data.keyword.instructlab_short}}
{: #data-storage}

Chat completion responses are stored so you can retrieve them. You have full control over this data and can delete it as needed.

## Deleting your data in {{site.data.keyword.instructlab_short}}
{: #data-delete}

You can delete individual chat completions. If you delete a {{site.data.keyword.instructlab_short}} project or the instance, all chat completions are deleted as well.

## Removing access to {{site.data.keyword.instructlab_short}}
{: #data-access-remove}

Access to {{site.data.keyword.instructlab_short}} service instances for users in your account is controlled by {{site.data.keyword.iamlong}} (IAM). Every user that accesses the {{site.data.keyword.instructlab_short}} service in your account must be assigned an access policy with an IAM role, which determines what actions a user can perform within the context of the service or specific instance that you select. To remove a user's access policy, see [Removing access by using the CLI](/docs/iam?topic=iam-assign-access-resources&interface=cli#removing-access-cli) or [Removing access in the console](/docs/iam?topic=iam-assign-access-resources&interface=ui#removing-access-console).
