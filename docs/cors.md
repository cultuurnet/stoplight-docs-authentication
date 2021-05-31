# CORS

[Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) makes it possible to send HTTP requests that would otherwise be disallowed by a browser's [Same Origin Policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy).

For example when you make a request from a **frontend** application to an external API endpoint, you might see the following error in your browser's console:

    Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at ...

This policy is built into modern browsers to for example prevent [CSRF](https://owasp.org/www-community/attacks/csrf) attacks.

## Circumventing Same Origin Policy & CORS

In some cases you can circumvent the Same Origin Policy, and thus the need for CORS, by only sending [simple requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#simple_requests).

This is possible on publiq's API endpoints that require no authentication at all or only [client identification](./client-identification.md).

*   When you send a request to an endpoint that requires no authentication, make sure **not to send an `Authorization` header** with a token even if you have one.
*   When you send a request to an endpoint that requires client identification, you can make your request a "simple" request by **using the `clientId` query parameter** instead of the `x-client-id` header (because simple requests can only contain very specific headers).

## Whitelisting your domain

If you need to send requests to API endpoints from a frontend application and cannot use simple requests, we are happy to add your domain name(s) to our list of allowed CORS domains. Contact vragen@uitdatabank.be for more information.
