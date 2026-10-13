# Backends configuration | Identity federation

Backends parameters help to __manage identity storage and associated features__ within the server. Those are to keep credentials and identities while providing them abilities helping to manage authorization and authentication provided by the identity provider interfaces.

:::note Parameters sections
[Backends](/docs/provider-configuration/configure-backends) can be customized through either the Administration API or the user interface providing 6 __categories of settings__:

- General configuration
- Type
- Email configuration
- __Identity federation__
- Verifiable credentials
- User metadata
:::

## Identity federation parameters

<div class="parameters">

<p><strong data-param="federated_servers">Add federated server</strong> adds a federated server configuration to the current backend, helping to enable identity federation, using remote authentication methods, with it which can be materialized by a ["login with" button](/docs/provider-configuration/configure-identity-providers#global-templates-variables).</p>

:::note federated server configuration

You'll need to fill the `redirect_uri` on the federated server client configuration `${BORUTA_OAUTH_HOST}/accounts/backends/:backend_id/:federated_server_name/callback`

:::

### Federated server

<p><strong data-param="name">Server name</strong> help to recognize the configured remote authentication server within the administration interface.</p>

<p><strong data-param="client_id">Client ID</strong> is the configured `client_id` on the remote authentication server OAuth client configuration.</p>

<p><strong data-param="client_secret">Client secret</strong> is the configured `client_secret` on the remote authentication server OAuth client configuration.</p>

<p><strong data-param="base_url">Base URL</strong> is the base URL used for the interactions with the remote authentication server.</p>

<p><strong data-param="scope">scope (separated with a whitespace)</strong> are the scopes that are used in the authorization code grant flow authenticating with the remote server.</p>

<div class="parameter-entry">
<p><strong data-param="metadata_endpoints">Add Federated metadata</strong> metadata endpoint configuration that help to fetch protected resources using the granted access token.</p>
<ul>
<li><strong>Metadata endpoint URL</strong> is the URL where to fetch the user metadata</li>
<li><strong>Metadata endpoint claims (separated with a whitespace)</strong> is the list of the jsonpaths used to retreive user metadata. You can use the token <code>:all</code> to select all current node claims.</li>
</ul>
</div>

<p><strong data-param="discovery_path">Use OpenID discovery</strong> define if OpenID discovery is used to fetch server configuration (endpoints)</p>

:::note paths

All remote authentication server configuration endpoints can be expressed with either a path relative to the Base URL or with a full URL.

:::
### Discovery endpoints

<p><strong data-param="discovery_path">Discovery path</strong> the OpenID discovery path used to fetch server configuration. Configuration is fetched while persisting the backend configuration.</p>

### OpenID endpoints

<p><strong data-param="userinfo_path">Userinfo path</strong> the OpenID Userinfo path used to fetch user information.</p>

<p><strong data-param="authorize_path">Authorize path</strong> the OAuth 2.0 authorize path used to authenticate the current user.</p>

<p><strong data-param="token_path">Token path</strong> the OAuth 2.0 token path used to fetch an `access_token` given an authorization `code`.</p>

</div>

## User interface

![backend form](/assets/images/backends-identity-federation.png)
