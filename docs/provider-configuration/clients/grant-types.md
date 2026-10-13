# Clients configuration | Grant types

Client attributes help to __manage the authorization capabilities for OAuth 2.0 and satellites flows__. They provide a high level of customization helping the server to be integrated within infrastructures seamlessly. Those configurations help the flows to be both business and technically adapted for the addressed use case.

:::note Parameters sections
[OAuth clients](/docs/provider-configuration/configure-clients) can be customized through either the [Administration API](/api/list-clients) or the user interface providing 4 __categories of settings__:

- General configuration
- Authentication
- Security
- __Grant types__
:::

## Grant types parameters

The Authorization Server allow to enable and disable the implemented flows for a specific client via the currently described switches. Those are to provide better security __restricting the means of access obtention__.

<div class="parameters">

<p><strong data-param="client_credentials">client_credentials</strong> switches the ability to perform the [Client Credentials](https://datatracker.ietf.org/doc/html/rfc6749#section-4.4) flow interacting with the configured client.</p>

<p><strong data-param="agent_credentials">agent_credentials</strong> switches the ability to issue an agent token for the configured client, binding the data and configuration supplied in the token request.</p>

<p><strong data-param="code_chain">code_chain</strong> switches the ability to issue an authorization code from an ID token and optionally link it to a previous authorization code, forming a code chain.</p>

<p><strong data-param="password">password</strong> switches the ability to perform the [Resource Owner Password Credentials](https://datatracker.ietf.org/doc/html/rfc6749#section-4.3) flow interacting with the configured client.</p>

<p><strong data-param="authorization_code">authorization_code</strong> switches the ability to perform the [Authorization Code Grant](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1) flow interacting with the configured client.</p>

<p><strong data-param="agent_code">agent_code</strong> switches the ability to exchange an authorization code for an agent token, binding the data and configuration supplied in the token request.</p>

<p><strong data-param="refresh_token">refresh_token</strong> switches the ability to perform the [Refresh Token](https://datatracker.ietf.org/doc/html/rfc6749#section-6) flow interacting with the configured client.</p>

<p><strong data-param="implicit">implicit</strong> switches the ability to perform the [Implicit Grant](https://datatracker.ietf.org/doc/html/rfc6749#section-4.2) flow interacting with the configured client.</p>

<p><strong data-param="preauthorized_code">preauthorized_code</strong> switches the ability to perform the OpenID 4 Verifiable Credentials Issuance [Preauthorized Code](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html#section-3.5) flow interacting with the configured client.</p>

<p><strong data-param="id_token">id_token</strong> switches the ability to perform the OpenID Connect [Hybrid Grant](https://openid.net/specs/openid-connect-core-1_0.html#HybridFlowAuth) flow interacting with the configured client.</p>

<p><strong data-param="vp_token">vp_token</strong> switches the ability to perform the [OpenID 4 Verifiable Presentations](https://openid.net/specs/openid-4-verifiable-presentations-1_0.html#section-3) and [SIOPV2](https://openid.net/specs/openid-connect-self-issued-v2-1_0.html#section-3) flow interacting with the configured client.</p>

<p><strong data-param="revoke">revoke</strong> switches the ability to perform the [Token Revocation](https://datatracker.ietf.org/doc/html/rfc7009#section-2) flow interacting with the configured client.</p>

<p><strong data-param="introspect">introspect</strong> switches the ability to perform the [Token Introspection](https://datatracker.ietf.org/doc/html/rfc7662) flow interacting with the configured client.</p>

</div>

## User interface
![client form](/assets/images/oauth-clients-grant-types.png)
