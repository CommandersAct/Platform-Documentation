# Partnerize

[Partnerize](https://partnerize.com/)[ ](https://www.awin.com)provides a global affiliation network connecting businesses with customers.\
Using this destination you can implement [server-side tracking](https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration).

## Key features

The Partnerize destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) leverages [Partnerize lead and sale tracking](https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Partnerize.
* **Commission group**: remunerate different products based on your categories.

## Destination setup

### Configuration

<table><thead><tr><th width="357">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Campaign Id</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>A unique identifier assigned to the campaign and provided by Partnerize. This setting supports dynamic values <strong>[1].</strong></p></td></tr><tr><td><code>Select your click ref holder</code></td><td>This can be either <code>Cookie</code> or <code>Event property</code>, depending on how you provide CJ "Click Reference" value.</td></tr><tr><td><code>Cookie Name for Click Tracking</code></td><td>If you select <code>Cookie</code> in <code>Select your click ref holder</code>, you can set your cookie name here.</td></tr><tr><td><code>Event property containing click ref</code></td><td>If you select <code>Event property</code> in <code>Select your click ref holder</code>, you can set your event property here. <strong>[2]</strong></td></tr><tr><td><code>Custom Conversion URL String</code></td><td>The Partnerize "Conversion URL" may differ based on your specific requirements. Using this setting, you can add a custom string before the <a href="https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration#h_01FANB7W0RHFZJFAYNXJJ8AWD6">campaign</a> parameter (E.g. https://prf.hn/conversion/tracking_mode:api/[CUSTOM_STRING]campaign:...).</td></tr><tr><td><code>Optional: Partnerize Device (device)</code></td><td>You can set a property holding the following allowed values: "bot", "desktop", "mobile", "tablet" and "Other". More details are available following this <a href="https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration#h_01FANBMH24SWP0F1A9M1D0E14T">LINK</a>. <strong>[2]</strong></td></tr><tr><td><code>Optional: Partnerize Context (context)</code></td><td>You can set a property holding the following allowed values: "web", "m_web", "m_app", "in_app", "cd_d", "cd_p", "other" and "offline". More details are available following this <a href="https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration#h_01FANBMH24SWP0F1A9M1D0E14T">LINK</a>. <strong>[2]</strong></td></tr><tr><td><code>Custom Event Properties</code></td><td><p>Map your custom event properties by setting their field names in <code>Partnerize property name</code> and adding the field name holding the value in <code>Your event property</code>. E.g. if you input<code>size</code>in the <code>Partnerize property name</code> and <code>properties.items.0.product.size</code> in <code>Your event property</code>, you'll have a custom event property in Partnerize called<code>size</code>with a value based on the content of the field <code>properties.items.0.product.size</code> <strong>[2]</strong>.</p><p><br>In the column <code>Your event property path</code> you should keep the default value <code>Default (root)</code> as this will add a custom parameter at the <a href="https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration#h_01FANB7W0RHFZJFAYNXJJ8AWD6">Base Level</a> (E.g. see <a href="https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration#h_01FANB7W0RHFZJFAYNXJJ8AWD6">campaign</a>) which better fits most scenarios. In case you select either <code>In "items" {items.X}</code> or <code>In "product" {items.X.product}</code> this destination will look for the input event property starting from the <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#item">items </a>or <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#product">product </a>level respectively and add it as a custom <a href="https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration#h_01FADKCBAZCZTRFZG43N1DP8TW">Basket Data</a> parameter.<br>The advanced operation <code>As Partnerize Basket Data</code> can be paired with the property path option <code>Default (root)</code> so your property value is set as a custom entry in the Partnerize "Basket Data" for each item.</p></td></tr></tbody></table>



{% hint style="info" %}
**\[1]** This feature allows you to set an event property holding a dynamic value by adding two open braces (`{{`) in front of your property name and two close braces (`}}`) at the end (E.g. `{{myEventPropertyPathAndName}}`).\
**\[2]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

| Commanders Act Events | Partnerize Tracking |
| --------------------- | ------------------- |
| `generate_lead`       | `lead`              |
| `purchase`            | `sale`              |

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
Both parameters<mark style="color:blue;">`clickref`</mark>and<mark style="color:blue;">`conversionref`</mark>are mandatory.\
The two [Basket Data](https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration#h\_01FADKCBAZCZTRFZG43N1DP8TW) parameters<mark style="color:blue;">`category`</mark>and<mark style="color:blue;">`quantity`</mark>are required, while<mark style="color:blue;">`value`</mark>is needed if you intend to award commission based on percentage basis.&#x20;
{% endhint %}

<table><thead><tr><th width="432">Commanders Act Properties</th><th>Partnerize Properties</th></tr></thead><tbody><tr><td><code>Campaign Id</code></td><td><code>campaign</code> <strong>[*]</strong></td></tr><tr><td><p><code>Cookie Name for Click Tracking</code> or</p><p><code>Event property containing click ref</code></p></td><td><code>clickref</code> <strong>[*][1]</strong></td></tr><tr><td><code>id</code></td><td><code>conversionref</code> <strong>[*]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code> <strong>[*]</strong></td></tr><tr><td><code>items.X.affiliation</code></td><td><code>category</code> <strong>[*]</strong></td></tr><tr><td><code>items.X.quantity</code></td><td><code>quantity</code> <strong>[*]</strong></td></tr><tr><td><code>partners.partnerize.device</code></td><td><code>device</code> <strong>[2]</strong></td></tr><tr><td><code>partners.partnerize.context</code></td><td><code>context</code> <strong>[2]</strong></td></tr><tr><td><code>user.type</code></td><td><code>customertype</code></td></tr><tr><td><code>coupon</code></td><td><code>voucher</code></td></tr><tr><td><code>country</code></td><td><code>country</code> <strong>[3]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>sku</code></td></tr><tr><td><code>items.X.product.price</code></td><td><code>value</code></td></tr><tr><td><code>Your event property</code></td><td><code>conversion_time</code> <strong>[4]</strong></td></tr><tr><td><code>Your event property</code></td><td><code>Partnerize property name</code> <strong>[5]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** See [Configuration](partnerize.md#configuration) for more details. if no value is provided, the default cookie named [<mark style="color:blue;">**clickref**</mark>](https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration#h\_01FADK3BAYNPZ8FC9YF08WVAWB) is used.\
**\[2]** See [valid values](https://help.phgsupport.com/hc/en-us/articles/360020395238-Tracking-Partnerize-Server-to-Server-S2S-Integration#h\_01FANBMH24SWP0F1A9M1D0E14T).\
**\[3]** Standard ISO 3166.\
**\[4]** This needs to be set in the<mark style="color:blue;">`Custom Event Properties`</mark>by adding the field <mark style="color:blue;">`conversion_time`</mark>as<mark style="color:blue;">`Partnerize property name`</mark>and setting a field holding a Unix epoch timestamp (10 or 13 digits) in<mark style="color:blue;">`Your event property`</mark>.\
**\[5]** See<mark style="color:blue;">`Custom Event Properties`</mark>in [Configuration ](partnerize.md#configuration)for more details on how you can bridge custom properties to Partnerize.
{% endhint %}

