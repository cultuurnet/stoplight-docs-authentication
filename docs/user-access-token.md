# User access token

<!-- theme: danger -->

> ##### References, remove before merge!
> - https://confluence.uitdatabank.be/display/UITIDV2/Authorize+publiq+APIs+using+Auth0+acces+token
> - https://confluence.uitdatabank.be/display/UITIDV2/How+to+integrate+UITIDv2+authentication+%28Auth0%29+in+your+project
> - https://auth0.com/docs/architecture-scenarios/spa-api
> - https://auth0.com/docs/api/authentication#authorization-code-flow
> - https://auth0.com/docs/authorization/configure-silent-authentication
> - https://auth0.com/docs/flows/authorization-code-flow
> - https://auth0.com/docs/flows/authorization-code-flow-with-proof-key-for-code-exchange-pkce

## Overview

User access tokens can be requested through various ways, each specific to the kind of application that you build.

**Regular web applications** that have a server-side backend to securely store their API client's secret can use the [Authorization Code Flow](#authorization-code-flow)

**Native, mobile, and single-page applications** should use the [Authorization Code Flow with Proof Key for Code Exchange](#authorization-code-flow-with-proof-key-for-code-exchange), which does not require a client secret, since they do not have a place to securely store that.

## Authorization Code Flow

\[To do\: Document]

## Authorization Code Flow with Proof Key for Code Exchange (PKCE)

\[To do\: Document]