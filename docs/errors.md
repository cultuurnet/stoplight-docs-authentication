# Errors

This page contains an overview of all possible error types inside the `https://api.publiq.be/probs/auth/` namespace that can be returned by publiq's APIs. (Not errors that can occur on Auth0 while trying to request a token!)

## unauthorized

-   **Complete type:** `https://api.publiq.be/probs/auth/unauthorized`
-   **Title**: `Unauthorized`
-   **Status**: `401`

Your request is missing the required credentials to authenticate.

Possible causes:

*   You forgot to include your client id (for endpoints that require client identification)
*   You forgot to include a token (for endpoints that require tokens)
*   Your token has expired
*   Your token is malformed and cannot be parsed
*   You are using the wrong authentication method (client id while it should be a token or the other way around)

## forbidden

-   **Complete type:** `https://api.publiq.be/probs/auth/forbidden`
-   **Title**: `Forbidden`
-   **Status**: `403`

Your request was successfully authenticated but you do not have permission to perform this particular request.

Possible causes:

*   Your client has no access to this API, or your token does not include the correct token to access this API. See [scopes](./scopes.md) for more info.
*   You are trying to perform an action on a specific resource inside the API to which you don't have access. Check the specific API endpoint's documentation for more info about possibly required permissions.
