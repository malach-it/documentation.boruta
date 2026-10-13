# Identity providers configuration | Features

As configuration, identity provider __features can be toggled__ to be activated or disabled. Those features __customize the authentication flow__ the user will encounter for identifying themselves to the service. The features give abilities such as session management, Multi-Factor Authentication, user management, or consent.

:::note Parameters sections
[Identity providers](/docs/provider-configuration/configure-identity-providers) can be customized through either the [Administration API](/api/list-identity-providers) or the user interface providing 2 __categories of settings__:

- General configuration
- Templates edition
- __Features__
:::

## Features parameters

<div class="parameters">

<p><strong data-param="choose_session">Choose session</strong> give the ability for the user to choose to keep current session or to create a new one on authorization.</p>

<div class="parameter-entry">
<p><strong data-param="webauthnable">Webauthn</strong> give the ability for end users to register an authentication second factor with Passkeys. __enforce Webauthn__ enforces to use webauthn as a second authentication factor.</p>
<ul>
<li>__webauthn_options__ variable is available on Webauthn registration template, corresponding to an object with all attributes required for a Webauthn registration.</li>
</ul>
</div>

<div class="parameter-entry">
<p><strong data-param="totpable">Time based One Time Password</strong> give the ability for end users to register an authentication second factor with TOTP. __enforce TOTP__ enforces to use TOTP as a second authentication factor.</p>
<ul>
<li>__totp_secret__ variable is available on TOTP registration template</li>
</ul>
</div>

<p><strong data-param="registrable">Registration</strong> give the ability for end users to register within the given identity provider. If activated the user have access to registration page and can provide its own credentials.</p>

<p><strong data-param="user_editable">User information edition</strong> give the ability for end users to update their account information.</p>

<p><strong data-param="confirmable">Email confirmation</strong> confirm new registred accounts. sends an email in order to confirm user's email.</p>

<div class="parameter-entry">
<p><strong data-param="consentable">User consent</strong> users have to consent requested scopes to be authorized.</p>
<ul>
<li><strong>scopes</strong> variable is available on consent template, corresponding to an array of objects with <code>name</code>, <code>label</code> and <code>public</code> attributes</li>
</ul>
</div>

<div class="parameter-entry">
<p><strong data-param="credential_offer">Credential offer</strong> OpenID 4 Verifiable Credentials Issuance credential offer template edition.</p>
<ul>
<li><strong>base64_credential_offer_qr_code</strong> variable is available on <strong>Credential offer</strong> template, corresponding to the base 64 encoded current credential offer deeplink</li>
<li><strong>credential_offer_deeplink</strong> variable is available on <strong>Credential offer</strong> template, corresponding to the current credential offer deeplink</li>
</ul>
</div>

<div class="parameter-entry">
<p><strong data-param="cross_device_presentation">Credential presentation</strong> OpenID 4 Verifiable Presentations presentation request template edition.</p>
<ul>
<li>__base64_presentation_qr_code__ variable is available on Presentation template, corresponding to the base 64 encoded current credential offer deeplink</li>
<li>__presentation_deeplink__ variable is available on Credential offer template, corresponding to the current credential offer deeplink</li>
</ul>
</div>

</div>

## User interface

![identity provider form](/assets/images/identity-providers-features.png)
