---

copyright:
  years: 2024, 2026
lastupdated: "2026-05-05"

keywords: instructlab, ai, about, how it works, billing

subcollection: instructlab

---

{{site.data.keyword.attribute-definition-list}}


# About {{site.data.keyword.instructlab_full_notm}}
{: #about}

{{site.data.keyword.instructlab_full}} is a business-ready, private, and secure generative AI solution powered by Red Hat Enterprise Linux AI. Red Hat AI on {{site.data.keyword.cloud_notm}} provides two core capabilities: inferencing for interacting with foundation models and model alignment (InstructLab) for customizing models to your specific needs.
{: shortdesc}

With inferencing, you can immediately start using foundation models through production-ready APIs to build AI-powered applications, test model behavior, and integrate conversational AI capabilities into your workflows. Whether you're prototyping a chatbot, building an AI assistant, or adding natural language understanding to your application, inferencing provides immediate access to foundation models without the complexity of model hosting.

For deeper customization, model alignment through InstructLab allows you to enhance large language models with your organization's specific knowledge and skills. You provide a taxonomy —a directory of curated data containing the knowledge and skills that matter most to your business. This taxonomy is used to generate synthetic data, which trains the model through multiple phases of fine-tuning. This process aligns your LLM with your goals by providing not just general knowledge, but the specific skills and contexts that are most important for your unique business needs.

[Learn more about InstructLab](https://www.redhat.com/en/topics/ai/what-is-instructlab#red-hat-enterprise-linux-ai){: external}.

## What are large language models?
{: #llm}

Large language models, or LLMs, are AI models that use machine learning techniques to generate human language. They are initially trained on large amounts of general data that allows them to understand and generate natural language, then later fine-tuned to align with more specific contexts. For example, a model trained on general knowledge can be fine-tuned with retail business data to create a customer service chatbot. You can fine-tune LLMs for various use cases, such as drafting emails, summarizing long bodies of text, or finding errors in code.

While LLMs can streamline processes in various ways, keep in mind there are some limitations to what they are capable of. LLMs work with the data they are supplied with. You wouldn't be able to ask an LLM for your birthday, for example, because your personal information is not part of the training data. Likewise, an LLM on its own wouldn't be the best option for predicting the future of a stock, in which case it would be more appropriate to use a forecasting model. Additionally, LLMs on their own are static and incapable of interacting with the environment. Tasks such as telling the time or date would require more agentic flows or frameworks.

For a more detailed explanation of LLMs and how they work, see [What are LLMs?](https://www.ibm.com/think/topics/large-language-models){: external}

## What is inferencing?
{: #inferencing}

Inferencing is the process of using a trained AI model to generate responses, make predictions, or process inputs. With Red Hat AI on {{site.data.keyword.cloud_notm}}, inferencing provides immediate access to foundation models through industry-standard OpenAI and Llama Stack compatible APIs. This eliminates the complexity of deploying and scaling AI models, allowing you to focus on creating value for your users.

Inferencing solves the challenge of integrating AI capabilities into your applications by providing:

Production-ready APIs
:   Use familiar, industry-standard endpoints to interact with foundation models without managing infrastructure.

Immediate model access
:   Start building AI-powered features without waiting for model deployment or training.

Flexible integration
:   Programmatically embed conversational AI into existing systems, handle high volumes of requests, and customize model behavior for your specific use cases.

Interactive testing
:   Experiment with different models and prompts in the console playground before integrating them into your applications.

For more information about using inferencing, see [Inferencing with Red Hat AI on {{site.data.keyword.cloud_notm}}](/docs/instructlab?topic=instructlab-inference).


### How inferencing works
{: #how-inferencing-works}

Inferencing provides immediate access to foundation models through a simple workflow:

Step 1. Authenticate
:   After you [create a {{site.data.keyword.instructlab_short}} project](/docs/instructlab?topic=instructlab-project), use a bearer token or an {{site.data.keyword.cloud_notm}} API key to securely access your project's inferencing capabilities.

Step 2. Select a model
:   Choose from available foundation models based on your use case requirements, such as response quality, speed, or cost considerations.

Step 3. Send requests
:   Use industry-standard OpenAI or Llama Stack compatible APIs to send messages to the model and receive AI-generated responses. You can customize model behavior with system prompts and adjust parameters like randomness and response limits.

Step 4. Integrate responses
:   Incorporate the model's responses into your application workflows, whether for conversational interfaces, content generation, or natural language processing tasks.

You can test and refine your interactions in the console playground before integrating them into production applications. For detailed examples, see [Inferencing with Red Hat AI on {{site.data.keyword.cloud_notm}}](/docs/instructlab?topic=instructlab-inference).


## What is model alignment?
{: #model-alignment}

Model alignment through InstructLab allows you to customize foundation models with your organization's specific knowledge and skills. Rather than using a general-purpose model, you can fine-tune models to understand your business context, terminology, and requirements.

The model alignment process involves:

Taxonomy creation
:   Provide a structured directory of human-curated data containing the knowledge and skills you want the model to learn.

Synthetic data generation
:   The taxonomy is used to generate synthetic data that augments your human-provided knowledge for more effective training.

Model training
:   The synthetic data trains the model through knowledge tuning (improving foundational understanding) and skills tuning (developing specific capabilities for your use case).

This approach minimizes the risk of catastrophic forgetting—where models lose previously learned information when learning new concepts—by using built-in Granite models as a foundation.

### How model alignment works
{: #how-model-alignment-works}

Model alignment through InstructLab follows a structured process to customize foundation models:

Step 1. Provide a taxonomy
:   A taxonomy is a directory of diverse, human-curated data that is used to train an LLM. The data contains examples of new knowledge and skills for the model to learn from. You can use and contribute to an existing taxonomy, or you can create your own. For more information, see [How taxonomies are structured for {{site.data.keyword.short_name}}](/docs/instructlab?topic=instructlab-taxonomy-overview).

Step 2. Generate synthetic data
:   The information in the taxonomy is used to generate synthetic data that augments the human-provided knowledge and is used to fine-tune the model. [Learn more about the data generation process from Red Hat](https://www.redhat.com/en/blog/how-instructlabs-synthetic-data-generation-enhances-llms){: external}.

Step 3. Train the model
:   The synthetic data is used to train the model in two phases: knowledge tuning and skills tuning. Knowledge tuning is training that focuses on improving the LLM's foundational knowledge of essential skills. Skills tuning trains the model on more specific skills that are required for its intended purpose, such as responding to customer inquiries or analyzing weather trends.

## Why Red Hat AI on {{site.data.keyword.cloud_notm}}?
{: #benefits}

Red Hat AI on {{site.data.keyword.cloud_notm}} provides comprehensive AI capabilities that address both immediate integration needs and long-term customization requirements.

Immediate AI integration with inferencing
:   Start building AI-powered features immediately without managing infrastructure. Use production-ready APIs to integrate conversational AI, test model behavior, and scale your applications alongside your business needs.

Flexible deployment options
:   You control your data and your models. Choose to use them in the cloud, on-premises, or anywhere else your business requires. Leverage unique business data to unlock efficiencies and drive innovation by creating AI-powered solutions.

Minimize the risk of catastrophic forgetting
:   For higher accuracy and less risk, built-in Granite models are used as a foundation for learning new skills and knowledge. Previously learned information is not lost when the models learn new information.

Cost-effective and scalable
:   Because Red Hat AI on {{site.data.keyword.cloud_notm}} is available as a service, you can reduce unnecessary costs by paying just for what you need. Optimize IT expenditures by delivering simpler, faster, and more economical AI solutions.

Industry-standard APIs
:   Use familiar OpenAI and Llama Stack compatible endpoints to integrate AI capabilities into your existing workflows and applications without learning proprietary interfaces.


## Resources for learning more
{: #resources}

See what others have to say about InstructLab. 

- [What is InstructLab?](https://www.redhat.com/en/topics/ai/what-is-instructlab){: external}
- [InstructLab](https://www.ibm.com/think/topics/instructlab?mhsrc=ibmsearch_a&mhq=instructlab){: external}.
- [What is InstructLab and why do developers need it?](https://developer.ibm.com/articles/awb-instructlab-why-developers-need-it/){: external}
- [What is a large language model?](https://www.redhat.com/en/topics/ai/what-are-large-language-models){: external}


## How does billing work?
{: #billing}

To learn more about billing, see the [FAQ](/docs/{{site.data.keyword.subcollection}}?topic={{site.data.keyword.subcollection}}-faq#costs).
