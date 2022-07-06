# Awin

Awin provides a global affiliation network connecting businesses with customers.\
Using this destination you can implement the [server-side tracking](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guide/Conversion\_Pixel\_Only\_Tracking#Server\_To\_Server\_.28S2S.29) using the same [client-side parameters](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guides#.5B.2B.5D\_Fall-back\_Conversion\_Pixel).

{% hint style="info" %}
Awin no longer support the use of pixel only implementations due to various browser constraints and limitations.
{% endhint %}

## Key features

The Awin destination provides the following key features:

* **Events structure**: our [Event reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model covers [Awin lead and sale tracking](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guide/Conversion\_Pixel\_Only\_Tracking#Server\_To\_Server\_.28S2S.29), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Awin.
* **Commission group**: remunerate different products based on your [commission groups](https://wiki.awin.com/index.php/How\_to\_create\_a\_commission\_group).

## Destination setup

{% hint style="info" %}
The [\*\*`awc` \*\* ](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guide/Conversion\_Pixel\_Only\_Tracking#Server\_To\_Server\_.28S2S.29)is appended to the landing page URL by Awin to identify the source of the click. This value is mandatory and is retrieved by getting the value of the [**awc** ](https://wiki.awin.com/index.php/Advertiser\_Tracking\_Guide/Conversion\_Pixel\_Only\_Tracking#Server\_To\_Server\_.28S2S.29)cookie.
{% endhint %}

### Configuration

| Settings        | Description                                                                                                                                                                                                                                                                                                                                                                             |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Advertiser Id   | <p><em><strong><code>Required</code></strong></em></p><p>Your advertiser programme ID. Consult your Awin account contact or assigned integrator for more information on this value.</p>                                                                                                                                                                                                 |
| Conversion Type | <p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>sale</code> or <code>lead</code>. If conversion type is <code>lead</code>, only <code>generate_lead</code> events are forwarded to Awn. If conversion type is <code>sale</code>, only <code>purchase</code> events are sent to the partner.</p> |
| Test Mode       | This is either `0` or `1` depending on whether the environment is the live production or test respectively. Default value is `0`.                                                                                                                                                                                                                                                       |

## Quick reference

| Commanders Act Events | Awin Tracking |
| --------------------- | ------------- |
| `generate_lead`       | `lead`        |
| `purchase`            | `sale`        |

## Field Mappings

{% hint style="info" %}
If you select`sale`as conversion type, the following fields are mandatory to properly set commission groups:\
\-`properties.items.X.affiliation`\
``-`properties.items.X.product.price`\
``-`properties.items.X.quantity`

Accepted characters for the commission group codes are alphanumerics (letter in upper case), underscore '\_' , point '.' and minus '-'`.`
{% endhint %}

| Commanders Act Properties                                                                                                                                                                                                                                                                                              | Awin Properties   |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------- |
| `Advertiser Id`                                                                                                                                                                                                                                                                                                        | `merchant`        |
| `properties.revenue`                                                                                                                                                                                                                                                                                                   | `amount` **\[1]** |
| `properties.items.X.affiliation`:`properties.items.X.product.price`\*`properties.items.X.quantity`                                                                                                                                                                                                                     | `parts` **\[2]**  |
| `properties.coupon`                                                                                                                                                                                                                                                                                                    | `vc`              |
| `properties.currency`                                                                                                                                                                                                                                                                                                  | `cr`              |
| `properties.id`                                                                                                                                                                                                                                                                                                        | `ref`             |
| `Test Mode`                                                                                                                                                                                                                                                                                                            | `testmode`        |
| AW:P\|`Advertiser Id`\|`properties.id`\|`properties.items.X.product.id`\|`properties.items.X.product.name`\|`properties.items.X.product.price`\|`properties.items.X.quantity`\|`properties.items.X.product.price`\|`properties.items.X.id`\|`properties.items.X.affiliation`\|`properties.items.X.product.category_1`. | `bd[X]` **\[3]**  |

{% hint style="info" %}
**\[1]** When you select`lead`as conversion type, it's set with `1`.\
**\[2]** Computed amounts are rounded with two decimals (E.g. "DOWNLOAD:551.18|FIX-NC:15302.67"). When you select`lead`as conversion type, it's set with `DEFAULT:1`.\
**\[3]** Only when`sale`is set as conversion type. This structure is applied for each product.
{% endhint %}
