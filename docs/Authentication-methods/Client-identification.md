# Client identification

Some APIs only expose public information and need to be accessible directly from a browser, like [Search API 3](https://publiq.stoplight.io/docs/uitdatabank/reference/Search-API.v3.json) or the UiTPAS advantages search. 

These APIs only require you to specify the client id of your integration for customization and technical support purposes. For example your client id can have a custom default query in Search API 3 to always filter out search results that are irrelevant to your integration.

You can specify your client id in requests to these APIs in two ways.

## Via header

You can specify your client id as an `x-client-id` HTTP header. For example on Search API 3:

```
curl https://search.uitdatabank.be/events/ -H "x-client-id: YrgBoha6aRSrfIcsFt8PISe4u0EoM45k"
```

Using a header can be helpful to only have to set it once depending on the programming language and/or HTTP library you are using. It also reduces the URL size.

**Try it!**

Set your client id in the **Headers** tab in the form below and send your request to try it out!

```json http
{
  url: 'https://search.uitdatabank.be/events/',
  method: "GET",
  headers: {
    "x-client-id": "YOUR_CLIENT_ID"
  }
}
```

## Via query parameter

Alternatively you can specify a `clientId` URL query parameter instead of an HTTP header. For example on Search API 3:

```
curl https://search.uitdatabank.be/events/?clientId=YrgBoha6aRSrfIcsFt8PISe4u0EoM45k
```

Using a query parameter can be helpful for link sharing or when doing quick manual tests.

**Try it!**

Set your client id in the **Query** tab in the form below and send your request to try it out!

```json http
{
  url: 'https://search.uitdatabank.be/events/',
  method: "GET",
  query: {
    "clientId": "YOUR_CLIENT_ID"
  }
}
```