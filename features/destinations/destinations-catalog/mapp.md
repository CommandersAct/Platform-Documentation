# Mapp

[Mapp](https://mapp.com/), formerly Webtrekk, generates actionable insights for brands to engage with their customers and deliver cross-channel marketing campaigns. Using this destination you can implement Mapp [server-side tracking](https://documentation.mapp.com/1.0/en/server-to-server-7240721.html).&#x20;

## Key features

The Mapp destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers [Mapp request types](https://documentation.mapp.com/1.0/en/which-request-types-are-supported-by-mapp-intelligence-36143348.html), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Custom events and properties**: you can freely push custom events and properties based on your specific needs.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to Mapp.

## Destination setup

{% hint style="info" %}
Ensure events are properly filtered, based on your expected configuration/needs, using&#x20;
{% endhint %}

### Configuration

| Settings                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Track Domain`            | <p><em><strong><code>Required</code></strong></em></p><p>Your track domain as provided by Mapp.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `Track Id`                | <p><em><strong><code>Required</code></strong></em></p><p>Your track identifier as provided by Mapp.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `Custom Event Properties` | <p>Map your custom event properties by setting their field names in <code>Event property name</code> and adding the field name holding the value <strong></strong> in <code>Commanders Act event property</code>. E.g. if you input<code>size</code>in the <code>Event property name</code> and <code>properties.items.0.product.size</code> in <code>Commanders Act event property</code>, you'll have a custom event property in Mapp called<code>size</code>with a value based on the content of the field <code>properties.items.0.product.size</code> <strong>[1]</strong>.</p><p><br>In the column <code>Commanders Act event property position</code> you should keep the default value <code>Default {properties}</code> as it better fits most  scenarios. In case you select either <code>In "items" {properties.items.X}</code> or <code>In "product" {properties.items.X.product}</code> this destination will look for the input event property starting from the <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#item">items </a>or <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#product">product </a>level respectively and concatenate values separated by a semicolon (";").</p> |

{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

| Commanders Act Events | Mapp Request Type                         |
| --------------------- | ----------------------------------------- |
| `[All events]`        | `page`or`event`or`media`or`form` **\[1]** |

{% hint style="info" %}
**\[1]** Custom events are also supported. More details on Mapp request types are available following this [LINK](https://documentation.mapp.com/1.0/en/which-request-types-are-supported-by-mapp-intelligence-36143348.html).
{% endhint %}

## Field mappings

{% hint style="info" %}
Session handling is done by Mapp using the ever id. If this information is not available, the session is recognized by the user agent and the IP address. More details are available following this [LINK](https://documentation.mapp.com/1.0/en/session-and-visitor-handling-7240758.html).\
Depending on Mapp request types you're sending, some properties may not be tracked by Mapp. More details are available following this [LINK](https://documentation.mapp.com/1.0/en/which-request-types-are-supported-by-mapp-intelligence-36143348.html).
{% endhint %}

| Commanders Act Properties                                                                                                                                                               | Mapp Properties                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| `partners.mapp.version`,`page.title`,0,`device.screen.width`x`device.screen.height`,`device.density`,0,`event_timestamp`,`page.referrer`,`device.screen.width`x`device.screen.height`,0 | `p` **\[1]**                      |
| <p><code>partners.mapp.ceid</code></p><p><code>device.sdk_id</code></p><p><code>properties.user.tcId</code></p>                                                                         | `ceid` **\[2]**                   |
| <p><code>partners.mapp.eid</code> </p><p><code>cookie</code> <a href="https://documentation.mapp.com/1.0/en/session-and-visitor-handling-7240758.html"><strong>wt3_eid</strong></a></p> | `eid` **\[2]**                    |
| `device.ip`                                                                                                                                                                             | `X-WT-IP`                         |
| `device.user_agent`                                                                                                                                                                     | `X-WT-UA` **\[3]**                |
| <p><code>page.url</code><br><code>page.location</code></p>                                                                                                                              | `X-WT-RQ` **\[2]\[3]**            |
| `page.lang`                                                                                                                                                                             | `la`                              |
| <p><code>partners.mapp.event_name</code> or</p><p><code>event_name</code></p>                                                                                                           | `ct` **\[2]\[4]**                 |
| `properties.currency`                                                                                                                                                                   | `cr`                              |
| `properties.id`                                                                                                                                                                         | `oi`                              |
| `properties.value`                                                                                                                                                                      | `ov`                              |
| `(event_name)`                                                                                                                                                                          | `st` **\[5]**                     |
| `properties.items.X.product.name`                                                                                                                                                       | `ba` **\[6]**                     |
| `properties.items.X.product.price`\*`properties.items.X.quantity`                                                                                                                       | `co` **\[6]**                     |
| `properties.items.X.quantity`                                                                                                                                                           | `qn` **\[6]**                     |
| `properties.items.X.list_position`                                                                                                                                                      | `plp` **\[6]**                    |
| `Custom Event Properties`                                                                                                                                                               | `[Custom Property Name]` **\[7]** |

{% hint style="info" %}
**\[1]** Default value: <mark style="color:blue;">`300,0,0,0,0,0,event_timestamp,0,0,0`</mark>.\ <mark style="color:blue;">``</mark>**\[2]** Priority order is listed in the left column.\
**\[3]** Encoded property.\
**\[4]** Property excluded with [**page\_view**](https://doc.commandersact.com/developers/tracking/events-reference#page\_view) event. **** \
**\[5]** If the [**items**](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is filled and depending on incoming events, this is set with:\
&#x20;     •<mark style="color:blue;">**`add`**</mark>, for [**add\_to\_cart**](https://doc.commandersact.com/developers/tracking/events-reference#add\_to\_cart) **** event.\
&#x20;     •<mark style="color:blue;">**`conf`**</mark>, for [**purchase**](https://doc.commandersact.com/developers/tracking/events-reference#purchase) event.\
&#x20;     •<mark style="color:blue;">**`view`**</mark>, as default value.\
**\[6]** Product information separated by semicolon and computed amounts are rounded with two decimals.\
**\[7]** See<mark style="color:blue;">`Custom Event Properties`</mark>in [Configuration ](mapp.md#configuration)for more details on how you can bridge custom properties to Mapp.
{% endhint %}
