# Effinity

[Effinity](https://www.effinity.fr/) is a digital acquisition agency. \
Using Effinity server-side tracking you can track lead and sale conversions.

## Key features

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) suits Effinity lead and sale tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.

## Destination setup

### Configuration

| Settings               | Description                                                                                                                                                                                                                                                                                                                                                                             |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Advertiser Id`        | <p><em><strong><code>Required</code></strong></em></p><p>Your unique advertiser identifier as provided by Effinity.</p>                                                                                                                                                                                                                                                                 |
| `Conversion Type`      | <p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>sale</code> or <code>lead</code>. If conversion type is <code>lead</code>, only <code>generate_lead</code> events are forwarded to Awn. If conversion type is <code>sale</code>, only <code>purchase</code> events are sent to the partner.</p> |
| `Effinity Cookie Name` | Enter a cookie name holding Effinity key landing values. Expected cookie structure: "\[ID\_COMPTEUR],\[PROD\_ID],\[EFFI\_ID],\[EFFI\_ID2]" (E.g. "01010101,1234,567890,098765", without quotes). **\[1]**                                                                                                                                                                               |

{% hint style="info" %}
**\[1]** If you don't provide a cookie name for effinity landing values, it's mandatory that you provide them using<mark style="color:blue;">`partners.effinity`</mark>fields. See [Field Mappings](effinity.md#field-mappings) for more details.
{% endhint %}

## Quick reference

| Commanders Act Events | Effinity Tracking |
| --------------------- | ----------------- |
| `generate_lead`       | `lead`            |
| `purchase`            | `sale`            |

## Field mappings

{% hint style="info" %}
The Effinity property<mark style="color:blue;">`consent_performance`</mark>is always set to<mark style="color:blue;">`1`</mark>. Manage your consent settings using the filter tab of this destination.
{% endhint %}

| Commanders Act Properties                                                                  | Effinity Properties    |
| ------------------------------------------------------------------------------------------ | ---------------------- |
| `Advertiser Id`                                                                            | `id`                   |
| `properties.currency`                                                                      | `monnaie`              |
| `properties.revenue`                                                                       | `montant`              |
| `properties.id`                                                                            | `ref`                  |
| <p><code>partners.effinity.id_compteur</code></p><p><code>Effinity Cookie Name</code> </p> | `id_compteur` **\[1]** |
| <p><code>partners.effinity.prod_id</code></p><p><code>Effinity Cookie Name</code></p>      | `prod_id` **\[1]**     |
| <p><code>partners.effinity.effi_id</code></p><p><code>Effinity Cookie Name</code></p>      | `effi_id` **\[1]**     |
| <p><code>partners.effinity.effi_id2</code></p><p><code>Effinity Cookie Name</code></p>     | `effi_id2` **\[1]**    |
| `properties.payment_method`                                                                | `payment`              |
| `properties.coupon`                                                                        | `voucher`              |

{% hint style="info" %}
**\[1]** <mark style="color:blue;">`partners.effinity`</mark>fields have priority over<mark style="color:blue;">`Effinity Cookie Name`</mark>.
{% endhint %}
