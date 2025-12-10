# Google Floodlight Mobile App Conversion

[Floodlight](https://support.google.com/searchads/answer/7298761?hl=en) provides you insight into the actions that users take after they view or click on ads. Using this destination you can track installs of your app or activities that take place in the app.

## Key features

The Google Floodlight Mobile App Conversion destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) covers [Floodlight ability to track in-app actions](https://support.google.com/sa360/answer/14442341?hl=en), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Refined data**: you can freely push additional custom event properties based on your specific needs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://doc.commandersact.com/developers/tracking/events-reference#item) array is dispatched to Floodlight.

## Destination setup

{% hint style="warning" %}
Some setup is required on the Floodlight side before configuring this destination. See more details by following this [LINK ](https://support.google.com/sa360/answer/14442341?hl=en)(See section <mark style="color:blue;">`Set up Floodlight in apps`</mark> → <mark style="color:blue;">`Ensure ad tags pass proper values from publishers`</mark>).
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><em><strong><code>Required</code></strong></em><br>This is the value of the <code>src</code> parameter. More details are available following this <a href="https://support.google.com/tagmanager/answer/6107168">LINK</a>.</td></tr><tr><td><code>Group Tag String</code></td><td><em><strong><code>Required</code></strong></em><br>This is the value of the <code>type</code> parameter. More details are available following this <a href="https://support.google.com/tagmanager/answer/6107168">LINK</a>.</td></tr><tr><td><code>Activity Tag String</code></td><td><em><strong><code>Required</code></strong></em><br>This is the value of the <code>cat</code> parameter. More details are available following this <a href="https://support.google.com/tagmanager/answer/6107168">LINK</a>.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Send custom properties ( <code>u</code> , <code>tran</code> , <code>num</code> , <code>u1</code> , <code>u2</code> , etc...) related to events.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | Floodlight conversion       |
| ---------------------- | --------------------------- |
| `[Any Event]` **\[1]** | `[Any Conversion]` **\[1]** |

{% hint style="info" %}
**\[1]** Use [Destination filters](https://doc.commandersact.com/features/destinations/destination-filters) to refine events matching your specific needs.
{% endhint %}

## Field mappings

<table><thead><tr><th width="383.29729729729735">Commanders Act Properties</th><th>Floodlight Properties</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><code>src</code> <strong>[*]</strong></td></tr><tr><td><code>Group Tag String</code></td><td><code>cat</code> <strong>[*]</strong></td></tr><tr><td><code>Activity Tag String</code></td><td><code>type</code> <strong>[*]</strong></td></tr><tr><td><code>context.device.advertising_id</code></td><td><code>dc_rdid</code> <strong>[*]</strong></td></tr><tr><td><code>partners.google.cdt</code></td><td><code>tag_for_child_directed_treatment</code></td></tr><tr><td><code>context.device.ad_tracking_enabled</code></td><td><code>dc_lat</code></td></tr><tr><td><code>items.X.quantity</code></td><td><code>qty</code> <strong>[1]</strong></td></tr><tr><td><code>revenue</code></td><td><code>cost</code></td></tr><tr><td><code>id</code></td><td><code>ord</code> <strong>[2]</strong></td></tr><tr><td><code>items.X.product.id</code> <code>items.X.product.price</code> <code>items.X.quantity</code></td><td><code>prd</code></td></tr><tr><td><code>Your value</code> <strong>[3]</strong></td><td><code>Floodlight property name</code> <strong>[3]</strong></td></tr></tbody></table>

{% hint style="info" %}
> **\[\*]** Mandatory property.  \
> &#xNAN;**\[1]** Sum of each product quantity.  \
> &#xNAN;**\[2]** If no property is provided, a random generated number is used.  \
> &#xNAN;**\[3]** See <mark style="color:blue;">`Custom Event Properties`</mark> in [Configuration ](google-floodlight-mobile-app-conversion.md#configuration)for more details on how you can add custom properties.
{% endhint %}
