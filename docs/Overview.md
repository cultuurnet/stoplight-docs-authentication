# Authentication

Each publiq API supports one or more authentication methods, depending on the functionality that it provides.

> ##### How to get client credentials
> 
> Every integration on publiq's APIs requires a client id and in most cases also a client secret to authenticate requests.
> 
> To get client credentials for your integration, contact jean-marie@publiq.be.

## When to use which method

Which authentication method you need to use will in the first place be **determined by which API endpoint(s) you want to access**. 

Usually an API endpoint will either require _client identification_, **OR** they will require a token. Most endpoints that require a token support both _user access tokens_ and _client access tokens_ (except for some rare edge cases).

- If the endpoint allows [client identification](Authentication-methods/Client-identification.md), you only need to include your client id in the request.
- If the endpoint **only** allows [user access tokens](Authentication-methods/User-access-token.md), you need to let your end user log in through UiTID and use the resulting token.
- If the endpoint **only** allows [client access tokens](Authentication-methods/Client-access-token.md), you need to fetch a token using your client id and secret from a backend.
- If the endpoint accepts **both** [user access tokens](Authentication-methods/User-access-token.md) and [client access tokens](Authentication-methods/Client-access-token.md), you can pick whatever token type is best suited to your situation. (See their respective documentation for more info.)

## Client identification

API endpoints that require no real authentication but need to know what client is accessing it for customization and technical support reasons use [Client identification](Authentication-methods/Client-identification.md). 

Usually used by APIs that need to provide info to anonymous users in web browsers, for example [Search API 3](https://publiq.stoplight.io/docs/uitdatabank/reference/Search-API.v3.json).

- ✅ Suitable for frontend applications
- ✅ Suitable for backend applications
- ⏱ Does not expire
- 🔓 Offers no real security, so only used in APIs that expose public information

## Tokens

API endpoints that expose private information and/or allow write access require a token to authenticate.

Most API endpoints that require a token accept both _**client** access tokens_ and _**user** access tokens_. Only some few exceptions require one or the other. For example an endpoint to request info on the current user will always require a user access token.

> If an endpoint accepts both client and user access tokens, you only need to provide one or the other, not both.

### Client access tokens

API endpoints that support the authentication of an API client with a client id and client secret use [Client access tokens](Authentication-methods/Client-access-token.md).

- ❌ Not suitable for frontend applications
- ✅ Suitable for backend applications
- ⏱ Expires, but can be renewed automatically
- 🔐 Secure, used by APIs that work with private information and/or write access

### User access tokens

API endpoints that support authentication as a user use [User access tokens](Authentication-methods/User-access-token.md). 

Usually used in situations where a user will log in through publiq's UiTID service and your application will then make requests in that user's name.

- ✅ Suitable for frontend applications
- ✅ Suitable for backend applications
- ⏱ Expires and requires your user to log in again through UiTID
- 🔐 Secure, used by APIs that work with private information and/or write access

### Token expiration

Both _client access tokens_ and _user access tokens_ expire after a period of time. We reserve the ability to change this period of time whenever we see fit, so you should never hardcode this in your app somewhere. 

Instead keep using your token until you get a `401` response from an API endpoint, which indicates that the token has expired. Or use the `expires_in` property that is included in the response with your token when you request one to determine the lifetime of the token.

To get a new client access token, you can simply request a new one using your client id and secret as described in [Client access tokens](Authentication-methods/Client-access-token.md).

To get a new user access token, you will need to let your user login again as described in [User access tokens](Authentication-methods/User-access-token.md).

