# Introduction

## How to get client credentials

Every integration on publiq's APIs requires a client id and in most cases also a client secret to authenticate requests.

To get client credentials for your integration, contact jean-marie@publiq.be.

## Different authentication methods

Each publiq API supports one or more authentication methods, depending on the functionality that it provides.

### Client identification

API endpoints that require no real authentication but need to know what client is accessing it for customization and technical support reasons use [Client identification](Authentication-methods/Client-identification.md). 

Usually used by APIs that need to provide info to anonymous users in web browsers, for example [Search API 3](https://publiq.stoplight.io/docs/uitdatabank/reference/Search-API.v3.json).

### Client access tokens

API endpoints that require the authentication of an API client with secret credentials use [Client access tokens](Authentication-methods/Client-access-token.md). 

Usually used for server-to-server communication to send data or retrieve sensitive data. For example, to [import events into UiTdatabank](https://publiq.stoplight.io/docs/uitdatabank/docs/Guides/Imports/Importing-events.md) or [register ticket sales in UiTPAS](https://publiq.stoplight.io/docs/uitpas/docs/Guides/Ticket-prices-and-sales.md).

### User access tokens

API endpoints that require authentication as a user use [User access tokens](Authentication-methods/User-access-token.md). 

Usually used in situations where a user will log in through publiq's UiTID service and the API client will make requests in that user's name.
