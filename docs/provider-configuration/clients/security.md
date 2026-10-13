# Clients configuration | Security

Client attributes help to __manage the authorization capabilities for OAuth 2.0 and satellites flows__. They provide a high level of customization helping the server to be integrated within infrastructures seamlessly. Those configurations help the flows to be both business and technically adapted for the addressed use case.

:::note Parameters sections
[OAuth clients](/docs/provider-configuration/configure-clients) can be customized through either the [Administration API](/api/list-clients) or the user interface providing 4 __categories of settings__:

- General configuration
- Authentication
- __Security__
- Grant types
:::

## Cryptographic Signatures

boruta gives means to __implement and connect signature adapters__ which provide means for signing the authorization artifacts both from the federated identity (ID Tokens) and the decentralized identity (Verifiable Credentials). __Out of the box__, an internal (boruta provided) and an Universal adapter are implemented and ready to use. Those support cryptographic material generation and use along side with Decentralized IDentifiers support. Public and Private Keys are the __base for enabling signatures__ and the public part of the keys is exposed through the jwks OpenID endpoint. Those keys will be used for the signature of ID Tokens, Userinfo (if needed) and Verifiable Credentials. This enables to connect boruta to __Hardware Security Modules (HSM)__ with low effort, enabling them to store cryptographic keys in a secure enclave.

:::note Key pair types
The type of the generated key pairs is tied to the signature algorithm used for JWTs signature:
- __RSA keys__ enforce the JWTs signature algorithm to be of the `RS` algorithm class
- __Elliptic curve keys__ enforce the JWTs signature algorithm to be of the `ES` algorithm class
- __Universal keys__ enforce the JWTs signature algorithm to be of the `EdDSA` algorithm class
:::

## Security parameters

<div class="parameters">

<p><strong data-param="signatures_adapter">Signatures adapter</strong> defines the adapter used to generate and use the client's cryptographic keys. The internal and Universal signatures adapters are available by default.</p>

<p><strong data-param="key_pair_type">Key type</strong> defines the type and parameters of the key pair generated for the client. RSA keys require a modulus and exponent size, elliptic curve keys require a curve, and Universal keys use the Universal signatures adapter.</p>

<p><strong data-param="id_token_signature_alg">ID token signature algorithm</strong> is the algorithm used to sign ID Token JWTs. It have to be in correspondance with the key pair type.</p>

<p><strong data-param="userinfo_signed_response_alg">Userinfo response signature algorithm</strong> is the algorithm used to sign userinfo response JWTs, the response being possibily not encoded and signed. It have to be in correspondance with the key pair type.</p>

### Authorization

<p><strong data-param="enforce_dpop">Enforce Demonstration Proof-of-Possession (DPoP)</strong> enables the client to only support [DPoP](https://datatracker.ietf.org/doc/html/rfc9449) requests.</p>

<p><strong data-param="enforce_tx_code">Enforce pre-authorized code transaction code</strong> enforces the presentation of a `tx_code` while issuing verifiable credentials.</p>

<p><strong data-param="authorize_scope">Authorize scope</strong> would determine if the client defines the specific public and private scopes to be authorized.</p>

<p><strong data-param="authorized_scopes">Authorized scopes</strong> would be the list of scopes that can be granted with this client.</p>

<p><strong data-param="check_public_client_id">Check public client id</strong> enforces the check of the presentation `vp_token` against the `client_id` parameter in OpenID 4 Verifiable Presentations flows.</p>

<p><strong data-param="trusted_hosts">Trusted hosts</strong> defines the hosts from which the client is allowed to retrieve remote resources such as a JSON Web Key Set.</p>

<p><strong data-param="trusted_authorities">Trusted authorities</strong> defines the trusted decentralized identifiers authorized as authorities for the client.</p>

### Proof Key for Code Exchange

<p><strong data-param="pkce">PKCE</strong> would determine if [Proof Key for Code Exchange](https://datatracker.ietf.org/doc/html/rfc7636) flow is enforced using this client.</p>

<p><strong data-param="public_refresh_token">Public refresh token</strong> allow refreshing tokens without providing a `client_secret`</p>

<p><strong data-param="public_revoke">Public revoke</strong> allow to revoke tokens without providing a `client_secret`</p>

</div>

## User interface

![client form](/assets/images/oauth-clients-security.png)
