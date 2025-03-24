# Effinity

[Effinity](https://www.effinity.fr/) is a digital acquisition agency. \
Using Effinity server-side tracking you can track lead and sale conversions.

## Key features

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) suits Effinity lead and sale tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.

## Destination setup

{% hint style="info" %}
Ensure you can provide the "Id Compteur" using one of the following:&#x20;

* `Id Compteur` input field.
* `partners.effinity.id_compteur` property field.
* `Effinity Cookie Name`

See more details in the [Configuration](effinity.md#configuration) and [Field mappings](effinity.md#field-mappings) sections.
{% endhint %}

### Configuration

| Settings                  | Description                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Advertiser Id`           | <p><em><strong><code>Required</code></strong></em> <br>Your unique advertiser identifier as provided by Effinity.</p>                                                                                                                                                                                                                                                                             |
| `Id Compteur`             | <p><em><strong>Required if not provided through the <code>Effinity Cookie Name</code>  field.</strong></em><br>The only information necessary for attribution as it's used to identify the ad.</p>                                                                                                                                                                                                |
| `Prod Id`                 | Optional information to identify the product at the origin of the transaction. This can also be provided through the `Effinity Cookie Name`  field.                                                                                                                                                                                                                                               |
| `Effi Id`                 | Optional information used by partners. This can also be provided through the `Effinity Cookie Name`  field.                                                                                                                                                                                                                                                                                       |
| `Effi Id2`                | Optional information used by partners. This can also be provided through the `Effinity Cookie Name`  field.                                                                                                                                                                                                                                                                                       |
| `Conversion Type`         | <p><em><strong><code>Required</code></strong></em>  <br>The conversion type that is bound with your activity. This can be either  <code>sale</code>  or  <code>lead</code> . If conversion type is <code>lead</code> , only  <code>generate_lead</code>  events are forwarded to Awn. If conversion type is  <code>sale</code> , only  <code>purchase</code>  events are sent to the partner.</p> |
| `Effinity Cookie Name`    | Enter a cookie name holding Effinity key landing values. Expected cookie structure: "\[ID\_COMPTEUR],\[PROD\_ID],\[EFFI\_ID],\[EFFI\_ID2]" (E.g. "01010101,1234,567890,098765", without quotes). **\[1]**                                                                                                                                                                                         |
| `Custom Event Properties` | Map your custom event properties by setting their field names in `Effinity property name`  and adding the value  in `Your value`. `Effinity property name`  must be set with `refX` where `X` is a number from 2 to 20 (inclusive).                                                                                                                                                               |



{% hint style="info" %}
**\[1]** If you don't provide a cookie name holding the "Id Computer" value, it's mandatory that you set it using the related input field `Id Compteur`  or using the property <mark style="color:blue;">`partners.effinity.id_compteur`</mark> . The other landing values such as "Prod Id", "Eff Id" and "Effi id2" are optional, but recommended. See [Field Mappings](effinity.md#field-mappings) for more details.
{% endhint %}

## Quick reference

| Commanders Act Events | Effinity Tracking |
| --------------------- | ----------------- |
| `generate_lead`       | `lead`            |
| `purchase`            | `sale`            |

## Field mappings

{% hint style="info" %}
The Effinity property <mark style="color:blue;">`consent_performance`</mark> is always set to <mark style="color:blue;">`1`</mark> . Manage your consent settings using the filter tab of this destination.
{% endhint %}

<table><thead><tr><th width="526">Commanders Act Properties</th><th>Effinity Properties</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><code>id</code></td></tr><tr><td><code>currency</code></td><td><code>monnaie</code></td></tr><tr><td><code>revenue</code></td><td><code>montant</code></td></tr><tr><td><code>id</code></td><td><code>ref</code></td></tr><tr><td><p><code>Id Compteur</code></p><p><code>partners.effinity.id_compteur</code></p><p><code>Effinity Cookie Name</code> </p></td><td><code>id_compteur</code> <strong>[1]</strong></td></tr><tr><td><p><code>Prod Id</code></p><p><code>partners.effinity.prod_id</code></p><p><code>Effinity Cookie Name</code></p></td><td><code>prod_id</code> <strong>[1]</strong></td></tr><tr><td><p><code>Effi Id</code><br><code>partners.effinity.effi_id</code></p><p><code>Effinity Cookie Name</code></p></td><td><code>effi_id</code> <strong>[1]</strong></td></tr><tr><td><p><code>Effi Id2</code></p><p><code>partners.effinity.effi_id2</code></p><p><code>Effinity Cookie Name</code></p></td><td><code>effi_id2</code> <strong>[1]</strong></td></tr><tr><td><code>payment_method</code></td><td><code>payment</code></td></tr><tr><td><code>coupon</code></td><td><code>voucher</code></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Priority order listed on the left.
{% endhint %}
