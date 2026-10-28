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

<p><strong data-param="BORUTA_ADMIN_OAUTH_CLIENT_ID">BORUTA_ADMIN_OAUTH_CLIENT_ID</strong> defines the administration OAuth client used to execute commands.</p>

<p><strong data-param="BORUTA_ADMIN_OAUTH_CLIENT_SECRET">BORUTA_ADMIN_OAUTH_CLIENT_SECRET</strong> defines the secret used to authenticate the administration OAuth client.</p>

<p><strong data-param="BORUTA_COMMAND_SUB">BORUTA_COMMAND_SUB</strong> defines the subject written to business-event logs for commands. It defaults to the current operating system user and hostname.</p>

</div>

The administration client must have the scope required by the selected resource. Every command creates a short-lived, single-use access token and revokes it after execution.

## Command syntax

```text
boruta-cli <resource> <action> [resource-id] [response-filter ...] [-- action-parameter ...]
```

<div class="parameters">

<p><strong data-param="Resource">Resource</strong> identifies an administration resource, such as `client`, `backend`, `identity_provider`, `scope`, `role`, `user`, `organization`, `upstream`, `key_pair`, `token`, or `logs`.</p>

<p><strong data-param="Action">Action</strong> identifies the administration API action to execute. Resource names and actions use snake case, for example `identity_provider` and `regenerate_key_pair`.</p>

<p><strong data-param="id">Resource ID</strong> identifies the resource affected by actions such as `show`, `update`, `delete`, `rotate`, `revoke`, and regeneration actions.</p>

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

## Provider configuration parameters

For available resource parameters, see the provider configuration pages:

- [Clients](/docs/provider-configuration/configure-clients) explains how OAuth clients are configured and managed.
  - [General configuration](/docs/provider-configuration/clients/general-configuration) lists the core client settings.
  - [Authentication](/docs/provider-configuration/clients/authentication) covers client and user authentication settings.
  - [Security](/docs/provider-configuration/clients/security) covers authorization, cryptographic signatures, and PKCE settings.
  - [Grant types](/docs/provider-configuration/clients/grant-types) lists the OAuth flows a client can use.
- [Identity providers](/docs/provider-configuration/configure-identity-providers) explains how end-user authentication interfaces are configured.
  - [General configuration](/docs/provider-configuration/identity-providers/general-configuration) lists the core identity provider settings.
  - [Templates edition](/docs/provider-configuration/identity-providers/templates-edition) describes editable authentication templates and their variables.
  - [Features](/docs/provider-configuration/identity-providers/features) lists optional authentication and user management features.
- [Backends](/docs/provider-configuration/configure-backends) explains how user registries and identity sources are configured.
  - [General configuration](/docs/provider-configuration/backends/general-configuration) lists the core backend settings.
  - [Type](/docs/provider-configuration/backends/type) covers internal and LDAP backend types.
  - [Email configuration](/docs/provider-configuration/backends/email-configuration) covers SMTP settings and email templates.
  - [Identity federation](/docs/provider-configuration/backends/identity-federation) covers external identity providers and their endpoints.
  - [Verifiable credentials](/docs/provider-configuration/backends/verifiable-credentials) covers credential issuance and presentation settings.
  - [User metadata](/docs/provider-configuration/backends/user-metadata) covers custom user attributes.
- [Scopes](/docs/provider-configuration/configure-scopes) explains scope names, labels, and visibility.
  - [Roles](/docs/provider-configuration/scopes/roles) explains how roles group scopes.
- [Service registry and upstreams](/docs/provider-configuration/configure-service-registry) explains node registration and gateway routing.
  - [General configuration](/docs/provider-configuration/service-registry/general-configuration) lists the core upstream settings.
  - [URIs](/docs/provider-configuration/service-registry/uris) covers the paths exposed by an upstream.
  - [Authorization](/docs/provider-configuration/service-registry/authorization) covers access rules for upstream requests.
  - [Security](/docs/provider-configuration/service-registry/security) covers upstream protection, rate limiting, and noise cancelling.
- [Error templates](/docs/provider-configuration/configuration/error-templates) describes the templates used for authentication and authorization errors.
- [Configuration files](/docs/provider-configuration/configuration-files) describes the YAML structure for static provider configuration.
- [Environment variables](/docs/provider-configuration/environment-variables) lists runtime settings used by the server and CLI.

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
