# Authentication

Each publiq API supports one or more authentication methods, depending on the functionality that it provides.

> ##### How to get client credentials
> 
> Every integration on publiq's APIs requires a client id and in most cases also a client secret to authenticate requests.
> 
> To get client credentials for your integration, contact jean-marie@publiq.be.

## Client identification

API endpoints that require no real authentication but need to know what client is accessing it for customization and technical support reasons use [Client identification](Authentication-methods/Client-identification.md). 

Usually used by APIs that need to provide info to anonymous users in web browsers, for example [Search API 3](https://publiq.stoplight.io/docs/uitdatabank/reference/Search-API.v3.json).

## Client access tokens

API endpoints that require the authentication of an API client with secret credentials use [Client access tokens](Authentication-methods/Client-access-token.md). 

Usually used for server-to-server communication to send data or retrieve sensitive data. For example, to [import events into UiTdatabank](https://publiq.stoplight.io/docs/uitdatabank/docs/Guides/Imports/Importing-events.md) or [register ticket sales in UiTPAS](https://publiq.stoplight.io/docs/uitpas/docs/Guides/Ticket-prices-and-sales.md).

## User access tokens

API endpoints that require authentication as a user use [User access tokens](Authentication-methods/User-access-token.md). 

Usually used in situations where a user will log in through publiq's UiTID service and the API client will make requests in that user's name.

## When to use which method

Which authentication method you need to use will in the first place be determined by which endpoint(s) you want to access. 

Usually an API endpoint will either require _client identification_, **OR** they will require a token and in most cases support both a _user access token_ or a _client access token_ (except for some edge cases).

So the **first step to decide which method to use**, is to **check the documentation of the endpoints** you will use to determine which methods they support.

- If the endpoint requires **client identification**, you can use it by simply including your client id in the request.
- If the endpoint uses tokens and accepts both **user access tokens** and **client access tokens**, the decision can be made based on the following factors:

Token type | Requires a user logged in via UiTID | Usable in frontend | Usable in backend
---------|----------|---------
 User access token | ✅ | ✅ | ✅
 Client access token | ❌ | ❌ | ✅

Here are some example scenario's to help you decide.

#### Scenario 1: Your users will log in through UiTID

If your app's users log in through UiTID, your application will get a user access token for the logged in user which is valid for a predefined period of time after which the user is considered to be logged out.

You can use this token to authenticate requests to endpoints that support _user access tokens_, and you can use it in both a frontend application and/or a backend application.

#### Scenario 2: Your app has no backend

If your app has no backend and needs to communicate with publiq's APIs through a frontend application, you should only use _user access tokens_ or _client identification_, **never _client access tokens_**. This is because you can only get client access tokens by requesting them using your client id and secret, and you should make sure that your client secret stays secret. If you put your client secret in a frontend application, it becomes public.

_User access tokens_ and _client identification_ on the other hand can safely be used in a frontend application.

#### Scenario 3: Your app has a backend

If your app has a backend, and you don't want your users to have to log in through UiTID, you can use _client access tokens_ to make requests in the name of your API client instead of a user.

This setup is also ideal for machine to machine communication, for example for imports on EntryAPI.

Client access tokens do expire, but your app's backend can always request a new client access token using it's client id and secret which don't change. So you can also use this authentication method in long-running background processes without user interaction for example.