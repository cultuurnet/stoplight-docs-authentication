# Overview

Each publiq API supports one or more authentication methods, depending on the functionality that it provides.

## When to use which method

Which authentication method you need to use will in the first place be **determined by which API endpoint(s) you want to access**. 

There are 4 possible scenarios for an endpoint:

1. The endpoint allows [client identification](#client-identification). You will only need to include your client id in the request and you don't need a token.
2. The endpoint accepts both [user access tokens](#user-access-tokens) and [client access tokens](#client-access-tokens). You can pick whatever token type is best suited to your situation. See their respective documentation for more info.
3. The endpoint requires _specifically_ [**client** access tokens](#client-access-tokens) . You will need to fetch a token using your client id and secret from a backend.
4. The endpoint requires _specifically_ [**user** access tokens](#user-access-tokens). You will need to let your end user log in through UiTID and use the resulting token.

You can find the authentication method(s) that an endpoint supports in its own documentation.

> ##### Most common scenarios
> Usually an endpoint will either require **client identification**, or it will require a **token of any kind**. Only very few endpoints will require a specific token type.

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
