# TikTok Offline Events

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[TikTok](https://www.tiktok.com/) is a social platform short-form video hosting service.\
This destination leverages TikTok [Events API](https://ads.tiktok.com/help/article/events-api?redirected=1) to [report offline events](https://business-api.tiktok.com/portal/docs?id=1758428013689857).

## Key features

The TikTok Offline Events destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers [TikTok offline events](https://ads.tiktok.com/marketing_api/docs?id=1758428013689857), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to TikTok.

## Destination setup

### Configuration

<table><thead><tr><th width="248">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Event Set Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your event set identifier value. More details are available following this <a href="https://ads.tiktok.com/marketing_api/docs?id=1758428013689857">LINK</a>. This setting supports dynamic values <strong>[1].</strong></td></tr><tr><td><code>Mapping</code></td><td><em><strong><code>Required</code></strong></em><br>Map "TikTok Event Types" with your "Commanders Act events" by setting at least a <code>TikTok Event Type</code> and a <code>Commanders Act Event Name</code> . One entry is required.</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** This feature allows you to set an event property holding a dynamic value by adding two open braces (`{{`) in front of your property name and two close braces (`}}`) at the end (E.g. `{{myEventPropertyPathAndName}}`).
{% endhint %}

## Quick reference

| Commanders Act Events | TikTok Event Type                                                     |
| --------------------- | --------------------------------------------------------------------- |
| `[All events]`        | `CompletePayment` , `Contact` , `Subscribe` and `SubmitForm` **\[1]** |

{% hint style="info" %}
**\[1]** See [Configuration](tiktok-offiline-events.md#configuration) for more details.
{% endhint %}

## Field Mappings

{% hint style="info" %}
See more details on phone format by following this [LINK](https://ads.tiktok.com/gateway/docs/index?identify_key=c0138ffadd90a955c1f0670a56fe348d1d40680b3c89461e09f78ed26785164b\&language=ENGLISH\&doc_id=1758428013689857#item-link-User%20context%20object%20parameters).
{% endhint %}

<table><thead><tr><th width="330.6685580062746">Commanders Act Properties</th><th>TikTok Properties</th></tr></thead><tbody><tr><td><code>Event Set Id</code></td><td><code>event_set_id</code></td></tr><tr><td><code>TikTok Event Type</code></td><td><code>event</code> <strong>[1]</strong></td></tr><tr><td><code>id</code></td><td><code>event_id</code></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>timestamp</code><strong>[2]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>context.user.phone_numbers.0</code> <strong>[3]</strong></td></tr><tr><td><code>user.email</code></td><td><code>context.user.emails.0</code> <strong>[3]</strong></td></tr><tr><td><code>id</code></td><td><code>properties.order_id</code></td></tr><tr><td><code>shop_id</code></td><td><code>properties.shop_id</code></td></tr><tr><td><code>items.X.id</code></td><td><code>properties.contents.X.content_id</code></td></tr><tr><td><code>items.X.product.name</code></td><td><code>properties.contents.X.content_name</code></td></tr><tr><td><code>items.X.product.price</code></td><td><code>properties.contents.X.price</code></td></tr><tr><td><code>items.X.quantity</code></td><td><code>properties.contents.X.quantity</code></td></tr><tr><td><code>items.X.type</code></td><td><code>properties.contents.X.content_type</code></td></tr><tr><td><code>items.X.product.category_1</code>><br><code>items.X.product.category_2</code>><br><code>items.X.product.category_3</code>><br><code>items.X.product.category_4</code>><br><code>items.X.product.category_5</code></td><td><code>properties.contents.X.content_category</code></td></tr><tr><td><code>currency</code></td><td><code>properties.currency</code></td></tr><tr><td><code>value</code></td><td><code>properties.value</code></td></tr><tr><td><code>type</code></td><td><code>properties.event_channel</code></td></tr></tbody></table>

{% hint style="info" %}
&#x20;**\[1]** See <mark style="color:blue;">`Mapping`</mark> in [Configuration](tiktok-offiline-events.md#configuration) for more details.\
&#x20;**\[2]** Timestamp to be provided in milliseconds. This is converted in [ISO-8601](https://en.wikipedia.org/wiki/ISO_8601) format.\
&#x20;**\[3]** Field automatically hashed with SHA256 if not passed in clear.
{% endhint %}
