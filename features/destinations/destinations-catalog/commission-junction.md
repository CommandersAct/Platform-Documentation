# Commission Junction

[Commission Junction](https://www.cj.com/)[ ](https://www.awin.com)(CJ) provides a global affiliation network connecting businesses with customers. Using this destination you can implement server-side tracking.

## Key features

The Commission Junction destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers Commission Junction server-side tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Refined data**: you can freely push additional information based on your specific needs.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Awin.

## Destination setup

### Configuration

<table><thead><tr><th width="369">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>CJ Enterprise Id</code></td><td><em><strong><code>Required</code></strong></em> <br>Your "Enterprise ID" as provided by Commission Junction. This setting supports dynamic values <strong>[1][2].</strong></td></tr><tr><td><code>Mapping</code></td><td><em><strong><code>Required</code></strong></em> <br>Map your Commanders Act event(s) with CJ ActionId(s) by setting a <code>Your Event Name</code> and a <code>CJ Action Id</code>. At least one entry is required.</td></tr><tr><td><code>CJ Event Cookie Name</code></td><td>Enter a cookie name holding CJ Event value. This value is passed by Commission Junction in landings (E.g. https://www.example.com/?cjevent=656e8fa049ec11ea8237023d0a240612). This is required if the "Smart Mapping" field <code>Click Id (cjevent)</code> is empty. The field <code>Click Id (cjevent)</code> has priority over this field.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>CJ property name</code> and adding the field name holding the value in <code>Your event property</code>. E.g. if you input<code>size</code>in the <code>CJ property name</code> and <code>items.0.product.size</code> in <code>Your event property</code>, you'll have a custom event property in CJ called<code>size</code>with a value based on the content of the field <code>items.0.product.size</code> <strong>[2]</strong>.</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** This feature allows you to set an event property holding a dynamic value by adding two open braces (`{{`) in front of your property name and two close braces (`}}`) at the end (E.g. `{{myEventPropertyPathAndName}}`).\
**\[2]** Using "dots" (".") you can navigate deeper to the specific property you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
Setting the [configuration](commission-junction.md#configuration) field <mark style="color:blue;">`CJ Event Cookie Name`</mark> is not mandatory if the "Smart Mapping" field <mark style="color:blue;">`Click Id (cjevent)`</mark> is set. The latter has precedence over the former.
{% endhint %}

<table><thead><tr><th width="444">Commanders Act Properties</th><th>CJ Properties</th></tr></thead><tbody><tr><td><code>CJ Enterprise Id</code></td><td><code>CID</code></td></tr><tr><td><code>CJ Action Id</code></td><td><code>TYPE</code></td></tr><tr><td><p><code>Click Id (cjevent)</code> <strong>[1]</strong></p><p><code>CJ Event Cookie Name</code></p></td><td><code>CJEVENT</code> <strong>[2]</strong></td></tr><tr><td><code>event_timestamp</code></td><td><code>eventTime</code> <strong>[3]</strong></td></tr><tr><td><code>id</code></td><td><code>OID</code></td></tr><tr><td><code>currency</code></td><td><code>currency</code></td></tr><tr><td><code>revenue</code></td><td><code>amount</code> <strong>[4]</strong></td></tr><tr><td><code>coupon</code></td><td><code>coupon</code></td></tr><tr><td><code>items.X.product.id</code></td><td><code>ITEMY</code> <strong>[5]</strong></td></tr><tr><td><code>items.X.product.price</code></td><td><code>AMTY</code> <strong>[5]</strong></td></tr><tr><td><code>items.X.quantity</code></td><td><code>QTYY</code> <strong>[5]</strong></td></tr><tr><td><code>items.X.discount</code></td><td><code>DCNTY</code> <strong>[5]</strong></td></tr><tr><td><code>Commanders Act event property or static value</code></td><td><code>Event property name</code> <strong>[6]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** "Smart Mapping" field.\
**\[2]** <mark style="color:blue;">`Click Id (cjevent)`</mark> has priority over <mark style="color:blue;">`CJ Event Cookie Name`</mark> .\
**\[3]** Automatically converted in the [ISO 8601 format](https://en.wikipedia.org/wiki/ISO\_8601).\
**\[4]** If [items ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)are present, this property won't be included.\
**\[5]** For each [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item): <mark style="color:blue;">`X`</mark> and <mark style="color:blue;">`Y`</mark> are incremental numbers, starting from<mark style="color:blue;">`0`</mark>and<mark style="color:blue;">`1`</mark>respectively.\
**\[6]** See <mark style="color:blue;">`Custom Event Properties`</mark> in [Configuration](commission-junction.md#configuration) for more details. The <mark style="color:blue;">`signature`</mark> CJ optional property can be set using this feature.&#x20;
{% endhint %}
