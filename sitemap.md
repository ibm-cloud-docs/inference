---

copyright:
  years: 2025, 2026
lastupdated: "2026-09-25"


keywords: instructlab, sitemap
subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}

# Site map for {{site.data.keyword.short_name}}
{: #sitemap}



## Getting started
{: #sitemap_getting_started}


[Getting started](/docs/inference?topic=inference-getting-started#getting-started)

* [What you'll accomplish](/docs/inference?topic=inference-getting-started#objectives)

* [Before you begin](/docs/inference?topic=inference-getting-started#prereqs)

* [Get your project ID and API endpoint](/docs/inference?topic=inference-getting-started#get-project-id)

    * [API endpoint](/docs/inference?topic=inference-getting-started#gs-api-endpoint)

* [Authenticate to the API](/docs/inference?topic=inference-getting-started#authenticate)

    * [Create a service ID and assign access](/docs/inference?topic=inference-getting-started#create-service-id)

    * [Create an API key](/docs/inference?topic=inference-getting-started#create-api-key)

* [Explore available models](/docs/inference?topic=inference-getting-started#explore-models)

* [Generate your first chat completion](/docs/inference?topic=inference-getting-started#generate-completion)

    * [Understanding the request](/docs/inference?topic=inference-getting-started#understand-request)

* [Next steps](/docs/inference?topic=inference-getting-started#next-steps)

    * [Continue with inference](/docs/inference?topic=inference-getting-started#continue-inference)


## How it works
{: #sitemap_how_it_works}


[How it works](/docs/inference?topic=inference-about#about)

* [What are large language models?](/docs/inference?topic=inference-about#llm)

* [What is inference?](/docs/inference?topic=inference-about#inference)

    * [How inference works](/docs/inference?topic=inference-about#how-inference-works)

* [Why Red Hat AI on {{site.data.keyword.cloud_notm}}?](/docs/inference?topic=inference-about#benefits)

* [Resources for learning more](/docs/inference?topic=inference-about#resources)

* [How does billing work?](/docs/inference?topic=inference-about#billing)


## Release notes
{: #sitemap_release_notes}


[Release notes](/docs/inference?topic=inference-release-notes#release-notes)

* [July 2026](/docs/inference?topic=inference-release-notes#july26)

    * [14 July 2026](/docs/inference?topic=inference-release-notes#8july26)

        * Model alignment is deprecated

* [June 2026](/docs/inference?topic=inference-release-notes#june26)

    * [25 June 2026](/docs/inference?topic=inference-release-notes#25june26)

        * New models available

* [May 2026](/docs/inference?topic=inference-release-notes#may26)

    * [22 May 2026](/docs/inference?topic=inference-release-notes#22may26)

        * Inference is now generally available

* [April 2026](/docs/inference?topic=inference-release-notes#apr26)

    * [23 April 2026](/docs/inference?topic=inference-release-notes#23apr26)

        * Inference with Red Hat AI on {{site.data.keyword.cloud_notm}} (Beta)

* [October 2025](/docs/inference?topic=inference-release-notes#oct25)

    * [10 October 2025](/docs/inference?topic=inference-release-notes#10oct25)

        * {{site.data.keyword.short_name}} CLI plug-in version 0.0.26

* [September 2025](/docs/inference?topic=inference-release-notes#sept25)

    * [23 September 2025](/docs/inference?topic=inference-release-notes#23aug25)

        * Version 1.5 of {{site.data.keyword.product_name}} is available

        * New base model

* [August 2025](/docs/inference?topic=inference-release-notes#aug25)

    * [22 August 2025](/docs/inference?topic=inference-release-notes#2aug25)

        * New! Import your own training data

        * New! Taxonomy validation

        * {{site.data.keyword.short_name}} CLI plug-in version `0.0.24`

* [May 2025](/docs/inference?topic=inference-release-notes#may25)

    * [09 May 2025](/docs/inference?topic=inference-release-notes#09may25)

        * New! Private repo support

* [April 2025](/docs/inference?topic=inference-release-notes#apr25)

    * [24 April 2025](/docs/inference?topic=inference-release-notes#24apr25)

        * Introducing {{site.data.keyword.instructlab_full_notm}}!


## Preparing your account
{: #sitemap_preparing_your_account}


[Creating an Inference project](/docs/inference?topic=inference-project#project)

* [Creating projects in the console for {{site.data.keyword.short_name}}](/docs/inference?topic=inference-project&interface=ui#project-create-ui)

* [Creating projects from the CLI for {{site.data.keyword.short_name}}](/docs/inference?topic=inference-project&interface=cli#project-create-cli)

* [What's next?](/docs/inference?topic=inference-project&interface=cli#whats-next-projects)

[Assigning access](/docs/inference?topic=inference-iam#iam)

* [Give InstuctLab permission to create and update {{site.data.keyword.cos_short}} artifacts](/docs/inference?topic=inference-iam&interface=cli#iam-ilab)

* [Assign user access to your resources](/docs/inference?topic=inference-iam&interface=cli#assign-access)

    * [Assigning access to resources in the console](/docs/inference?topic=inference-iam&interface=ui#iam-include-access-resources-console)

    * [Assigning access within a resource group in the console](/docs/inference?topic=inference-iam&interface=ui#iam-include-access-to-resources-console)

    * [Assigning access to manage a resource group](/docs/inference?topic=inference-iam&interface=ui#iam-include-access-to-resource-group)

    * [Assigning access to {{site.data.keyword.short_name}} by using the CLI](/docs/inference?topic=inference-iam&interface=cli#assign-access-cli)

    * [Assigning user access to {{site.data.keyword.short_name}} by using the API](/docs/inference?topic=inference-iam&interface=api#assign-access-api)

    * [Assigning access to resources by using the API](/docs/inference?topic=inference-iam&interface=api#iam-include-access-resources-api)

    * [Assigning access within a resource group by using the API](/docs/inference?topic=inference-iam&interface=api#iam-include-access-resourcegroups-api)

[Setting up logging](/docs/inference?topic=inference-logging#logging)

* [Enabling logging](/docs/inference?topic=inference-logging#log-enable)

* [Setting up {{site.data.keyword.atracker_short}}](/docs/inference?topic=inference-logging#at-event-routing)

* [Viewing logs](/docs/inference?topic=inference-logging#log-viewing)

[Enabling notifications](/docs/inference?topic=inference-event-notifications-events#event-notifications-events)

* [Enabling resource lifecycle events](/docs/inference?topic=inference-event-notifications-events#event-notifications-events-include-en-enabling-resource-lifecycle-events)

* [Delivering notifications to select destinations](/docs/inference?topic=inference-event-notifications-events#event-notifications-destinations)

    * [Email notifications](/docs/inference?topic=inference-event-notifications-events#event-notifications-email)

    * [Webhooks](/docs/inference?topic=inference-event-notifications-events#event-notifications-webhook)


## Running inference
{: #sitemap_running_inference}


[Inference a model](/docs/inference?topic=inference-inference#inference)

* [Before you begin](/docs/inference?topic=inference-inference#inf-prereqs)

* [Inference a model by using the console](/docs/inference?topic=inference-inference&interface=ui#inf-chat-ui)

* [Inference a model by using the API](/docs/inference?topic=inference-inference&interface=api#inf-chat-api)

    * [API endpoint](/docs/inference?topic=inference-inference&interface=api#inf-api-endpoint)

    * [Authenticating to the API](/docs/inference?topic=inference-inference&interface=api#inf-chat-auth)

    * [Generating a chat completion](/docs/inference?topic=inference-inference&interface=api#inf-chat-generate)

    * [Getting a chat completion by ID](/docs/inference?topic=inference-inference&interface=api#inf-chat-get-completion)

    * [Listing chat completions](/docs/inference?topic=inference-inference&interface=api#inf-chat-list)

    * [Deleting a chat completion](/docs/inference?topic=inference-inference&interface=api#inf-chat-delete)

    * [Listing models](/docs/inference?topic=inference-inference&interface=api#inf-chat-list-models)

    * [Getting a model by ID](/docs/inference?topic=inference-inference&interface=api#inf-chat-get-model)

[Setting up a model gateway with LiteLLM proxy](/docs/inference?topic=inference-model-gateway#model-gateway)

* [Before you begin](/docs/inference?topic=inference-model-gateway#inference-non-openai-prereqs)

* [Installing and configuring LiteLLM proxy](/docs/inference?topic=inference-model-gateway#inference-non-openai-litellm)

* [Starting LiteLLM proxy](/docs/inference?topic=inference-model-gateway#inference-non-openai-start)

* [Connecting your client to LiteLLM proxy](/docs/inference?topic=inference-model-gateway#inference-non-openai-connect)


## Enhancing security
{: #sitemap_enhancing_security}


[Learning the architecture](/docs/inference?topic=inference-compute-isolation#compute-isolation)

* [{{site.data.keyword.instructlab_short}} architecture](/docs/inference?topic=inference-compute-isolation#architecture)

    * [Storage](/docs/inference?topic=inference-compute-isolation#arch-data)

    * [Backend components](/docs/inference?topic=inference-compute-isolation#arch-backend)

    * [Security and access control](/docs/inference?topic=inference-compute-isolation#arch-access)

    * [Data flow](/docs/inference?topic=inference-compute-isolation#arch-dataflow)

* [{{site.data.keyword.instructlab_short}} workload isolation](/docs/inference?topic=inference-compute-isolation#workload-isolation)

[Securing your data](/docs/inference?topic=inference-mng-data#mng-data)

* [How your data is stored and encrypted in {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-mng-data#data-storage)

    * [How model alignment data is stored and encrypted](/docs/inference?topic=inference-mng-data#data-ma)

    * [How inference data is stored and encrypted](/docs/inference?topic=inference-mng-data#data-inference)

* [Deleting your data in {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-mng-data#data-delete)

* [Deleting or canceling jobs in {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-mng-data#data-jobs)

    * [Deleting {{site.data.keyword.instructlab_short}} instances](/docs/inference?topic=inference-mng-data#service-delete)

    * [Restoring deleted data for {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-mng-data#data-restore)

* [Removing access to {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-mng-data#data-access-remove)


## Observability
{: #sitemap_observability}


[Activity tracking events for {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-at_events#at_events)

* [Locations where activity tracking events are generated](/docs/inference?topic=inference-at_events#at-locations)

* [Viewing activity tracking events for {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-at_events#at-viewing)

    * [Launching {{site.data.keyword.logs_full_notm}} from the Observability page](/docs/inference?topic=inference-at_events#log-launch-standalone)

* [List of platform events](/docs/inference?topic=inference-at_events#at_actions_platform)

* [Events for model alignment](/docs/inference?topic=inference-at_events#at_actions_model_alignment)

* [Events for inference](/docs/inference?topic=inference-at_events#at_actions_inference)


## Your responsibilities
{: #sitemap_your_responsibilities}


[Your responsibilities](/docs/inference?topic=inference-responsibilities#responsibilities)

* [Incident and operations management](/docs/inference?topic=inference-responsibilities#incident-and-ops)

* [Change management](/docs/inference?topic=inference-responsibilities#change-management)

* [Identity and access management](/docs/inference?topic=inference-responsibilities#iam-responsibilities)

* [Security and regulation compliance](/docs/inference?topic=inference-responsibilities#security-compliance)

* [Disaster recovery](/docs/inference?topic=inference-responsibilities#disaster-recovery)


## Service settings
{: #sitemap_service_settings}


[Service settings](/docs/inference?topic=inference-service-settings#service-settings)

* [Training settings](/docs/inference?topic=inference-service-settings#training-defaults)

* [Synthetic data generation (SDG) settings](/docs/inference?topic=inference-service-settings#sdg-defaults)

* [Model settings](/docs/inference?topic=inference-service-settings#model-defaults)


## Lifecycle policy
{: #sitemap_lifecycle_policy}


[Lifecycle policy](/docs/inference?topic=inference-lifecycle-policy#lifecycle-policy)

* [{{site.data.keyword.instructlab_short}} recommended and supported versions](/docs/inference?topic=inference-lifecycle-policy#ilab-service-version)

* [Customer communications for {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-lifecycle-policy#customer-communications)


## High availability and disaster recovery
{: #sitemap_high_availability_and_disaster_recovery}


[High availability and disaster recovery](/docs/inference?topic=inference-ilab-ha-dr#ilab-ha-dr)

* [High availability architecture](/docs/inference?topic=inference-ilab-ha-dr#ha-architecture)

    * [High availability features](/docs/inference?topic=inference-ilab-ha-dr#ha-features)

* [Disaster recovery features](/docs/inference?topic=inference-ilab-ha-dr#dr-features)

    * [Planning for DR](/docs/inference?topic=inference-ilab-ha-dr#features-for-disaster-recovery)

* [Your responsibilities for HA and DR for model alignment](/docs/inference?topic=inference-ilab-ha-dr#feature-responsibilities)

* [Recovery time objective (RTO) and recovery point objective (RPO)](/docs/inference?topic=inference-ilab-ha-dr#rto-rpo-features)

* [Change management](/docs/inference?topic=inference-ilab-ha-dr#change-management-hadr)

* [How {{site.data.keyword.IBM_notm}} recovers from regional failures](/docs/inference?topic=inference-ilab-ha-dr#ibm-regional-failure)

* [How {{site.data.keyword.IBM_notm}} maintains services](/docs/inference?topic=inference-ilab-ha-dr#ibm-service-maintenance)


## Data portability
{: #sitemap_data_portability}


[Data portability](/docs/inference?topic=inference-data-portability#data-portability)

* [Responsibilities](/docs/inference?topic=inference-data-portability#data-portability-responsibilities)

* [Data export procedures](/docs/inference?topic=inference-data-portability#data-portability-procedures)

* [Exported data formats](/docs/inference?topic=inference-data-portability#data-portability-data-formats)

* [Data ownership](/docs/inference?topic=inference-data-portability#data-portability-ownership)

[Service availability by location](/docs/overview?topic=overview-services_region)


## API reference
{: #sitemap_api_reference}


[IBM Cloud API docs](https://{DomainName}/apidocs/inference){: external}

[Swagger](https://us-east.rhai.ibm.com/swagger-red-hat-ai-inference-api/#/){: external}


## Getting help and support
{: #sitemap_getting_help_and_support}


[Getting help and support](/docs/inference?topic=inference-get-help#get-help)


## FAQs
{: #sitemap_faqs}


[FAQ about {{site.data.keyword.instructlab_short}}](/docs/inference?topic=inference-faq-rhaii#faq-rhaii)

* [What is {{site.data.keyword.short_name}}?](/docs/inference?topic=inference-faq-rhaii#faq-rhai-1)

* [What are the benefits of {{site.data.keyword.short_name}}?](/docs/inference?topic=inference-faq-rhaii#faq-benefits)

* [What is inference?](/docs/inference?topic=inference-faq-rhaii#faq-what-is-inference)

[FAQ about chat models](/docs/inference?topic=inference-faq-chat#faq-chat)

* [How do I get started with chat completions?](/docs/inference?topic=inference-faq-chat#faq-chat-start)

* [What models are available for chat completions?](/docs/inference?topic=inference-faq-chat#faq-chat-models)

* [Can I customize model behavior?](/docs/inference?topic=inference-faq-chat#faq-chat-customize)

[FAQ about billing](/docs/inference?topic=inference-faq-b#faq-b)

* [How does billing work?](/docs/inference?topic=inference-faq-b#costs-faq)

* [How is cost calculated in {{site.data.keyword.product_name}}?](/docs/inference?topic=inference-faq-b#costs-ilab)

* [How do I find and track cost information as I train a model?](/docs/inference?topic=inference-faq-b#costs-tracking)

* [Are failed operations billed?](/docs/inference?topic=inference-faq-b#costs-operations)
