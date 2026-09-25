---

copyright:
  years: 2025, 2026

lastupdated: "2026-09-14"

keywords: red hat ai, chat, chat completions, faq

subcollection: inference

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}


# FAQ about chat models
{: #faq-chat}


Frequently asked questions about chat models might include questions about how to get started, available models, and customization. To find all of the FAQs for {{site.data.keyword.cloud}}, see our [FAQ library](/docs/faqs).
{: shortdesc}

<!--<qna:faq-chat>-->

## How do I get started with chat completions?
{: #faq-chat-start}
{: faq}

Getting started with chat completions is straightforward. First, create a {{site.data.keyword.short_name}} project and obtain your project ID. Then, authenticate using either a bearer token or an {{site.data.keyword.cloud_notm}} API key. Finally, use the OpenAI-compatible APIs to send messages to foundation models and receive AI-generated responses. You can test and refine your interactions in the console playground before integrating them into production applications. For detailed instructions, see [Getting started with {{site.data.keyword.short_name}}](/docs/inference?topic=inference-getting-started).

## What models are available for chat completions?
{: #faq-chat-models}
{: faq}

{{site.data.keyword.short_name}} provides access to multiple foundation models, including Granite models. Different models have different strengths, capabilities, and performance characteristics. You can list all available models using the API and choose the one that best fits your use case based on factors like response quality, speed, and cost considerations. You can also experiment with different models in the console playground to find the right fit for your application.

## Can I customize model behavior?
{: #faq-chat-customize}
{: faq}

Yes, you can customize model behavior by using system prompts (developer messages) to instruct the model on how to behave, adjusting parameters like temperature to control randomness, setting maximum token limits for responses, and managing conversation history by including previous messages in your requests. This flexibility allows you to tailor the model's responses to your specific use case without needing to train a custom model.

<!--</qna:faq-chat>-->
