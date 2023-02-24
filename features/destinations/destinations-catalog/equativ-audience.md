# Equativ Audience

[Equativ ](https://equativ.com/)is an advertising technology company.\
Using this destination you can share audiences with Equativ using the [Audience data - API integration](https://help.smartadserver.com/s/article/Audience-data-API-integration-v2).

{% hint style="info" %}
This destination is currently under final review and it will be released soon.
{% endhint %}

## Key features

The Equativ Audience destination provides the following key features:

* **Audience sharing**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model drives audience sharing with Equativ, meaning that you can synchronize your existing user segments, with your partner, in a seamless way.

## Destination setup

{% hint style="info" %}
Select your audiences/user segments to be shared and synchronized with Equativ.
{% endhint %}

## Field mappings

Created segments using [Equativ Segment API](https://datasync-eu.smartadserverapis.com/swagger/v2/index.html#/Segments/post\_segmentproviders\_\_segmentProviderId\_\_segments) holds the following properties:

| Property Name | Property Value                              |
| ------------- | ------------------------------------------- |
| `active`      | true                                        |
| `description` | `context.segment_name`                      |
| `name`        | `context.segment_name`                      |
| `price`       | 0                                           |
| `segmentId`   | ca\_`context.site_id`\_`context.segment_id` |
| `selectable`  | true                                        |
| `ttl`         | 2147483646                                  |

