# Service registry configuration | General configuration

Upstream attributes help __manage gateway routing and protection rules__ for services registered behind boruta. They define where a request is forwarded, which public paths expose the service, and which security rules the gateway applies before proxying traffic.

:::note Parameters sections
[Service registry](/docs/provider-configuration/configure-service-registry) upstreams can be customized through either the [Administration API](/api/list-upstreams), the user interface, or static configuration files. The configuration is organized around:

- __General configuration__
- [URIs](/docs/provider-configuration/service-registry/uris)
- [Authorization](/docs/provider-configuration/service-registry/authorization)
- [Security](/docs/provider-configuration/service-registry/security)
:::

## General configuration parameters

<div class="parameters">

<p><strong data-param="node_name">Node</strong> defines where the upstream is active. `global` upstreams are used by the main gateway entrypoint. A service registry node name makes the upstream active for the matching sidecar or microgateway node.</p>

<p><strong data-param="virtual_host">Virtual host</strong> restricts matching to requests received for a specific host. Leave it empty to match any host. When both a virtual-host upstream and a path-only upstream can match, the virtual-host upstream is selected first.</p>

<p><strong data-param="scheme">Scheme</strong> defines the protocol used to reach the upstream service. Accepted values are `http` and `https`.</p>

<p><strong data-param="host">Host</strong> is the network host of the upstream service.</p>

<p><strong data-param="port">Port</strong> is the network port of the upstream service.</p>

</div>

## User interface

The general configuration tab defines where the upstream is active and which backend service the gateway forwards traffic to.

![upstream general configuration](/assets/images/upstream-general-configuration.png)
