# Client identification

Some APIs only expose public information and need to be accessible directly from a browser, like [Search API 3](https://publiq.stoplight.io/docs/uitdatabank/reference/Search-API.v3.json) or the UiTPAS advantages search. 

These APIs only require you to specify the client id of your integration for customization and technical support purposes. For example your client id can have a custom default query in Search API 3 to always filter out search results that are irrelevant to your integration.

You can specify your client id in requests to these APIs in two ways.

#### `x-client-id` header

You can specify your client id as an `x-client-id` HTTP header. For example on Search API 3:

```
curl https://search.uitdatabank.be/events/ -H "x-client-id: YrgBoha6aRSrfIcsFt8PISe4u0EoM45k"
```

#### `clientId` query parameter

Alternatively you can specify a `clientId` URL query parameter instead of an HTTP header, which can help with caching, link sharing, etc. For example on Search API 3:

```
curl https://search.uitdatabank.be/events/?clientId=YrgBoha6aRSrfIcsFt8PISe4u0EoM45k
```