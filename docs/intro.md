# (WIP) boruta server documentation

:::info Status
boruta is currently in an __open beta phase__. If you are interested by the project and the tools it provides, you are encouraged to test the software within your context. Production readiness will depend on your feedback, helping to fix possible bugs and improve the solution's usability. While mostly stable and security-assessed in some areas, boruta is a work in progress. Please read the [General Terms and Conditions](https://github.com/malach-it/boruta-server/blob/master/GENERAL_TERMS_AND_CONDITIONS.md).
:::

## What is boruta?

boruta is an authorization server that aims to implement OAuth 2.0 and satelite
specifications. On top of authorization, it provides identity management, an
experimental gateway and administration interfaces. Those provide an identity
and access management solution that helps to solve identity related problems,
up to decentralized identity.

<div class="centered">

![components](/assets/images/components.png)

</div>

## Open core / Application layer architecture

boruta is splited into an open core and an application layer giving from one side the authorization business logic and the other the exposition and authentication topics to provide a standalone server. This core is open source and avalilable as an [Elixir package on hex.pm](https://hex.pm/packages/boruta).

## Why another authorization server?

boruta has been designed to be both __end-user and developer friendly__. With a high level of customization, it helps to have an immersive experience for your users giving them custom interfaces. The administration interface gives an exhaustive set of configuration parameters that are also accessible through REST API calls for automation.

As an __open-source product__, it takes the advantage of being backed by a community of developers making it a secure and extensible solution. All suggestions, feature requests, or any kind of contribution will be very welcome.

> Have a look at the [GitHub repository](https://github.com/malach-it/boruta-server)

With an implementation of __OpenID 4 Verifiable Credentials Issuance__ (OID4VCI) and __OpenID 4 Verifiable presentations__ (OID4VP), boruta provides means to be __compliant with the eIDAS 2.0 regulation__. On top of those protocols, it brings ways to get identities from a data source still being secure and with __low integration costs__, being part of your infrastructure by addition, not replacement. Indeed, boruta can leverage identity federation to restrict access to verifiable credentials making it a __secure and privacy preserving solution__.

![Tripartite authorization](/assets/images/authorization-tripartite.png)

## About an identity provider

boruta comes up with an __integrated idenity provider__, it can both __store the users' credentials__ internaly and provide an experimental __LDAP adapter__. It helps more than enable password authentication abilities, to __enhance users__ with features like having __custom attributes__, __enforce email confirmation__, or __consent__ to the client's requested scopes.

## About a gateway

boruta is __coupled to an experimental gateway__ that acts as a __reverse-proxy__ sitting between your frontends and backends in order to __apply security rules__ in a fast and non-intrusive way. To perform those access restrictions, the gateway is based on boruta-provided access tokens or HTTP Basic. With scope management, it helps mitigating the incoming traffic and allow to get access to profile attributes in a secure way.

![Gateway authorization flow](/assets/images/authorization-gateway-en.png)

## Implemented specifications and certification

As it, boruta server aim to follow the RFCs from IETF:
- [RFC 6749 - The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749)
- [RFC 7662 - OAuth 2.0 Token Introspection](https://tools.ietf.org/html/rfc7662)
- [RFC 7009 - OAuth 2.0 Token Revocation](https://tools.ietf.org/html/rfc7009)
- [RFC 7636 - Proof Key for Code Exchange by OAuth Public Clients](https://tools.ietf.org/html/rfc7636)
- [RFC 7521 - Assertion Framework for OAuth 2.0 Client Authentication and Authorization Grants](https://www.rfc-editor.org/rfc/rfc7521)
- [RFC 7523 - JSON Web Token (JWT) Profile for OAuth 2.0 Client Authentication and Authorization Grants](https://tools.ietf.org/html/rfc7523)
- [RFC 9449 - OAuth 2.0 Demonstrating Proof-of-Possession at the Application Layer (DPoP)](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-dpop)
- [RFC 9126 - OAuth 2.0 Pushed Authorization Requests](https://datatracker.ietf.org/doc/html/rfc9126)

And the specifications from the OpenID Foundation:
- [OpenID Connect core 1.0](https://openid.net/specs/openid-connect-core-1_0.html)
- [OpenID Connect Dynamic Client Registration 1.0 incorporating errata set 1](https://openid.net/specs/openid-connect-registration-1_0.html)
- [OpenID for Verifiable Credential Issuance](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html)
- [Self-Issued OpenID Provider v2](https://openid.net/specs/openid-connect-self-issued-v2-1_0.html)
- [OpenID for Verifiable Presentations - draft 21](https://openid.net/specs/openid-4-verifiable-presentations-1_0.html)

This server has been certified for the Basic, Implicit, and Hybrid OpenID Provider profiles by the OpenID Foundation on October 18th, 2022 for the tagged versions 0.1.0 and October 17th, 2024 for 0.5.0

This server has been certified for the Config and Dynamic OpenID Provider profiles by the OpenID Foundation on May, 16th 2023 for the tagged version 0.2.0

![OpenID certified](/assets/images/oid-certification-mark.png)

This server has also been certified against the [European Blockchain Service Infrastructure (EBSI)](https://ec.europa.eu/digital-building-blocks/sites/display/EBSI) issuance test suite for the tagged version 0.4.0 and for verifiable credential verification for the tagged version 0.5.0.

![EBSI certified - issue](/assets/images/ebsi-certification-issuance.png)
![EBSI certified - verify](/assets/images/ebsi-certification-verify.png)

## Navigation

1. Getting up and running - [Quickstart](quickstart.md)
2. Understand how to configure the server - [provider configuration](provider-configuration/configure-clients.md)
