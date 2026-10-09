---

copyright:
  years: 2025, 2026
lastupdated: "2026-10-09"

keywords: red hat ai, inference, model alignment, faq

subcollection: inference

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}


# FAQ about billing for {{site.data.keyword.instructlab_short}}
{: #faq-b}


Frequently asked questions about billing for {{site.data.keyword.instructlab_short}} might include questions about how cost is calculated. To find all of the FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs).
{: shortdesc}

## How is cost calculated in {{site.data.keyword.product_name}}?
{: #costs-ilab}
{: faq}

The cost from {{site.data.keyword.product_name}} usage is based on metrics that are measured in tokens. Each token corresponds to a specific amount of computational power that is required for the processing tasks. The total number of tokens consumed directly influences the scale of inference. This metric serves as a basis for our billing system, enabling users to monitor and control their costs according to the computational resources used.

Inference with a model
:   Inference costs are calculated separately for input and output tokens on a per-model basis. Input tokens represent your prompt or query sent to the model, while output tokens represent the model's generated response. Each model has its own pricing structure based on its size and computational requirements.




## Are failed operations billed?
{: #costs-operations}
{: faq}

Failed operations are not billed. Successful operations and user canceled operations are billed, though user canceled operations are prorated based on the processing that completed.
