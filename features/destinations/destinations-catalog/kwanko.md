# Kwanko

[Kwanko ](https://www.kwanko.com/)provides a global affiliation network connecting businesses with customers.\
Using this destination you can implement server-side lead and sale tracking.

## Key features

The Kwanko destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers Kwanko lead and sale tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Custom properties**: you can freely push custom properties based on your specific needs.

## Destination setup

### Configuration

<table><thead><tr><th width="338">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Collection Server Base Url</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Your collection server base URL (E.g. "http://server.client.fr") as provided by Kwanko. Default value: "https://action.metaffiliation.com/trk.php".</p></td></tr><tr><td><code>Tracking Id</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Your tracking identifier as provided by Kwanko. It's used to identify your campaigns.</p></td></tr><tr><td><code>Conversion Type</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>The conversion type that is bound with your activity. This can be either <code>sale</code> or <code>lead</code>. If conversion type is <code>lead</code>, only <code>generate_lead</code> events are forwarded to Kwanko. If conversion type is <code>sale</code>, only <code>purchase</code> events are sent to the partner.</p></td></tr><tr><td><code>Cookie Click Id</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>For each click on Kwanko links a new "Click Id" is automatically generated. This can be found as value for the parameter <code>kwks2s</code> in landings. Input the cookie name holding this value.</p></td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>Event property name</code> and adding the field name holding the value in <code>Commanders Act event property or static value</code>. E.g. if you input<code>size</code>in the <code>Event property name</code> and <code>items.0.product.size</code> in <code>Commanders Act event property or static value</code>, you'll have a custom event property in Kwanko called<code>size</code>with a value based on the content of the field <code>items.0.product.size</code> <strong>[1]</strong>. You also have the option to set a static string/numeric value in <code>Commanders Act event property or static value</code>.</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

| Commanders Act Events | Kwanko Tracking |
| --------------------- | --------------- |
| `generate_lead`       | `lead`          |
| `purchase`            | `sale`          |

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
The Kwanko property<mark style="color:blue;">`gdpr_kwk`</mark>is always set to<mark style="color:blue;">`1`</mark>. Manage your consent settings using the filter tab of this destination.
{% endhint %}

| Commanders Act Properties | Kwanko Properties |
| ------------------------- | ----------------- |
| `Tracking Id`             | `mclic` **\[1]**  |
| `revenue`                 | `argmon`          |
| `id`                      | `argann`          |
| `coupon`                  | `argmodp`         |
| `currency`                | `nacur`           |
| `Cookie Click Id`         | `cible`           |
| `coupon`                  | `argbr`           |

{% hint style="info" %}
**\[1]** If<mark style="color:blue;">`Collection Server Base Url`</mark>is not the default value, the<mark style="color:blue;">`Tracking Id`</mark>is appended as part of base URL and the<mark style="color:blue;">`mclic`</mark>is not set.
{% endhint %}
