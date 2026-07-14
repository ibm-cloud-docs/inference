---

copyright:
  years: 2025, 2026
lastupdated: "2026-07-09"

keywords: taxonomy, troubleshooting

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}

# `Failed to process invalid taxonomy files` error during data generation in {{site.data.keyword.short_name}}
{: #ts-taxonomy-invalid}

{{site.data.keyword.instructlab_short}} model alignment, synthetic data generation, and taxonomy management features are deprecated and will be removed on 25 September 2026. To continue model customization and alignment workflows, migrate to {{site.data.keyword.redhat_openshift_full}} AI On OpenShift. [Learn more about {{site.data.keyword.redhat_openshift_full}} AI](/docs/openshift?topic=openshift-ai-addon-about){: external}.
{: deprecated}

When you try to generate data, you get the following error.
{: tsSymptoms}

```txt
Failed to process invalid taxonomy files.  See detailed logs in COS.
```
{: screen}


The taxonomy was in invalid format.
{: tsCauses}

When a taxonomy is uploaded, the file structure is validated. During data generation, additional validation is done to verify the content of the taxonomy.


Fix issues with the taxonomy.
{: tsResolve}

1. In the {{site.data.keyword.cos_short}} log files, look for errors.

    Example:
    ```txt
    ERROR 2025-04-16 12:47:57,890 instructlab.schema.taxonomy:131: taxonomy-small/knowledge/opensource/instructlab/qna.yaml:14:27 trailing spaces (trailing-spaces)
    ERROR 2025-04-16 12:47:57,890 instructlab.schema.taxonomy:131: taxonomy-small/knowledge/opensource/instructlab/qna.yaml:15:20 trailing spaces (trailing-spaces)
    ```
    {: screen}

1. Fix the errors locally.

1. Run the `ilab` validation command.

    ```sh
    ilab taxonomy diff
    ```
    {: pre}

1. [Upload the taxonomy updates](/docs/inference?topic=inference-getting-started&interface=ui#taxonomy-add-ui) to {{site.data.keyword.cos_short}}.

1. Run the [data generation](/docs/inference?topic=inference-data-generate) again.
