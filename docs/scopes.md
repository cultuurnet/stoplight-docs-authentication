# Scopes

Because not all API clients need access to every publiq API, we work with a permission model to limit your client's access to the APIs that you need.

This permission works through *scopes* that are granted to your API client on publiq's authorization server. Each API requires 1 specific scope. For example to access the UiTPAS API, your client will need to have the `https://api.publiq.be/auth/uitpas` scope.

When requesting a [client access token](./client-access-token.md) or [user access token](./user-access-token.md), you also need to explicitly list which scopes should be included in the token. Tokens that do not include a specific API's scope cannot be used on that API. Note that you cannot request to include scopes that your client is not allowed to have access to.

When using [client identification](./client-identification.md), you do not need to request scopes because you do not need to request a token. Instead the API will look up your client's allowed scopes on the authorization server using the client id included in your request.

> ##### Multiple APIs and scopes
> You only need **one API client id** and secret to communicate with multiple of publiq's APIs. You can also communicate with multiple APIs with a **single token**, but the token needs to contain all the required scopes for the APIs.
>
> To request multiple scopes when requesting a token, **separate them with a space**.

## Possible scopes

API | Scope
---------|----------
 [UiTPAS API](https://publiq.stoplight.io/docs/uitpas) | https://api.publiq.be/auth/uitpas

## Adding scopes to your API client

If you already have a client id and secret, but it is missing scopes that you need, please send an email to vragen@uitdatabank.be with your client id (but not your client secret!) and a short summary of what scopes you need and why.

## Additional permissions

Each API can require additional permissions for specific endpoints. These permissions are managed inside each separate API and do not work with scopes.

For example inside UiTPAS, your API client can be allowed to search passholders inside a specific card system, but not other card systems. Or you may or may not be able to register ticket sales.

If your client or user is missing required permissions for functionality needed in your app, contact vragen@uitdatabank.be with info on what permissions you need and for which user.