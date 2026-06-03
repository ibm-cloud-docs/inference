---

copyright:
  years: 2026
lastupdated: "2026-06-03"

keywords:

subcollection: inference

---

{{site.data.keyword.attribute-definition-list}}


# Activity tracking events for {{site.data.keyword.instructlab_short}}
{: #at_events}

{{site.data.keyword.cloud_notm}} services, such as {{site.data.keyword.instructlab_short}}, generate activity tracking events.
{: shortdesc}

Activity tracking events report on activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use the events to investigate abnormal activity and critical actions and to comply with regulatory audit requirements.

You can use {{site.data.keyword.atracker_full_notm}}, a platform service, to route auditing events in your account to destinations of your choice by configuring targets and routes that define where activity tracking events are sent. For more information, see [About {{site.data.keyword.atracker_full_notm}}](/docs/atracker?topic=atracker-about).

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.


## Locations where activity tracking events are generated
{: #at-locations}

Activity tracking events for {{site.data.keyword.instructlab_short}} are generated in the `us-east` region. 


## Viewing activity tracking events for {{site.data.keyword.instructlab_short}}
{: #at-viewing}

You can use {{site.data.keyword.logs_full_notm}} to visualize and alert on events that are generated in your account and routed by {{site.data.keyword.atracker_full_notm}} to an {{site.data.keyword.logs_full_notm}} instance.

### Launching {{site.data.keyword.logs_full_notm}} from the Observability page
{: #log-launch-standalone}

For information on launching the {{site.data.keyword.logs_full_notm}} UI, see [Launching the UI in the {{site.data.keyword.logs_full_notm}} documentation.](/docs/cloud-logs?topic=cloud-logs-instance-launch)


## List of platform events
{: #at_actions_platform}



The following table lists the activity tracking event actions that the {{site.data.keyword.cloud_notm}} platform generates {{site.data.keyword.instructlab_short}} instances are processed.

| Action                                   | Description |
|------------------------------------------|---------|
| `instructlab.instance.create`           | An event is generated when you provision a service instance. |
| `instructlab.instance.delete`           | An event is generated when a service instance is deleted. |
| `instructlab.instance.schedule_reclaim` | An event is generated when a service instance is pending reclamation. |
{: caption="Actions that generate platform events" caption-side="bottom"}

## Events for model alignment
{: #at_actions_model_alignment}

The following table lists the activity tracking events that are generated when you perform model alignment operations in {{site.data.keyword.instructlab_short}}. These events track actions related to managing models, taxonomies, and synthetic data generation (SDG) throughout the model alignment workflow. The events also include {{site.data.keyword.cos_short}} operations that occur when {{site.data.keyword.instructlab_short}} accesses or stores data in your connected storage buckets during the alignment process.

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `instructlab.model.read`                                 | An event is generated when you read details of a model training run. |
| `instructlab.model.list`                                 | An event is generated when you list model training runs. |
| `instructlab.model.create`                                 | An event is generated when you create a model training run. |
| `instructlab.model.delete`                                 | An event is generated when you delete a model training run. |
| `instructlab.model.stop`                                 | An event is generated when you stop a model training run. |
| `cloud-object-storage.bucket.get`                                 | An event is generated when you list all the objects in a bucket.                                   |
| `cloud-object-storage.object.put`                                 | An event is generated when you write and upload objects.                                   |
| `cloud-object-storage.object.get`                                 | An event is generated when you view and download objects.                                    |
| `instructlab.taxonomy.read`                                 | An event is generated when you read details of a taxonomy. |
| `instructlab.taxonomy.list`      | An event is generated when you list taxonomies. |
| `instructlab.taxonomy.create`      | An event is generated when you create taxonomies. |
| `instructlab.taxonomy.delete`      | An event is generated when you delete taxonomies. |
| `instructlab.sdgdata.read`      | An event is generated when you read details of a data generation run. |
| `instructlab.sdgdata.list`      | An event is generated when you list data generation runs. |
| `instructlab.sdgdata.create`      | An event is generated when you create a data generation run. |
| `instructlab.sdgdata.delete`      | An event is generated when you delete a data generation run. |
| `instructlab.sdgdata.stop`      | An event is generated when you stop a data generation run. |
{: caption="List of model alignment events" caption-side="bottom"}

## Events for inference
{: #at_actions_inference}

The following table lists the activity tracking events that are generated when you perform inference operations in {{site.data.keyword.instructlab_short}}. These events track actions related to managing inference models and creating, reading, and deleting inference requests. Use these events to monitor how your aligned models are being deployed and used for inference workloads.

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `instructlab.inference-model.read`                                | An event is generated when you get a model by its identifier. |
| `instructlab.inference-model.list`                                | An event is generated when you list models using the OpenAI API. |
| `instructlab.inference.create`                                | An event is generated when you generate an OpenAI-compatible chat completion for the given messages using the specified model. |
| `instructlab.inference.read`                                | An event is generated when you describe a chat completion by its ID. |
| `instructlab.inference.list`                                | An event is generated when you list chat completions. |
| `instructlab.inference.delete`                                | An event is generated when you delete a stored chat completion. |
| `instructlab.inference-session.read` | An event is generated when internal APIs are used for storing session read state in the UI. |
| `instructlab.inference-session.list` | An event is generated when internal APIs are used for storing session list state for the UI. |
| `instructlab.inference-session.delete` | An event is generated when internal APIs are used for storing session delete state in the UI. |
| `instructlab.inference-session.update` | An event is generated when internal APIs are used for storing session update state in the UI. |
{: caption="Lists of inference events" caption-side="bottom"}
