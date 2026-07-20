# Commission Junction

[Commission Junction](https://www.cj.com/)[ ](https://www.awin.com)(CJ) provides a global affiliation network connecting businesses with customers. Using this destination you can implement server-side tracking.

## Key features

The Commission Junction destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers Commission Junction server-side tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Refined data**: you can freely push additional information based on your specific needs.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Awin.

## Destination setup

### Configuration

<table><thead><tr><th width="369">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>CJ Enterprise Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your "Enterprise ID" as provided by Commission Junction. </td></tr><tr><td><code>Actions</code></td><td><em><strong><code>Required</code></strong></em><br>Map your Commanders Act event(s) with CJ ActionId(s) by setting a <code>Your Event Name</code> and a <code>CJ Action Id</code>. At least one entry is required.</td></tr><tr><td><code>CJ Event Cookie Name</code></td><td>Enter a cookie name holding CJ Event value. This value is passed by Commission Junction in landings (E.g. https://www.example.com/?cjevent=656e8fa049ec11ea8237023d0a240612). This is required if the "Smart Mapping" field <code>Click Id (cjevent)</code> is empty. The field <code>Click Id (cjevent)</code> has priority over this field.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>CJ property name</code> and adding the field name holding the value in <code>Your event property</code>. </td></tr></tbody></table>

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.\
The [configuration](commission-junction.md#configuration) field <mark style="color:blue;">`CJ Event Cookie Name`</mark> is not mandatory if the "Smart Mapping" field <mark style="color:blue;">`Click Id (cjevent)`</mark> is set. The latter has priority over the former.
{% endhint %}

| Smart Mapping Fields                                        | Commanders Act Properties                                                       | CJ Properties                                         |
| ----------------------------------------------------------- | ------------------------------------------------------------------------------- | ----------------------------------------------------- |
| `-`                                                         | `CJ Enterprise Id`                                                              | `CID` **\[\*]**                                       |
| `-`                                                         | `CJ Action Id`                                                                  | `TYPE` **\[\*]**                                      |
| <p><code>Click Id (cjevent)</code></p><p><code>-</code></p> | <p><code>partners.cj.cjevent</code></p><p><code>CJ Event Cookie Name</code></p> | `CJEVENT` **\[\*]\[1]**                               |
| `Event Timestamp`                                           | `event_timestamp`                                                               | `eventTime` **\[\*]\[2]**                             |
| `Order Id`                                                  | `id`                                                                            | `OID` **\[\*]**                                       |
| `Currency`                                                  | `currency`                                                                      | `currency` **\[\*]**                                  |
| `Amount`                                                    | `revenue`                                                                       | `amount` **\[\*]\[3]**                                |
| `Coupon`                                                    | `coupon`                                                                        | `coupon`                                              |
| `Item Id`                                                   | `items.X.id`                                                                    | `ITEM`<mark style="color:blue;">`[Y]`</mark> **\[4]** |
| `Item Price`                                                | `items.X.product.price`                                                         | `AMT`<mark style="color:blue;">`[Y]`</mark> **\[4]**  |
| `Item Quantity`                                             | `items.X.quantity`                                                              | `QTY`<mark style="color:blue;">`[Y]`</mark> **\[4]**  |
| `Item Discount`                                             | `items.X.discount`                                                              | `DCNT`<mark style="color:blue;">`[Y]`</mark> **\[4]** |
| `-`                                                         | `Your event property`                                                           | `CJ property name` **\[5]**                           |

{% hint style="info" %}
**\*** Mandatory property.\
**1.** <mark style="color:blue;">`Click Id (cjevent)`</mark> has priority over <mark style="color:blue;">`CJ Event Cookie Name`</mark> .\
**2.** Automatically converted in the [ISO 8601 format](https://en.wikipedia.org/wiki/ISO_8601).\
**3.** If [items ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)are present, this property won't be included.\
**4.** For each [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item): <mark style="color:blue;">`[Y]`</mark> is an incremental number, starting from <mark style="color:blue;">`1`</mark> .\
**5.** See <mark style="color:blue;">`Custom Event Properties`</mark> in [Configuration](commission-junction.md#configuration) for more details. The <mark style="color:blue;">`signature`</mark> CJ optional property can be set using this feature.
{% endhint %}
