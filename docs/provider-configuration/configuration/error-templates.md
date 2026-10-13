# Global configuration | Error templates

While the user navigates through authentication or authorization, he can __encounter errors__. Naigation errors depend on the HTTP status, templates are provided for each of those. You can edit them to have a __complete coverage of where the user can navigate to__.

## Error templates

<div class="parameters">

<div class="parameter-entry">
<p><strong data-param="400">Bad request</strong> encountered when the user emits a bad request.</p>
<ul>
<li><strong>reason.message</strong> variable is available on the bad request template. It gives the current error message.</li>
</ul>
</div>

<div class="parameter-entry">
<p><strong data-param="403">Forbidden</strong> encountered when the user is forbidden to access the page.</p>
<ul>
<li><strong>reason.message</strong> variable is available on the forbidden template. It gives the current error message.</li>
</ul>
</div>

<div class="parameter-entry">
<p><strong data-param="404">Not found</strong> encountered when the requested page is not found.</p>
<ul>
<li><strong>reason.message</strong> variable is available on the not found template. It gives the current error message.</li>
</ul>
</div>

<div class="parameter-entry">
<p><strong data-param="500">Internal server error</strong> encountered when the server crashes.</p>
<ul>
<li><strong>reason.message</strong> variable is available on the internal server error template. It gives the current error message.</li>
</ul>
</div>

</div>

## Manage through User Interface

The Administration interface gives the ability to create, update and delete backends. Backends are listed through the `Configuration > error templates` section in the sidebar menu.

![error templates view](/assets/images/error-templates.png)

## Manage through API

All client operations are accessible through a REST API following the below description. All client management endpoints are protected with a Bearer token that can be obtained with any OAuth flow. In order to get access, you need to have an access token with the [private](provider-configuration/configure-scopes.md#public-vs-private-scopes) scope `configuration:manage:all` granted.

> Have a look at the [API documentation](/api/show-an-error-template)

## Static configuration

Error templates can be updated from static configuration files with the `error_template` section. The referenced template `type` must already exist.

```yaml
---
version: "1.0"
configuration:
  error_template:
    - type: "400"
      content: |
        {"error":"bad_request","message":"{{ reason.message }}"}
    - type: "403"
      content: |
        {"error":"forbidden","message":"{{ reason.message }}"}
    - type: "404"
      content: |
        {"error":"not_found","message":"{{ reason.message }}"}
    - type: "500"
      content: |
        {"error":"server_error","message":"{{ reason.message }}"}
```

> Have a look at [configuration files](/docs/provider-configuration/configuration-files#error_template)
