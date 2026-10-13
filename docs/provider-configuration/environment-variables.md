# Provider configuration | Environment variables

boruta-server is configured at runtime with environment variables. Those variables define secrets, database connections, public URLs, gateway listeners, service discovery, static configuration files, administration bootstrap values, and DID service integrations.

## Core server variables

<div class="parameters">

<p><strong data-param="SECRET_KEY_BASE">SECRET_KEY_BASE</strong> is the Phoenix secret key base used by the server. It must be at least 64 characters long.</p>

<p><strong data-param="BORUTA_SESSION_COOKIE_KEY">BORUTA_SESSION_COOKIE_KEY</strong> defines the session cookie key shared by the web, identity, and administration endpoints. Defaults to `_boruta_web_key`.</p>

<p><strong data-param="BORUTA_SESSION_COOKIE_SIGNING_SALT">BORUTA_SESSION_COOKIE_SIGNING_SALT</strong> defines the signing salt used for the shared session cookie. Defaults to `OCKBuS86`.</p>

<p><strong data-param="BORUTA_REMEMBER_ME_COOKIE">BORUTA_REMEMBER_ME_COOKIE</strong> defines the identity remember-me cookie name. Defaults to `_boruta_identity_web_user_remember_me`.</p>

<p><strong data-param="MAX_LOG_RETENTION_DAYS">MAX_LOG_RETENTION_DAYS</strong> defines how many days server logs are retained. Defaults to `60`.</p>

<p><strong data-param="DISABLE_FILE_LOGGING">DISABLE_FILE_LOGGING</strong> disables file logging when set to `true`. Console logging remains enabled. Defaults to `false`.</p>

</div>

## Database variables

<div class="parameters">

<p><strong data-param="POSTGRES_USER">POSTGRES_USER</strong> defines the PostgreSQL user used by boruta applications.</p>

<p><strong data-param="POSTGRES_PASSWORD">POSTGRES_PASSWORD</strong> defines the PostgreSQL password used by boruta applications.</p>

<p><strong data-param="POSTGRES_DATABASE">POSTGRES_DATABASE</strong> defines the PostgreSQL database name.</p>

<p><strong data-param="POSTGRES_HOST">POSTGRES_HOST</strong> defines the PostgreSQL host.</p>

<p><strong data-param="POOL_SIZE">POOL_SIZE</strong> defines the PostgreSQL pool size of each application. The total connection count depends on the applications enabled in the release. Defaults to `5`.</p>

</div>

## Cluster variables

<div class="parameters">

<p><strong data-param="LIBCLUSTER_HOSTS">LIBCLUSTER_HOSTS</strong> defines a comma-separated list of Erlang node names used for Docker Compose discovery, for example `boruta@boruta-1,boruta@boruta-2`.</p>

<p><strong data-param="K8S_NAMESPACE">K8S_NAMESPACE</strong> configures Kubernetes service discovery when it is set together with `K8S_SELECTOR`.</p>

<p><strong data-param="K8S_SELECTOR">K8S_SELECTOR</strong> configures Kubernetes service discovery when it is set together with `K8S_NAMESPACE`.</p>

</div>

## Administration variables

<div class="parameters">

<p><strong data-param="BORUTA_ADMIN_OAUTH_CLIENT_ID">BORUTA_ADMIN_OAUTH_CLIENT_ID</strong> defines the OAuth client id used by the administration interface. It is used when seeding the default administration client.</p>

<p><strong data-param="BORUTA_ADMIN_OAUTH_CLIENT_SECRET">BORUTA_ADMIN_OAUTH_CLIENT_SECRET</strong> defines the OAuth client secret used by the administration interface. It is used when seeding the default administration client.</p>

<p><strong data-param="BORUTA_ADMIN_OAUTH_BASE_URL">BORUTA_ADMIN_OAUTH_BASE_URL</strong> defines the authorization server base URL used by the administration interface, without trailing slash.</p>

<p><strong data-param="BORUTA_ADMIN_EMAIL">BORUTA_ADMIN_EMAIL</strong> defines the first administration user email. It is used by the setup task.</p>

<p><strong data-param="BORUTA_ADMIN_PASSWORD">BORUTA_ADMIN_PASSWORD</strong> defines the first administration user password. It is used by the setup task.</p>

