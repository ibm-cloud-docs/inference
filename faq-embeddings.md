---

copyright:
  years: 2025, 2026

lastupdated: "2026-10-05"

keywords: embeddings, faq, vector database, limits

subcollection: inference

content-type: faq

---

{{site.data.keyword.attribute-definition-list}}


# FAQ about embeddings
{: #faq-embeddings}


Frequently asked questions about embeddings might include questions about limits, inputs, and vector databases.
{: shortdesc}

<!--<qna:embeddings>-->

## What is a vector embedding?
{: #faq-embeddings-what-is}
{: faq}

A vector embedding is a numerical representation of text — a list of numbers that captures the semantic meaning of a word, sentence, or passage. Embedding models convert text into these vectors so that content with similar meaning is positioned closer together in a multidimensional space, enabling semantic search, clustering, and retrieval-augmented generation (RAG).

For more information, see [What is embedding?](/docs/inference?topic=inference-about#embedding).

## What is the input token limit for embeddings?
{: #faq-embeddings-token-limit}
{: faq}

Each embedding model defines its maximum input token limit based on its context window size. This limit applies to each text individually if you send an array of text as input.

## How does the service handle text that exceeds the limit?
{: #faq-embeddings-exceed-limit}
{: faq}

If any text input exceeds the model's token limit, the API rejects the request entirely and returns an `HTTP 400 Bad Request` error. For more details on diagnosing this error, see [Why does my embeddings request fail with an HTTP 400 Bad Request error?](/docs/inference?topic=inference-ts-embeddings-exceed-limit).

## How are limits applied when multiple text inputs are included in a single API call?
{: #faq-embeddings-multiple-inputs}
{: faq}

When you submit an array of text inputs, the token limit is applied to each input individually.

## What is the maximum batch size supported per API call?
{: #faq-embeddings-max-batch}
{: faq}

The maximum batch size depends on the model's context window. To find the context window for a model, go to the [Model catalog](/inference/model-catalog){: external}.

## What are valid inputs to the embeddings API?
{: #faq-embeddings-valid-inputs}
{: faq}

The embeddings API supports the following input formats:
- A single text string
- An array of text strings
- An array of integers representing tokens
- An array of arrays of integers representing tokens

## Does a larger output vector provide a better representation of the input?
{: #faq-embeddings-vector-size}
{: faq}

A larger output vector size can represent more detail and capture more granular semantic meaning. However, larger vectors require more memory for storage and search, which can increase resource usage.

## Can I configure the size of the output vector?
{: #faq-embeddings-configure-dimensions}
{: faq}

The size of the output vector is model-dependent. Although the embeddings API supports a `dimensions` parameter, this parameter is used only if the selected model is compatible with configuring dimension sizes.

## Do you offer managed vector database services?
{: #faq-embeddings-vector-databases}
{: faq}

Yes. {{site.data.keyword.IBM_notm}} offers managed vector database services. You can use [{{site.data.keyword.databases-for-elasticsearch_full_notm}}](/docs/databases-for-elasticsearch?topic=databases-for-elasticsearch-es-ml-ai) or [{{site.data.keyword.lakehouse_full_notm}}](/docs/watsonxdata?topic=watsonxdata-wxd_ov) to store and search your vector embeddings.

<!--</qna:embeddings>-->
