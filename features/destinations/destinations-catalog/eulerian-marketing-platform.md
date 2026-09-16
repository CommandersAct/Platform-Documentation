---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Eulerian Marketing Platform

[Eulerian Marketing Platform](https://www.eulerian.com/en) is a comprehensive data-centric marketing solution designed to help businesses collect, analyze, attribute, and activate their marketing data across all digital and offline channels. Using this destination you can send data to Eulerian Analytics by leveraging the [Eulerian Measurement Protocol](https://doc.api.eulerian.com/#section/Eulerian-Measurement-Protocol).

## Key features

The Eulerian Marketing Platform destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [Eulerian's JSON POST request structure](https://doc.api.eulerian.com/#section/Eulerian-Measurement-Protocol/Protocol-Reference), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Custom events and properties**: you can freely push custom events and properties based on your specific needs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is bridged to Eulerian.

## Destination setup

{% hint style="warning" %}
Ensure the domain you declared when creating your Eulerian account matches the one sent in the `url` parameter (See [Field mappings](eulerian-marketing-platform.md#field-mappings)). You can contact Eurlerian to enable more domains.
{% endhint %}

### Configuration

<table data-header-hidden="false" data-header-sticky><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Domain Name</code></td><td><em><strong><code>Required</code></strong></em><br>This is the value of the domain provided in Eulerian data-collection domain (E.g. with "https://io1.eulerian.net" you need to provide just <code>io1.eulerian.net</code>).</td></tr><tr><td><code>Traffic is always consented</code></td><td>Traffic is always consented. <code>WARNING</code>: this mean consent is properly decided <code>BEFORE</code> this is triggered.</td></tr><tr><td><code>Disallowed Category</code></td><td>Use this field to provide the categories that are disabled for the current user (E.g. <code>89-5-3</code>). These are the same ids as defined in the Eulerian user interface for each category. You can set this with <code>-</code> (dash) to allow all categories available to the user.</td></tr><tr><td><code>TCF String</code></td><td>Use this field to send the full TCFv2 String as defined in the TCF.</td></tr><tr><td><code>TCF Custom Vendor</code></td><td>Use this parameter to send the full list of non TCFv2 vendors, you create them in Eulerian platform and map them to your CMP. The internal ids have to be sent to Eulerian (E.g. <code>89.426.1526</code>).</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>Eulerian property name</code> and adding the value in <code>Your value</code>.</td></tr></tbody></table>

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.\
Eulerian `products` property is set for the following events:\
• `add_to_cart`

• `remove_from_cart`

• `purchase`

• `generate_lead`

• `view_item`

All the other events are considered Eurlerian custom events.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Smart Mapping Fields</th><th width="374">Commanders Act Properties</th><th width="340">Eulerian Properties</th></tr></thead><tbody><tr><td><code>Page URL</code></td><td><code>context.page.url</code></td><td><code>url</code> <strong>[*]</strong></td></tr><tr><td><code>Page Referrer</code></td><td><code>context.page.referrer</code></td><td><code>rf</code> <strong>[*]</strong></td></tr><tr><td><code>Device Id</code></td><td><code>user.consistent_anonymous_id</code></td><td><code>euidl</code> <strong>[*][1]</strong></td></tr><tr><td><code>Device IP</code></td><td><code>context.device.ip</code></td><td><code>ereplay-ip</code> <strong>[*]</strong></td></tr><tr><td><code>-</code></td><td><code>event_name</code></td><td><code>actn0</code></td></tr><tr><td><code>Page Name</code></td><td><code>page_name</code></td><td><code>urlp</code></td></tr><tr><td><code>Page Group</code></td><td><code>page_group</code></td><td><code>pagegroup</code></td></tr><tr><td><p><code>Device Screen Width</code></p><p><code>Device Screen Height</code></p></td><td><code>context.device.screen.width</code><br><code>context.device.screen.height</code></td><td><code>ss</code></td></tr><tr><td><code>Device User Agent</code></td><td><code>context.device.user_agent</code></td><td><code>ereplay-ua</code></td></tr><tr><td><code>Event Timestamp</code></td><td><code>context.event_timestamp</code></td><td><code>ereplay-time</code></td></tr><tr><td><code>Client Device</code></td><td><code>partners.eulerian.device_type</code></td><td><code>ereplay-mdevicetype</code></td></tr><tr><td><code>Currency</code></td><td><code>currency</code></td><td><code>currency</code></td></tr><tr><td><code>User Id</code></td><td><code>user.id</code></td><td><code>uid</code></td></tr><tr><td><code>User Email SHA256</code></td><td><code>user.email_sha256</code></td><td><code>eemail</code> <strong>[1]</strong></td></tr><tr><td><code>Device OS Version</code></td><td><code>context.device.os.version</code></td><td><code>eos</code></td></tr><tr><td><code>Device Model</code></td><td><code>context.device.model</code></td><td><code>ehw</code></td></tr><tr><td><code>Application Namespace</code></td><td><code>context.app.namespace</code></td><td><code>ea-appname</code></td></tr><tr><td><code>Application Version</code></td><td><code>context.app.version</code></td><td><code>ea-appversion</code></td></tr><tr><td><code>Application Already Installed</code></td><td><code>partners.eulerian.app_already_installed</code></td><td><code>ea-appinstalled</code></td></tr><tr><td><code>Device Advertising Id</code></td><td><code>context.device.advertising_id</code></td><td><p><code>ea-android-adi</code> <strong>[2]</strong></p><p><code>ea-ios-idfa</code> <strong>[3]</strong></p></td></tr><tr><td><code>Ad Tracking Enabled</code></td><td><code>context.device.ad_tracking_enabled</code></td><td><p><code>ea-android-islat</code> <strong>[2]</strong></p><p><code>ea-ios-islat</code> <strong>[3]</strong></p></td></tr><tr><td><code>Device Android Referrer</code></td><td><code>context.device.android_referrer</code></td><td><code>ea-android-referer</code></td></tr><tr><td><code>Device IDFV</code></td><td><code>context.device.idfv</code></td><td><code>ea-ios-idfv</code></td></tr><tr><td><code>-</code></td><td><code>Traffic is always consented</code></td><td><code>enoepm</code> <strong>[4]</strong></td></tr><tr><td><code>-</code></td><td><code>Disallowed Category</code></td><td><code>pmcat</code> <strong>[5]</strong></td></tr><tr><td><code>-</code></td><td><code>TCF String</code></td><td><code>gdpr_consent</code> <strong>[5]</strong></td></tr><tr><td>-</td><td><code>TCF String</code></td><td><code>gdpr</code> <strong>[5][6]</strong></td></tr><tr><td><code>-</code></td><td><code>TCF Custom Vendor</code></td><td><code>gdpr_customvendor</code></td></tr><tr><td><code>Item Id</code></td><td><code>items.X.id</code></td><td><code>products.X.ref</code></td></tr><tr><td><code>Item Name</code></td><td><code>items.X.product.name</code></td><td><code>products.X.name</code></td></tr><tr><td><code>Item Quantity</code></td><td><code>items.X.quantity</code></td><td><code>products.X.quantity</code> <strong>[13]</strong></td></tr><tr><td><code>Item Price</code></td><td><code>items.X.product.price</code></td><td><code>products.X.amount</code></td></tr><tr><td><code>Item Brand</code></td><td><code>items.X.product.brand</code></td><td><code>products.X.params.item_brand</code></td></tr><tr><td><code>Item Category 1</code></td><td><code>items.X.product.category_1</code></td><td><code>products.X.params.item_category</code></td></tr><tr><td><code>Item Category 2</code></td><td><code>items.X.product.category_2</code></td><td><code>products.X.params.item_category2</code></td></tr><tr><td><code>Item Category 3</code></td><td><code>items.X.product.category_3</code></td><td><code>products.X.params.item_category3</code></td></tr><tr><td><code>Item Category 4</code></td><td><code>items.X.product.category_4</code></td><td><code>products.X.params.item_category4</code></td></tr><tr><td><code>Item Category 5</code></td><td><code>items.X.product.category_5</code></td><td><code>products.X.params.item_category5</code></td></tr><tr><td><code>Item List Id</code></td><td><code>items.X.list_id</code></td><td><code>products.X.params.item_list_id</code></td></tr><tr><td><code>Item List Name</code></td><td><code>items.X.item_list_name</code></td><td><code>products.X.params.item_list_name</code></td></tr><tr><td><code>-</code></td><td><code>event_name</code></td><td><code>scart</code> <strong>[7]</strong><br><code>order</code> <strong>[10]</strong><br><code>estimate</code> <strong>[11]</strong><br><code>enopagedt</code> <strong>[12]</strong></td></tr><tr><td><code>Transaction Id</code></td><td><code>id</code></td><td><code>ref</code> <strong>[8]</strong><br><code>actions.0.params.id</code> <strong>[15]</strong></td></tr><tr><td><code>Transaction Value</code></td><td><code>value</code></td><td><code>amount</code> <strong>[8]</strong><br><code>actions.0.params.value</code> <strong>[15]</strong></td></tr><tr><td><code>Transaction Status</code></td><td><code>status</code></td><td><code>status</code> <strong>[8][9]</strong><br><code>actions.0.params.status</code> <strong>[15]</strong></td></tr><tr><td><code>Coupon</code></td><td><code>coupon</code></td><td><code>coupon</code> <strong>[8]</strong><br><code>actions.0.params.coupon</code> <strong>[15]</strong></td></tr><tr><td><code>Shipping Amount</code></td><td><code>shipping_amount</code></td><td><code>shipping_amount</code> <strong>[8]</strong></td></tr><tr><td><code>Tax Amount</code></td><td><code>tax_amount</code></td><td><code>tax_amount</code> <strong>[8]</strong></td></tr><tr><td><code>Payment Method</code></td><td><code>payment_method</code></td><td><code>payment</code> <strong>[8]</strong><br><code>actions.0.params.payment_method</code> <strong>[15]</strong></td></tr><tr><td><code>Conversion Type</code></td><td><code>type</code></td><td><code>type</code> <strong>[8]</strong><br><code>actions.0.params.type</code> <strong>[15]</strong></td></tr><tr><td><code>Shipping Provider</code></td><td><code>shipping_provider</code></td><td><code>shipping_provider</code> <strong>[8]</strong></td></tr><tr><td><code>Discount Value</code></td><td><code>discount_value</code></td><td><code>discount_value</code> <strong>[8]</strong></td></tr><tr><td><code>Original Value</code></td><td><code>original_value</code></td><td><code>original_value</code> <strong>[8]</strong></td></tr><tr><td><code>Original Revenue</code></td><td><code>original_revenue</code></td><td><code>original_revenue</code> <strong>[8]</strong></td></tr><tr><td><code>Original Tax Amount</code></td><td><code>original_tax_amount</code></td><td><code>original_tax_amount</code> <strong>[8]</strong></td></tr><tr><td><code>Returned Value</code></td><td><code>returned_value</code></td><td><code>returned_value</code> <strong>[8]</strong></td></tr><tr><td><code>Returned Quantity</code></td><td><code>returned_quantity</code></td><td><code>returned_quantity</code> <strong>[8]</strong></td></tr><tr><td><code>Cancelled Value</code></td><td><code>cancelled_value</code></td><td><code>cancelled_value</code> <strong>[8]</strong></td></tr><tr><td><code>Cancelled Quantity</code></td><td><code>cancelled_quantity</code></td><td><code>cancelled_quantity</code> <strong>[8]</strong></td></tr><tr><td><code>Margin</code></td><td><code>partners.eulerian.margin</code></td><td><code>margin</code> <strong>[8]</strong></td></tr><tr><td><code>Shop</code></td><td><code>partners.eulerian.shop</code></td><td><code>shop</code> <strong>[8]</strong></td></tr><tr><td><code>Search Term</code></td><td><code>search_term</code></td><td><code>eisd0</code> <strong>[14]</strong><br><code>actions.0.params.search_term</code> <strong>[15]</strong></td></tr><tr><td><code>-</code></td><td><code>event_name</code></td><td><code>actions.0.name</code> <strong>[15]</strong></td></tr><tr><td><code>Transaction Revenue</code></td><td><code>revenue</code></td><td><code>actions.0.params.revenue</code> <strong>[15]</strong></td></tr><tr><td><code>Shipping Tier</code></td><td><code>shipping_tier</code></td><td><code>actions.0.params.shipping_tier</code> <strong>[15]</strong></td></tr><tr><td><code>Method</code></td><td><code>method</code></td><td><code>actions.0.params.method</code> <strong>[15]</strong></td></tr><tr><td><code>Content Type</code></td><td><code>content_type</code></td><td><code>actions.0.params.content_type</code> <strong>[15]</strong></td></tr><tr><td><code>Content Item Id</code></td><td><code>item_id</code></td><td><code>actions.0.params.content_item_id</code> <strong>[15]</strong></td></tr><tr><td><code>Item List Name</code></td><td><code>item_list_name</code></td><td><code>actions.0.params.item_list_name</code> <strong>[15]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\*** Mandatory property.\
**1.** Automatically hashed via SHA256 when provided in clear text.\
**2.** Set if `context.device.os.name` is set with `android` (case insensitive).\
**3.** Set if `context.device.os.name` is set with `ios` (case insensitive).\
**4.** Set with `1` when `Traffic is always consented (enoepm)` is flagged.\
**5.** Set if `Traffic is always consented` is not flagged.\
**6.** Set with `1` when `TCF String` is provided.\
**7.** Set with `1` if `event_name` is `add_to_cart` or `remove_from_cart` .\
**8.** Set if `event_name` is `purchase` or `generate_lead` and required.\
**9.** Default value: `pending` .\
**10.** Set with `1` if `event_name` is `purchase` .\
**11.** Set with `1` if `event_name` is `generate_lead` .\
**12.** Set with `0` if `event_name` is `page_view` or `1` for Eulerian custom events.\
**13.** The value is set to its opposite when the event is `remove_from_cart` .\
**14.** Set if `event_name` is set with `search` .\
**15.** Set for Eulerian custom events.
{% endhint %}
