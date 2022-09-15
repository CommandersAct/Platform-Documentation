# Commission Junction

{% hint style="info" %}
This destination is currently under final review and will be released soon.
{% endhint %}

[Commission Junction](https://www.cj.com/)[ ](https://www.awin.com)(CJ) provides a global affiliation network connecting businesses with customers. Using this destination you can implement server-side tracking.

## Key features

The Commission Junction destination provides the following key features:

* **Events structure**: our [Event reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers Commission Junction server-side tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Refined data**: you can freely push additional information based on your specific needs.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Awin.

## Destination setup

### Configuration

| Settings                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `CJ Enterprise Id`        | <p><em><strong><code>Required</code></strong></em></p><p>Your "Enterprise ID" as provided by Commission Junction.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `CJ Event Cookie Name`    | <p><em><strong><code>Required</code></strong></em></p><p>Enter a cookie name holding CJ Event value. This value is passed by Commission Junction in landings (E.g. https://www.example.com/?cjevent=656e8fa049ec11ea8237023d0a240612).</p>                                                                                                                                                                                                                                                                                                                                                                   |
| `Mapping`                 | <p><em><strong><code>Required</code></strong></em><br>Map your Commanders Act event(s) with CJ ActionId(s) by setting at least a  <code>Commanders Act Event Name</code> and a <code>CJ Action Id</code>.</p>                                                                                                                                                                                                                                                                                                                                                                                                |
| `Custom Event Properties` | Map your custom event properties by setting their field names in `Event property name` and adding the field name holding the value **** in `Commanders Act event property or static value`. E.g. if you input`size`in the `Event property name` and `properties.items.0.product.size` in `Commanders Act event property or static value`, you'll have a custom event property in CJ called`size`with a value based on the content of the field `properties.items.0.product.size` **\[1]**. You also have the option to set a static string/numeric value in `Commanders Act event property or static value`. |

{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Field Mappings

| Commanders Act Properties                       | CJ Properties                  |
| ----------------------------------------------- | ------------------------------ |
| `CJ Enterprise Id`                              | `CID`                          |
| `CJ Action Id`                                  | `TYPE`                         |
| `CJ Event Cookie Name`                          | `CJEVENT`                      |
| `event_timestamp`                               | `eventTime` **\[1]**           |
| `properties.id`                                 | `OID`                          |
| `properties.currency`                           | `currency`                     |
| `properties.revenue`                            | `amount` **\[2]**              |
| `properties.coupon`                             | `coupon`                       |
| `properties.items.X.product.id`                 | `ITEMY` **\[3]**               |
| `properties.items.X.product.price`              | `AMTY` **\[3]**                |
| `properties.items.X.quantity`                   | `QTYY` **\[3]**                |
| `properties.items.X.discount`                   | `DCNTY` **\[3]**               |
| `Commanders Act event property or static value` | `Event property name` **\[4]** |

{% hint style="info" %}
**\[1]** Automatically converted in the [ISO 8601 format](https://en.wikipedia.org/wiki/ISO\_8601).\
**\[2]** If [items ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)are present, this property won't be included.\
**\[3]** For each [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item):<mark style="color:blue;">`X`</mark>and<mark style="color:blue;">`Y`</mark>are incremental numbers, starting from<mark style="color:blue;">`0`</mark>and<mark style="color:blue;">`1`</mark>respectively.\
**\[4]** See<mark style="color:blue;">`Custom Event Properties`</mark>in [Configuration](commission-junction.md#configuration) for more details.\
The<mark style="color:blue;">`signature`</mark>CJ optional property can be set using this feature.&#x20;
{% endhint %}