<p><strong data-param="BORUTA_ADMIN_HOST">BORUTA_ADMIN_HOST</strong> defines the public host where the administration server is deployed.</p>

<p><strong data-param="BORUTA_ADMIN_BIND">BORUTA_ADMIN_BIND</strong> defines the IP address the administration server binds to.</p>

<p><strong data-param="BORUTA_ADMIN_PORT">BORUTA_ADMIN_PORT</strong> defines the port where the administration server listens. Defaults to `8081` in releases.</p>

<p><strong data-param="BORUTA_ADMIN_SERVER">BORUTA_ADMIN_SERVER</strong> enables the administration HTTP listener. Defaults to `true` in releases.</p>

<p><strong data-param="BORUTA_ADMIN_BASE_URL">BORUTA_ADMIN_BASE_URL</strong> defines the administration HTTP endpoint base URL, without trailing slash.</p>

<p><strong data-param="BORUTA_SUB_RESTRICTED">BORUTA_SUB_RESTRICTED</strong> restricts administration access to a single user id when set.</p>

<p><strong data-param="BORUTA_ORGANIZATION_RESTRICTED">BORUTA_ORGANIZATION_RESTRICTED</strong> restricts administration access to a single organization id when set.</p>

<p><strong data-param="BORUTA_COMMAND_SUB">BORUTA_COMMAND_SUB</strong> defines the subject recorded for commands executed with `boruta-cli`. Defaults to the current operating system user and hostname.</p>

</div>

## OAuth server variables

<div class="parameters">

<p><strong data-param="BORUTA_OAUTH_SCHEME">BORUTA_OAUTH_SCHEME</strong> defines the scheme used for OAuth URL generation. Defaults to `https`.</p>

<p><strong data-param="BORUTA_OAUTH_HOST">BORUTA_OAUTH_HOST</strong> defines the public host where the OAuth server is deployed.</p>

<p><strong data-param="BORUTA_OAUTH_BIND">BORUTA_OAUTH_BIND</strong> defines the IP address the OAuth server binds to. Defaults to `::`.</p>

<p><strong data-param="BORUTA_OAUTH_PORT">BORUTA_OAUTH_PORT</strong> defines the port where the OAuth server listens. Defaults to `8080` in releases.</p>

<p><strong data-param="BORUTA_OAUTH_SERVER">BORUTA_OAUTH_SERVER</strong> enables the OAuth HTTP listener. Defaults to `true` in releases.</p>

<p><strong data-param="BORUTA_OAUTH_ACCEPTORS">BORUTA_OAUTH_ACCEPTORS</strong> defines the number of acceptor processes for the OAuth server. Defaults to `8`.</p>

<p><strong data-param="BORUTA_OAUTH_BASE_URL">BORUTA_OAUTH_BASE_URL</strong> defines the OAuth server HTTP endpoint base URL, without trailing slash.</p>

</div>

## Gateway variables

<div class="parameters">

<p><strong data-param="BORUTA_GATEWAY_SERVER">BORUTA_GATEWAY_SERVER</strong> enables the HTTP gateway listener. Defaults to `false` in releases.</p>

<p><strong data-param="BORUTA_GATEWAY_PORT">BORUTA_GATEWAY_PORT</strong> defines the HTTP gateway port. Defaults to `8083`.</p>

<p><strong data-param="BORUTA_GATEWAY_HTTPS_SERVER">BORUTA_GATEWAY_HTTPS_SERVER</strong> enables the HTTPS gateway listener. Defaults to `false`.</p>

<p><strong data-param="BORUTA_GATEWAY_HTTPS_PORT">BORUTA_GATEWAY_HTTPS_PORT</strong> defines the HTTPS gateway port. Defaults to `8043`.</p>

<p><strong data-param="BORUTA_GATEWAY_HTTPS_VERIFY_CLIENT_CERTIFICATE">BORUTA_GATEWAY_HTTPS_VERIFY_CLIENT_CERTIFICATE</strong> requires and verifies client certificates on the HTTPS gateway listener. Defaults to `false`.</p>

<p><strong data-param="BORUTA_GATEWAY_MOUNTED_CERTIFICATE_PATH">BORUTA_GATEWAY_MOUNTED_CERTIFICATE_PATH</strong> defines the path to a mounted certificate used by the HTTPS gateway listener. It must be set together with `BORUTA_GATEWAY_MOUNTED_PRIVATE_KEY_PATH`.</p>

