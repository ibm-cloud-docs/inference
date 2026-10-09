---

copyright:
  years: 2024, 2026
lastupdated: "2026-10-09"

keywords: instructlab, ai, about, how it works, billing

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}


# About {{site.data.keyword.instructlab_full_notm}}
{: #about}

{{site.data.keyword.instructlab_full}} is a business-ready, private, and secure generative AI solution powered by Red Hat OpenShift AI. {{site.data.keyword.instructlab_short}} provides two core capabilities: inference for interacting with foundation models and model alignment for fine-tuning models to your specific needs.
{: shortdesc}

With inference, you can immediately start using foundation models through production-ready APIs to build AI-powered applications, test model behavior, and integrate conversational AI capabilities into your workflows. Whether you're prototyping a chatbot, building an AI assistant, or adding natural language understanding to your application, inference provides immediate access to foundation models without the complexity of model hosting.

For deeper customization, model alignment through allows you to enhance large language models with your organization's specific knowledge and skills. You provide a taxonomy —a directory of curated data containing the knowledge and skills that matter most to your business. This taxonomy is used to generate synthetic data, which trains the model through multiple phases of fine-tuning. This process aligns your LLM with your goals by providing not just general knowledge, but the specific skills and contexts that are most important for your unique business needs.

[Learn more about {{site.data.keyword.instructlab_short}}](https://www.redhat.com/en/topics/ai/what-is-instructlab#red-hat-enterprise-linux-ai){: external}.

## What are large language models?
{: #llm}

Large language models, or LLMs, are AI models that use machine learning techniques to generate human language. They are initially trained on large amounts of general data that allows them to understand and generate natural language, then later fine-tuned to align with more specific contexts. For example, a model trained on general knowledge can be fine-tuned with retail business data to create a customer service chatbot. You can fine-tune LLMs for various use cases, such as drafting emails, summarizing long bodies of text, or finding errors in code.

While LLMs can streamline processes in various ways, keep in mind there are some limitations to what they are capable of. LLMs work with the data they are supplied with. You wouldn't be able to ask an LLM for your birthday, for example, because your personal information is not part of the training data. Likewise, an LLM on its own wouldn't be the best option for predicting the future of a stock, in which case it would be more appropriate to use a forecasting model. Additionally, LLMs on their own are static and incapable of interacting with the environment. Tasks such as telling the time or date would require more agentic flows or frameworks.

For a more detailed explanation of LLMs and how they work, see [What are LLMs?](https://www.ibm.com/think/topics/large-language-models){: external}

## What is inference?
{: #inference}

Inference is the process of using a trained AI model to generate responses, make predictions, or process inputs. {{site.data.keyword.instructlab_short}} provides immediate access to foundation models through industry-standard OpenAI-compatible APIs. This eliminates the complexity of deploying and scaling AI models, allowing you to focus on creating value for your users.

Inference solves the challenge of integrating AI capabilities into your applications by providing:

Production-ready APIs
:   Use familiar, industry-standard endpoints to interact with foundation models without managing infrastructure.

Immediate model access
:   Start building AI-powered features without waiting for model deployment or training.

Flexible integration
:   Programmatically embed conversational AI into existing systems, handle high volumes of requests, and customize model behavior for your specific use cases.

Interactive testing
:   Experiment with different models and prompts in the console playground before integrating them into your applications.

For more information about inference, see [AI inference, simplified and explained](https://www.ibm.com/think/topics/ai-inference){: external}.

For more information about how to inference, see [Working with chat completions](/docs/inference?topic=inference-inf-chat-completions&interface=ui).


### How inference works
{: #how-inference-works}

Inference provides immediate access to foundation models through a simple workflow:

Step 1. Authenticate
:   After you [create a {{site.data.keyword.instructlab_short}} project](/docs/inference?topic=inference-project), use a bearer token or an {{site.data.keyword.cloud_notm}} API key to securely access your project's inference capabilities.

Step 2. Select a model
:   Choose from available foundation models based on your use case requirements, such as response quality, speed, or cost considerations.

Step 3. Send requests
:   Use industry-standard OpenAI-compatible APIs to send messages to the model and receive AI-generated responses. You can customize model behavior with system prompts and adjust parameters like randomness and response limits.

Step 4. Integrate responses
:   Incorporate the model's responses into your application workflows, whether for conversational interfaces, content generation, or natural language processing tasks.

You can test and refine your interactions in the console playground before integrating them into production applications. For detailed examples, see [Working with chat completions](/docs/inference?topic=inference-inf-chat-completions&interface=ui).

## What is embedding?
{: #embedding}

Text embedding is a way of representing text as a numerical vector — a list of numbers that captures the semantic meaning of a sentence or passage. By converting text into these vectors, the model can perform comparisons and groupings based on meaning rather than exact words, which is something computers can do quickly and accurately.

When an embedding model generates a vector for a piece of text, it assigns values that reflect that text's meaning and positions the vector in a multidimensional space relative to all other vectors. Texts with similar meanings are placed closer together in that space, and texts with different meanings are placed farther apart. For example, two sentences about the same subject — even if they use different words — would produce vectors that are near each other, while sentences with unrelated subjects would produce vectors that are far apart.

You can store generated vectors in a vector database. When the same embedding model is used to generate vectors for all content in the database, the vector store can use the relationships between vectors to return relevant results quickly. Unlike traditional keyword-based search, semantic search using embeddings retrieves information that is similar in meaning, not just in vocabulary. This produces better results in cases where users phrase queries differently from the source content.

Common uses for text embeddings include:

- Semantic search and information retrieval
- Clustering and classification of documents
- Retrieval-augmented generation (RAG), in which retrieved content is passed to a language model to produce grounded responses

### How embedding works
{: #how-embedding-works}

Embedding in {{site.data.keyword.instructlab_short}} follows a simple workflow:

Step 1. Authenticate
:   Use a bearer token or an {{site.data.keyword.cloud_notm}} API key to securely access your project's embedding capabilities.

Step 2. Select a model
:   Choose an embedding model based on your use case. The `granite-embedding-278m-multilingual` model is available and supports multiple languages.

Step 3. Send input text
:   Use the embeddings API to submit one or more text inputs. The model returns a vector representation for each input — a list of floating-point numbers that encodes the semantic content of the text.

Step 4. Use the vectors
:   Store the generated vectors in a vector database, use them to power semantic search, or integrate them into a RAG pipeline to ground model responses in your own data.

For vector storage, use [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/databases-for-elasticsearch?topic=databases-for-elasticsearch-es-ml-ai) or [{{site.data.keyword.lakehouse_full_notm}}](https://www.ibm.com/docs/en/watsonxdata/saas?topic=overview){: external}.
{: tip}

For a step-by-step walkthrough, see [Improving chat completions with vector embeddings and RAG](/docs/inference?topic=inference-embeddings-rag).

## Why Red Hat AI on {{site.data.keyword.cloud_notm}}?
{: #benefits}

Red Hat AI on {{site.data.keyword.cloud_notm}} provides comprehensive AI capabilities that address both immediate integration needs and long-term customization requirements.

Immediate AI integration with inference
:   Start building AI-powered features immediately without managing infrastructure. Use production-ready APIs to integrate conversational AI, test model behavior, and scale your applications alongside your business needs.

Flexible deployment options
:   You control your data and your models. Choose to use them in the cloud, on-premises, or anywhere else your business requires. Leverage unique business data to unlock efficiencies and drive innovation by creating AI-powered solutions.

Minimize the risk of catastrophic forgetting
:   For higher accuracy and less risk, built-in Granite models are used as a foundation for learning new skills and knowledge. Previously learned information is not lost when the models learn new information.

Cost-effective and scalable
:   Because Red Hat AI on {{site.data.keyword.cloud_notm}} is available as a service, you can reduce unnecessary costs by paying just for what you need. Optimize IT expenditures by delivering simpler, faster, and more economical AI solutions.

Industry-standard APIs
:   Use familiar OpenAI-compatible endpoints to integrate AI capabilities into your existing workflows and applications without learning proprietary interfaces.

## How does billing work?
{: #billing}

To learn more about billing, see the [FAQ](/docs/{{site.data.keyword.subcollection}}?topic={{site.data.keyword.subcollection}}-faq#costs).
