# Command line interface

The boruta command line interface provides access to administration resources without using the administration user interface. The `boruta` and `boruta_admin` releases include the `bin/boruta-cli` executable.

With a release, run commands from the release directory:

```bash
bin/boruta-cli role index
```

With the default Docker Compose environment, run the executable in the boruta container:

```bash
docker compose exec boruta /app/bin/boruta-cli role index
```

## Authentication

The command line interface authenticates with the administration OAuth client configured by the following [environment variables](/docs/provider-configuration/environment-variables):

<div class="parameters">

__BORUTA_ADMIN_OAUTH_CLIENT_ID__ defines the administration OAuth client used to execute commands.

__BORUTA_ADMIN_OAUTH_CLIENT_SECRET__ defines the secret used to authenticate the administration OAuth client.

__BORUTA_COMMAND_SUB__ defines the subject written to business-event logs for commands. It defaults to the current operating system user and hostname.

</div>

The administration client must have the scope required by the selected resource. Every command creates a short-lived, single-use access token and revokes it after execution.

## Command syntax

```text
boruta-cli <resource> <action> [resource-id] [response-filter ...] [-- action-parameter ...]
```

<div class="parameters">

__Resource__ identifies an administration resource, such as `client`, `backend`, `identity_provider`, `scope`, `role`, `user`, `organization`, `upstream`, `key_pair`, `token`, or `logs`.

__Action__ identifies the administration API action to execute. Resource names and actions use snake case, for example `identity_provider` and `regenerate_key_pair`.

__Resource ID__ identifies the resource affected by actions such as `show`, `update`, `delete`, `rotate`, `revoke`, and regeneration actions.

__Response filters__ select attributes or nested paths from the YAML response. They are placed before `--`.

__Action parameters__ are sent to the administration action. They are placed after `--` and use `key:value` syntax.

</div>

Common actions are available as follows:

| Resource | Actions |
| --- | --- |
| `backend`, `client`, `identity_provider`, `key_pair`, `organization`, `role`, `scope`, `upstream`, `user` | `index`, `create`, `show`, `update`, `delete` |
| `client` | `regenerate_did`, `regenerate_key_pair` |
| `key_pair` | `rotate` |
| `logs` | `index` |
| `service_registry` | `index` |
| `token` | `index`, `revoke` |
| `upstream` | `node_list` |
| `configuration` | `configuration`, `example_configuration_file` |

## Reading resources

Use `index` to list resources and `show` with a resource ID to retrieve one resource:

```bash
bin/boruta-cli client index
bin/boruta-cli client show 00000000-0000-0000-0000-000000000001
bin/boruta-cli upstream node_list
```

Successful commands return YAML. For example, listing service-registry nodes returns:

```yaml
---
"data":
  - "boruta@boruta"
  - "boruta@kagome-1"
  - "boruta@kagome-2"
```

## Filtering responses

Place attribute names after the optional resource ID to restrict the YAML response:

```bash
bin/boruta-cli client show 00000000-0000-0000-0000-000000000001 id name public_client_id
```

```yaml
---
"data":
  "id": "00000000-0000-0000-0000-000000000001"
  "identity_provider":
    "id": "00000000-0000-0000-0000-000000000001"
    "name": "Example identity provider"
  "name": "Example client"
  "public_client_id": null
```

Attribute filters match at every level of the response. In this example, `id` and `name` therefore also select matching identity-provider attributes.

Use colon-separated paths to select nested values. Numeric segments select zero-based array indices:

```bash
bin/boruta-cli backend show BACKEND_ID verifiable_credentials:0:claims:0
```

## Creating and updating resources

Place action parameters after `--` to distinguish them from response filters:

```bash
bin/boruta-cli scope create -- 'name:"billing:read"' label:"Read billing data"
bin/boruta-cli upstream update UPSTREAM_ID -- scheme:https port:443
bin/boruta-cli client update CLIENT_ID -- identity_provider:id:IDENTITY_PROVIDER_ID
```

Colon-separated parameter segments create nested maps:

```bash
bin/boruta-cli client update CLIENT_ID -- identity_provider:id:IDENTITY_PROVIDER_ID
```

Numeric segments address zero-based array indices:

```bash
bin/boruta-cli backend update BACKEND_ID -- verifiable_credentials:0:claims:0:label:"Given name"
```

An unquoted `[]` sends an empty array:

```bash
bin/boruta-cli client update CLIENT_ID -- redirect_uris:[]
bin/boruta-cli backend update BACKEND_ID -- verifiable_credentials:0:claims:[]
```

Quote the value as `"[]"` when the literal string is required. Explicit action parameters override defaults applied by the command.

:::note Parameter parsing without a separator
Commands can omit `--` and pass action parameters directly. Indexed paths on read actions are treated as response filters. Using `--` for create and update actions makes the distinction between response filters and action parameters explicit.
:::

## Query parameters

Parameters for read actions are sent as query parameters. The following command requests business events and filters the output to three attributes:

```bash
bin/boruta-cli logs index request_id status label -- events_only:true
```

```yaml
---
"events":
  - "label": "boruta_admin - client update"
    "request_id": "GNRZFdWLKwXFB7AABeZB"
    "status": "success"
```

## Errors and exit status

Administration errors are returned as YAML and cause a non-zero exit status. An unknown resource or action returns a CLI error:

```bash
bin/boruta-cli unknown index
```

```yaml
---
"code": "CLI_ERROR"
"errors":
  "resource":
    - "{:unknown_resource_action, \"unknown\", \"index\"}"
"message": "{:unknown_resource_action, \"unknown\", \"index\"}"
```

Calling `boruta-cli` without the required resource and action prints the command usage and exits with status `64`.

## Running against an active release

When `RELEASE_NODE` and `RELEASE_COOKIE` are set and the release node is reachable, `boruta-cli` executes the command through release RPC. Otherwise, it starts the required applications locally with their network listeners disabled and accesses the configured database directly.

The CLI changes database-backed configuration. Static configuration loaded later can overwrite those changes.
