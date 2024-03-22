# Awin

[Awin ](https://www.awin.com)provides a global affiliation network connecting businesses with customers.\
Using this destination you can implement [server-side tracking](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guide/Conversion\_Pixel\_Only\_Tracking#Server\_To\_Server\_.28S2S.29) using the same [client-side parameters](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guides#.5B.2B.5D\_Fall-back\_Conversion\_Pixel).

{% hint style="info" %}
Awin no longer support the use of pixel only implementations due to various browser constraints and limitations.
{% endhint %}

## Key features

The Awin destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers [Awin lead and sale tracking](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guide/Conversion\_Pixel\_Only\_Tracking#Server\_To\_Server\_.28S2S.29), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Awin.
* **Commission group**: remunerate different products based on your [commission groups](https://wiki.awin.com/index.php/How\_to\_create\_a\_commission\_group).

## Destination setup

{% hint style="info" %}
The [**awc**](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guide/Conversion\_Pixel\_Only\_Tracking#Server\_To\_Server\_.28S2S.29) parameter is appended to the landing page URL by Awin to identify the source of the click. This value is mandatory and is retrieved by getting the value of the [**awc** ](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guide/Conversion\_Pixel\_Only\_Tracking#Server\_To\_Server\_.28S2S.29)cookie.
{% endhint %}

### Configuration

<table><thead><tr><th width="349">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Your advertiser programme ID. Consult your Awin account contact or assigned integrator for more information on this value. This setting supports dynamic values <strong>[1].</strong></p></td></tr><tr><td><code>Conversion Type</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>Sale</code> or <code>Lead</code>. If conversion type is <code>Sale</code>, only <code>purchase</code> events are sent to the partner, if it's <code>Lead</code>, only <code>generate_lead</code> events are forwarded to Awin. </p></td></tr><tr><td><code>Click Id</code></td><td>Awin click identifier (awc). If it's not set the cookie "awc" is used. More details are available following this <a href="https://wiki.awin.com/index.php/Advertiser_Tracking_Guide/Conversion_Pixel_Only_Tracking#Server_To_Server_.28S2S.29">LINK</a> <strong>[1].</strong></td></tr><tr><td><code>Test Mode</code></td><td>This is either <code>0</code> (default value) for live production or <code>1</code> for UAT/test environment: when setting to the latter, the incoming tracking requests will not be processed by Awin.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>Awin property name</code> and adding the field name holding the value in <code>Your event property</code>. E.g. if you input <code>size</code> in the <code>Awin property name</code> and <code>items.0.product.size</code> <strong>[1]</strong> in <code>Your event property</code>, you will have a custom event property in Awin called <code>size</code> with a value based on the content of the field <code>items.0.product.size</code>.</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** This feature allows you to set an event property holding a dynamic value by adding two open braces (`{{`) in front of your property name and two close braces (`}}`) at the end (E.g. `{{myEventPropertyPathAndName}}`).
{% endhint %}

## Quick reference

| Commanders Act Events | Awin Tracking |
| --------------------- | ------------- |
| `generate_lead`       | `lead`        |
| `purchase`            | `sale`        |

## Field mappings

{% hint style="info" %}
The following fields are mandatory to properly set commission groups:\
\- <mark style="color:blue;">`items.X.affiliation`</mark>\
\- <mark style="color:blue;">`items.X.product.price`</mark>\
\- <mark style="color:blue;">`items.X.quantity`</mark>

Accepted characters for the commission group codes are alphanumerics and letter in upper case, underscore (\_) , point (.) and minus (-).
{% endhint %}

<table><thead><tr><th width="369">Commanders Act Properties</th><th>Awin Properties</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><code>merchant</code></td></tr><tr><td><code>revenue</code></td><td><code>amount</code></td></tr><tr><td><code>items.X.affiliation</code>:<code>items.X.product.price</code>*<code>items.X.quantity</code></td><td><code>parts</code> <strong>[1]</strong></td></tr><tr><td><code>coupon</code></td><td><code>vc</code></td></tr><tr><td><code>currency</code></td><td><code>cr</code></td></tr><tr><td><code>id</code></td><td><code>ref</code></td></tr><tr><td><code>Test Mode</code></td><td><code>testmode</code></td></tr><tr><td>AW:P|<code>Advertiser Id</code>|<code>id</code>|<code>items.X.product.id</code>|<code>items.X.product.name</code>|<code>items.X.product.price</code>|<code>items.X.quantity</code>|<code>items.X.product.price</code>|<code>items.X.id</code>|<code>items.X.affiliation</code>|<code>items.X.product.category_1</code>.</td><td><code>bd[X]</code> <strong>[2]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Computed amounts are rounded with two decimals (E.g. "DOWNLOAD:551.18|FIX-NC:15302.67"). When you select <mark style="color:blue;">`lead`</mark> as conversion type, the price part is set as integer if its decimal part is neutral (E.g. "5.00" will result in "5" being set).\
**\[2]** It takes into account each product.
{% endhint %}
