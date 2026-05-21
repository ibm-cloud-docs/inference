---

copyright:
  years: 2025, 2026

lastupdated: "2026-05-21"

keywords: red hat ai, inference, model alignment, faq

subcollection: inference

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}


# FAQ about inferencing
{: #faq-i}


Frequently asked questions about inferencing might include questions about what inferencing is or how to get started. To find all of the FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs). To find all of the FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs).
{: shortdesc}

<!--<qna:inferencing>-->

## What is inferencing?
{: #inferencing-faq}
{: faq}

Inferencing is the process of using an LLM to generate responses, make predictions, or process inputs. With {{site.data.keyword.short_name}}, inferencing provides immediate access to foundation models through industry-standard OpenAI and OGX compatible APIs. This eliminates the complexity of deploying and scaling AI models, allowing you to focus on creating value for your users. You can use inferencing to build chatbots, add natural language understanding to applications, generate content, or integrate conversational AI capabilities into your workflows.

## How do I get started with inferencing?
{: #inferencing-start-faq}
{: faq}

Getting started with inferencing is straightforward. First, create a {{site.data.keyword.short_name}} project and obtain your project ID. Then, authenticate using either a bearer token or an IBM Cloud API key. Finally, use the OpenAI or OGX compatible APIs to send messages to foundation models and receive AI-generated responses. You can test and refine your interactions in the console playground before integrating them into production applications. For detailed instructions, see [Getting started with {{site.data.keyword.short_name}}](/docs/inference?topic=inference-getting-started).

## What models are available for inferencing?
{: #inferencing-models-faq}
{: faq}

{{site.data.keyword.short_name}} provides access to multiple foundation models, including Granite models. Different models have different strengths, capabilities, and performance characteristics. You can list all available models using the API and choose the one that best fits your use case based on factors like response quality, speed, and cost considerations. You can also experiment with different models in the console playground to find the right fit for your application.

## Can I customize model behavior during inferencing?
{: #inferencing-customize-faq}
{: faq}

Yes, you can customize model behavior during inferencing by using system prompts (developer messages) to instruct the model on how to behave, adjusting parameters like temperature to control randomness, setting maximum token limits for responses, and managing conversation history by including previous messages in your requests. This flexibility allows you to tailor the model's responses to your specific use case without needing to train a custom model.


<!--</qna:inferencing>-->
