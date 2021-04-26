# Client access token

Client access tokens are used to secure API endpoints that require more robust authentication between two backend systems.

Examples include EntryAPI 3 and various endpoints on the UiTPAS API, where data needs to be written and/or more sensitive data gets exposed.

Before accessing an API like this, a client needs to obtain a client access token using its credentials (the client id and secret).

![Auth Diagram](https://acc.uitid.be/api/publiq-auth-diagram.png)

1. The client makes a request to the authorization server. It sends its client id and client secret, along with the required `audience` needed to access the API. All publiq APIs currently share the same audience: `https://api.publiq.be`. 

2. The authorization server validates the request and, if successful, sends a response with an access token.

3. The client can now use the access token to call the API by using the obtained access token as a `Bearer` token in the `Authorization` header.

<!-- theme: warning -->

> ##### Security warning
> Because you need to specify your client secret to retrieve a client access token, **you should only perform this request from a backend server** and not through a client-side application like a web browser where anyone could see your client secret!

<!-- theme: info -->

> ##### Auth0
> publiq currently uses [Auth0](https://auth0.com/) as its authentication and authorization service. For more in-depth information about client access tokens, please refer to the [Auth0 documentation](https://auth0.com/docs/). (Client access token are also known as machine-to-machine tokens in the Auth0 docs.)

Read on below to see a concrete example of how to get a client access token for your client credentials.


## Example flow

To obtain a client access token, send a `POST` request to the `/oauth/token` endpoint of the authentication server for the test or production environment with the following JSON body:

```json
{
  "client_id": "YOUR_CLIENT_ID",
  "client_secret": "YOUR_CLIENT_SECRET",
  "audience": "https://api.publiq.be",
  "grant_type": "client_credentials"
}
```

The URLs for the authentication servers are:
- Testing environment: `https://account-test.uitid.be`
- Production environment: `https://account.uitid.be`

<!-- theme: warning -->

> ##### Environments
> Every publiq API has a testing and production environment. **Initially when building your integration, you should connect to the testing environment** of the APIs that you integrate with.
> 
> These different environments will require client access tokens from the respective testing and production environments of the authentication service.
> 
> Additionally, **your client id and secret will be different** for the testing environment and production environment.

After sending your request to the correct environment for your client credentials, you will get a response with a JSON body like this:

```json
{
 "access_token":"YOUR_ACCESS_TOKEN",
 "scope":"https://api.publiq.be/uit/mailing_m2m",
 "expires_in":86400,
 "token_type":"Bearer"
}
```

You can then include the returned access token as a [Bearer token](https://swagger.io/docs/specification/authentication/bearer-authentication/) in the `Authorization` header of your requests:

```
curl https://api.uitpas.be/example -H "authorization: Bearer YOUR_ACCESS_TOKEN"
```

<!-- theme: warning -->

> ##### Caching tokens
> Make sure to **cache and reuse** the obtained client access token for as long as possible! Do not request a new access token for each API request you make. The expiration time of a client access token is usually 24 hours. 
> 
> The response with your access token will include an `expires_in` parameter with the exact expiration time in seconds. You can make your cached token expire after that time has elapsed and request a new one then. Another option is to not look at the expiration time and request a new token as soon as you get a `401` or `403` response from an API, indicating that the token has expired.


## Try it out!

You can use the request form below to request a client access token using your client id and secret for the test environment. You can then use the `access_token` from the response body to authorize other example requests to the test environment in the documentation.

Make sure to set your **client id** and **secret** in the **body** tab!

```json http
{
  url: 'https://account-test.uitid.be/oauth/token',
  method: "POST",
  headers: {
    "content-type": "application/json"
  },
  body: {
    "client_id": "YOUR_CLIENT_ID",
    "client_secret": "YOUR_CLIENT_SECRET",
    "audience": "https://api.publiq.be",
    "grant_type":"client_credentials"    
  }
}
```