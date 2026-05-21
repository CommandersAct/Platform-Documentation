# OpenAI Conversions API

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[OpenAI](https://openai.com/) is artificial intelligence research organization. Using this destination you can can leverage [OpenAI Conversions API](https://developers.openai.com/ads/conversions-api) to send conversion events directly to OpenAI for downstream attribution and reporting.

{% hint style="warning" %}
At present, [OpenAI/ChatGPT Ads](https://ads.openai.com/) is in an early stage, and availability for businesses is limited.\
Moreover, the European Union is not yet whitelisted to leverage OpenAI Ads.
{% endhint %}

## Key features

The OpenAI Conversions API destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) model covers [OpenAI events](https://developers.openai.com/ads/supported-events), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Event mapping**: change standard mapping between OpenAI events and yours.
* **Support for multi-item data**: information included in the [item](https://doc.commandersact.com/developers/tracking/events-reference#item) array is dispatched to OpenAI.
* **Support batch mode**: send multiple events in one single request.

## Destination setup

Ensure you have access to [OpenAI Ads](https://ads.openai.com/).

{% hint style="info" %}
Event deduplication is peformed using <mark style="color:blue;">`id`</mark> and <mark style="color:blue;">`type`</mark> (see [Field mappings](openai-conversions-api.md#field-mappings)) and the <mark style="color:blue;">`Pixel Id`</mark> (See [Configuration](openai-conversions-api.md#configuration)).
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>API Key</code></td><td><em><strong><code>Required</code></strong></em><br>Your API key. You can contact OpenAI account team to get this value.</td></tr><tr><td><code>Pixel Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your pixel identifier. You can contact OpenAI account team to get this value.</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping between OpenAI event types and your events. Accepted values for <code>OpenAI event type</code> : <code>appointment_scheduled</code> , <code>checkout_started</code> , <code>contents_viewed</code> , <code>custom</code> , <code>items_added</code> , <code>lead_created</code> , <code>order_created</code> , <code>page_viewed</code> , <code>registration_completed</code> , <code>subscription_created</code> and <code>trial_started</code> .</td></tr></tbody></table>

## Quick reference

| Commanders Act Events                                               | OpenAI Event Types                 |
| ------------------------------------------------------------------- | ---------------------------------- |
| `appointment_scheduled`                                             | `appointment_scheduled`            |
| <p><code>checkout_started</code><br><code>begin_checkout</code></p> | `checkout_started`                 |
| `contents_viewed`                                                   | `contents_viewed`                  |
| `custom`                                                            | `custom`                           |
| `items_added`                                                       | `items_added`                      |
| <p><code>lead_created</code><br><code>generate_lead</code></p>      | `lead_created`                     |
| <p><code>order_created</code><br><code>purchase</code></p>          | `order_created`                    |
| <p><code>page_view</code><br><code>page_viewed</code></p>           | `page_viewed`                      |
| <p><code>registration_completed</code><br><code>sign_up</code></p>  | `registration_completed`           |
| `subscription_created`                                              | `subscription_created`             |
| `trial_started`                                                     | `trial_started`                    |
| `[Any Event]`                                                       | `[Any OpenAI Event Type]` **\[1]** |

{% hint style="info" %}
**1.** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](openai-conversions-api.md#configuration).
{% endhint %}

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th width="246">Smart Mapping Fields</th><th width="323.6685580062746">Commanders Act Default Properties</th><th width="330.3314419937253">OpenAI Properties</th></tr></thead><tbody><tr><td><code>Event Id</code></td><td><code>context.event_id</code></td><td><code>id</code> <strong>[*]</strong></td></tr><tr><td>-</td><td><code>(event_name)</code></td><td><code>type</code> <strong>[1]</strong></td></tr><tr><td><code>Event Timestamp</code></td><td><code>context.event_timestamp</code></td><td><code>timestamp_ms</code> <strong>[2]</strong></td></tr><tr><td><code>Custom Event Name</code></td><td><p><code>partners.openai.custom_event_name</code></p><p><code>event_name</code></p></td><td><code>custom_event_name</code> <strong>[3]</strong></td></tr><tr><td><code>OpenAI Privacy Identifier</code></td><td><code>partners.openai.oppref</code></td><td><code>oppref</code></td></tr><tr><td><code>Action Source</code></td><td><code>type</code></td><td><code>action_source</code> <strong>[4]</strong></td></tr><tr><td><code>Page URL</code></td><td><code>context.page.url</code></td><td><code>source_url</code> <strong>[5]</strong></td></tr><tr><td><code>User Email</code></td><td><code>user.email</code></td><td><code>email_sha256</code> <strong>[6][7]</strong></td></tr><tr><td><code>User Phone</code></td><td><code>user.phone</code></td><td><code>phone_number_sha256</code> <strong>[6][7]</strong></td></tr><tr><td><code>User Id</code></td><td><code>user.id</code></td><td><code>external_id_sha256</code> <strong>[6][7]</strong><br><code>external_id</code> <strong>[6]</strong></td></tr><tr><td><code>User Country</code></td><td><code>user.country</code></td><td><code>country_sha256</code> <strong>[6][7]</strong></td></tr><tr><td><code>User City</code></td><td><code>user.city</code></td><td><code>city_sha256</code> <strong>[6][7]</strong></td></tr><tr><td><code>User ZIP Code</code></td><td><code>user.zipcode</code></td><td><code>zip_code_sha256</code> <strong>[6]</strong></td></tr><tr><td><code>Device IP</code></td><td><code>context.device.ip</code></td><td><code>ip_address</code> <strong>[6]</strong></td></tr><tr><td><code>Device User Agent</code></td><td><code>context.device.user_agent</code></td><td><code>user_agent</code> <strong>[6]</strong></td></tr><tr><td><code>Opt-out</code></td><td><code>partners.openai.opt_out</code></td><td><code>opt_out</code></td></tr><tr><td>-</td><td><code>(event_name)</code></td><td><code>type</code> <strong>[8]</strong></td></tr><tr><td><code>Value</code></td><td><code>value</code></td><td><code>amount</code> <strong>[8]</strong></td></tr><tr><td><code>Currency</code></td><td><code>currency</code></td><td><code>currency</code> <strong>[8]</strong></td></tr><tr><td><code>Plan Identifier</code></td><td><code>partners.openai.plan_id</code></td><td><code>plan_id</code> <strong>[8][9]</strong></td></tr><tr><td><code>Item List</code></td><td><code>items</code></td><td><code>contents</code> <strong>[8]</strong></td></tr><tr><td><code>Item Id</code></td><td><code>items.X.id</code></td><td><code>contents.X.id</code> <strong>[8]</strong></td></tr><tr><td><code>Item Name</code></td><td><code>items.X.product.name</code></td><td><code>contents.X.name</code> <strong>[8]</strong></td></tr><tr><td><code>Item Content Type</code><br><code>Content Type</code></td><td><code>items.X.content_type</code><br><code>content_type</code></td><td><code>contents.X.content_type</code> <strong>[8][10]</strong></td></tr><tr><td><code>Item Price</code></td><td><code>items.X.product.price</code></td><td><code>contents.X.amount</code> <strong>[8]</strong></td></tr><tr><td><code>Item Quantity</code></td><td><code>items.X.quantity</code></td><td><code>contents.X.quantity</code> <strong>[8]</strong></td></tr><tr><td><code>Item Currency</code></td><td><code>items.X.currency</code></td><td><code>contents.X.currency</code> <strong>[8][11]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\*** Mandatory property.\
**1.** See [Quick reference](openai-conversions-api.md#quick-reference) for more details.\
**2.** If it's not passed, the current timestamp is used.\
**3.** Set if <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`custom`</mark> . Default: value in <mark style="color:blue;">`event_name`</mark> .\
**4.** Accepted values: <mark style="color:blue;">`web`</mark> , <mark style="color:blue;">`mobile_app`</mark> , <mark style="color:blue;">`offline`</mark> , <mark style="color:blue;">`physical_store`</mark> , <mark style="color:blue;">`phone_call`</mark> and <mark style="color:blue;">`email`</mark> . Default: value in <mark style="color:blue;">`type`</mark> .\
**5.** Required if <mark style="color:purple;">`action_source`</mark> is <mark style="color:blue;">`web`</mark> .\
**6.** Set in <mark style="color:blue;">`user`</mark> .\
**7.** Automatically normalized and hashed if passed in clear text.\
**8.** Set in <mark style="color:blue;">`data`</mark> when <mark style="color:blue;">`data.type`</mark> is <mark style="color:blue;">`customer_action`</mark> . Value in the currency’s lowest denomination.\
**9.** Set if <mark style="color:blue;">`data.type`</mark> is <mark style="color:blue;">`custom`</mark> or <mark style="color:blue;">`plan_enrollment`</mark> .\
**10.** Priority on the left. Default value: <mark style="color:blue;background-color:blue;">`product`</mark> .\
**11.** Required if <mark style="color:blue;">`amount`</mark> is set and <mark style="color:blue;">`currency`</mark> (top level) is not set.
{% endhint %}
