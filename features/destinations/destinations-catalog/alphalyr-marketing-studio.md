# Alphalyr Marketing Studio

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Alphalyr](https://alphalyr.fr/) helps you boosting your omnichannel commerce with the data that matters.\
Using this destination you can connect your activities and events with [Alphalyr Marketing Studio](https://alphalyr.fr/marketing-studio/).&#x20;

## Key features

The Alphalyr Marketing Studio destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports Alphalyr's page types, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Rakuten Advertising.

## Destination setup

### Configuration

<table><thead><tr><th width="404">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Client Public Key</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Your unique public key as given by Alphalyr Marketing Studio. This setting supports dynamic values <strong>[1].</strong></p></td></tr><tr><td><code>Customer Type</code></td><td>Defines your customer type. Takes the value <code>0</code> when it is an old client and <code>1</code> when it is a new one. This setting supports dynamic values <strong>[1].</strong></td></tr><tr><td><code>User Unique Identifier (UUID)</code></td><td>UUID value of the user's cookie. Following the latest updates to the ITP protocol on Safari / iOS, Alphalyr strongly recommends that you use a "server" cookie coming directly from your first party domain. This setting supports dynamic values <strong>[1].</strong></td></tr><tr><td><code>Custom Data</code></td><td>Additional data that can be added for custom data processing. This setting supports dynamic values <strong>[1].</strong></td></tr><tr><td><code>Is SPA</code></td><td>Whether your website is a Single Page Application.</td></tr><tr><td><code>GDPR Consent</code></td><td>GDPR consent. It takes the value <code>1</code> when GDPR applies or <code>0</code> otherwise. This setting supports dynamic values <strong>[1].</strong></td></tr><tr><td><code>Consent Status for Ads &#x26; Marketing</code></td><td>Consent status for ads &#x26; marketing. It takes the value <code>1</code> if the user has consented to the use of his data for targeting and marketing or <code>0</code> otherwise. This parameter is transmitted to Alphalyr's partners. This setting supports dynamic values <strong>[1].</strong></td></tr><tr><td><code>Consent Status for Performance</code></td><td>Consent status for performance. It takes the value <code>1</code> if the user has consented to the use of his data for the measurement of performance measurement or <code>0</code> otherwise. This parameter is transmitted to Alphalyr's partners. This setting supports dynamic values <strong>[1].</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** This feature allows you to set an event property holding a dynamic value by adding two open braces (`{{`) in front of your property name and two close braces (`}}`) at the end (E.g. `{{myEventPropertyPathAndName}}`).
{% endhint %}

## Quick reference

{% hint style="info" %}
Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.
{% endhint %}

| Commanders Act Events | Alphalyr Page Types |
| --------------------- | ------------------- |
| `purchase`            | `purchase`          |
| `view_cart`           | `cart`              |
| `view_item`           | `product`           |
| `view_item_list`      | `category`          |
| `[All other events]`  | `home`              |

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table><thead><tr><th width="412.6685580062746">Commanders Act Properties</th><th>Alphalyr Properties</th></tr></thead><tbody><tr><td><code>(event_name)</code></td><td><code>page</code> <strong>[1]</strong></td></tr><tr><td><code>Client Public Key</code></td><td><code>aid</code></td></tr><tr><td><code>user.email_md5</code></td><td><code>cid</code></td></tr><tr><td><p><code>User Unique Identifier (UUID)</code></p><p><code>user.consistent_anonymous_id</code></p></td><td><code>uuid</code> <strong>[2]</strong></td></tr><tr><td><code>context.page.referrer</code></td><td><code>referrer</code></td></tr><tr><td><code>context.device.ip</code></td><td><code>ip_address</code> <strong>[3]</strong></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>user_agent</code></td></tr><tr><td><code>(eventModel.app.name)</code></td><td><code>deviceType</code> <strong>[4]</strong></td></tr><tr><td><code>context.page.url</code></td><td><code>path</code> <strong>[5]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>prodId</code> <strong>[6]</strong></td></tr><tr><td><code>items.X.product.name</code></td><td><code>prodDescription</code> <strong>[6]</strong></td></tr><tr><td><code>items.X.product.price</code></td><td><code>prodPrice</code> <strong>[6]</strong></td></tr><tr><td><code>item_list_id</code></td><td><code>catId</code> <strong>[7]</strong></td></tr><tr><td><code>item_list_name</code></td><td><code>catDescription</code> <strong>[7]</strong></td></tr><tr><td><code>items.X.id</code>:<code>items.X.quantity</code>:<code>items.X.product.price</code></td><td><code>products</code> <strong>[8][9]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code> <strong>[9]</strong></td></tr><tr><td><p><code>revenue</code></p><p><code>value</code></p></td><td><code>totalPrice</code> <strong>[9][10]</strong></td></tr><tr><td><code>value</code></td><td><code>totalPriceWithTax</code> <strong>[11]</strong></td></tr><tr><td><code>shipping_amount</code></td><td><code>shippingPrice</code> <strong>[11]</strong></td></tr><tr><td><code>id</code></td><td><code>reference</code> <strong>[11]</strong></td></tr><tr><td><code>Customer Type</code></td><td><code>new</code> <strong>[11]</strong></td></tr><tr><td><code>coupon</code></td><td><code>discountCode</code> <strong>[11]</strong></td></tr><tr><td><code>items.X.discount</code></td><td><code>discountAmount</code> <strong>[8][11]</strong></td></tr><tr><td><code>Custom Data</code></td><td><code>customData</code> <strong>[11]</strong></td></tr><tr><td><code>GDPR Consent</code></td><td><code>gdpr_consent</code></td></tr><tr><td><code>Consent Status for Ads &#x26; Marketing</code></td><td><code>consent_ads</code></td></tr><tr><td><code>Consent Status for Performance</code></td><td><code>consent_performance</code></td></tr><tr><td><code>context.device.lifecycle.session_id</code></td><td><code>gaSessionId</code> <strong>[12]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See [Quick reference](alphalyr-marketing-studio.md#quick-reference) for more details.\
**\[2]** Field automatically hashed with SHA256 if passed in clear. Priority order is provided on the left column.\
**\[3]** Field anonymized.\
**\[4]** This is either<mark style="color:blue;">`m`</mark>or<mark style="color:blue;">`d`</mark>depending if<mark style="color:blue;">`eventModel.app.name`</mark>is set or not.\
**\[5] T**he<mark style="color:blue;">`pathname`</mark>part of<mark style="color:blue;">`context.page.url`</mark>is set: additional parameter are added to the request based on<mark style="color:blue;">`searchParams`</mark>(See [URL object](https://developer.mozilla.org/en-US/docs/Web/API/URL) for more details).\
**\[6]** For Alphalyr<mark style="color:blue;">`product`</mark>page type only.\
**\[7]** For Alphalyr<mark style="color:blue;">`category`</mark>page type only.\
**\[8]** All items are taken into account.\
**\[9]** For Alphalyr<mark style="color:blue;">`purchase`</mark>and<mark style="color:blue;">`cart`</mark>page type only.\
**\[10]** Depending if Alphalyr page type is<mark style="color:blue;">`purchase`</mark>or<mark style="color:blue;">`cart`</mark>then<mark style="color:blue;">`revenue`</mark>or<mark style="color:blue;">`value`</mark>is used respectively.\
**\[11]** For Alphalyr<mark style="color:blue;">`purchase`</mark>page type only.\
**\[12] W**hen<mark style="color:blue;">`Is SPA`</mark>is flagged only.
{% endhint %}
