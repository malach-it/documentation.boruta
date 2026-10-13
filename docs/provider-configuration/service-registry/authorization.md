# Service registry configuration | Authorization

Authorization parameters help __protect upstream routes__ before traffic reaches the backend service. They define the access-token requirement, the required OAuth scopes, and the forwarded identity context sent to the upstream.

:::note Parameters sections
[Service registry](/docs/provider-configuration/configure-service-registry) upstreams can be customized through either the [Administration API](/api/list-upstreams), the user interface, or static configuration files. The configuration is organized around:

- [General configuration](/docs/provider-configuration/service-registry/general-configuration)
- [URIs](/docs/provider-configuration/service-registry/uris)
- __Authorization__
- [Security](/docs/provider-configuration/service-registry/security)
:::

## Authorization parameters

<div class="parameters">

<p><strong data-param="authorize">Authorize</strong> requires requests to provide a valid OAuth access token before they are forwarded.</p>

<p><strong data-param="authorization_type">Authorization type</strong> defines authorization protocol, either Basic Auth credentials, or OAuth bearer.</p>

<p><strong data-param="required_scopes">Required scopes</strong> restrict authorized traffic by HTTP method. Keys can be HTTP methods such as `GET`, `POST`, `PUT`, `PATCH`, `DELETE`, `HEAD`, `OPTIONS`, or `*` for the default rule. Values are the OAuth scopes required for the method.</p>

<p><strong data-param="error_content_type">Error content type</strong> defines the content type returned for gateway authorization errors.</p>

<p><strong data-param="forbidden_response">Forbidden response</strong> customizes the response returned when the access token is valid but does not contain the required scopes.</p>

<p><strong data-param="unauthorized_response">Unauthorized response</strong> customizes the response returned when the request has no valid access token.</p>

<p><strong data-param="forwarded_token_signature_alg">Forwarded token signature algorithm</strong> enables boruta to send backend request context in the `X-Forwarded-Authorization` header. Supported algorithms are `HS256`, `HS384`, `HS512`, `RS256`, `RS384`, and `RS512`.</p>

<p><strong data-param="forwarded_token_secret">Forwarded token secret</strong> signs forwarded tokens when using an `HS*` algorithm. Leave it empty to let boruta generate one.</p>

<p><strong data-param="forwarded_token_private_key">Forwarded token private key</strong> signs forwarded tokens when using an `RS*` algorithm. Leave it empty to let boruta generate a key pair.</p>

<p><strong data-param="forwarded_token_public_key">Forwarded token public key</strong> is the public key matching the generated or configured private key.</p>

</div>

## User interface

![upstream authorization](/assets/images/upstream-authorization.png)
