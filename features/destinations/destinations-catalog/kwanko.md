# Kwanko

[Kwanko ](https://www.kwanko.com/)provides a global affiliation network connecting businesses with customers.\
Using this destination you can implement server-side lead and sale tracking.

## Key features

The Awin destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers Kwanko lead and sale tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Custom properties**: you can freely push custom properties based on your specific needs.

## Destination setup

### Configuration

| Settings                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Tracking Id`             | <p><em><strong><code>Required</code></strong></em></p><p>Your tracking identifier as provided by Kwanko. It's used to identify your campaigns.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `Conversion Type`         | <p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>sale</code> or <code>lead</code>. If conversion type is <code>lead</code>, only <code>generate_lead</code> events are forwarded to Kwanko. If conversion type is <code>sale</code>, only <code>purchase</code> events are sent to the partner.</p>                                                                                                                                                                                                                  |
| `Cookie Click Id`         | <p><em><strong><code>Required</code></strong></em></p><p>For each click on Kwanko links a new "Click Id" is automatically generated. This can be found as value for the parameter <code>kwks2s</code> in landings. Input the cookie name holding this value.</p>                                                                                                                                                                                                                                                                                                                                            |
| `Custom Event Properties` | Map your custom event properties by setting their field names in `Event property name` and adding the field name holding the value in `Commanders Act event property or static value`. E.g. if you input`size`in the `Event property name` and `properties.items.0.product.size` in `Commanders Act event property or static value`, you'll have a custom event property in Kwanko called`size`with a value based on the content of the field `properties.items.0.product.size` **\[1]**. You also have the option to set a static string/numeric value in `Commanders Act event property or static value`. |

{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

| Commanders Act Events | Kwanko Tracking |
| --------------------- | --------------- |
| `generate_lead`       | `lead`          |
| `purchase`            | `sale`          |

## Field Mappings

{% hint style="info" %}
The Kwanko property<mark style="color:blue;">`gdpr_kwk`</mark>is always set to<mark style="color:blue;">`1`</mark>. Manage your consent settings using the filter tab of this destination.
{% endhint %}

| Commanders Act Properties | Kwanko Properties |
| ------------------------- | ----------------- |
| `Tracking Id`             | `mclic`           |
| `properties.revenue`      | `argmon`          |
| `properties.id`           | `argann`          |
| `properties.coupon`       | `argmodp`         |
| `properties.currency`     | `nacur`           |
| `Cookie Click Id`         | `cible`           |
| `properties.coupon`       | `argbr`           |
