# HTTP tracking API source

The HTTP Tracking API lets you record data from any website or application. Requests are routed to our servers, and your data is routed to any destination you desire.

## Event API <a href="track" id="track"></a>

You may use the event API to capture the actions that your users perform. Every action results in what is known as an "event," which have associated properties. 

You should keep track of activities that are indications of your app's performance, such as Signed Up, Item Purchased, and Article Bookmarked. To begin, we recommend tracking only a few key events. More may easily be added later!

Example `event` call:

```c
POST  https://api.commander1.com/v2/{siteId}/events
```

```json
{
  "event": "search",
  "eventId": "202110130000000000"
  "properties": {
      "search_term": "t-shirts", 
      "user": {
          "id": "12345",
          "email":"toto@domain.fr",
          "consent_categories": [1,3]
      }
  },
  "device": {
   "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.86 Safari/537.36",
    "ip": "108.0.78.21", 
    "cookies":"fbp=123; fbc=456; _ga=GA1.3.593276215.1565602323"
 },
 "eventTimestamp": "2015-12-12T19:11:01.249Z"

}
```

Find details on **best practices in event naming** as well as the **`event` method payload** in our [Spec](../../../../developers/tracking/about-events/).

## User API

User API let's you update/delete/create users in the database. Find details on [User API spec](https://community.commandersact.com/datacommander/api/users).

## Product API

Product API let's you import your product's catalog in the database. It is mostly used to enrich conversion events with product's properties. Find details in [Product API spec](https://community.commandersact.com/datacommander/api/conversions-and-product-catalog-v2.0#upsert-products).
