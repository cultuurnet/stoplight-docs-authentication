# CORS

[Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) makes it possible to send HTTP requests that would otherwise be disallowed by a browser's [Same Origin Policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy).

For example when you make a request from a **frontend** application to an external API endpoint, you might see the following error in your browser's console:

    Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at ...

This policy is built into modern browsers to for example prevent [CSRF](https://owasp.org/www-community/attacks/csrf) attacks due to the browser making an authenticated request to another domain using cookies, without the consent or the knowledge of the user.

Additionally the Same Origin Policy prevents attacks at websites hosted on an intranet by limiting the requests that a website can make to another website through a browser.

## CORS on publiq's APIs

Because publiq's APIs do not work with cookies and are publicly hosted, there is no need for a strict Same Origin Policy in our case. Therefore our APIs generally allow CORS requests from any origin (unless noted otherwise).
