# Kwanko

Kwanko provides a global affiliation network connecting businesses with customers.\
Using this destination you can implement server-side lead and sale tracking.

## Key features

The Awin destination provides the following key features:

* **Events structure**: our [Event reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model covers Kwanko lead and sale tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.

## Destination setup

### Configuration

| Settings          | Description                                                                                                                                                                                                                                                                                                                                                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Tracking Id`     | <p><em><strong><code>Required</code></strong></em></p><p>Your tracking identifier as provided by Kwanko. It's used to identify your campaigns.</p>                                                                                                                                                                                                                                         |
| `Conversion Type` | <p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>sale</code> or <code>lead</code>. If conversion type is <code>lead</code>, only <code>generate_lead</code> events are forwarded to Kwanko. If conversion type is <code>sale</code>, only <code>purchase</code> events are sent to the partner.</p> |
| `Cookie Click Id` | <p><em><strong><code>Required</code></strong></em></p><p>For each click on Kwanko links a new "Click Id" is automatically generated. This can be found as value for the parameter <code>kwks2s</code> in landings. Input the cookie name holding this value.</p>                                                                                                                           |

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
