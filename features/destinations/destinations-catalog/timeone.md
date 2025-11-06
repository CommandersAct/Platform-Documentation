# TimeOne

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[TimeOne ](https://www.timeone.io/en/)combines affiliation platform, lead management technology and proprietary media.\
Using this destination, you can take advantage of TimeOne server-side tracking.

## Key features

The TimeOne destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model covers TimeOne postback server-side tracking, meaning that your data is properly bridged to the expected fields in an optimized way..
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to TimeOne.

## Destination setup

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Program Id</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Your program identifier as provided by TimeOne.</p></td></tr><tr><td><code>Publisher Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your publisher identifier as provided by TimeOne.</td></tr><tr><td><code>Creative Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your creative identifier as provided by TimeOne.</td></tr><tr><td><code>Subtracking</code></td><td>TimeOne click identifier value. When a user clicks on TimeOne affiliate link, the parameter "tog_sb" is appended to the redirection url. This includes the following information: timestamp, affiliate program identifier, publisher identifier, and clicked promo element identifier.</td></tr><tr><td><code>Subtracking Cookie Name</code></td><td>As an additional way to pass TimeOne click identifier, you can input a cookie name holding its value. This also acts as a fallback method when no value can be retrieved from the "Subtracking" field.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | TimeOne Tracking |
| ---------------------- | ---------------- |
| `[Any Event]` **\[1]** | `lead`           |
| `[Any Event]` **\[1]** | `sale`           |

{% hint style="info" %}
**\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table><thead><tr><th width="364.6685580062746">Commanders Act Properties</th><th>TimeOne Properties</th></tr></thead><tbody><tr><td><code>Program Id</code></td><td><code>progid</code> <strong>[*]</strong></td></tr><tr><td><code>Publisher Id</code></td><td><code>comid</code> <strong>[*]</strong></td></tr><tr><td><code>Creative Id</code></td><td><code>iu</code> <strong>[*]</strong></td></tr><tr><td><p><code>Subtracking</code></p><p><code>Subtracking Cookie Name</code></p></td><td><code>subtracking</code> <strong>[*][1]</strong></td></tr><tr><td><code>id</code></td><td><code>uniqid</code> <strong>[*]</strong></td></tr><tr><td><code>revenue</code></td><td><code>price</code></td></tr><tr><td><code>items.X.id</code>;<code>items.X.product.name</code>;<code>items.X.product.price</code>;<code>items.X.quantity</code></td><td><code>data</code> <strong>[2]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
\&#xNAN;**\[1]** <mark style="color:blue;">`Subtracking`</mark> has priority over <mark style="color:blue;">`Subtracking Cookie Name`</mark>. See [Configuration](timeone.md#configuration) for more details.\
&#xNAN;**\[2]** All items are taken into account, separeted by a pipe character ("|") and encoded.
{% endhint %}
