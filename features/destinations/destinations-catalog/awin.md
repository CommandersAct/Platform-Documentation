# Awin

[Awin ](https://www.awin.com)provides a global affiliation network connecting businesses with customers.\
Using this destination you can implement [server-side tracking](https://developer.awin.com/docs/direct-s2s) using the same [client-side parameters](https://developer.awin.com/v1/docs/fall-back-conversion-pixel).

{% hint style="info" %}
Awin no longer support the use of pixel only implementations due to various browser constraints and limitations.
{% endhint %}

## Key features

The Awin destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers [Awin lead and sale tracking](https://developer.awin.com/docs/tracking), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Awin.
* **Commission group**: remunerate different products based on your [commission groups](https://wiki.awin.com/index.php/How_to_create_a_commission_group).

## Destination setup

{% hint style="warning" %}
The [**awc**](https://wiki.awin.com/index.php/Advertiser_Tracking_Guide/Conversion_Pixel_Only_Tracking#Server_To_Server_.28S2S.29) parameter is appended to the landing page URL by Awin to identify the source of the click. This value is mandatory and is retrieved by getting the value of either the <mark style="color:blue;">`Click Id`</mark> (See [Configuration](awin.md#configuration)) or the [**awc** ](https://wiki.awin.com/index.php/Advertiser_Tracking_Guide/Conversion_Pixel_Only_Tracking#Server_To_Server_.28S2S.29)cookie, in this priority order.
{% endhint %}

### Configuration

<table><thead><tr><th width="349">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your advertiser programme ID. Consult your Awin account contact or assigned integrator for more information on this value.</td></tr><tr><td><code>Conversion Type</code></td><td><em><strong><code>Required</code></strong></em><br>The conversion type that is bound with your activity. This can be either <code>Sale</code> or <code>Lead</code>. If conversion type is <code>Sale</code>, only <code>purchase</code> events are sent to the partner, if it's <code>Lead</code>, only <code>generate_lead</code> events are forwarded to Awin.</td></tr><tr><td><code>Click Id</code></td><td>Awin click identifier (awc). If it's not set the cookie "awc" is used. More details are available following this <a href="https://wiki.awin.com/index.php/Advertiser_Tracking_Guide/Conversion_Pixel_Only_Tracking#Server_To_Server_.28S2S.29">LINK</a>.</td></tr><tr><td><code>Default Commission Code</code></td><td>Default commission group code. If this is not set, the standard commission group code <code>DEFAULT</code>, for <code>Sale</code>, or <code>LEAD</code>, for <code>Lead</code>, is used.</td></tr><tr><td><p><code>Force parts with default commission code</code></p><p><code>and amount</code></p></td><td>Set Awin parameter <code>parts</code> with default commission code and total amount.</td></tr><tr><td><code>Test Mode</code></td><td>This field is available when flagging the <code>Advanced Settings</code> . It's either <code>0</code> (default value) for live production or <code>1</code> for UAT/test environment: when setting to the latter, the incoming tracking requests will not be processed by Awin.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>Awin property name</code> and adding the field name holding the value in <code>Your event property</code>. E.g. if you input <code>size</code> in the <code>Awin property name</code> and <code>items.0.product.size</code> in <code>Your event property</code>, you will have a custom event property in Awin called <code>size</code> with a value based on the content of the field <code>items.0.product.size</code>.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Awin Tracking |
| --------------------- | ------------- |
| `generate_lead`       | `Lead`        |
| `purchase`            | `Sale`        |

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
The following fields are recommended when having more than one commission group code:\
\- <mark style="color:blue;">`items.X.affiliation`</mark>\
\- <mark style="color:blue;">`items.X.product.price`</mark>\
\- <mark style="color:blue;">`items.X.quantity`</mark>

Alternatively, you can <mark style="color:blue;">`Force parts with default commission code and amount`</mark> . See [Configuration](awin.md#configuration) for more details. Accepted characters for the commission group codes are alphanumerics and letter in upper case, underscore (\_) , point (.) and minus (-).
{% endhint %}

<table data-full-width="true"><thead><tr><th width="679">Commanders Act Properties</th><th>Awin Properties</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><code>merchant</code> <strong>[*]</strong></td></tr><tr><td><code>Click Id</code></td><td><code>cks</code> <strong>[1][*]</strong></td></tr><tr><td><code>revenue</code></td><td><code>amount</code></td></tr><tr><td><code>channel</code></td><td><code>ch</code> <strong>[2]</strong></td></tr><tr><td><code>items.X.affiliation</code>:<code>items.X.product.price</code>*<code>items.X.quantity</code><br><code>Default Commission Code</code>:<code>revenue</code></td><td><code>parts</code> <strong>[3]</strong></td></tr><tr><td><code>coupon</code></td><td><code>vc</code></td></tr><tr><td><code>currency</code></td><td><code>cr</code></td></tr><tr><td><code>id</code></td><td><code>ref</code></td></tr><tr><td><code>Test Mode</code></td><td><code>testmode</code></td></tr><tr><td>AW:P|<code>Advertiser Id</code>|<code>id</code>|<code>items.X.product.id</code>|<code>items.X.product.name</code>|<code>items.X.product.price</code>|<code>items.X.quantity</code>|<code>items.X.product.price</code>|<code>items.X.id</code>|<code>items.X.affiliation</code>|<code>items.X.product.category_1</code></td><td><code>bd[X]</code> <strong>[4]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
&#xNAN;**\[1]** See [Destination setup](awin.md#destination-setup) for more details.\
&#xNAN;**\[2]** Default value <mark style="color:blue;">`aw`</mark> .\
&#xNAN;**\[3]** For <mark style="color:blue;">`Sale`</mark> conversion type, computed amounts are rounded with two decimals (E.g. "DOWNLOAD:551.18|FIX-NC:15302.67"). When the "Smart Mapping" field <mark style="color:blue;">`Item Affiliation`</mark> is not filled with a proper value, the commission group code is set with the value provided in <mark style="color:blue;">`Default Commission Code`</mark> . If <mark style="color:blue;">`Force parts with default commission code and amount`</mark> is flagged the value is set using the <mark style="color:blue;">`Default Commission Code`</mark> and <mark style="color:blue;">`revenue`</mark> : for leads, the latter is statically set to <mark style="color:blue;">`1`</mark> . See [Configuration](awin.md#configuration) for more details.\
&#xNAN;**\[4]** It takes into account each product.
{% endhint %}
