# Backends configuration | Type

Backends parameters help to __manage identity storage and associated features__ within the server. Those are to keep credentials and identities while providing them abilities helping to manage authorization and authentication provided by the identity provider interfaces.

:::note Parameters sections
[Backends](/docs/provider-configuration/configure-backends) can be customized through either the Administration API or the user interface providing 6 __categories of settings__:

- General configuration
- __Type__
- Email configuration
- Identity federation
- Verifiable credentials
- User metadata
:::

## Type parameters

<div class="parameters">

<div class="parameter-entry">
<p><strong data-param="type">Type</strong> is the backend type, can be one of:</p>
<ul>
<li><strong>Internal</strong> user credentials are stored within boruta postgreSQL dependency database</li>
<li><strong>LDAP</strong> user credentials are checked and updated against a LDAP compliant server</li>
</ul>
</div>

### Internal configuration

<div class="parameter-entry">
<p><strong data-param="password_hashing_alg">Password hashing algorithm</strong> is the algorithm used to hash the user passwords that then will be stored in their hashed form. All those hashing algorithms are provided with their __custom parameters__.</p>
<ul>
<li><strong>Argon2</strong> uses <a href="https://en.wikipedia.org/wiki/Argon2">Argon2</a> hashing algorithm</li>
<li><strong>Bcrypt</strong> uses <a href="https://en.wikipedia.org/wiki/Bcrypt">Bcrypt</a> hashing algorithm</li>
<li><strong>Pbkdf2</strong> uses <a href="https://en.wikipedia.org/wiki/PBKDF2">Pbkdf2</a> hashing algorithm</li>
</ul>
</div>

:::danger hashing algorithms
Any change in either the algorithm or the parameters will __invalidate all already stored passwords__.
:::

### LDAP configuration (experimental)

<p><strong data-param="ldap_host">Host</strong> would be the LDAP server hostname.</p>

<p><strong data-param="ldap_user_rdn_attribute">User RDN attribute</strong> would be the user `username` Relative Distinguished Name.</p>

<p><strong data-param="ldap_base_dn">Base distinguished name (dn)</strong> would be the base Distinguished Name.</p>

<p><strong data-param="ldap_ou">Users organization unit (ou)</strong> would be the users Organization Unit.</p>

<p><strong data-param="ldap_master_dn">Master distinguished name (needed only for user edition)</strong> used for `username` or `passowrd` edition, would be the master Distinguished Name.</p>

<p><strong data-param="ldap_master_password">Master password (needed only for user edition)</strong> used for `username` or `passowrd` edition, would be the master password.</p>

<p><strong data-param="ldap_pool_size">Pool size</strong> would be the connection pool size kept alive with the LDAP server</p>
</div>

## User interface

![backend form](/assets/images/backends-type.png)
