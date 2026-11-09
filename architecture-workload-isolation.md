---

copyright:
  years: 2025, 2026
lastupdated: "2026-11-09"

keywords: instructlab, workload isolation, architecture, data, tenants

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}

# Learning about {{site.data.keyword.short_name}} architecture and workload isolation
{: #compute-isolation}


{{site.data.keyword.instructlab_full_notm}} operates on a Software-as-a-Service (SaaS) model, ensuring that operations run on dedicated GPU machines. After completion, all data is securely wiped, guaranteeing complete isolation between tenant workloads.
{: shortdesc}

By understanding the following architectural principles and isolation levels, you can select the solution that best aligns with your workload requirements. Our commitment to data isolation and security is unwavering, ensuring that your operations are conducted in a safe, controlled, and independent environment.

## {{site.data.keyword.instructlab_short}} architecture
{: #architecture}

{{site.data.keyword.instructlab_short}} is a comprehensive, cloud-based service designed for model inference. The architecture is built on a Software-as-a-Service (SaaS) model, which inherently provides a high level of isolation between tenant workloads. Inference operations run on multi-tenanted Red Had OpenShift clusters running the Red Hat OpenShift AI operator on GPUs against stateless foundation models.

After an operation completes, all data is meticulously wiped from the system. This practice not only adheres to stringent data privacy standards but also ensures that no residual data from one tenant's workload can impact another. This rigorous data sanitization process, which is coupled with our SaaS-based architecture, provides a robust isolation mechanism, making {{site.data.keyword.instructlab_short}} an ideal choice for running sensitive workloads in the cloud.

### Storage
{: #arch-data}

Inference uses OpenAI compatible APIs. Model responses are optionally stored, accessible, and deletable with IAM controls against the project.


### Backend components
{: #arch-backend}

{{site.data.keyword.instructlab_short}} operates {{site.data.keyword.redhat_openshift_notm}} AI using {{site.data.keyword.containerfull_notm}} with one or more GPU machines to run multi-tenant models.

### Security and access control
{: #arch-access}

You have full control over the IAM policies that determine what actions can be executed in your account, and can implement IAM-controlled access to keep data separated within individual projects in your account. You can use IBM Cloud Activity Tracker to audit events that change the state of the service. All API requests are authenticated by and authorized through IBM Cloud IAM. 



### Data flow
{: #arch-dataflow}

The data flow is as follows:
1. The service uses Red Hat OpenShift AI on {{site.data.keyword.containerfull_notm}} to serve multi-tenanted, stateless models for inference operations like chat completions.
2. The service uses OpenAI compatible interfaces for chat completions for API responses in get, create, delete, and list operations.



## {{site.data.keyword.instructlab_short}} workload isolation
{: #workload-isolation}

Inference models are stateless, but multi-tenanted.
