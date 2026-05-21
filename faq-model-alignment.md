---

copyright:
  years: 2025, 2026

lastupdated: "2026-05-21"

keywords: red hat ai, inference, model alignment, faq

subcollection: inference

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}

# FAQ about model alignment 
{: #faq-ma}

Frequently asked questions about model alignment might include questions about the training process or how to fine-tune foundation models. To find all FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs).
{: shortdesc}


## What is model alignment?
{: #faq-model-train}
{: faq}



Model alignment, also called model training, is the process of fine-tuning a foundation model with your specific knowledge and skills. The synthetic data generated from your taxonomy is used to train the model in two phases: knowledge tuning, which focuses on improving the model's foundational knowledge, and skills tuning, which trains the model on more specific capabilities required for its intended purpose.

## What are Granite models?
{: #granite}
{: faq}

Fit for purpose and open source, these enterprise-ready, multimodal models deliver exceptional performance against safety benchmarks and across a wide range of enterprise tasks from cybersecurity to RAG.

## What is a taxonomy?
{: #taxonomy-faq}
{: faq}

A taxonomy is a structured directory of human-curated data containing the knowledge and skills you want a model to learn. It is organized in a cascading structure where each sub-directory, or "branch", of the taxonomy "tree" ends with a "leaf node", which is a set of files that contain the relevant data. Taxonomies are used in the model alignment process to generate synthetic data for training. You can contribute to a taxonomy by adding an entirely new "branch", or by adding new data to an existing `qna.yaml` file. For more information on the taxonomy structure, see [How taxonomies are structured for {{site.data.keyword.short_name}}](/docs/inference?topic=inference-taxonomy-overview&interface=ui){: external}. You can also view the [taxonomy on GitHub](https://github.com/IBM-Cloud/redhat-ai-instructlab-taxonomy){: external}.

## What is synthetic data generation?
{: #faq-data-gen}
{: faq}

Synthetic data generation is the process of creating training data from your taxonomy. The information in the taxonomy is used to generate synthetic data that augments the human-provided knowledge and is used to fine-tune the model during the model alignment process. This synthetic data helps train the model more effectively while minimizing the risk of catastrophic forgetting.


## How does taxonomy validation work?
{: #faq-tax-validation}
{: faq}

When you upload a taxonomy to {{site.data.keyword.short_name}}, the checks are performed: 
- Validating the formatting and syntax of your `qna.yaml` files by using the `ilab diff` command.
- Attempting to clone the knowledge and skills documents that are referenced in your `qna.yaml` files.
- Checking that you have the correct service authorizations in place, such as for {{site.data.keyword.cos_short}} and {{site.data.keyword.secrets-manager_short}}.

<!--<qna:time>-->

## How long does data generation take?
{: #faq-time-data}
{: faq}

After queuing, data generation usually takes 2-6 hours to run. For an estimate, the general formula is to take the number of output tokens, divided by about 5000 tokens per second, divided by 60 seconds per minute, and divided by 60 minutes in an hour.

```txt
Tokens / 5000 / 60 / 60 = Number of hours
```
{: codeblock}

You can find general estimates in the console when you start the processes.

Factors that impact completion time:
- The contents of the knowledge documents
- The number of other jobs in the queue

## How long does model training take?
{: #faq-model}
{: faq}

For model training, the general formula is to take the number of output tokens, divided by about 4000 tokens per second, divided by 60 seconds per minute, and divided by 60 minutes in an hour.

```txt
Tokens / 4000 / 60 / 60 = Number of hours
```
{: codeblock}

You can find general estimates in the console when you start the processes.

Factors that impact completion time:
- The contents of the knowledge documents
- The number of other jobs in the queue

<!--</qna:time>-->

## Can I import my own training data?
{: #faq-byo-sdg}

Yes, you can import your own training data. Importing your own training data is beneficial for a variety of use cases and can help you optimize performance and efficiency across hybrid environments.

- Training models to your specific needs and maintain control over your data sources, whether that's on-premises or in {{site.data.keyword.cloud_notm}}.
- Generating data in smaller, manageable chunks, so that you can avoid timeouts or system limits. You can later combine these smaller data sets into a single data set for training.
- Combining previously generated training data with new data, so that you can iteratively retrain models with both existing and newly acquired knowledge.

Other use cases:

{{_include-segments/byo-sdg-use-cases.md}}
