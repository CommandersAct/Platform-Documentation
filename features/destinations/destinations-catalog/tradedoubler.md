# Tradedoubler

[Tradedoubler ](https://www.tradedoubler.com)provides a global affiliation network connecting businesses with customers.\
Using this destination you can implement [server-side tracking](https://dev.tradedoubler.com/tracking/advertiser/) using the same [client-side parameters](https://dev.tradedoubler.com/tracking/advertiser/#Pixel).

## Key features

The Tradedoubler destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) leverages [Tradedoubler lead and sale tracking](https://dev.tradedoubler.com/tracking/advertiser/#Pixel), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Tradedoubler.
* **User identifier**: you can openly select a user identifier field for logged users.

## Destination setup

{% hint style="info" %}
The [**tduid** ](https://dev.tradedoubler.com/tracking/advertiser/#Pixel)parameter is appended to the landing page URL by Tradedoubler to identify the source of the click. This is retrieved by getting the value of the [**tduid**](https://dev.tradedoubler.com/tracking/advertiser/#Pixel)[ ](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guide/Conversion\_Pixel\_Only\_Tracking#Server\_To\_Server\_.28S2S.29)cookie.
{% endhint %}

### Configuration

| Settings              | Description                                                                                                                                                                                                                                                                                                                                                                         |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Organization Id`     | <p><em><strong><code>Required</code></strong></em></p><p>Your organization identifier as provided by Tradedoubler.</p>                                                                                                                                                                                                                                                              |
| `Conversion Type`     | <p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>Sale</code> or <code>Lead</code>. If conversion type is <code>Sale</code>, only <code>purchase</code> events are sent to the partner, if it's <code>Lead</code>, only <code>generate_lead</code> events are forwarded to Tradedoubler. </p> |
| `Event Id`            | <p><em><strong><code>Required</code></strong></em></p><p>The event identifier for the lead/sale taking place and as provided by Tradedoubler.</p>                                                                                                                                                                                                                                   |
| `Cookie Name (tduid)` | Tradedoubler unique tracking identifier that is set in a cookie by the [redirect page](https://dev.tradedoubler.com/tracking/advertiser/#Pixel\_Redirect).                                                                                                                                                                                                                          |
| `User Id Type`        | You can bridge your selected user identifier for logged users.                                                                                                                                                                                                                                                                                                                      |

## Quick reference

| Commanders Act Events | Tradedoubler Tracking |
| --------------------- | --------------------- |
| `generate_lead`       | `lead`                |
| `purchase`            | `sale`                |

## Field Mappings

<table><thead><tr><th width="392">Commanders Act Properties</th><th>Tradedoubler Properties</th></tr></thead><tbody><tr><td><code>Organization Id</code></td><td><code>organization</code></td></tr><tr><td><code>Event Id</code></td><td><code>event</code></td></tr><tr><td><code>properties.id</code></td><td><code>orderNumber</code></td></tr><tr><td><code>properties.value</code></td><td><code>orderValue</code></td></tr><tr><td><code>properties.currency</code></td><td><code>currency</code></td></tr><tr><td><code>properties.coupon</code></td><td><code>voucher</code></td></tr><tr><td><code>properties.user.email</code> or <code>properties.user.id</code></td><td><code>extid</code> <strong>[1]</strong></td></tr><tr><td><code>(User Id Type)</code></td><td><code>exttype</code> <strong>[2]</strong></td></tr><tr><td>f1=<code>properties.items.X.product.id</code>&#x26;f2=<code>properties.items.X.product.name</code>&#x26;<br>f3=<code>properties.items.X.product.price</code>&#x26;<br>f4=<code>properties.items.X.quantity</code> |</td><td><code>reportInfo</code> <strong>[3]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Hashed using`SHA-256`and default value:<mark style="color:blue;">`properties.user.email`</mark>\
**\[2]** Either<mark style="color:blue;">`1`</mark>or<mark style="color:blue;">`0`</mark>, depending if your selected<mark style="color:blue;">`User Id Type`</mark>is<mark style="color:blue;">`User Email`</mark>or<mark style="color:blue;">`User Id`</mark> respectively.\
**\[3]** It takes into account each product.
{% endhint %}
