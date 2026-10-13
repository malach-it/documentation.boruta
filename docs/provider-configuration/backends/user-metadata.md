# Backends configuration | User metadata

Backends parameters help to __manage identity storage and associated features__ within the server. Those are to keep credentials and identities while providing them abilities helping to manage authorization and authentication provided by the identity provider interfaces.

:::note Parameters sections
[Backends](/docs/provider-configuration/configure-backends) can be customized through either the Administration API or the user interface providing 6 __categories of settings__:

- General configuration
- Type
- Email configuration
- Identity federation
- Verifiable credentials
- __User metadata__
:::

## User metadata parameters

<div class="parameters">

<p><strong data-param="metadata_fields">Add metadata field</strong> add an attribute to users' schema that would sit on top of base identification credentials. Those would be present in resource owner claims.</p>

### Metadata field

<p><strong data-param="user_editable">User editable</strong> define if users can update the metadata field.</p>

<p><strong data-param="scopes">Scope restriction (leave blank for no restriction)</strong> gives the list of scopes needed to access the metadata field.</p>

<p><strong data-param="attribute_name">Attribute name</strong> is the name of the attribute, the `key` of the attribute when expressed as JSON.</p>

</div>

## User interface

![backend form](/assets/images/backends-user-metadata.png)
