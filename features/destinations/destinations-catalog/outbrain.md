# Outbrain

[Outbrain](https://www.outbrain.com/) is a web recommendation platform.\
Using this destination you can implement [server-side tracking](https://www.outbrain.com/help/advertisers/server2server-integrations/).

## Key features

The Outbrain destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers [Outbrain unique events](https://www.outbrain.com/help/advertisers/server2server-integrations/), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Custom events**: you can freely push custom events based on your specific needs.

## Destination setup

{% hint style="info" %}
Ensure you added the "Click Parameter" to your Outbrain campaign's tracking code: see the following [LINK](https://www.outbrain.com/help/advertisers/server2server-integrations/) for more details (See "Add a Click Parameter to Your Campaign’s Tracking Code" section). Moreover, create at least one Outbrain event by following this [LINK](https://www.outbrain.com/help/advertisers/server2server-integrations/) (See "Create a Unique Event Name" section): you need to set the Outbrain event name in the related field in <mark style="color:blue;">`Mapping`</mark> : see [Configuration](outbrain.md#configuration) for more details.
{% endhint %}

### Configuration

| Settings            | Description                                                                                                                                                                                                                                                                                                                                                                                      |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Outbrain Click Id` | <p><em><strong><code>Required</code></strong></em><br>Outbrain click identifier. More details are available by following this <a href="https://www.outbrain.com/help/advertisers/server2server-integrations/">LINK</a> (See "Add a Click Parameter to Your Campaign’s Tracking Code" section).</p>                                                                                               |
| `Mapping`           | <p><em><strong><code>Required</code></strong></em><br>Your mapping between Outbrain's events and yours. At least one couple <code>Outbrain event name</code> and <code>Your event name</code> is required. More details are available by following this <a href="https://www.outbrain.com/help/advertisers/server2server-integrations/">LINK</a> (See "Create a Unique Event Name" section).</p> |

## Quick reference

| Commanders Act Events  | Outbrain Events        |
| ---------------------- | ---------------------- |
| `[Any Event]` **\[1]** | `[Any Event]` **\[1]** |

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Mapping`</mark> in [Configuration](outbrain.md#configuration) for more details.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table><thead><tr><th width="364.6685580062746">Commanders Act Properties</th><th>Outbrain Properties</th></tr></thead><tbody><tr><td><code>Outbrain Click Id</code></td><td><code>ob_click_id</code> <strong>[*]</strong></td></tr><tr><td><code>Outbrain event name</code></td><td><code>name</code> <strong>[1]</strong></td></tr><tr><td><code>id</code></td><td><code>orderId</code></td></tr><tr><td><code>value</code></td><td><code>orderValue</code></td></tr><tr><td><code>currency</code></td><td><code>currency</code></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>timestamp</code> <strong>[2]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Mapping`</mark> in [Configuration](outbrain.md#configuration) for more details.\
\&#xNAN;**\[2]** Automatically converted from timestamp (mills) in format: <mark style="color:blue;">yyyy-mm-dd</mark>T<mark style="color:blue;">hh:mm:ss</mark>Z.
{% endhint %}
