# Eulerian Marketing Platform

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Eulerian Marketing Platform](https://www.eulerian.com/en) is a comprehensive data-centric marketing solution designed to help businesses collect, analyze, attribute, and activate their marketing data across all digital and offline channels. Using this destination you can send data to Eulerian Analytics by levereging the [Eulerian Measurement Protocol](https://doc.api.eulerian.com/#section/Eulerian-Measurement-Protocol).

## Key features

The Eulerian Marketing Platform destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [Eulerian's JSON POST request structure](https://doc.api.eulerian.com/#section/Eulerian-Measurement-Protocol/Protocol-Reference), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Custom events and properties**: you can freely push custom events and properties based on your specific needs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Eulerian.

## Destination setup

{% hint style="warning" %}
Ensure the domain you declared when creating your Eulerian account matches the one sent in the `url`  parameter (See [Field mappings](eulerian-marketing-platform.md#field-mappings)). You can contact Eurlerian to enable more domains.
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Domain Name</code></td><td><em><strong><code>Required</code></strong></em><br>This is the value of the domain provided in Eulerian data-collection domain (E.g. with "https://io1.eulerian.net" you need to provide just <code>io1.eulerian.net</code>).</td></tr><tr><td><code>Traffic is always consented</code></td><td>Traffic is always consented. <code>WARNING</code>: this mean consent is properly decided <code>BEFORE</code> this is triggered.</td></tr><tr><td><code>TCF String</code></td><td>Use this field to send the full TCFv2 String as defined in the TCF.</td></tr><tr><td><code>TCF Custom Vendor</code></td><td>Use this parameter to send the full list of non TCFv2 vendors, you create them in Eulerian platform and map them to your CMP. The internal ids have to be sent to Eulerian (E.g. <code>89.426.1526</code>).</td></tr></tbody></table>

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.

Eulerian `products` property is set for the following events: \
• `add_to_cart`\
<br>

• `remove_from_cart`

• `purchase`

• `generate_lead`

• `view_item`

All the other events are considered Eurlerian custom events.&#x20;
{% endhint %}

<table><thead><tr><th width="396.6685580062746">Commanders Act Properties</th><th>Eulerian Properties</th></tr></thead><tbody><tr><td><code>event_name</code></td><td><code>actn0</code></td></tr><tr><td><code>context.page.url</code></td><td><code>url</code></td></tr><tr><td><code>page_name</code></td><td><code>urlp</code></td></tr><tr><td><code>page_group</code></td><td><code>pagegroup</code></td></tr><tr><td><code>context.page.referrer</code></td><td><code>rf</code></td></tr><tr><td><code>context.device.screen.width</code> <br><code>context.device.screen.height</code></td><td><code>ss</code></td></tr><tr><td><code>context.device.ip</code></td><td><code>ereplay-ip</code></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>ereplay-ua</code></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>ereplay-time</code></td></tr><tr><td><code>partners.eulerian.device_type</code></td><td><code>ereplay-mdevicetype</code></td></tr><tr><td><code>user.consistent_anonymous_id</code></td><td><code>euidl</code> <strong>[1]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code></td></tr><tr><td><code>user.id</code></td><td><code>uid</code></td></tr><tr><td><code>user.email_sha256</code></td><td><code>eemail</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.os.version</code></td><td><code>eos</code></td></tr><tr><td><code>context.device.model</code></td><td><code>ehw</code></td></tr><tr><td><code>context.app.namespace</code></td><td><code>ea-appname</code></td></tr><tr><td><code>context.app.version</code></td><td><code>ea-appversion</code></td></tr><tr><td><code>partners.eulerian.app_already_installed</code></td><td><code>ea-appinstalled</code></td></tr><tr><td><code>context.device.advertising_id</code></td><td><p><code>ea-android-adi</code> <strong>[2]</strong></p><p><code>ea-ios-idfa</code> <strong>[3]</strong> <br><br></p></td></tr><tr><td><code>context.device.ad_tracking_enabled</code></td><td><p><code>ea-android-islat</code> <strong>[2]</strong></p><p><code>ea-ios-islat</code> <strong>[3]</strong><br></p></td></tr><tr><td><code>context.device.android_referrer</code></td><td><code>ea-android-referer</code></td></tr><tr><td><code>context.device.idfv</code></td><td><code>ea-ios-idfv</code></td></tr><tr><td><code>Traffic is always consented</code></td><td><code>enoepm</code> <strong>[4]</strong></td></tr><tr><td><code>Disallowed Category</code></td><td><code>pmcat</code> <strong>[5]</strong></td></tr><tr><td><code>TCF String</code></td><td><code>gdpr_consent</code> <strong>[5]</strong></td></tr><tr><td><code>(TCF String)</code></td><td><code>gdpr</code> <strong>[5][6]</strong></td></tr><tr><td><code>TCF Custom Vendor</code></td><td><code>gdpr_customvendor</code></td></tr><tr><td><code>items.X.id</code></td><td><code>products.X.ref</code></td></tr><tr><td><code>items.X.product.name</code></td><td><code>products.X.name</code></td></tr><tr><td><code>items.X.quantity</code></td><td><code>products.X.quantity</code> <strong>[13]</strong></td></tr><tr><td><code>items.X.product.price</code></td><td><code>products.X.amount</code></td></tr><tr><td><code>items.X.product.brand</code></td><td><code>products.X.params.item_brand</code></td></tr><tr><td><code>items.X.product.category_1</code></td><td><code>products.X.params.item_category</code></td></tr><tr><td><code>items.X.product.category_2</code></td><td><code>products.X.params.item_category2</code></td></tr><tr><td><code>items.X.product.category_3</code></td><td><code>products.X.params.item_category3</code></td></tr><tr><td><code>items.X.product.category_4</code></td><td><code>products.X.params.item_category4</code></td></tr><tr><td><code>items.X.product.category_5</code></td><td><code>products.X.params.item_category5</code></td></tr><tr><td><code>items.X.list_id</code></td><td><code>products.X.params.item_list_id</code></td></tr><tr><td><code>items.X.item_list_name</code></td><td><code>products.X.params.item_list_name</code></td></tr><tr><td><code>(event_name)</code></td><td><code>scart</code> <strong>[7]</strong><br><code>order</code> <strong>[10]</strong><br><code>estimate</code> <strong>[11]</strong><br><code>enopagedt</code> <strong>[12]</strong></td></tr><tr><td><code>id</code></td><td><code>ref</code> <strong>[8]</strong><br><code>actions.0.params.id</code> <strong>[15]</strong></td></tr><tr><td><code>value</code></td><td><code>amount</code> <strong>[8]</strong><br><code>actions.0.params.value</code> <strong>[15]</strong></td></tr><tr><td><code>status</code></td><td><code>status</code> <strong>[8][9]</strong><br><code>actions.0.params.status</code> <strong>[15]</strong></td></tr><tr><td><code>coupon</code></td><td><code>coupon</code> <strong>[8]</strong><br><code>actions.0.params.coupon</code> <strong>[15]</strong></td></tr><tr><td><code>shipping_amount</code></td><td><code>shipping_amount</code> <strong>[8]</strong></td></tr><tr><td><code>tax_amount</code></td><td><code>tax_amount</code> <strong>[8]</strong></td></tr><tr><td><code>payment_method</code></td><td><code>payment</code> <strong>[8]</strong><br><code>actions.0.params.payment_method</code> <strong>[15]</strong></td></tr><tr><td><code>type</code></td><td><code>type</code> <strong>[8]</strong></td></tr><tr><td><code>shipping_provider</code></td><td><code>shipping_provider</code> <strong>[8]</strong></td></tr><tr><td><code>discount_value</code></td><td><code>discount_value</code> <strong>[8]</strong></td></tr><tr><td><code>original_value</code></td><td><code>original_value</code> <strong>[8]</strong></td></tr><tr><td><code>original_revenue</code></td><td><code>original_revenue</code> <strong>[8]</strong></td></tr><tr><td><code>original_tax_amount</code></td><td><code>original_tax_amount</code> <strong>[8]</strong></td></tr><tr><td><code>returned_value</code></td><td><code>returned_value</code> <strong>[8]</strong></td></tr><tr><td><code>returned_quantity</code> </td><td><code>returned_quantity</code> <strong>[8]</strong></td></tr><tr><td><code>cancelled_value</code> </td><td><code>cancelled_value</code> <strong>[8]</strong></td></tr><tr><td><code>cancelled_quantity</code></td><td><code>cancelled_quantity</code> <strong>[8]</strong></td></tr><tr><td><code>partners.eulerian.margin</code></td><td><code>margin</code> <strong>[8]</strong></td></tr><tr><td><code>partners.eulerian.shop</code></td><td><code>shop</code> <strong>[8]</strong></td></tr><tr><td><code>search_term</code></td><td><code>eisd0</code> <strong>[14]</strong><br><code>actions.0.params.search_term</code> <strong>[15]</strong></td></tr><tr><td><code>event_name</code></td><td><code>actions.0.name</code> <strong>[15]</strong></td></tr><tr><td><code>revenue</code></td><td><code>actions.0.params.revenue</code> <strong>[15]</strong></td></tr><tr><td><code>shipping_tier</code></td><td><code>actions.0.params.shipping_tier</code> <strong>[15]</strong></td></tr><tr><td><code>method</code></td><td><code>actions.0.params.method</code> <strong>[15]</strong></td></tr><tr><td><code>type</code></td><td><code>actions.0.params.type</code> <strong>[15]</strong></td></tr><tr><td><code>content_type</code></td><td><code>actions.0.params.content_type</code> <strong>[15]</strong></td></tr><tr><td><code>item_id</code></td><td><code>actions.0.params.content_item_id</code> <strong>[15]</strong></td></tr><tr><td><code>item_list_name</code></td><td><code>actions.0.params.item_list_name</code> <strong>[15]</strong></td></tr></tbody></table>

{% hint style="info" %}
> **\[1]** Automatically hashed via SHA256 when provided in clear text.\
> &#xNAN;**\[2]** Set if `context.device.os.name`  is set with `android`  (case insensitive).\
> &#xNAN;**\[3]** Set if `context.device.os.name`  is set with `ios`  (case insensitive).\
> &#xNAN;**\[4]** Set with `1`  when `Traffic is always consented (enoepm)`  is flagged.\
> &#xNAN;**\[5]** Set if `Traffic is always consented`  is not flagged.\
> &#xNAN;**\[6]** Set with `1`  when `TCF String`  is provided.\
> &#xNAN;**\[7]** Set with `1`  if `event_name` is `add_to_cart`  or `remove_from_cart`  .\
> &#xNAN;**\[8]** Set if `event_name` is `purchase`  or `generate_lead`  and required.\
> &#xNAN;**\[9]** Default value: `pending`  .\
> &#xNAN;**\[10]** Set with `1`  if `event_name`  is `purchase`  .\
> &#xNAN;**\[11]** Set with `1`  if `event_name`  is `generate_lead`  .\
> &#xNAN;**\[12]** Set with `0`  if `event_name`  is `page_view`  or `1` for Eulerian custom events.\
> &#xNAN;**\[13]** The value is set to its opposite when the event is `remove_from_cart`  .\
> &#xNAN;**\[14]** Set if `event_name` is set with `search`  .\
> &#xNAN;**\[15]** Set for Eulerian custom events.
{% endhint %}
