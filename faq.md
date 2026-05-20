---

copyright:
  years: 2025, 2026

lastupdated: "2026-05-20"

keywords: red hat ai, inference, model alignment, faq

subcollection: inference

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}


# FAQ for {{site.data.keyword.product_name}}
{: #faq}


Review the following FAQ for {{site.data.keyword.short_name}}. To find all FAQ for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs).
{: shortdesc}




## What is {{site.data.keyword.short_name}}?
{: #faq-rhai-1}
{: faq}

{{site.data.keyword.short_name}} is a business-ready, private, and secure generative AI solution powered by Red Hat OpenShift AI, available on {{site.data.keyword.cloud_notm}}. It provides two core capabilities: inferencing for interacting with foundation models and model alignment for fine-tuning models to your specific needs.



## Why should I use {{site.data.keyword.short_name}} for my generative AI solution?
{: #faq-rhai-2}
{: faq}

{{site.data.keyword.short_name}} offers several benefits for your generative AI solution. It allows you to retain ownership of your data, giving you control over how your data is used. It is available as a service on {{site.data.keyword.cloud_notm}}, allowing you to reduce unnecessary costs by paying just for what you need and optimize IT expenditures by delivering simpler, faster, and more economical AI solutions.

### Why should I use {{site.data.keyword.short_name}} for inferencing?
{: #faq-inferencing-benefits}

{{site.data.keyword.short_name}} provides immediate AI integration through inferencing, allowing you to start building AI-powered features without managing infrastructure. You can quickly deploy and interact with foundation models in a secure, enterprise-grade environment.

### Why should I use {{site.data.keyword.short_name}} for model alignment?
{: #faq-alignment-benefits}

With {{site.data.keyword.short_name}}, you retain ownership of your models, giving you control over how your model performs. You can leverage unique business data to unlock efficiencies and drive innovation by creating AI-powered solutions through model alignment. Additionally, it minimizes the risk of catastrophic forgetting by using built-in Granite models as a foundation for learning new skills and knowledge.

## What are the benefits of {{site.data.keyword.short_name}} on {{site.data.keyword.cloud_notm}}?
{: #faq-benefits}
{: faq}

{{site.data.keyword.short_name}} on {{site.data.keyword.cloud_notm}} offers several benefits, including:

Immediate AI integration with inferencing
:   Start building AI-powered features immediately without managing infrastructure. Use production-ready APIs to integrate conversational AI, test model behavior, and scale your applications.

Data ownership
:   Users fine-tuning a model retain ownership of both the data and the model, allowing them to control both. Inferencing users retain ownership of their data, as well, but not the model. 

Leveraging unique business data
:   Users can unlock efficiencies and drive innovation by creating AI-powered solutions using their unique business data.

Minimizing the risk of catastrophic forgetting
:   {{site.data.keyword.short_name}} uses Granite models as a foundation for learning new skills and knowledge, minimizing the risk of losing previously learned information when learning new information.

Secure, up-to-date, and available
:   {{site.data.keyword.short_name}} is available as a service on IBM Cloud, allowing users to reduce unnecessary costs and optimize IT expenditures.

Data portability
:   Users can export their content and configuration to other infrastructures.

Enterprise-grade cloud infrastructure
:   {{site.data.keyword.short_name}} uses IBM Cloud's robust and secure infrastructure, designed to meet the stringent requirements of business critical workloads.

Flexibility and advanced cloud services 
:   Inferencing leverages Red Hat OpenShift AI capabilities, which include llm-d components for efficient scheduling and routing. The service also runs on IBM Cloud, which provides on-demand access to compute hardware needed to run and scale the models.

## What is inferencing?
{: #inferencing-faq}
{: faq}

Inferencing is the process of using an LLM to generate responses, make predictions, or process inputs. With {{site.data.keyword.short_name}}, inferencing provides immediate access to foundation models through industry-standard OpenAI and OGX compatible APIs. This eliminates the complexity of deploying and scaling AI models, allowing you to focus on creating value for your users. You can use inferencing to build chatbots, add natural language understanding to applications, generate content, or integrate conversational AI capabilities into your workflows.

### How do I get started with inferencing?
{: #inferencing-start-faq}
{: faq}

Getting started with inferencing is straightforward. First, create a {{site.data.keyword.short_name}} project and obtain your project ID. Then, authenticate using either a bearer token or an IBM Cloud API key. Finally, use the OpenAI or OGX compatible APIs to send messages to foundation models and receive AI-generated responses. You can test and refine your interactions in the console playground before integrating them into production applications. For detailed instructions, see [Getting started with {{site.data.keyword.short_name}}](/docs/inference?topic=inference-getting-started).

### What models are available for inferencing?
{: #inferencing-models-faq}
{: faq}

{{site.data.keyword.short_name}} provides access to multiple foundation models, including Granite models. Different models have different strengths, capabilities, and performance characteristics. You can list all available models using the API and choose the one that best fits your use case based on factors like response quality, speed, and cost considerations. You can also experiment with different models in the console playground to find the right fit for your application.

### Can I customize model behavior during inferencing?
{: #inferencing-customize-faq}
{: faq}

Yes, you can customize model behavior during inferencing by using system prompts (developer messages) to instruct the model on how to behave, adjusting parameters like temperature to control randomness, setting maximum token limits for responses, and managing conversation history by including previous messages in your requests. This flexibility allows you to tailor the model's responses to your specific use case without needing to train a custom model.

## What is model training?
{: #faq-model-train}
{: faq}



Model training, also called model alignment, is the process of fine-tuning a foundation model with your specific knowledge and skills. The synthetic data generated from your taxonomy is used to train the model in two phases: knowledge tuning, which focuses on improving the model's foundational knowledge, and skills tuning, which trains the model on more specific capabilities required for its intended purpose.

### What is a taxonomy?
{: #taxonomy-faq}
{: faq}

A taxonomy is a structured directory of human-curated data containing the knowledge and skills you want a model to learn. It is organized in a cascading structure where each sub-directory, or "branch", of the taxonomy "tree" ends with a "leaf node", which is a set of files that contain the relevant data. Taxonomies are used in the model alignment process to generate synthetic data for training. You can contribute to a taxonomy by adding an entirely new "branch", or by adding new data to an existing `qna.yaml` file. For more information on the taxonomy structure, see [How taxonomies are structured for {{site.data.keyword.short_name}}](/docs/inference?topic=inference-taxonomy-overview&interface=ui){: external}. You can also view the [taxonomy on GitHub](https://github.com/IBM-Cloud/redhat-ai-instructlab-taxonomy){: external}.

### What is synthetic data generation?
{: #faq-data-gen}
{: faq}

Synthetic data generation is the process of creating training data from your taxonomy. The information in the taxonomy is used to generate synthetic data that augments the human-provided knowledge and is used to fine-tune the model during the model alignment process. This synthetic data helps train the model more effectively while minimizing the risk of catastrophic forgetting.


### How does taxonomy validation work?
{: #faq-tax-validation}
{: faq}

When you upload a taxonomy to {{site.data.keyword.short_name}}, the checks are performed: 
- Validating the formatting and syntax of your `qna.yaml` files by using the `ilab diff` command.
- Attempting to clone the knowledge and skills documents that are referenced in your `qna.yaml` files.
- Checking that you have the correct service authorizations in place, such as for {{site.data.keyword.cos_short}} and {{site.data.keyword.secrets-manager_short}}.

<!--<qna:time>-->

### How long does data generation take?
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

### How long does model training take?
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

### Can I import my own training data?
{: #faq-byo-sdg}

Yes, you can import your own training data. Importing your own training data is beneficial for a variety of use cases and can help you optimize performance and efficiency across hybrid environments.

- Training models to your specific needs and maintain control over your data sources, whether that's on-premises or in {{site.data.keyword.cloud_notm}}.
- Generating data in smaller, manageable chunks, so that you can avoid timeouts or system limits. You can later combine these smaller data sets into a single data set for training.
- Combining previously generated training data with new data, so that you can iteratively retrain models with both existing and newly acquired knowledge.

Other use cases:

{{_include-segments/byo-sdg-use-cases.md}}

## When should I use inferencing versus model alignment?
{: #inferencing-vs-alignment-faq}
{: faq}

Use inferencing when you need immediate access to AI capabilities and the general-purpose foundation models meet your needs. Inferencing is ideal for building chatbots, adding conversational AI to applications, testing model behavior, or integrating natural language processing without customization. Use model alignment when you need models that understand your specific business context, terminology, or requirements that go beyond what general-purpose models can provide. Model alignment is best for creating domain-specific AI solutions that require deep knowledge of your organization's unique data and processes.

## What are Granite models?
{: #granite}
{: faq}

Fit for purpose and open source, these enterprise-ready, multimodal models deliver exceptional performance against safety benchmarks and across a wide range of enterprise tasks from cybersecurity to RAG.

## How does billing work?
{: #costs-faq}
{: faq}

You incur costs for using {{site.data.keyword.product_name}}. If you use model alignment, you also incur costs for [{{site.data.keyword.cos_full}}](https://cloud.ibm.com/objectstorage/create#pricing){: external}, which is used as a storage location.

If you deploy your model on another service, you incur additional charges from that service.


### How is cost calculated in {{site.data.keyword.product_name}}?
{: #costs-ilab}
{: faq}

The cost from {{site.data.keyword.product_name}} usage is based on metrics that are measured in tokens. Each token corresponds to a specific amount of computational power that is required for the processing tasks. The total number of tokens consumed directly influences the scale of data generation, model fine-tuning, or inferencing. This metric serves as a basis for our billing system, enabling users to monitor and control their costs according to the computational resources used.

Synthetic data generation (SDG)
:   Output tokens (`SYN-DATA-TOKEN`) are calculated by the volume of generated data produced by the service from the entire input taxonomy. The text is tokenized by using [Hugging Face's tokenizer library](https://huggingface.co/docs/transformers/en/main_classes/tokenizer){: external} with the tokenization information for the [Mistral teacher model](https://huggingface.co/docs/transformers/main/en/model_doc/mistral#mistral){: external}.

Model alignment training
:   Input tokens (`MODEL-TRAIN-TOKEN`) are calculated based on the amount of data fed that into the system for model alignment training, as well as the Granite base knowledge that is used to increase accuracy without knowledge loss. Because of the foundational knowledge that is used, there is a minimum cost.

Model inferencing
:   Inferencing costs are calculated separately for input and output tokens on a per-model basis. Input tokens represent your prompt or query sent to the model, while output tokens represent the model's generated response. Each model has its own pricing structure based on its size and computational requirements.




### How do I find and track cost information as I train a model?
{: #costs-tracking}
{: faq}

1. Before you begin running anything in {{site.data.keyword.short_name}}, you can use the [cost estimator](https://cloud.ibm.com/estimator) to get an estimate of what the cost might be.

1. [Upload your taxonomy](/docs/inference?topic=inference-getting-started&interface=ui#taxonomy-add-ui)

1. When you set the details for [data generation](/docs/{{site.data.keyword.subcollection}}?topic={{site.data.keyword.subcollection}}-data-generate), review the estimated cost before starting the job.

1. After the data is generated, you can also view the estimated **Output tokens** in the details for that data generation. 

1. When you set the details for the [training](/docs/{{site.data.keyword.subcollection}}?topic={{site.data.keyword.subcollection}}-model-train) job, review the estimated cost before starting the job.

1. When the jobs are complete, you can review the actual costs in [Billing and usage](https://cloud.ibm.com/billing). You can view the costs for both {{site.data.keyword.product_name}} and the [{{site.data.keyword.cos_full}}](https://cloud.ibm.com/objectstorage/create#pricing) service, which is used as a storage location.


### Are failed operations billed?
{: #costs-operations}
{: faq}

Failed operations are not billed. Successful operations and user canceled operations are billed, though user canceled operations are prorated based on the processing that completed.
