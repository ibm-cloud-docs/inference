---

copyright:
  years: 2026
lastupdated: "2026-10-16"

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
| `instructlab.inference-embeddings.create` | An event is generated when you create an embedding vector representing the input text. |
| `instructlab.inference-session.read` | An event is generated when internal APIs are used for storing session read state in the UI. |
| `instructlab.inference-session.list` | An event is generated when internal APIs are used for storing session list state for the UI. |
| `instructlab.inference-session.delete` | An event is generated when internal APIs are used for storing session delete state in the UI. |
| `instructlab.inference-session.update` | An event is generated when internal APIs are used for storing session update state in the UI. |
{: caption="Lists of inference events" caption-side="bottom"}

## Mapping events to IAM roles and actions
{: #at-events-iam}

The following tables list actions and events along with the roles in {{site.data.keyword.iamlong}} (IAM) that you need to perform the action and generate the event.

| Platform role | Description |
| --- | --- |
| Viewer | As a viewer, you can view projects, but you can't modify them. |
| Operator | As an operator, you can perform platform actions required to configure and operate projects, such as viewing a service's dashboard. |
| Editor | As an editor, you can perform all platform actions except for managing the account and assigning access policies. |
| Administrator | As an administrator, you can perform all platform actions based on the resource to which this role is assigned, including assigning access policies to other users. |
| Service Configurator Reader | As a Service Configurator Reader, you can read service configurations for governance management. |
| Key Manager | As a key manager, you can perform platform actions required to manage resource keys, such as creating a new resource key. |
{: class="simple-tab-table"}
{: caption="IAM platform roles" caption-side="bottom"}
{: #iamrolesplatform}
{: tab-title="Platform roles"}
{: tab-group="IAM"}

| Service role | Description |
| --- | --- |
| Reader | As a reader, you can perform read-only actions within a service, such as viewing service-specific resources. |
| Writer | As a writer, you have permissions beyond the reader role, including creating and editing service-specific resources. |
| Manager | As a manager, you have permissions beyond the writer role to complete privileged actions as defined by the service. In addition, you can create and edit service-specific resources. |
{: class="simple-tab-table"}
{: caption="IAM service access roles" caption-side="bottom"}
{: #iamrolesservice}
{: tab-title="Service roles"}
{: tab-group="IAM"}

| Actions and events | Description | Roles |
| --- | --- | --- |
| `instructlab.dashboard.view` | View {{site.data.keyword.instructlab_short}} dashboards. | Operator, Administrator, Editor |
| `instructlab.inference.create` | Generate an OpenAI-compatible chat completion for the given messages by using the specified model. | Manager, Writer |
| `instructlab.inference.read` | Describe a chat completion by its ID. | Manager, Reader, Writer |
| `instructlab.inference.list` | List chat completions. | Manager, Reader, Writer |
| `instructlab.inference-model.read` | Get a model by its identifier. | Manager, Reader, Writer |
| `instructlab.inference-model.list` | List models by using the OpenAI API. | Manager, Reader, Writer |
| `instructlab.inference.delete` | Delete a stored chat completion. | Manager, Writer |
| `instructlab.inference-embeddings.create` | Create an embedding vector that represents the input text. | Manager, Writer |
| `instructlab.inference-session.read` | Internal APIs used for storing session read state in the console. | Manager, Reader, Writer |
| `instructlab.inference-session.list` | Internal APIs used for storing session list state for the console. | Manager, Reader, Writer |
| `instructlab.inference-session.delete` | Internal APIs used for storing session delete state in the console. | Manager, Writer |
| `instructlab.inference-session.update` | Internal APIs used for storing session update state for the console. | Manager, Writer |
{: class="simple-tab-table"}
{: caption="IAM actions" caption-side="bottom"}
{: #iamactions}
{: tab-title="Actions"}
{: tab-group="IAM"}
