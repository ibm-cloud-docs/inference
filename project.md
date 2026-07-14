---

copyright:
  years: 2025, 2026
lastupdated: "2026-07-09"

keywords: instructlab, ai, project

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}


# Creating projects for {{site.data.keyword.short_name}}
{: #project}

Complete the following steps to create an {{site.data.keyword.short_name}} project.
{: shortdesc}

## Creating projects in the console for {{site.data.keyword.short_name}}
{: #project-create-ui}
{: ui}

1. Navigate to [{{site.data.keyword.short_name}} in the console](https://cloud.ibm.com/instructlab/overview)

1. Review the pricing plan.

1. In the **Configure resource** section, enter the following details.

    Service name
    :   Give your {{site.data.keyword.instructlab_short}} project a name.

    Select a resource group
    :   Select the resource group where you want to create your project.

    Tags and Access management tags
    :   Enter any tags or access management tags that you want to use. Tags can help you organize your resources.

1. Accept the license agreement and click **Create**.

After your project is created, the project details page is shown.



## Creating projects from the CLI for {{site.data.keyword.short_name}}
{: #project-create-cli}
{: cli}

To log in:
{{_include-segments/login.md}}

To create a project, run the following command.

```sh
ibmcloud resource service-instance-create <project_name> instructlab instructlab-pricing-plan us-east
```
{: pre}


## What's next?
{: #whats-next-projects}

After creating your project, you can run inference with models or proceed with model alignment. Either way, you can [assign users in your account access to your project](/docs/inference?topic=inference-project) so they can collaborate on the project as well.

For more information about running inference, see [inference a model](/docs/inference?topic=inference-inference).

[Deprecated]{: tag-deprecated} If you're interested in model alignment, make sure to [create an {{site.data.keyword.cos_short}} instance](/docs/inference?topic=inference-storage&interface=ui). Then, you can [learn how taxonomies are structured](/docs/inference?topic=inference-taxonomy-overview), and, when you're ready, you can [prepare your taxonomy and upload it to {{site.data.keyword.cos_short}}](/docs/inference?topic=inference-taxonomy-prep).
