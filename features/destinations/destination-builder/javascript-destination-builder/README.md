# Javascript destination builder

For more advanced users, we propose to create custom destinations using server-side **javascript** (aka Node.js), but with an **easy and simplified** subset of Node.js : the _**Javascript Sandbox**_.

## Javascript Sandbox

Sandboxed JavaScript is a simplified Javascript that allows you to execute arbitrary JavaScript logic from your custom destination securely and easily (no need to learn Node.js or to understand the async/await syntax for example. If you know the basics of Javascript ES5, it is enough)

This simplified Javascript is based on [helpers](serverside-js-helpers.md), set of methods that allow you to easily and quickly process and send your data.

{% hint style="info" %}
The technology for destination's template javascript sandbox in the platform is, to a large extent, compatible with Google Tag manager templates. \
In most cases, templates written for GTM run in Commanders'act with no (or few) changes
{% endhint %}

{% hint style="info" %}
You can also import templates created on GTM inside your catalog in a few clics with a 100% no-code experience.
{% endhint %}

## Event or Audience destination

You can choose to create an **Event** destination (send events like purchase, page view...) or **Audience** destination (send users who entered or were removed from a specific segment).

For **Event** destination, please refer to our [event reference documentation](../../../../developers/tracking/events-reference/).

Example of event:

```json
{
  "event_name": "search",
  "search_term": "blue t-shirt",
  "user": {
    "id": "12345",
    "email": "anakin.skywalker@domain.com",
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

For **Audience** destination, only 2 dedicated events are managed:&#x20;

* `user_enters_segment`
* `user_leaves_segment`

Example of audience events:

```
{
  "event_name": "user_enters_segment",
  "user": {
    "id": "user1",
    "email": "user1@example.com",
    "firstname": "john user1",
    "lastname": "Doe"
  },
  "context": {
    "segment_id": 1,
    "segment_name": "Audience 1"
  }
}
```

```
{
  "event_name": "user_leaves_segment",
  "user": {
    "id": "user1",
    "email": "user1@example.com",
    "firstname": "john user1",
    "lastname": "Doe"
  },
  "context": {
    "segment_id": 1,
    "segment_name": "Audience 1"
  }
}
```
