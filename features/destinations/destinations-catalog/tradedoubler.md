# Tradedoubler

[Tradedoubler ](https://www.tradedoubler.com)provides a global affiliation network connecting businesses with customers.\
Using this destination you can implement [server-side tracking](https://dev.tradedoubler.com/tracking/advertiser/) using the same [client-side parameters](https://dev.tradedoubler.com/tracking/advertiser/#Pixel).

## Key features

The Tradedoubler destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) leverages [Tradedoubler lead and sale tracking](https://dev.tradedoubler.com/tracking/advertiser/#Pixel), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Tradedoubler.

## Destination setup

{% hint style="info" %}
The [**tduid** ](https://dev.tradedoubler.com/tracking/advertiser/#Pixel)parameter is appended to the landing page URL by Tradedoubler to identify the source of the click. This is retrieved by getting the value of the [**tduid**](https://dev.tradedoubler.com/tracking/advertiser/#Pixel)[ ](https://wiki.awin.com/index.php/Advertiser_Tracking_Guide/Conversion_Pixel_Only_Tracking#Server_To_Server_.28S2S.29)cookie.
{% endhint %}

### Configuration

| Settings              | Description                                                                                                                                                                                                                                                                                                                                                                        |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Organization Id`     | <p><em><strong><code>Required</code></strong></em></p><p>Your organization identifier as provided by Tradedoubler.</p>                                                                                                                                                                                                                                                             |
| `Event Id`            | <p><em><strong><code>Required</code></strong></em></p><p>The event identifier for the lead/sale taking place and as provided by Tradedoubler.</p>                                                                                                                                                                                                                                  |
| `Program Id`          | <p><em><strong><code>Recommended</code></strong></em></p><p>Your program identifier as provided by Tradedoubler.</p>                                                                                                                                                                                                                                                               |
| `Conversion Type`     | <p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>Sale</code> or <code>Lead</code>. If conversion type is <code>Sale</code>, only <code>purchase</code> events are sent to the partner, if it's <code>Lead</code>, only <code>generate_lead</code> events are forwarded to Tradedoubler.</p> |
| `Cookie Name (tduid)` | Tradedoubler unique tracking identifier that is set in a cookie by the [redirect page](https://dev.tradedoubler.com/tracking/advertiser/#Pixel_Redirect). See [Field Mappings](tradedoubler.md#field-mappings) for more details.                                                                                                                                                   |

## Quick reference

| Commanders Act Events | Tradedoubler Tracking |
| --------------------- | --------------------- |
| `generate_lead`       | `lead`                |
| `purchase`            | `sale`                |

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table><thead><tr><th width="351.29729729729735">Commanders Act Properties</th><th>Tradedoubler Properties</th></tr></thead><tbody><tr><td><code>Organization Id</code></td><td><code>organization</code> <strong>[*]</strong></td></tr><tr><td><code>Event Id</code></td><td><code>event</code> <strong>[*]</strong></td></tr><tr><td><code>Program Id</code></td><td><code>program</code></td></tr><tr><td><code>id</code></td><td><code>orderNumber</code> <strong>[1]</strong></td></tr><tr><td><code>value</code></td><td><code>orderValue</code> <strong>[1]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code> <strong>[1]</strong></td></tr><tr><td><code>coupon</code></td><td><code>voucher</code> <strong>[1]</strong></td></tr><tr><td><code>items.X.product.id</code><br><code>items.X.product.name</code><br><code>items.X.product.price</code><br><code>items.X.quantity</code></td><td><code>reportInfo</code> <strong>[1][6]</strong></td></tr><tr><td><code>id</code></td><td><code>leadNumber</code> <strong>[2]</strong></td></tr><tr><td><p><code>partners.tradedoubler.tduid</code> or</p><p><code>Cookie Name (tduid)</code></p></td><td><code>tduid</code> <strong>[3]</strong></td></tr><tr><td><code>user.id</code></td><td><code>extid</code> <strong>[4]</strong></td></tr><tr><td><code>(user.id)</code></td><td><code>exttype</code> <strong>[5]</strong></td></tr></tbody></table>

>

{% hint style="info" %}
> **\[\*]** Mandatory property.  \
> &#xNAN;**\[1]** Set when `Conversion Type` is `Sale` .  \
> &#xNAN;**\[2]** Set when `Conversion Type` is `Lead` .  \
> &#xNAN;**\[3]** Value is set based on the priority in the left column.  \
> &#xNAN;**\[4]** Value hashed using`SHA-256` .  \
> &#xNAN;**\[5]** Either <mark style="color:blue;">`1`</mark> or <mark style="color:blue;">`0`</mark> , depending if `user.id` is a valid email or an non-email identifier respectively.  \
> &#xNAN;**\[6]** All products are taken into account.
{% endhint %}
