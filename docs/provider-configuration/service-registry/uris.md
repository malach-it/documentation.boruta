# Service registry configuration | URIs

Upstreams attributes help organizations __manage access to services__ registered behind boruta. Together, they define where requests are routed, which public paths are exposed, how callers are authorized, and how upstream traffic is protected. The gateway applies these configured rules before forwarding requests to backend services.

:::note Parameters sections
[Service registry](/docs/provider-configuration/configure-service-registry) upstreams can be customized through either the [Administration API](/api/list-upstreams), the user interface, or static configuration files. The configuration is organized around:

- [General configuration](/docs/provider-configuration/service-registry/general-configuration)
- __URIs__
- [Authorization](/docs/provider-configuration/service-registry/authorization)
- [Security](/docs/provider-configuration/service-registry/security)
:::

## URIs parameters

<div class="parameters">

<p><strong data-param="uris">URIs</strong> are the public path prefixes exposed by the gateway. The gateway matches requests by path prefix and gives priority to the longest matching URI, making it possible to define broad and specific routes on the same gateway.</p>

<p><strong data-param="strip_uri">Strip URI</strong> removes the matched URI prefix before forwarding the request to the upstream service. For example, with `/api` configured as URI, a request to `/api/users` is forwarded as `/users` when strip URI is enabled.</p>

</div>

## User interface

![upstream URIs](/assets/images/upstream-uris.png)
