---

copyright:
  years: 2025, 2026
lastupdated: "2026-07-24"

keywords: instructlab, ai, project

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}


# Creating storage locations for {{site.data.keyword.short_name}}
{: #storage}

Complete the following steps to create one or more {{site.data.keyword.cos_short}} buckets to store {{site.data.keyword.short_name}} resources in.
{: shortdesc}

{{site.data.keyword.instructlab_short}} model alignment, synthetic data generation, and taxonomy management features are deprecated and will be removed on 25 September 2026. To continue model customization and alignment workflows, migrate to {{site.data.keyword.redhat_openshift_full}} AI On OpenShift. [Learn more about {{site.data.keyword.redhat_openshift_full}} AI](/docs/openshift?topic=openshift-ai-addon-about){: external}.
{: deprecated}

{{site.data.keyword.cos_short}} buckets are only required if you want to fine-tune or align models with your own data. If you use the inference feature with pre-trained models, you do not need to create a bucket.
{: important}

[Learn more about {{site.data.keyword.cos_short}}](/docs/cloud-object-storage?topic=cloud-object-storage-about-cloud-object-storage).

## Creating an {{site.data.keyword.cos_short}} instance in the console for {{site.data.keyword.short_name}}
{: #storage-ui}
{: ui}


1. Navigate to the [{{site.data.keyword.cos_short}} in the console](https://cloud.ibm.com/objectstorage/overview).
1. Click **Create an instance**.
1. Choose a plan.
1. Give your instance a name, select a resource group, and enter any tags that you want to use.
1. Click **Create**.


## Creating an {{site.data.keyword.cos_short}} instance and bucket by using the CLI for {{site.data.keyword.short_name}}
{: #storage-cli}
{: cli}

To log in:
{{_include-segments/login.md}}

To create {{site.data.keyword.cos_short}} resources:
1. Run the following command to create an instance.
    ```sh
    ibmcloud resource service-instance-create <instance-name> cloud-object-storage <plan> global
    ```
    {: pre}

1. [Create a new bucket](/docs/cloud-object-storage?topic=cloud-object-storage-ic-cos-cli#create-a-new-bucket) and make a note of the bucket name for later.
    ```sh
    ibmcloud cos bucket-create --bucket BUCKET-NAME [--class CLASS-NAME] [--ibm-service-instance-id INSTANCE-ID] [--region REGION] [--output FORMAT]
    ```
    {: pre}


## What's next?
{: #whats-next-storage}

After creating your project, review the following links for next steps.


- [Assign users in your account access to your project and {{site.data.keyword.cos_short}}](/docs/inference?topic=inference-project).
- [Learn how taxonomies are structured](/docs/inference?topic=inference-taxonomy-overview).
- [Prepare your taxonomy and upload it to {{site.data.keyword.cos_short}}](/docs/inference?topic=inference-taxonomy-prep).
