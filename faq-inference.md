---

copyright:
  years: 2025, 2026

lastupdated: "2026-06-03"

keywords: red hat ai, inference, model alignment, faq

subcollection: inference

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}


# FAQ about inference
{: #faq-i}


Frequently asked questions about inference might include questions about what inference is or how to get started. To find all of the FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs). To find all of the FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs).
{: shortdesc}

<!--<qna:inference>-->

## What is inference?
{: #inference-faq}
{: faq}

Inference is the process of using an LLM to generate responses, make predictions, or process inputs. {{site.data.keyword.short_name}} provides immediate access to foundation models through industry-standard OpenAI-scompatible APIs. This eliminates the complexity of deploying and scaling AI models, allowing you to focus on creating value for your users. You can use inference to build chatbots, add natural language understanding to applications, generate content, or integrate conversational AI capabilities into your workflows.

## How do I get started with inference?
{: #inference-start-faq}
{: faq}

Getting started with inference is straightforward. First, create a {{site.data.keyword.short_name}} project and obtain your project ID. Then, authenticate using either a bearer token or an {{site.data.keyword.cloud_notm}} API key. Finally, use the OpenAI-compatible APIs to send messages to foundation models and receive AI-generated responses. You can test and refine your interactions in the console playground before integrating them into production applications. For detailed instructions, see [Getting started with {{site.data.keyword.short_name}}](/docs/inference?topic=inference-getting-started).

## What models are available for inference?
{: #inference-models-faq}
{: faq}

{{site.data.keyword.short_name}} provides access to multiple foundation models, including Granite models. Different models have different strengths, capabilities, and performance characteristics. You can list all available models using the API and choose the one that best fits your use case based on factors like response quality, speed, and cost considerations. You can also experiment with different models in the console playground to find the right fit for your application.

## Can I customize model behavior during inference?
{: #inference-customize-faq}
{: faq}

Yes, you can customize model behavior during inference by using system prompts (developer messages) to instruct the model on how to behave, adjusting parameters like temperature to control randomness, setting maximum token limits for responses, and managing conversation history by including previous messages in your requests. This flexibility allows you to tailor the model's responses to your specific use case without needing to train a custom model.


<!--</qna:inference>-->
