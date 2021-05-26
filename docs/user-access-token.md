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

User access tokens can be requested through one of two ways, depending on the type of application that you're building.

**Regular web applications** (with a backend) should use the [Authorization Code Flow](#authorization-code-flow) with their client id and secret. The secret should always be stored and used only on the backend.

**Native (mobile & desktop)** and **frontend applications without a backend (single-page applications)** on the other hand, do not have a way to securely store their client secret. Native binaries can be decompiled to reveal the secret, and Javascript applications running in the browser are running in an inherently unsafe environment to store secrets. Those applications should instead use the [Authorization Code Flow with Proof Key for Code Exchange](#authorization-code-flow-with-proof-key-for-code-exchange-pkce).

Both flows are standard OAuth2 flows and work largely the same. In both cases you will redirect the user to the authorization server where they can login, and afterward the user will be redirected back to your application and you will receive an authorization code. With this code you can request an access token. The main difference between the two flows is that with Proof Key for Code Exchange (PKCE), your app can utilize a dynamically-generated secret to initiate and validate the flow instead of your fixed client secret that should never be made public.

## Authorization Code Flow

\[To do\: Document]

## Authorization Code Flow with Proof Key for Code Exchange (PKCE)

\[To do\: Document]