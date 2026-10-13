# Service registry configuration | Security

Security parameters help __protect upstream connections and traffic volume__. They enable mutual TLS to the backend service and gateway-side rate limiting before requests are forwarded.

:::note Parameters sections
[Service registry](/docs/provider-configuration/configure-service-registry) upstreams can be customized through either the [Administration API](/api/list-upstreams), the user interface, or static configuration files. The configuration is organized around:

- [General configuration](/docs/provider-configuration/service-registry/general-configuration)
- [URIs](/docs/provider-configuration/service-registry/uris)
- [Authorization](/docs/provider-configuration/service-registry/authorization)
- __Security__
:::

## Security parameters

<div class="parameters">

<p><strong data-param="mtls_enabled">Mutual TLS</strong> makes the gateway use mutual TLS when connecting to the upstream. This option requires the upstream scheme to be `https`.</p>

<p><strong data-param="rate_limit_enabled">Enable rate limiting</strong> applies request throttling before traffic is forwarded to the upstream.</p>

### Rate limiting

<p><strong data-param="rate_limit_count">Request count</strong> defines how many requests are accepted during the selected time unit.</p>

<p><strong data-param="rate_limit_time_unit">Time unit</strong> defines the rate-limit window. Accepted values are `millisecond`, `second`, and `minute`.</p>

<p><strong data-param="rate_limit_penality">Penality (ms)</strong> defines the delay applied after the accepted request count is exceeded.</p>

<p><strong data-param="rate_limit_timeout">Timeout (ms)</strong> defines the maximum throttling wait time before the request is rejected.</p>

<p><strong data-param="rate_limit_memory_length">Memory length</strong> defines how many recent rate-limit entries are kept in memory for the upstream.</p>

### Noise cancelling

<p><strong data-param="noise_cancelling_enabled">Enable noise cancelling</strong> enables Phi-based filtering of requests that do not match the trained upstream API model.</p>

<p><strong data-param="openapi_spec">OpenAPI specification</strong> defines the JSON or YAML OpenAPI document used to train the Phi noise-cancelling model. The uploaded specification is not stored.</p>

</div>

## User interface

![upstream security](/assets/images/upstream-security.png)
