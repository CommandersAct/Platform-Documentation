---
description: version 2.0
---

# HTTP Tracking API source

The HTTP Tracking API is used to track **events** from any website or application. The data is collected by our servers, and then processed and routed to any configured destination.

To manage users, check instead the dedicated [User API](../../../features/sources/sources-catalog/import-crm-users.md), and for products, the [Product API](../../../features/sources/sources-catalog/import-conversions/api-conversions-and-product-catalog.md).

## Endpoint URL

The API's collect endpoint is available at the following URL:
```
https://collect.commander1.com/events?tc_s={siteId}&token={sourceKey}
```

HTTP method: `POST`

## Parameters

- `tc_s` (required): site id
- `token` (required): source key

{% hint style="info" %}
The source key is displayed in the settings of any [source](../../../features/sources/overview.md).
{% endhint %}

## Headers

### Content type <a href="#content-type" id="content-type"></a>

The endpoint requires a `Content-Type` header set to `application/json`:

```
Content-Type: application/json
```

### Source key

An _alternative_ way to provide the required **source key** to each request is by using an `Authorization` header:

```
Authorization: Bearer 7183b9d4-1031-11ee-be56-0242ac120002
```

{% hint style="info" %}
Instead of a header, the source key should usually be provided through the `token` [URL parameter](#parameters) of the endpoint.
{% endhint %}

## Payload

The properties of the event must be provided in the request body in JSON format.

Find details on **best practices in event naming** as well as the **`event` method payload** in our [specifications](../../../developers/tracking/about-events/).

{% hint style="warning" %}
The format of the payload evolved on Nov. 2022. The old format will still be supported during one year. [More information here](http-tracking-api/http-tracking-api1\_0.md).
{% endhint %}

{% hint style="info" %}
Timestamps must be in milliseconds (ms).
{% endhint %}

{% hint style="info" %}
`consistent_anonymous_id` corresponds to a unique identifier for a user, used on the CAX platform to identify a user. It is the equivalent of CAID cookie on a Web source.
{% endhint %}

## Errors

The endpoint returns a 200 HTTP response to all API requests. Thus, debugging should be done using the platform interface or our [config API](../../../developers/config-api.md) (event inspector or event delivery API).

As an exception, a 400 HTTP code is returned in case the request is too large or the payload JSON is invalid.

## Max Request Size <a href="#max-request-size" id="max-request-size"></a>

There is a maximum of `32KB` per API request.

## Rate limit

There is no real rate limit above which the system will discard your data. But if you need to import at a rate faster than **500 requests per second**, please [contact us](mailto:support@commandersact.com) beforehand.

## Example

Example of an API request:

```
POST https://collect.commander1.com/events?tc_s=29&token=7183b9d4-1031-11ee-be56-0242ac120002
```

```json
{
  "event_name": "search",
  "search_term": "t-shirts",
  "user": {
    "id": "12345",
    "consistent_anonymous_id": "67892"
    "email": "toto@domain.fr",
    "consent_categories": [
      "1",
      "3"
    ]
  },
  "context": {
    "event_id": "202110130000000000",
    "page": {
      "title": "Search page",
      "url": "https://shop.com/search?q=...",
      "lang": "en",
      "referrer": "https://www.google.fr",
      "viewport": {
        "width": 320,
        "height": 568
      }
    },
    "device": {
      "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.86 Safari/537.36",
      "ip": "102.3.4.56",
      "lang": "fr",
      "cookie": "_fbp=123; _fbc=456; _ga=789",
      "timezone": "Europe/Paris"
    },
    "event_timestamp": "1639044446636"
  }
}
```
