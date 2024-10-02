# Adform

[Adform](https://site.adform.com/) is a global digital media advertising technology company specializing in real-time programmatic marketing automation technologies. Using this destination you can implement [server-side tracking](https://www.adformhelp.com/hc/en-us/articles/9740579489041-Use-Server-Side-Tracking).

## Key features

The Adform destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) covers [Adform server-side tracking](https://www.adformhelp.com/hc/en-us/articles/9740579489041-Use-Server-Side-Tracking), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item ](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item)array is bridged to Partnerize.

## Destination setup

{% hint style="info" %}
A client-side tag template named "Adform - Get 3rd Party Cookie ID" is available in our library to help you retrieve the Adform Third-Party Identifier.\
Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to refine events and/or other properties matching your specific needs.
{% endhint %}

### Configuration

<table><thead><tr><th width="345">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Tracking Domain</code></td><td><em><strong><code>Required</code></strong></em><br>Your tracking domain as set on Adform UI (E.g. "a1.adform.net", without quotes). More details are available following this <a href="https://www.adformhelp.com/hc/articles/9740579553169#UUID-f565672b-d386-6014-c06e-054f43b67a2d">LINK</a>. This setting supports dynamic values <strong>[1][2]</strong>.</td></tr><tr><td><code>Tracking Setup Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your client tracking ID, which can be found under "Site Tracking" in Adform UI (E.g. "1257163", without quotes). This setting supports dynamic values <strong>[1][2]</strong>.</td></tr><tr><td><code>Tracking Point Name Property</code></td><td>Your property holding the tracking point name. In case it's not set, <code>Page URL (pageUrl)</code> will be used.</td></tr><tr><td><code>Select your Adform third-party holder</code></td><td>This can be either <code>Cookie</code> or <code>Event property</code>, depending on how you provide Adform third-party identifier value. A client-side tag template named "Adform - Get 3rd Party Cookie ID" is available in our library to help you retrieve this value.</td></tr><tr><td><code>Third-Party Id Cookie Name</code></td><td>If you select <code>Cookie</code> in <code>Select your Adform third-party holder</code>, you can set your Adform third-party cookie name here.</td></tr><tr><td><code>Third-Party Id Property</code></td><td>If you select <code>Event property</code> in <code>Select your Adform third-party holder</code>, you can set your Adform third-party property name here.</td></tr><tr><td><code>Select your Adform first-party holder</code></td><td>This can be either <code>Cookie</code> or <code>Event property</code>, depending on how you provide Adform first-party identifier value.</td></tr><tr><td><code>First-Party Id Cookie Name</code></td><td>If you select <code>Cookie</code> in <code>Select your Adform first-party holder</code>, you can set your Adform first-party cookie name here. Only use for hybrid setups, where part of site tracking is implemented client-side to be able to pass its value that Adform has set previously.</td></tr><tr><td><code>First-Party Id Cookie Domain</code></td><td>If you select <code>Cookie</code> in <code>Select your Adform first-party holder</code>, you can set your Adform first-party cookie domain here. Only use for hybrid setups, where part of site tracking is implemented client-side to be able to pass its value that Adform has set previously.</td></tr><tr><td><code>First-Party Id Property</code></td><td>If you select <code>Event property</code> in <code>Select your Adform first-party holder</code>, you can set your Adform first-party property name here.</td></tr><tr><td><code>Custom Event Properties</code></td><td><p>Map your custom event properties by setting their field names in <code>Adform property name</code> and adding the field name holding the value in <code>Your event property</code>. E.g. if you input<code>size</code>in the <code>Partnerize property name</code> and <code>items.0.product.size</code> in <code>Your event property</code>, you'll have a custom event property in Adform called<code>size</code>with a value based on the content of the field <code>items.0.product.size</code> <strong>[2]</strong>.</p><p><br>In the column <code>Your event property path</code> you should keep the default value <code>Default (root)</code> as it fits most scenarios. In case you select either <code>In "items" {items.X}</code> or <code>In "product" {items.X.product}</code> this destination will look for the input event property starting from the <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#item">items </a>or <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#product">product </a>level respectively and add its value as a custom entry in the "subVariables" array. The advanced operation <code>As Adform subVariables Data</code> can be paired with the property path option <code>Default (root)</code> so your property value is set as a custom entry in the "subVariables" array for each item. More details on Adform custom variables are available following this <a href="https://www.adformhelp.com/hc/en-us/articles/9740579489041-Use-Server-Side-Tracking">LINK</a> (section: "Add Custom Variables").</p></td></tr></tbody></table>



{% hint style="info" %}
**\[1]** This feature allows you to set an event property holding a dynamic value by adding two open braces (`{{`) in front of your property name and two close braces (`}}`) at the end (E.g. `{{myEventPropertyPathAndName}}`).\
**\[2]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

| Commanders Act Events  | Adform Tracking          |
| ---------------------- | ------------------------ |
| `[Any Event]` **\[1]** | `[Tracking Point Names]` |

{% hint style="info" %}
**\[1]** Ensure to apply [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) configuring your relevant events for this destination. Custom events are also supported.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
For audience building and retargeting, make sure to pass a user identifier.\
Geo and device information come from the provided user ip and agent.\
Adform standard attribution works only if <mark style="color:blue;">`identity.cookieId`</mark> (Adform 3rd party cookie) or <mark style="color:blue;">`identity.advertisingId`</mark> (mobile advertising ID) is passed correctly.\
Adform Cookieless Insights reporting is enabled by passing values in both <mark style="color:blue;">`userContext.userAgent`</mark> and <mark style="color:blue;">`userContext.userIp`</mark> .
{% endhint %}

<table><thead><tr><th width="347">Commanders Act Properties</th><th>Adform Properties</th></tr></thead><tbody><tr><td><p><code>Third-Party Id Cookie Name</code> </p><p><code>Third-Party Id Property</code></p></td><td><code>identity.cookieId</code> <strong>[1]</strong></td></tr><tr><td><p><code>First-Party Id Cookie Name</code></p><p><code>First-Party Id Property</code></p></td><td><code>identity.firstPartyId.id</code> <strong>[1]</strong></td></tr><tr><td><p><code>First-Party Id Cookie Domain</code> </p><p><code>(context.page.url)</code></p></td><td><code>identity.firstPartyId.domain</code> <strong>[2]</strong></td></tr><tr><td><code>Tracking Point Name Property</code></td><td><code>name</code></td></tr><tr><td><code>context.page.url</code></td><td><code>pageUrl</code></td></tr><tr><td><code>context.page.referrer</code></td><td><code>refererUrl</code></td></tr><tr><td><code>context.device.advertising_id</code></td><td><code>identity.advertisingId</code></td></tr><tr><td><code>partners.adform.provider_id</code></td><td><code>identity.eids.0.source</code></td></tr><tr><td><code>user.id</code></td><td><code>identity.eids.0.uids.0.id</code></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>userContext.userAgent</code></td></tr><tr><td><code>context.device.ip</code></td><td><code>userContext.userIp</code></td></tr><tr><td><code>value</code></td><td><code>variables.sales</code></td></tr><tr><td><code>id</code></td><td><code>variables.orderid</code></td></tr><tr><td><code>items.X.id</code></td><td><code>variables.subVariables.X.productid</code></td></tr><tr><td><code>items.X.product.price</code></td><td><code>variables.subVariables.X.productsales</code></td></tr><tr><td><code>partners.adform.consent_string</code></td><td><code>compliance.gdprConsent</code> <strong>[3]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Cookie name or property is used based on your [Configuration](adform.md#configuration).\
**\[2]** Priority order is listed in the left column.\
**\[3]** IAB TCF consent string.
{% endhint %}