<p><strong data-param="BORUTA_GATEWAY_MOUNTED_PRIVATE_KEY_PATH">BORUTA_GATEWAY_MOUNTED_PRIVATE_KEY_PATH</strong> defines the path to the private key associated with the mounted HTTPS gateway certificate. It must be set together with `BORUTA_GATEWAY_MOUNTED_CERTIFICATE_PATH`.</p>

<p><strong data-param="BORUTA_GATEWAY_SIDECAR">BORUTA_GATEWAY_SIDECAR</strong> enables the HTTP sidecar gateway listener. Defaults to `false` in releases.</p>

<p><strong data-param="BORUTA_GATEWAY_SIDECAR_PORT">BORUTA_GATEWAY_SIDECAR_PORT</strong> defines the HTTP sidecar gateway port. Defaults to `8084`.</p>

<p><strong data-param="BORUTA_GATEWAY_SIDECAR_HTTPS_SERVER">BORUTA_GATEWAY_SIDECAR_HTTPS_SERVER</strong> enables the HTTPS sidecar gateway listener. Defaults to `false`.</p>

<p><strong data-param="BORUTA_GATEWAY_SIDECAR_HTTPS_PORT">BORUTA_GATEWAY_SIDECAR_HTTPS_PORT</strong> defines the HTTPS sidecar gateway port. Defaults to `8044`.</p>

<p><strong data-param="BORUTA_GATEWAY_SIDECAR_HTTPS_VERIFY_CLIENT_CERTIFICATE">BORUTA_GATEWAY_SIDECAR_HTTPS_VERIFY_CLIENT_CERTIFICATE</strong> requires and verifies client certificates on the HTTPS sidecar gateway listener. Defaults to `false`.</p>

<p><strong data-param="BORUTA_GATEWAY_PROXY_SERVER">BORUTA_GATEWAY_PROXY_SERVER</strong> enables the HTTP forward proxy listener. Defaults to `false` in releases.</p>

<p><strong data-param="BORUTA_GATEWAY_PROXY_PORT">BORUTA_GATEWAY_PROXY_PORT</strong> defines the HTTP forward proxy port. Defaults to `5555`.</p>

<p><strong data-param="BORUTA_GATEWAY_HTTPS_PROXY_SERVER">BORUTA_GATEWAY_HTTPS_PROXY_SERVER</strong> enables the HTTPS forward proxy listener. Defaults to `false` in releases.</p>

<p><strong data-param="BORUTA_GATEWAY_HTTPS_PROXY_PORT">BORUTA_GATEWAY_HTTPS_PROXY_PORT</strong> defines the HTTPS forward proxy port. Defaults to `4444`.</p>

<p><strong data-param="BORUTA_GATEWAY_ACCEPTORS">BORUTA_GATEWAY_ACCEPTORS</strong> defines the number of acceptor processes for gateway, sidecar, and proxy listeners. Defaults to `8`.</p>

<p><strong data-param="BORUTA_GATEWAY_CONFIGURATION_PATH">BORUTA_GATEWAY_CONFIGURATION_PATH</strong> defines the path containing the gateway static configuration file. Defaults to `config/example-configuration.yml` in releases.</p>

</div>

## Static configuration variables

<div class="parameters">

<p><strong data-param="BORUTA_CONFIGURATION_PATH">BORUTA_CONFIGURATION_PATH</strong> defines the path containing the boruta static configuration file.</p>

</div>

## DID service variables

<div class="parameters">

<p><strong data-param="DID_RESOLVER_BASE_URL">DID_RESOLVER_BASE_URL</strong> defines the DID resolver API endpoint, according to the W3C DID resolution specification. Defaults to `https://api.godiddy.com/1.0.0/universal-resolver`.</p>

<p><strong data-param="DID_REGISTRAR_BASE_URL">DID_REGISTRAR_BASE_URL</strong> defines the DID registrar API endpoint, according to the DID registration specification. Defaults to `https://api.godiddy.com/1.0.0/universal-registrar`.</p>

<p><strong data-param="DID_SERVICES_API_KEY">DID_SERVICES_API_KEY</strong> defines the API key granting access to DID resolver and registrar services.</p>

</div>
