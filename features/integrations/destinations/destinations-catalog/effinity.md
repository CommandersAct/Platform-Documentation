# Effinity

[Effinity](https://www.effinity.fr/) is a digital acquisition agency. \
With Effinity server-side tracking you can track lead and sale conversions.

## Key features

* **Events structure**: our [Event reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model suits Effinity lead and sale tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Awin.

## Destination setup

### Configuration

| Settings               | Description                                                                                                                                                                                                                                                                                                                                                                             |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Advertiser Id`        | <p><em><strong><code>Required</code></strong></em></p><p>Your unique advertiser identifier as provided by Effinity.</p>                                                                                                                                                                                                                                                                 |
| `Conversion Type`      | <p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>sale</code> or <code>lead</code>. If conversion type is <code>lead</code>, only <code>generate_lead</code> events are forwarded to Awn. If conversion type is <code>sale</code>, only <code>purchase</code> events are sent to the partner.</p> |
| `Effinity Cookie Name` | Enter a cookie name holding Effinity key landing values. Expected cookie structure: "\[ID\_COMPTEUR],\[PROD\_ID],\[EFFI\_ID],\[EFFI\_ID2]" (E.g. "01010101,1234,567890,098765", without quotes).                                                                                                                                                                                        |

## Quick reference

| Commanders Act Events | Effinity Tracking |
| --------------------- | ----------------- |
| `generate_lead`       | `lead`            |
| `purchase`            | `sale`            |

## Field Mappings

{% hint style="info" %}
The Effinity property<mark style="color:blue;">`consent_performance`</mark>is always set to<mark style="color:blue;">`1`</mark>. Please manage your consent using the filter tab of this destination.
{% endhint %}

| Commanders Act Properties   | Effinity Properties                                                                                               |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `Advertiser Id`             | `id`                                                                                                              |
| `properties.currency`       | `monnaie`                                                                                                         |
| `properties.revenue`        | `montant`                                                                                                         |
| `properties.id`             | `ref`                                                                                                             |
| `Effinity Cookie Name`      | <p><code>id_compteur</code></p><p><code>prod_id</code></p><p><code>effi_id</code></p><p><code>effi_id2</code></p> |
| `properties.payment_method` | `payment`                                                                                                         |
| `properties.coupon`         | `voucher`                                                                                                         |
