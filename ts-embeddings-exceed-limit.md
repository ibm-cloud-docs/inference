---

copyright:
  years: 2025, 2026
lastupdated: "2026-10-05"

keywords: embeddings, limit, bad request, 400, encoding_format, dimensions, invalid model, empty input

subcollection: inference

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}



# Why does my embeddings request fail with an HTTP 400 Bad Request error?
{: #ts-embeddings-exceed-limit}
{: troubleshoot}
{: support}

When you submit an API request to create embeddings, the request fails with an `HTTP 400 Bad Request` error.
{: shortdesc}

You receive an `HTTP 400 Bad Request` error response from the embeddings API endpoint.
{: tsSymptoms}

An `HTTP 400 Bad Request` error indicates that the API rejected the request because of a problem with the request itself. Common causes include:
{: tsCauses}

Input exceeds the model's context window
:   Each embedding model has a fixed maximum input token limit based on its context window size. If any single input in your request exceeds that limit, the entire request is rejected. The error message includes the model's maximum and your requested token count: `This model's maximum context length is N tokens, but you requested M tokens.`

Unsupported `encoding_format`
:   The embeddings API accepts only `float` and `base64` as valid values for the `encoding_format` parameter. Any other value causes the request to fail.

`dimensions` parameter set on an unsupported model
:   Some embedding models do not support configuring the output vector size. If you set the `dimensions` parameter on a model that does not support it, the API returns a 400 error.

Review the error message in the API response and apply the appropriate fix.
{: tsResolve}

Input exceeds the context window
:   Truncate or chunk any input text that exceeds the model's token limit. Split large documents into smaller, logically coherent passages such as paragraphs or sentences before calling the embeddings API. If you are sending an array of multiple text inputs, inspect each text individually to verify its length. Confirm that the total number of inputs in a single request does not exceed the maximum batch size for the model. To find the context window, go to the [Model catalog](/inference/model-catalog){: external}.

Unsupported `encoding_format`
:   Set the `encoding_format` parameter to either `float` or `base64`, or omit it to use the default value.

`dimensions` on an unsupported model
:   Remove the `dimensions` parameter from your request, or select a model that supports configurable output dimensions.
