# Taboola Events

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Taboola ](https://www.taboola.com)drives business results by reaching people at the right moment.\
This integration allows [server-side tracking](https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-).

## Key features

The Taboola Events destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [Taboola events](https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.

## Destination setup

{% hint style="info" %}
First you need to enable server-side tracking in your Taboola campaigns by including the<mark style="color:blue;">`{click_id}`</mark>macro to your tracking code. More details are available by following this [LINK](https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-) (See section "Add S2S Tracking to your Taboola Campaign"). \
The macro value needs to be saved in a property (See<mark style="color:blue;">`Taboola Click Id Property`</mark> in [Configuration](taboola-events.md#configuration)). When creating a server-side conversion in Taboola (See [LINK](https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-) section "Create S2S Conversions"), take note of your "Event Name": this has to be set as<mark style="color:blue;">`Taboola Event Name`</mark>in [Configuration](taboola-events.md#configuration).\
Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to refine events and/or other properties matching your specific needs.
{% endhint %}

### Configuration

| Settings                    | Description                                                                                                                                                                                                                                                                                                                                                        |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Taboola Click Id Property` | <p><em><strong><code>Required</code></strong></em></p><p>Your property name holding Taboola click identifier (E.g. "click_id", without quotes). More details are available by following this <a href="https://help.taboola.com/hc/en-us/articles/115006850567-How-to-Track-Conversions-Using-Server-to-Server-Integration-S2S-">LINK</a> <strong>[1]</strong>.</p> |
| `Mapping`                   | <p><em><strong><code>Required</code></strong></em><br>Map Taboola Ads events with your Commanders Act events by setting at least a <code>Taboola Event Name</code> and a <code>Commanders Act Event Name</code>. One entry is required.</p>                                                                                                                        |

{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

| Commanders Act Events | Taboola Events     |
| --------------------- | ------------------ |
| `[All events]`        | `[Taboola events]` |

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

| Commanders Act Properties     | Taboola Properties |
| ----------------------------- | ------------------ |
| `Taboola Event Name` **\[1]** | `name`             |
| `Taboola Click Id Property`   | `click-id`         |
| `revenue`                     | `revenue`          |
| `currency`                    | `currency`         |
| `id`                          | `orderid`          |

{% hint style="info" %}
**\[1]** See<mark style="color:blue;">`Mapping`</mark>in [Configuration](taboola-events.md#configuration).
{% endhint %}
