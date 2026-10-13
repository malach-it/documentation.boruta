# Identity providers configuration | Templates edition

Identity provider templates are to be seen by the end-user, they are __editable using [Mustache](https://mustache.github.io/) templating engine__ helping to get access to global and page-specific variables. You can at any moment reset your changes to go back to a default template. User navigation help going through the customized templates giving the __best user experience__.

:::note Parameters sections
[Identity providers](/docs/provider-configuration/configure-identity-providers) can be customized through either the [Administration API](/api/list-identity-providers) or the user interface providing 2 __categories of settings__:

- General configuration
- __Templates edition__
- Features
:::

### Global templates variables

<div class="parameters">

<p><strong data-param="federated_servers.{name}.login_url">federated_servers.&#123;federated server name&#125;.login_url</strong> gives the login URL in case of identity federation helping to implement "login with" button. That variable is associated with the [configuration of a federated server](/docs/provider-configuration/backends/identity-federation).</p>

<p><strong data-param="messages">messages</strong> gives the server messages array having for each of them `type` and `content` attributes.</p>

<p><strong data-param="_csrf_token">_csrf_token</strong> gives the anti request forgery token that is to be sent along with each end-user form.</p>

<p><strong data-param="errors">errors</strong> gives the current errors array having for each of them a `message` attribute.</p>

<p><strong data-param="client">client</strong> gives the current client associated to the request, it has all the corresponding client attributes.</p>

#### The server URL that the end-user can navigate to

<p><strong data-param="delete_user_session_path">delete_user_session_path</strong> accessible through `DELETE`</p>

<p><strong data-param="edit_user_path">edit_user_path</strong> accessible through `GET`</p>

<p><strong data-param="destroy_user_path">destroy_user_path</strong> accessible through `POST`</p>

<p><strong data-param="new_user_totp_registration_path">new_user_totp_registration_path</strong> accessible through `GET`</p>

<p><strong data-param="create_user_totp_registration_path">create_user_totp_registration_path</strong> accessible through `POST`</p>

<p><strong data-param="new_user_webauthn_registration_path">new_user_webauthn_registration_path</strong> accessible through `GET`</p>

<p><strong data-param="create_user_webauthn_registration_path">create_user_webauthn_registration_path</strong> accessible through `POST`</p>

<p><strong data-param="new_user_registration_path">new_user_registration_path</strong> accessible through `GET`</p>

<p><strong data-param="new_user_reset_password_path">new_user_reset_password_path</strong> accessible through `GET`</p>

<p><strong data-param="new_user_session_path">new_user_session_path</strong> accessible through `GET`</p>

<p><strong data-param="update_user_reset_password_path">update_user_reset_password_path</strong> accessible through `POST`</p>

<p><strong data-param="update_user_path">update_user_path</strong> accessible through `POST`</p>

#### Identity provider configurations

<p><strong data-param="registrable?">registrable?</strong> equals to `true` if the identity provider user registration feature is enabled.</p>

<p><strong data-param="totpable?">totpable?</strong> equals to `true` if the identity provider Time base One Time Password feature is enabled.</p>

<p><strong data-param="user_editable?">user_editable?</strong> equals to `true` if the identity provider user edition feature is enabled.</p>

</div>

### Page specific variables

<div class="parameters">

<p><strong data-param="current_user">current_user</strong> the current user object navigating on the interface. The `username`, `webauthn_registered_at`, `totp_registered_at` and `metadata` attributes are exposed.</p>

<p><strong data-param="client">client</strong> the current oauth client the user is navigating to. The `name` attribute is exposed.</p>

<p><strong data-param="scopes">scopes</strong> the list of requested scopes objects. The `name`, `label` and `public` attributes are exposed.</p>

<p><strong data-param="webauthn_options">webauthn_options</strong> the webauthn option to be given to given to the browser API. The `rp`, `user`, `challenge`, `credential_id` and `publicKeyCredParams` attributes are exposed.</p>

<p><strong data-param="base64_credential_offer_qr_code">base64_credential_offer_qr_code</strong> the base64 encoded credential offer QR code image.</p>

<p><strong data-param="credential_offer_deeplink">credential_offer_deeplink</strong> the credential offer deeplink text.</p>

<p><strong data-param="base64_presentation_qr_code">base64_presentation_qr_code</strong> the base64 encoded verifiable presentation QR code image.</p>

<p><strong data-param="presentation_deeplink">presentation_deeplink</strong> the verifiable presentation deeplink text.</p>

<p><strong data-param="code">code</strong> the credential offer or verifiable presentation code used to trigger presentation server sent events.</p>
</div>
