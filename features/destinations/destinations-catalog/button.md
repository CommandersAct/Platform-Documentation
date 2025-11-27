# Button

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Button](https://www.usebutton.com/) provides deep linking and optimizing affiliate, creator & social traffic.\
Using this destination you can leverage Button [Orders API to report a purchase](https://developer.usebutton.com/reference/report-an-order).

## Key features

The Button destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers [Button Orders API](https://developer.usebutton.com/reference/report-an-order), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Button.

## Destination setup

### Configuration

<table><thead><tr><th width="349">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>API Key</code></td><td><em><strong><code>Required</code></strong></em><br>Your Button generated API key. For more details, you can check the following <a href="https://developer.usebutton.com/reference/authentication">LINK</a>.</td></tr><tr><td><code>Source Token</code></td><td>Button source/attribution token. This field is optional to create an order, but is required for attribution. When testing your integration, you should send dummy source tokens to Button, in the following format: <code>^fakesrctok-[a-f0-9]{16}$</code> (E.g. <code>fakesrctok-abcdef0123456789</code>). URL safe string up to 255 characters.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>Button property name</code> and adding the field name holding the value in <code>Your event property</code>. In the column <code>Your event property position</code> you should keep the default value <code>Default (root)</code> as it better fits most scenarios. In case you select either <code>In "items" {items.X}</code> or <code>In "product" {items.X.product}</code> this destination will look for the input event property starting from the <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#item">items </a>or <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#product">product </a>level respectively and set the value in <code>line_items.X.attributes</code> .</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Button Tracking |
| --------------------- | --------------- |
| `[Any event]`         | `Order record`  |

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table data-full-width="true"><thead><tr><th width="673.3333740234375">Commanders Act Properties</th><th>Butto Properties</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>order_id</code> <strong>[*]</strong></td></tr><tr><td><code>revenue</code></td><td><code>total</code> <strong>[*]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code> <strong>[*]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>line_items.X.identifier</code> <strong>[*]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>line_items.X.sku</code> <strong>[*]</strong></td></tr><tr><td><code>items.X.product.price</code> <strong>[*]</strong>, <code>items.X.quantity</code> <strong>[*]</strong> and <code>items.X.discount</code></td><td><code>line_items.X.total</code> <strong>[*][1]</strong></td></tr><tr><td><p><code>items.X.product.category_1</code> <strong>[*]</strong></p><p><code>items.X.product.category_2</code></p><p><code>items.X.product.category_3</code></p><p><code>items.X.product.category_4</code></p><p><code>items.X.product.category_5</code></p></td><td><code>line_items.X.category</code> <strong>[*][2]</strong></td></tr><tr><td><code>items.X.product.name</code></td><td><code>line_items.X.description</code> <strong>[*]</strong></td></tr><tr><td><code>source_token</code></td><td><code>btn_ref</code></td></tr><tr><td><p><code>partners.button.purchase_date</code></p><p><code>context.event_timestamp</code></p></td><td><code>purchase_date</code> <strong>[3]</strong></td></tr><tr><td><code>partners.button.total_as_decimal</code></td><td><code>total_as_decimal</code> <strong>[4]</strong></td></tr><tr><td><code>user.id</code></td><td><code>customer.id</code></td></tr><tr><td><code>user.email</code></td><td><code>customer.email_sha256</code> <strong>[5]</strong></td></tr><tr><td><code>context.device.advertising_id</code></td><td><code>customer.device_id</code></td></tr><tr><td><code>user.new_user</code></td><td><code>customer.is_new_user</code></td></tr><tr><td><code>id_variant</code></td><td><code>customer_order_id</code></td></tr><tr><td><code>partners.button.order_channel</code></td><td><code>partner_order_channel</code> <strong>[6]</strong></td></tr><tr><td><code>partners.button.finalization_date</code></td><td><code>finalization_date</code></td></tr><tr><td><code>items.X.quantity</code></td><td><code>line_items.X.quantity</code></td></tr><tr><td><code>items.X.id</code></td><td><code>line_items.X.upc</code></td></tr><tr><td><code>items.X.coupon</code></td><td><code>line_items.X.attributes.coupon_code</code></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
&#xNAN;**\[1]** Based on the values on the left and depending on the property `partners.button.total_as_decimal` .\
&#xNAN;**\[2]** Set as an array with all the provided categories.\
&#xNAN;**\[3]** if `partners.button.purchase_date` is not provided, `context.event_timestamp` is used.\
&#xNAN;**\[4]** Pass `true` (Boolean) if you want to set decimal values for both Button property `total` and `line_items.X.total` , `false` (Boolean) or don't set otherwise.\
&#xNAN;**\[5]** If it's passed in clear text, it's automatically hashed via SHA256.\
&#xNAN;**\[6]** Accepted values: `app` and `webview`. If it's not provided, automatically set to `app` when property `context.app.name` is non-empty. Default value: `webview`.
{% endhint %}
