---

copyright:
  years: 2026
lastupdated: "2026-05-12"

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
| `resource-controller.instance.create`           | An event is generated when you provision a service instance. |
| `resource-controller.instance.update`           | An event is generated when you rename a service instance or when you change the service plan. |
| `<service-name>.instance.delete`           | An event is generated when a service instance is deleted. |
| `<service-name>.instance.schedule_reclaim` | An event is generated when a service instance is pending_reclamation. |
| `<service-name>.instance.restore`          | An event is generated when a service instance is restored. |
{: caption="Actions that generate platform events" caption-side="bottom"}

## Events for model alignment
{: #at_actions_model_alignment}

The following table lists the activity tracking events that are generated when you perform model alignment operations in {{site.data.keyword.instructlab_short}}. These events track actions related to managing models, taxonomies, and synthetic data generation (SDG) throughout the model alignment workflow. The events also include {{site.data.keyword.cos_short}} operations that occur when {{site.data.keyword.instructlab_short}} accesses or stores data in your connected storage buckets during the alignment process.

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `instructlab.model.read`                                 | Read details of a model training run |
| `instructlab.model.list`                                 | List model training runs |
| `instructlab.model.create`                                 | Create a model training run. |
| `instructlab.model.delete`                                 | Delete a model training run. |
| `instructlab.model.stop`                                 | Stop a model training run. |
| `cloud-object-storage.bucket.get`                                 | List all the objects in a bucket.                                   |
| `cloud-object-storage.object.put`                                 | Write and upload objects.                                   |
| `cloud-object-storage.object.get`                                 | View and download objects.                                    |
| `instructlab.taxonomy.read`                                 | Read details of a taxonomy |
| `instructlab.taxonomy.list`      | List taxonomies |
| `instructlab.taxonomy.create`      | Create taxonomies |
| `instructlab.taxonomy.delete`      | Delete taxonomies. |
| `instructlab.sdgdata.read`      | Read details of a data generation run |
| `instructlab.sdgdata.list`      | List data generation runs. |
| `instructlab.sdgdata.create`      | Create a data generation run. |
| `instructlab.sdgdata.delete`      | Delete a data generation run. |
| `instructlab.sdgdata.stop`      | Stop a data generation run. |
{: caption="List of model alignment events" caption-side="bottom"}
{: #modelalignment-table-1}
{: tab-title="Model alignment events"}
{: tab-group="model alignment"}
{: class="simple-tab-table"}

## Events for inferencing
{: #at_actions_inferencing}

The following table lists the activity tracking events that are generated when you perform inferencing operations in {{site.data.keyword.instructlab_short}}. These events track actions related to managing inference models and creating, reading, and deleting inference requests. Use these events to monitor how your aligned models are being deployed and used for inference workloads.

| Action                           | Description                        |
|----------------------------------|------------------------------------|
| `instructlab.inference-model.read`                                | Get a model by its identifier |
| `instructlab.inference-model.list`                                | List models using the OpenAI API |
| `instructlab.inference.create`                                | Generate an OpenAI-compatible chat completion for the given messages using the specified model |
| `instructlab.inference.read`                                | Describe a chat completion by its ID |
| `instructlab.inference.list`                                | List chat completions |
| `instructlab.inference.delete`                                | Delete a stored chat completion |
{: caption="Lists of inferencing events" caption-side="bottom"}
{: #inferencing-table-1}
{: tab-title="Inferencing events"}
{: tab-group="inferencing"}
{: class="simple-tab-table"}
