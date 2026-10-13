# Identity providers configuration | General configuration

Identity providers parameters help to __manage end-user means of authentication__. It gives the ability for them to follow the configured way they have to authenticate themselves to the service. Beyond authentication, the server provide ways for the end-users to manage identities and access.


:::note Parameters sections
[Identity providers](/docs/provider-configuration/configure-identity-providers) can be customized through either the [Administration API](/api/list-identity-providers) or the user interface providing 2 __categories of settings__:

- __General configuration__
- Templates edition
- Features
:::

## General configuration parameters

<div class="parameters">

<p><strong data-param="name">Name</strong> help to recognize the configured identity provider within the administration interface.</p>

<p><strong data-param="backend_id">Backend</strong> set the associated backend providing the end-user credentials, configurations and attributes.</p>

<div class="parameter-entry">
<p><strong data-param="check_password">Sessions</strong> help to configure the log in temaplates and features giving means for the user to be identified giving its username.</p>
<ul>
<li><strong>check password</strong> switches the password requirement for authentication. Whenn disabled, the server creates a one time login associated to the username.</li>
</ul>
</div>

<div class="parameter-entry">
<p><strong data-param="templates">Global templates</strong> allow to edit templates that can't be desactivated:</p>
<ul>
<li><strong>Send password instructions</strong> is the template that help to send a <a href="/docs/provider-configuration/backends/email-configuration">recover password email</a> giving the end-user username</li>
<li><strong>Reset password</strong> help for the end-user to edit his password after following the recovery link that has been sent through an email</li>
</ul>
</div>

</div>

## User interface

![identity provider form](/assets/images/identity-providers-general-configuration.png)
