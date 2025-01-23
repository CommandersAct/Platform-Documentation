# The Trade Desk Conversions API

[The Trade Desk](https://www.thetradedesk.com/us) is one of the largest independent demand-side platform (DSP) providing real-time ad pricing and placement for advertisers, ad agencies and brands.\
Using this destination, you can leverage [The Trade Desk Real-Time Conversion Events API](https://api.thetradedesk.com/v3/portal/data/doc/DataConversionEventsApi) to send events via server-side hits.

## Key features

The Trade Desk destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model matches [The Trade Desk's events](https://api.thetradedesk.com/v3/portal/data/doc/DataConversionEventsApi#event-mapping), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.&#x20;
* **Event mapping**: change standard mapping between your partners' events and yours or add new mappings.&#x20;
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to The Trade Desk.

## Destination setup

{% hint style="info" %}
On user identifiers, you should pass either `User/Device ID Type` **AND** `User/Device Identifier` **OR** "Smart Mapping" fields like `Device Mobile Identifier`, `The Trade Desk GUID`, `Encrypted UID2 token`, `Encrypted EUID token`, `RampID`.
{% endhint %}

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>TTD Conversion API URL</code></td><td><em><strong><code>Required</code></strong></em> <br>Your TTD Conversion API URL. Default: "https://insight.adsrvr.org/track/realtimeconversion".</td></tr><tr><td><code>Tracking Tag Type</code></td><td><em><strong><code>Required</code></strong></em> <br>Choose the type of tracking tag. This is either <code>Event Tracking</code> or <code>URL Mapping (page views)</code>.</td></tr><tr><td><code>Merchant Id</code></td><td><em><strong><code>Required for Event Tracking</code></strong></em> <strong>[1]</strong><br>The platform identifier of the merchant assigned by The Trade Desk to the merchant during the onboarding process.</td></tr><tr><td><code>Event Tracker Id</code></td><td><p><em><strong><code>Required for Event Tracking</code></strong></em> <strong>[1]</strong></p><p>The Trade Desk platform identifier of the event tracker.</p></td></tr><tr><td><code>Advertiser Id</code></td><td><em><strong><code>Required for URL Mapping (page views)</code></strong></em> <strong>[1]</strong><br>The Trade Desk platform identifier for the advertiser on whose behalf the tracking call is made.</td></tr><tr><td><code>Universal Pixel Id</code></td><td><em><strong><code>Required for URL Mapping (page views)</code></strong></em> <strong>[1]</strong><br>The Trade Desk platform identifier of the "Universal Pixel".</td></tr><tr><td><code>User/Device ID Type</code></td><td>The type of the advertising identifier, specified in the <code>User/Device Identifier</code>. Supported values: TDID, IDFA, AAID, DAID, NAID, IDL, EUID, or UID2.</td></tr><tr><td><code>User/Device Identifier</code></td><td>The unique advertising identifier for the event. This can be any of the identifiers as specified in the following <a href="https://api.thetradedesk.com/v3/portal/data/doc/DataConversionEventsApi">LINK</a> (See <code>adid</code> property).</td></tr><tr><td><code>TTD TDID Cookie Name</code></td><td>The first party cookie in which you stored the TTD TDID cookie value. This is used when no value can be retrieved from the field<code>User/Device Identifier</code>. Default value: "ttd_TDID".</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>The Trade Desk property name</code> and adding the field name holding the values in <code>Your value</code> . E.g. if you input <code>size</code> in the <code>The Trade Desk property name</code>  and <code>items.0.product.size</code> <strong>[2]</strong> in <code>Your value</code> , you will have a custom event property in The Trade Desk called <code>size</code> with a value based on the content of the field <code>items.0.product.size</code> .</td></tr><tr><td><code>Event Mapping</code></td><td>Change the <a href="the-trade-desk-conversions-api.md#quick-reference">standard mapping</a> between The Trade Desk's events and yours or add new mappings.</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See[`Tracking Tag Type`](the-trade-desk-conversions-api.md#configuration)for more details.\
&#xNAN;**\[2]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

{% hint style="info" %}
Using the [Event Mapping](the-trade-desk-conversions-api.md#configuration) you can change the [standard mapping](the-trade-desk-conversions-api.md#quick-reference) between The Trade Desk's events and yours or add new mappings.
{% endhint %}

| Commanders Act Events | The Trade Desk Events  |
| --------------------- | ---------------------- |
| `add_to_cart`         | `addtocart`            |
| `add_to_wishlist`     | `wishlistitem`         |
| `begin_checkout`      | `startcheckout`        |
| `login`               | `login`                |
| `page_view`           | `sitevisit`            |
| `purchase`            | `purchase`             |
| `search`              | `searchitem`           |
| `view_cart`           | `viewcart`             |
| `view_item`           | `viewitem`             |
| `[Any Event]`         | `[Any Event]` **\[1]** |

{% hint style="info" %}
&#x20;**\[1]** See [Event Mapping](the-trade-desk-conversions-api.md#configuration) for more details.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
All The Trade Desk properties on the right column are set in the object <mark style="color:blue;">`data.0`</mark> .
{% endhint %}

{% hint style="warning" %}
The following The Trade Desk properties can be set if `Device OS`, in the "Smart Mapping", is present with supported values:

* `aaid`
* `idfa`
* `naid`
{% endhint %}

<table><thead><tr><th width="341.6685580062746">Commanders Act Properties</th><th>The Trade Desk Properties</th></tr></thead><tbody><tr><td><code>Merchant Id</code></td><td><code>merchant_id</code> <strong>[*]</strong></td></tr><tr><td><code>Event Tracker Id</code></td><td><code>tracker_id</code> <strong>[*]</strong></td></tr><tr><td><code>Advertiser Id</code></td><td><code>adv</code> <strong>[*]</strong></td></tr><tr><td><code>Universal Pixel Id</code></td><td><code>upixel_id</code> <strong>[*]</strong></td></tr><tr><td><code>User/Device ID Type</code></td><td><code>adid_type</code></td></tr><tr><td><code>User/Device Identifier</code></td><td><code>adid</code></td></tr><tr><td>See <a href="the-trade-desk-conversions-api.md#quick-reference">Quick reference</a></td><td><code>event_name</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.advertising_id</code></td><td><code>daid</code> <strong>[2]</strong><br><code>aaid</code> <strong>[3]</strong><br><code>idfa</code> <strong>[4]</strong><br><code>naid</code> <strong>[5]</strong></td></tr><tr><td><code>partners.ttd.tduid</code></td><td><code>tdid</code> <strong>[6]</strong></td></tr><tr><td><code>partners.ttd.uid2_token</code></td><td><code>uid2_token</code> <strong>[7]</strong></td></tr><tr><td><code>partners.ttd.euid_token</code></td><td><code>euid_token</code> <strong>[8]</strong></td></tr><tr><td><code>partners.ttd.idl</code></td><td><code>idl</code> <strong>[9]</strong></td></tr><tr><td><code>user.country</code></td><td><code>country</code></td></tr><tr><td><code>user.state</code></td><td><code>region</code></td></tr><tr><td><code>user.metro</code></td><td><code>metro</code></td></tr><tr><td><code>user.city</code></td><td><code>city</code></td></tr><tr><td><code>user.zipcode</code></td><td><code>zip</code></td></tr><tr><td><code>context.device.ip</code></td><td><code>client_ip</code></td></tr><tr><td><code>context.page.url</code></td><td><code>referrer_url</code></td></tr><tr><td><code>id</code></td><td><code>order_id</code></td></tr><tr><td><code>value</code></td><td><code>value</code></td></tr><tr><td><code>currency</code></td><td><code>currency</code></td></tr><tr><td><code>partners.ttd.iattr</code></td><td><code>iattr</code> <strong>[10]</strong></td></tr><tr><td><code>partners.ttd.imp</code></td><td><code>imp</code> <strong>[11]</strong></td></tr><tr><td><code>partners.ttd.ivtc</code></td><td><code>ivtc</code> <strong>[12]</strong></td></tr><tr><td><code>partners.ttd.privacy_type</code></td><td><code>privacy_settings.0.privacy_type</code> <strong>[13]</strong></td></tr><tr><td><code>partners.ttd.is_applicable</code></td><td><code>privacy_settings.0.is_applicable</code> <strong>[14]</strong></td></tr><tr><td><code>partners.ttd.consent_string</code></td><td><code>privacy_settings.0.consent_string</code> <strong>[15]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>items.X.item_code</code></td></tr><tr><td><code>items.X.product.name</code></td><td><code>items.X.name</code></td></tr><tr><td><code>items.X.quantity</code></td><td><code>items.X.qty</code></td></tr><tr><td><code>items.X.product.price</code></td><td><code>items.X.price</code></td></tr><tr><td><code>items.X.product.category_id</code></td><td><code>items.X.cat</code></td></tr><tr><td><code>Custom Event Properties</code></td><td><code>[Custom Property Name]</code> <strong>[16]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** See [Configuration](the-trade-desk-conversions-api.md#configuration) for more details on mandatory properties.\
&#xNAN;**\[1]** See [`Event Remapping`](the-trade-desk-conversions-api.md#configuration) for more details.\
&#xNAN;**\[2]** The device advertising identifier for Android, iOS or Windows device.\
&#xNAN;**\[3]** The device advertising identifier for Android device. This is only set if `Device OS` "Smart Mapping" field is set with `Android` (case insensitive).\
&#xNAN;**\[4]** The device advertising identifier for iOS device. This is only set if `Device OS` "Smart Mapping" field is set with `iOS` (case insensitive).\
&#xNAN;**\[5]** The device advertising identifier for Windows device. This is only set if `Device OS` "Smart Mapping" field is set with `Windows` (case insensitive).\
&#xNAN;**\[6]** The Trade Desk 36-character GUID (including dashes) for this user.\
&#xNAN;**\[7]** The encrypted UID2 token, also known as an advertising token. This token is case-sensitive. Tokens are generated and managed using UID2 APIs. More details on the UID2 API/endpoints are available following this [LINK](https://unifiedid.com/docs/endpoints/summary-endpoints).\
&#xNAN;**\[8] T**he encrypted EUID token, also known as an advertising token. This token is case-sensitive. More details on the Unified IDs are available following this [LINK](https://partner.thetradedesk.com/v3/portal/data/doc/UnifiedIDs#id-types).\
&#xNAN;**\[9]** The 49-character or 70-character RampID (previously known as IdentityLink). This must be a RampID from LiveRamp that is mapped specifically for The Trade Desk. More details about mapping a RampID are available following this [LINK](https://sidecar.readme.io/docs/getting-started).\
&#xNAN;**\[10]** A flag that indicates whether the event is attributed to The Trade Desk. If set to <mark style="color:blue;">`true`</mark> (boolean), The Trade Desk attributes the event to the specified impression identifier (See <mark style="color:blue;">`data.0.imp`</mark> ), bypasses The Trade Desk attribution models, and aligns attribution results with those delivered by the partner to advertisers.\
&#xNAN;**\[11]** A 36-character string (including dashes) that serves as the unique identifier for the impression to which the event is attributed.\
&#xNAN;**\[12]** A flag that indicates whether the event is a view-through conversion.\
&#xNAN;**\[13]** This can be one of the following:`GDPR`,`CCPA`or`GPP`depending on the privacy regulation that applies. This is only included if <mark style="color:blue;">`is_applicable`</mark> and <mark style="color:blue;">`consent_string`</mark> are also set. More details are available by following this [LINK](https://api.thetradedesk.com/v3/portal/data/doc/DataConversionEventsApi#properties-privacy).\
&#xNAN;**\[14]** Indicates if the value specified in <mark style="color:blue;">`privacy_type`</mark> is applicable. This either <mark style="color:blue;">`true`</mark> (or <mark style="color:blue;">`1`</mark> ) or <mark style="color:blue;">`false`</mark> (or <mark style="color:blue;">`0`</mark> ), boolean or integer type. This is only included if <mark style="color:blue;">`privacy_type`</mark> and <mark style="color:blue;">`consent_string`</mark> are also set. More details are available by following this [LINK](https://api.thetradedesk.com/v3/portal/data/doc/DataConversionEventsApi#properties-privacy).\
&#xNAN;**\[15]** The user's TCF consent string. This is only included if <mark style="color:blue;">`privacy_type`</mark> and <mark style="color:blue;">`is_applicable`</mark> are also set. More details are available by following this [LINK](https://api.thetradedesk.com/v3/portal/data/doc/DataConversionEventsApi#properties-privacy).\
&#xNAN;**\[16]** See <mark style="color:blue;">`Custom Event Properties`</mark> in [Configuration ](the-trade-desk-conversions-api.md#configuration)for more details on how you can bridge custom properties to The Trade Desk.
{% endhint %}
