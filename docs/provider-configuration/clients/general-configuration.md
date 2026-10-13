# Clients configuration | General configuration

Client attributes help __manage the authorization capabilities for OAuth 2.0 and satellites flows__. They provide a high level of customization helping the server to be integrated within infrastructures seamlessly. Those configurations help the flows to be both business and technically adapted for the addressed use case.

:::note Parameters sections
[OAuth clients](/docs/provider-configuration/configure-clients) can be customized through either the [Administration API](/api/list-clients) or the user interface providing 4 __categories of settings__:

- __General configuration__
- Authentication
- Security
- Grant types
:::

## General configuration parameters

<div class="parameters">

 <p><strong data-param="id">Id</strong> would be the identifier of the client, it will be used as the OAuth `client_id` parameter. Note that once the client is created this value can't be changed.</p>

 <p><strong data-param="public_client_id">Public client ID</strong> would be the identifier of the public client, linked to the issuer, to be active it must have the `BORUTA_OAUTH_BASE_URL` environment variable value.</p>

:::note public clients

Public clients are used in __Verifiable Credentials presentations__. They are identified by a DID as the provided `client_id` in authorization requests and __do not require authentication__ as the identified resource owner is represented by the wallet that is cryptographically verified.

:::

 <p><strong data-param="secret">Secret</strong> would be used as the `client_secret` parameter in OAuth flows.</p>

 <p><strong data-param="name">Name</strong> would be accessible in the consent template to highlight for which client the resource owner delegates access to the requested scopes</p>

 <p><strong data-param="access_token_ttl">Access token TTL</strong> would be the access tokens time to live.</p>

 <p><strong data-param="agent_token_ttl">Agent token TTL</strong> would be the time to live of tokens issued through the agent credentials grant.</p>

 <p><strong data-param="authorization_code_ttl">Authorization code TTL</strong> would be the time to live of codes during authorization code grant.</p>

 <p><strong data-param="refresh_token_ttl">Refresh token TTL</strong> would be the time to live of refresh tokens helping to obtain newly generated access tokens.</p>

 <p><strong data-param="id_token_ttl">Id token TTL</strong> would be the time to live of ID tokens expressed in `exp` JWT claim.</p>

 <p><strong data-param="authorization_request_ttl">Authorization request TTL</strong> would be the time to live of the requests as described in [RFC 9126 - OAuth 2.0 Pushed Authorization Requests](https://datatracker.ietf.org/doc/html/rfc9126).</p>

 <p><strong data-param="redirect_uris">Redirect URIs</strong> would be the allowed redirect URIs in OAuth / OpenID Connect flows.</p>

<div class="parameter-entry">
<p><strong data-param="response_mode">Response mode</strong> enables to determine if Verifiables Credentials issuance and presentation deeplinks are redirections (same device) or displayed within an interface:</p>
<ul>
<li>__direct_post__ the user is redirected with an HTTP 302</li>
<li><strong>post</strong> a QR code and a link is displayed to the user</li>
</ul>
</div>

</div>

## User interface
![client form](/assets/images/oauth-clients-general-configuration.png)
