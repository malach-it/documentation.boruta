# Backends configuration | Email configuration

Backends parameters help to __manage identity storage and associated features__ within the server. Those are to keep credentials and identities while providing them abilities helping to manage authorization and authentication provided by the identity provider interfaces.

:::note Parameters sections
[Backends](/docs/provider-configuration/configure-backends) can be customized through either the Administration API or the user interface providing 6 __categories of settings__:

- General configuration
- Type
- __Email configuration__
- Identity federation
- Verifiable credentials
- User metadata
:::

## Email configuration parameters

<div class="parameters">

### SMTP configuration

<p><strong data-param="smtp_from">From</strong> is the `from` email header field, corresponding to the sender email.</p>

<p><strong data-param="smtp_relay">Relay</strong> is the SMTP server hostname which will be relaying the emails.</p>

<p><strong data-param="smtp_username">Username</strong> the `username` part of the credentials used to connect to the SMTP server.</p>

<p><strong data-param="smtp_password">Password</strong> the `password` part of the credentials used to connect to the SMTP server.</p>

<p><strong data-param="smtp_ssl">SSL</strong> determine if the connection to the SMTP server is to be encrypted using SSL.</p>

<p><strong data-param="smtp_tls">TLS</strong> can be one of __Always__, __Never__, __If available__, determine if the emails are to be encrypted using TLS.</p>

<p><strong data-param="smtp_port">Port</strong> is the SMTP server port to be used.</p>

### Email templates

<p><strong data-param="confirmation_instructions">Edit confirmation template</strong> is the template used while sending email confirmation emails.</p>

<p><strong data-param="reset_password_instructions">Edit reset password template</strong> is the template used while sending reset password emails.</p>

<p><strong data-param="tx_code">Edit transaction code template</strong> is the template used while sending OpenID 4 Verifiable Credentials issuance `tx_code` emails.</p>

</div>

## User interface

![backend form](/assets/images/backends-email-configuration.png)
