# Backends configuration | Verifiable Credentials

Backends parameters help to __manage identity storage and associated features__ within the server. Those are to keep credentials and identities while providing them abilities helping to manage authorization and authentication provided by the identity provider interfaces.

:::note Parameters sections
[Backends](/docs/provider-configuration/configure-backends) can be customized through either the Administration API or the user interface providing 6 __categories of settings__:

- General configuration
- Type
- Email configuration
- Identity federation
- __Verifiable credentials__
- User metadata
:::

## Verifiable credentials parameters

<div class="parameters">

<p><strong data-param="verifiable_credentials">Add Verifiable credential</strong> exposes a Verifiable Credential for the client, provided its [configuration](/docs/provider-configuration/backends/verifiable-credentials#verifiable-credentials-issuance).</p>

<p><strong data-param="verifiable_presentations">Add Verifiable presentation</strong> enable the users to present Verifiable Credentials, given their [definition](/docs/provider-configuration/backends/verifiable-credentials#verifiable-presentations).</p>

### Verifiable Credentials Issuance

<p><strong data-param="credential_identifier">Credential identifier</strong> the identifier used to identify the credential within the issuance protocols. Would be accessible through `presentation_details` or an OAuth scope. The latter overiding the other.</p>

<p><strong data-param="vct">Verifiable credential type</strong> would set the `vct` claim in Verifiable Credentials depending their format.</p>

<div class="parameter-entry">
<p><strong data-param="version">Version</strong> the OpenID 4 Verifiable Credentials Issuance version used to expose the credential. Would be one of:</p>
<ul>
<li><strong>Draft 11</strong></li>
<li><strong>Draft 13</strong></li>
</ul>
</div>

<div class="parameter-entry">
<p><strong data-param="format">Format</strong> would be the format of the exposed credential.</p>
<ul>
<li>__jwt_vc__ from <a href="https://www.w3.org/TR/vc-data-model-1.0">W3C Verifiable Credential Data Model 1.0</a></li>
<li><strong>jwt_vc_json</strong> from <a href="https://www.w3.org/TR/vc-data-model-1.0">W3C Verifiable Credential Data Model 1.0</a></li>
<li><strong>vc+sd-jwt</strong> from <a href="https://www.ietf.org/archive/id/draft-ietf-oauth-sd-jwt-vc-08.html">SD-JWT-based Verifiable Credentials</a></li>
</ul>
</div>

<p><strong data-param="defered">Defered</strong> define whenever the credential issuance is deffered or not.</p>

<p><strong data-param="types">Types (separated with a whitespace)</strong> the types used to identify the credential within the issuance protocols.</p>

<p><strong data-param="time_to_live">Time to live (in seconds)</strong> the time to live of the overall credential, defining its expiration.</p>

<p><strong data-param="claims">Add claim</strong> would add a claim containing identity information to the credential.</p>

<p><strong data-param="scopes">Scope restriction</strong> to access the verifiable credential, a list of scopes can be requested. The access token used to obtain the credential must be granted those scopes.</p>

#### Claims

<div class="parameter-entry">
<p><strong data-param="type">Type</strong> the type of the current node in the claim tree.</p>
<ul>
<li><strong>attribute</strong> would be a standard attribute</li>
<li><strong>object</strong> would be an object giving the ability to have children claims</li>
<li><strong>array</strong> would be an array containing different claims</li>
</ul>
</div>

<p><strong data-param="name">Name</strong> would be the name of the claim giving the `key` of the attribute.</p>

<p><strong data-param="label">Label</strong> would be a friendly labeling of the claim, stated in the `display` of exposed supported credentials.</p>

<p><strong data-param="pointer">Pointer</strong> would give the way to access the claim `value` within the current resource owner claims.</p>

#### Display

<p><strong data-param="display.name">Name</strong> would be the display name of the credential.</p>

<p><strong data-param="display.background_color">Background color</strong> would give the background color of the displayed credential card.</p>

<p><strong data-param="display.text_color">Text color</strong> would give the text color of the displayed credential card.</p>

<p><strong data-param="display.logo.url">Logo URL</strong> would give the logo URL of the displayed credential card.</p>

<p><strong data-param="display.logo.alt_text">Logo alt text</strong> would give the logo alternative text of the displayed credential card.</p>

### Verifiable Presentations

<p><strong data-param="presentation_identifier">Presentation identifier</strong> the identifier of the presentation that would be requested while asking to request a credential presentation.</p>

<p><strong data-param="presentation_definition">Presentation definition</strong> the given definition of the requested presentation to be validated.</p>

</div>

## User interface

![backend form](/assets/images/backends-verifiable-credentials.png)
