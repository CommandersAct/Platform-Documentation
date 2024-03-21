# Taboola Events

[Taboola ](https://www.taboola.com)is a public advertising company that provides advertisements such as "Around the Web" and "Recommended For You" boxes at the bottom of many online news articles.\
This destination allows [server-side tracking](https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-).

## Key features

The Taboola Events destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [Taboola events](https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.

## Destination setup

{% hint style="info" %}
First, you need to enable server-side tracking in your Taboola campaigns by including the <mark style="color:blue;">`{click_id}`</mark> macro to your tracking code. More details are available by following this [LINK](https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-) (See section "Add S2S Tracking to your Taboola Campaign"). \
Lastly, if you're not already sending events to Taboola Ads, you need to create a server-side conversion (See [LINK](https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-) and section "Create S2S Conversions") and take note of your "Event Name": this has to be set as <mark style="color:blue;">`Taboola Event Name`</mark> in [Configuration](taboola-events.md#configuration).
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Taboola Click Id</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Taboola click identifier. Learn how to add the click identifier in your campaign target landings by following this <a href="https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-">LINK</a> (See section "Add S2S Tracking to your Taboola Campaign").</p></td></tr><tr><td><code>Mapping</code></td><td><em><strong><code>Required</code></strong></em><br>Map Taboola Ads events with your events by setting at least a <code>Taboola Event Name</code> and a <code>Your event</code>. One entry is required. See <a href="taboola-events.md#destination-setup">Destination setup</a> for more details.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | Taboola Events    |
| ---------------------- | ----------------- |
| `[Any Event]` **\[1]** | `[Taboola Event]` |

{% hint style="info" %}
**\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table><thead><tr><th width="456">Commanders Act Properties</th><th>Taboola Properties</th></tr></thead><tbody><tr><td><code>Taboola Click Id</code></td><td><code>click-id</code> <strong>[*]</strong></td></tr><tr><td><code>Taboola Event Name</code> <strong>[1]</strong></td><td><code>name</code> <strong>[*]</strong></td></tr><tr><td><code>revenue</code></td><td><code>revenue</code></td></tr><tr><td><code>currency</code></td><td><code>currency</code></td></tr><tr><td><code>id</code></td><td><code>orderid</code></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** See <mark style="color:blue;">`Mapping`</mark> in [Configuration](taboola-events.md#configuration).
{% endhint %}
