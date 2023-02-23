# Javascript destination builder

For more advanced users, we propose to create custom destinations using server-side **javascript** (aka Node.js), but with an **easy and simplified** subset of Node.js : the _**Javascript Sandbox**_.

## Javascript Sandbox

Sandboxed JavaScript is a simplified Javascript that allows you to execute arbitrary JavaScript logic from your custom destination securely and easily (no need to learn Node.js or to understand the async/await syntax for example. If you know the basics of Javascript ES5, it is enough)

This simplified Javascript is based on [helpers](serverside-js-helpers.md), set of methods that allow you to easily and quickly process and send your data.

{% hint style="info" %}
The technology for destination's template javascript sandbox in the platform is, to a large extent, compatible with Google Tag manager templates.\
In most cases, templates written for GTM run in Commanders'act with no (or few) changes
{% endhint %}

{% hint style="info" %}
You can also import templates created on GTM inside your catalog in a few clics with a 100% no-code experience.
{% endhint %}

## Event or Audience destination

You can choose to create an **Event** destination (to forward events like purchase, page view...) or **Audience** destination (send users who entered or were removed from a specific segment).

For **Event** destination, all [standard ](../../../../developers/tracking/events-reference/)and custom events can be used as input.

For **Audience** destination, only 2 system events are managed:

* `user_enters_segment`
* `user_leaves_segment`

These 2 events are automatically trigger by the system when a user enter or leave a segment.\
\
Format of audience events:

```json
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

```json
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
