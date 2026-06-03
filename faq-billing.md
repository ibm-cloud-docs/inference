---

copyright:
  years: 2025, 2026
lastupdated: "2026-06-03"

keywords: red hat ai, inference, model alignment, faq

subcollection: inference

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}


# FAQ about billing for {{site.data.keyword.instructlab_short}}
{: #faq-b}


Frequently asked questions about billing for {{site.data.keyword.instructlab_short}} might include questions about costs or storage pricing. To find all of the FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs).
{: shortdesc}

## How does billing work?
{: #costs-faq}
{: faq}

You incur costs for using {{site.data.keyword.product_name}}. If you use model alignment, you also incur costs for [{{site.data.keyword.cos_full}}](https://cloud.ibm.com/objectstorage/create#pricing){: external}, which is used as a storage location.

If you deploy your model on another service, you incur additional charges from that service.


## How is cost calculated in {{site.data.keyword.product_name}}?
{: #costs-ilab}
{: faq}

The cost from {{site.data.keyword.product_name}} usage is based on metrics that are measured in tokens. Each token corresponds to a specific amount of computational power that is required for the processing tasks. The total number of tokens consumed directly influences the scale of data generation, model fine-tuning, or inference. This metric serves as a basis for our billing system, enabling users to monitor and control their costs according to the computational resources used.

Synthetic data generation (SDG)
:   Output tokens (`SYN-DATA-TOKEN`) are calculated by the volume of generated data produced by the service from the entire input taxonomy. The text is tokenized by using [Hugging Face's tokenizer library](https://huggingface.co/docs/transformers/en/main_classes/tokenizer){: external} with the tokenization information for the [Mistral teacher model](https://huggingface.co/docs/transformers/main/en/model_doc/mistral#mistral){: external}.

Model alignment training
:   Input tokens (`MODEL-TRAIN-TOKEN`) are calculated based on the amount of data fed that into the system for model alignment training, as well as the Granite base knowledge that is used to increase accuracy without knowledge loss. Because of the foundational knowledge that is used, there is a minimum cost.

Inference with a model
:   Inference costs are calculated separately for input and output tokens on a per-model basis. Input tokens represent your prompt or query sent to the model, while output tokens represent the model's generated response. Each model has its own pricing structure based on its size and computational requirements.




## How do I find and track cost information as I train a model?
{: #costs-tracking}
{: faq}

1. Before you begin running anything in {{site.data.keyword.short_name}}, you can use the [cost estimator](https://cloud.ibm.com/estimator) to get an estimate of what the cost might be.

1. [Upload your taxonomy](/docs/inference?topic=inference-getting-started&interface=ui#taxonomy-add-ui)

1. When you set the details for [data generation](/docs/{{site.data.keyword.subcollection}}?topic={{site.data.keyword.subcollection}}-data-generate), review the estimated cost before starting the job.

1. After the data is generated, you can also view the estimated **Output tokens** in the details for that data generation. 

1. When you set the details for the [training](/docs/{{site.data.keyword.subcollection}}?topic={{site.data.keyword.subcollection}}-model-train) job, review the estimated cost before starting the job.

1. When the jobs are complete, you can review the actual costs in [Billing and usage](https://cloud.ibm.com/billing). You can view the costs for both {{site.data.keyword.product_name}} and the [{{site.data.keyword.cos_full}}](https://cloud.ibm.com/objectstorage/create#pricing) service, which is used as a storage location.


## Are failed operations billed?
{: #costs-operations}
{: faq}

Failed operations are not billed. Successful operations and user canceled operations are billed, though user canceled operations are prorated based on the processing that completed.
