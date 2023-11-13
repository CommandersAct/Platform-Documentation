# Moebel

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Moebel](https://www.moebel.de/) helps users find modern furniture across multiple stores.\
Using this destination you can leverage Moebel [server-side specifications](https://partner-integration.moebel.de/sales-tracking/1/manual-server-side-integration.html)

## Key features

The Moebel destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model covers Moebel sales tracking, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.&#x20;

## Destination setup

{% hint style="info" %}
The click identifier (`moeclid`) is required. You can set it using the field <mark style="color:blue;">`Click Identifier Cookie Name`</mark> or through the "Smart Mapping" section: see field <mark style="color:blue;">`Click Identifier (moeclid)`</mark>.
{% endhint %}

### Configuration

<table><thead><tr><th width="325">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Partner Key</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Your partner key as provided by Moebel.</p></td></tr><tr><td><code>Portal</code></td><td><em><strong><code>Required</code></strong></em><br>Choose the portal you want to send the sale request to. Available entries: <code>moebel.de</code>, <code>meubles.fr</code>, <code>meubelo.nl</code>, <code>moebel24.at</code> and <code>moebel24.ch</code>.</td></tr><tr><td><code>Click Identifier Cookie Name</code></td><td>Cookie name holding the click identifier (<code>moeclid</code>) value. More details are available by following this <a href="https://partner-integration.moebel.de/sales-tracking/1/manual-server-side-integration.html#_how_does_it_work">LINK</a>.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | Moebel Tracking |
| ---------------------- | --------------- |
| `[Any Event]` **\[1]** | `sale`          |

{% hint style="info" %}
**\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.
{% endhint %}

## Field Mappings

<table><thead><tr><th width="352.6685580062746">Commanders Act Properties</th><th>Moebel Properties</th></tr></thead><tbody><tr><td><p><code>Click Identifier Cookie Name</code></p><p><code>Click Identifier (moeclid)</code></p></td><td><code>moeclid</code> <strong>[*][1]</strong></td></tr><tr><td><code>shipping_amount</code></td><td><code>shipping</code> <strong>[*][2]</strong></td></tr><tr><td>(<code>value</code> - <code>shipping_amount</code>)</td><td><code>value</code> <strong>[*]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code> <strong>[*]</strong></td></tr><tr><td><code>id</code></td><td><code>order_id</code></td></tr><tr><td><code>items.X.id</code></td><td><code>items.X.item_id</code> <strong>[*]</strong></td></tr><tr><td><code>items.X.quantity</code></td><td><code>items.X.quantity</code> <strong>[*]</strong></td></tr><tr><td><code>items.X.product.price</code></td><td><code>items.X.price</code> <strong>[*]</strong></td></tr><tr><td><code>items.X.product.category_1</code></td><td><code>items.X.item_category</code> <strong>[*]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** See [Destination setup](moebel.md#destination-setup) for more details.\
**\[2]** Default value: <mark style="color:blue;">`0`</mark>.
{% endhint %}
