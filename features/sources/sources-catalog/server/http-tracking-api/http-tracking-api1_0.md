---
description: Deprecated
---

# (deprecated) HTTP tracking API source 1.0

{% hint style="danger" %}
You are looking to the old version of the API (version 1.0)\
Commanders Act will end support and maintenance for HTTP tracking API source 1.0 on August 31, 2023.\
**This API will be fully deprecated on December 2023**. After this date, the current format will no longer be supported and any requests using it may generates error.

We encourage you to begin using the new payload format as soon as possible to ensure a smooth transition. The new format is described [here](./#track). Please refer to our documentation for more information on how to use the new format.
{% endhint %}

{% hint style="warning" %}
What changed in the payload format from the 1.0 to the 2.0 version :&#x20;

1. All event data were inside the **`properties`** object. They are now at the root. The `properties` object doesn't exist any more.
2. All contextual meta-data were at the root, they are now inside a new **`context`** object. For example these meta-data obects `event_id`, `device`, `page`, `app`, `event_timestamp` are now in the `context` object.
{% endhint %}

The HTTP Tracking API 1.0 lets you record data from any website or application. Requests are routed to our servers, and your data is routed to any destination you desire.

## Setup

### Headers

#### Authentication

Authenticate to the Tracking API by sending your project’s **Source Key** along with a request in the headers like so: `Authorization: Bearer NJtcKaoCYu...mGZDxRgMBMUw==`

{% hint style="info" %}
The source key is provided to you when you create a source in the [`source catalogue`](../../)
{% endhint %}

#### Content-Type <a href="#content-type" id="content-type"></a>

To send data to our HTTP API, a content-type header must be set to `'application/json'`.

### Errors

We presently return a 200 response for all API requests, thus debugging should be done using the platform interface or our [config API](../../../../../developers/config-api.md) (event inspector or event delivery API). The sole exception is that if the request is too large or the JSON is invalid, it will return a 400.

### Max Request Size <a href="#max-request-size" id="max-request-size"></a>

There is a maximum of `32KB` per API request.

### Rate limit

There is no real rate limit above which the system will discard your data. But if you need to import at a rate faster than **500 requests per second**, please [contact us](mailto:support@commandersact.com) beforehand.

## Event API <a href="#track" id="track"></a>

You may use the event API to capture the actions that your users perform. Every action results in what is known as an "event," which have associated properties.

You should keep track of activities that are indications of your app's performance, such as Signed Up, Item Purchased, and Article Bookmarked. To begin, we recommend tracking only a few key events. More may easily be added later!

Example `event` call: <mark style="color:red;">**(**</mark>[<mark style="color:red;">**deprecated**</mark>](#user-content-fn-1)[^1]<mark style="color:red;">**)**</mark>

```c
POST  https://collect.commander1.com/events?tc_s={siteId}
```

```json
{
  "event_name": "search",
  "event_id": "202110130000000000",
  "event_timestamp": 1639044446636,
  "properties": {
      "search_term": "t-shirts", 
      "user": {
          "id": "12345",
          "email":"toto@domain.fr",
          "consent_categories": [1,3]
      }
  },
  "page": {
    "title": "Search page",
    "location": "https://shop.com/search?q=..."
  },
  "device": {
    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.86 Safari/537.36",
    "ip": "102.3.4.56", 
    "cookie":"_fbp=123; _fbc=456; _ga=789"
 }
}
```

Find details on **best practices in event naming** as well as the **`event` method payload** in our [Spec](../../../../../developers/tracking/about-events/).

{% hint style="info" %}
If you want to use Http tracking API from you mobile APP instead of SDK, look at the [Mobile event specificity](../../../../../developers/tracking/about-events/mobile-sdk-event-specificity.md)
{% endhint %}

{% hint style="info" %}
Timestamps supported are in milliseconds (ms).
{% endhint %}

## User API

User API let's you update/delete/create users in the database. Find details on [User API spec](https://community.commandersact.com/datacommander/api/users).

## Product API

Product API let's you import your product's catalog in the database. It is mostly used to enrich conversion events with product's properties. Find details in [Product API spec](https://community.commandersact.com/datacommander/api/conversions-and-product-catalog-v2.0#upsert-products).

[^1]: See information at the top of the page
