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
