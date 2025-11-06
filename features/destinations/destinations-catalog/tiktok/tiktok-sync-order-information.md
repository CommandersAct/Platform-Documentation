# TikTok Sync Order Information

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[TikTok for Business](https://www.tiktok.com/business/en) is a global platform designed to give brands and marketers the solutions to be creative storytellers and meaningfully engage with the TikTok community.\
Using this destination, you can leverage [Tiktok Sync Order Information endpoint](https://bytedance.sg.larkoffice.com/docx/CslIdiRnaoSnwuxMpJQljyUagAg) to update the status of your orders.

## Key features

The TikTok Sync Order Information destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [TikTok order status](https://bytedance.sg.larkoffice.com/docx/CslIdiRnaoSnwuxMpJQljyUagAg#doxlgbogCjcbcoAPBIVYZOOJVIf), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to TikTok.

## Destination setup

### Configuration

<table><thead><tr><th width="330">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Credentials</code></td><td><em><strong><code>Required</code></strong></em> <br>Your credentials with TikTok as set directly in your destination or, in the left menu, following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>TikTok</code> .</td></tr><tr><td><code>TikTok Organic Tracking Id</code></td><td><em><strong><code>Required</code></strong></em> <br>The TikTok Organic Tracking Id (ttoclid) is a tracking parameter that is appended to your page URL when a user clicks on your product page (E.g. https://www.url.com/product?ttoclid=<mark style="color:blue;"><code>opfed89ds90132344n2dkkl12321s321va</code></mark>).</td></tr><tr><td><code>Third Merchant Id</code></td><td><em><strong><code>Required</code></strong></em> <br>Must match the <code>third_merchant_id</code> you used to create the merchant within TikTok.</td></tr><tr><td><code>Third Shop Id</code></td><td><em><strong><code>Required</code></strong></em> <br>The identifier of the hotel as in your system.</td></tr><tr><td><code>Third Shop Name</code></td><td><em><strong><code>Required</code></strong></em> <br>The name of the hotel as in your system.</td></tr><tr><td><code>Payment Value</code></td><td><em><strong><code>Required</code></strong></em> <br>The total amount the customer is expected to pay on the panel site. This includes all fees and taxes, but excludes any discounts applied. Calculated as: <code>payment_value = total_value - discounts</code>. This value reflects the full price of the order, even if the customer completes payment at a later stage (E.g. during checkout).</td></tr><tr><td><code>Total Value</code></td><td><em><strong><code>Required</code></strong></em> <br>Total order value before discounts, including taxes and service fees. Calculated as: <code>total_value = total_room_fee + total_tax + total_service_fee</code>. This value is related to the price of the order.</td></tr><tr><td><code>Order Country</code></td><td><em><strong><code>Required</code></strong></em> <br>The country where the hotel is located.</td></tr><tr><td><code>Create Time</code></td><td><em><strong><code>Required</code></strong></em> <br>The time of order created in your system (timestamp in seconds).</td></tr><tr><td><code>Length Of Stay</code></td><td><em><strong><code>Required</code></strong></em> <br>Length of stay.</td></tr><tr><td><code>Amount Of Room</code></td><td><em><strong><code>Required</code></strong></em> <br>Amount of room stayed.</td></tr><tr><td><code>Check-In Date</code></td><td><em><strong><code>Required</code></strong></em> <br>Check-In date.</td></tr><tr><td><code>Check-Out Date</code></td><td><em><strong><code>Required</code></strong></em> <br>Check-Out date.</td></tr><tr><td><code>Event Mapping</code></td><td><em><strong><code>Required</code></strong></em> <br>Map <mark style="color:blue;"><code>TikTok order status</code></mark>  with <mark style="color:blue;"><code>Your event name</code></mark>  . More details are available following this <a href="https://bytedance.sg.larkoffice.com/docx/CslIdiRnaoSnwuxMpJQljyUagAg#doxlgbogCjcbcoAPBIVYZOOJVIf">LINK</a>. At least one entry is required.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | TikTok Order Status           |
| --------------------- | ----------------------------- |
| `[Any Event]`         | `[Any Order Status]` **\[1]** |

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](tiktok-sync-order-information.md#configuration) for more details.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
All TikTok properties are set in the path <mark style="color:blue;">`order_info`</mark> .
{% endhint %}

<table data-full-width="false"><thead><tr><th width="417.6685580062747">Commanders Act Properties</th><th>TikTok Properties</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>order_id</code> <strong>[*]</strong></td></tr><tr><td><code>Third Merchant Id</code></td><td><code>third_merchant_id</code> <strong>[*]</strong></td></tr><tr><td><code>Third Shop Id</code></td><td><code>third_shop_id</code> <strong>[*]</strong></td></tr><tr><td><code>Third Shop Name</code></td><td><code>third_shop_name</code> <strong>[*]</strong></td></tr><tr><td><code>event_name</code></td><td><code>order_status</code> <strong>[*][1]</strong></td></tr><tr><td><code>Order Country</code></td><td><code>order_country</code> <strong>[*]</strong></td></tr><tr><td><code>Create Time</code></td><td><code>create_time</code> <strong>[*]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>update_time</code> <strong>[*]</strong></td></tr><tr><td><code>partners.tiktok.initiator</code></td><td><code>initiator</code> <strong>[2]</strong></td></tr><tr><td><code>currency</code></td><td><code>value.currency</code> <strong>[*]</strong></td></tr><tr><td><code>Payment Value</code></td><td><code>value.payment_value</code> <strong>[*]</strong></td></tr><tr><td><code>Total Value</code></td><td><code>value.total_value</code> <strong>[*]</strong></td></tr><tr><td><code>Length Of Stay</code></td><td><code>extra.length_of_stay</code> <strong>[*]</strong></td></tr><tr><td><code>Amount Of Room</code></td><td><code>extra.amount_of_room</code> <strong>[*]</strong></td></tr><tr><td><code>Check-In Date</code></td><td><code>extra.check_in_date</code> <strong>[*]</strong></td></tr><tr><td><code>Check-Out Date</code></td><td><code>extra.check_out_date</code> <strong>[*]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>third_sku_id</code> <strong>[*][3]</strong></td></tr><tr><td><code>items.X.product.name</code></td><td><code>third_sku_name</code> <strong>[*][3]</strong></td></tr><tr><td><code>items.X.third_spu_id</code></td><td><code>spu_list.0.third_spu_id</code></td></tr><tr><td><code>items.X.third_spu_name</code></td><td><code>spu_list.0.third_spu_name</code></td></tr><tr><td><code>partners.tiktok.actual_occupancy</code></td><td><code>extra.actual_occupancy</code></td></tr><tr><td><code>partners.tiktok.no_show</code></td><td><code>extra.no_show</code></td></tr><tr><td><code>partners.tiktok.cancel_reason</code></td><td><code>extra.cancel_reason</code></td></tr><tr><td><code>partners.tiktok.fulfillment_value</code></td><td><code>value.fulfillment_value</code> <strong>[4]</strong></td></tr><tr><td><code>partners.tiktok.fulfillment_tax</code></td><td><code>value.fulfillment_tax</code> <strong>[4]</strong></td></tr><tr><td><code>partners.tiktok.fulfillment_service_fee</code></td><td><code>value.fulfillment_service_fee</code> <strong>[4]</strong></td></tr><tr><td><code>partners.tiktok.commission_currency</code></td><td><code>currency</code> <strong>[4][5]</strong></td></tr><tr><td><code>partners.tiktok.commission_base_amount</code></td><td><code>commission_base_amount</code> <strong>[4][5]</strong></td></tr><tr><td><code>partners.tiktok.total_room_fee</code></td><td><code>value.total_room_fee</code></td></tr><tr><td><code>tax_amount</code></td><td><code>value.total_tax</code></td></tr><tr><td><code>partners.tiktok.total_service_fee</code></td><td><code>value.total_service_fee</code></td></tr><tr><td><code>partners.tiktok.discounts</code></td><td><code>value.discounts</code></td></tr><tr><td><code>context.page.url</code></td><td><code>order_url</code></td></tr><tr><td><code>partners.tiktok.promotion_id</code></td><td><code>promotion_info.promotion_id</code></td></tr><tr><td><code>partners.tiktok.promotion_description</code></td><td><code>promotion_info.description</code></td></tr><tr><td><code>partners.tiktok.promotion_saved_amount</code></td><td><code>promotion_info.saved_amount</code></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
&#xNAN;**\[1]** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](tiktok-sync-order-information.md#configuration) for more details.\
&#xNAN;**\[2]** Mandatory property for order status <mark style="color:blue;">`CANCEL_ORDER`</mark> . This is either <mark style="color:blue;">`MERCHANT`</mark>  or <mark style="color:blue;">`CUSTOMER`</mark> .\
&#xNAN;**\[3]** Set in path <mark style="color:blue;">`spu_list.0.sku_list.0`</mark> .\
&#xNAN;**\[4]** Mandatory property for order status <mark style="color:blue;">`COMPLETE_ORDER`</mark> .\
&#xNAN;**\[5]** Set in path <mark style="color:blue;">`value.commission_value.0`</mark> .\

{% endhint %}
