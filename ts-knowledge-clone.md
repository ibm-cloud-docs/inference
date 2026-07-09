---

copyright:
  years: 2025, 2026
lastupdated: "2026-07-09"

keywords: knowledge documents, clone, taxonomy, troubleshooting

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}

# `Failed to clone knowledge document repository` error during data generation in {{site.data.keyword.short_name}}
{: #ts-knowledge-clone}

{{site.data.keyword.instructlab_short}} model alignment, synthetic data generation, and taxonomy management features are deprecated and will be removed on 25 September 2026. To continue model customization and alignment workflows, migrate to {{site.data.keyword.redhat_openshift_full}} AI On OpenShift. [Learn more about {{site.data.keyword.redhat_openshift_full}} AI](/docs/openshift?topic=openshift-ai-addon-about){: external}.
{: deprecated}

When you try to generate data, you get the following error.
{: tsSymptoms}

```txt
Failed to clone knowledge document repository.  See detailed logs in COS.
```
{: screen}


The repository (`repo`) specified in the QNA was not accessible.
{: tsCauses}

When a taxonomy is uploaded, the file structure is validated. During data generation, additional validation is done to verify the content of the taxonomy.


Fix issues with the knowledge QNA files.
{: tsResolve}

1. In the `document` section, verify that the `repo` value is valid.
    ```yaml
    document:
    repo: https://github.com/<organization>/<repository>
    commit: <commit_sha>
    patterns:
        - <folder>/<filename>.md
    ```
    {: codeblock}

2. Ensure the repo exists already.

3. Ensure that valid authorization was granted in the repository.
