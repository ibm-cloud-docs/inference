---

copyright:
  years: 2025, 2026
lastupdated: "2026-07-09"

keywords: taxonomy, troubleshooting

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}

# `Failed to retrieve taxonomy from COS` error during data generation in {{site.data.keyword.short_name}}
{: #ts-taxonomy-retrieve}

{{site.data.keyword.instructlab_short}} model alignment, synthetic data generation, and taxonomy management features are deprecated and will be removed on 25 September 2026. To continue model customization and alignment workflows, migrate to {{site.data.keyword.redhat_openshift_full}} AI On OpenShift. [Learn more about {{site.data.keyword.redhat_openshift_full}} AI](/docs/openshift?topic=openshift-ai-addon-about){: external}.
{: deprecated}

When you try to generate data, you get the following error.
{: tsSymptoms}

```txt
Failed to retrieve taxonomy from COS.
```
{: screen}


The taxonomy `tar.gz` file could not be downloaded from {{site.data.keyword.cos_short}}.
{: tsCauses}


Verify that the taxonomy `tar.gz` exists in the specified {{site.data.keyword.cos_short}} bucket and that the {{site.data.keyword.cos_short}} authorization policy is still active.
{: tsResolve}
