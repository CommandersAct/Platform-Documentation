# Exactag

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Exactag](https://exactag.com/) is a marketing performance platform specializing in multi-touch attribution and marketing mix modeling. Using this destination you can enable server-side tracking to send events to Exactag.

## Key features

The Exactag destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) model covers Exactag's events, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Event mapping**: change standard mapping between Exactag events and yours.

## Destination setup

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Campaign Code</code></td><td><em><strong><code>Required</code></strong></em><br>Encrypted campaign code.</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping between Exactag events and your events or add new mappings.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Send custom properties related to events.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Exactag Events (sitegroup) |
| --------------------- | -------------------------- |
| `[Any Event]`         | `[Any Event]` **\[1]**     |

{% hint style="info" %}
**1.** Your same event name is sent to Exactag as <mark style="color:blue;">`sitegroup`</mark>  . See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](exactag.md#configuration) to change the standard mapping based on your needs.
{% endhint %}

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.
{% endhint %}

{% hint style="warning" %}
For optin users (See property `optout`), at least one of the following user identifier properties is required:

• `Partner User Identifier` (`euk`)\
• `Exactag User Key` (`uk`)\
• `Device Mobile Identifier` (`did`)

If you need to use Exactag's "Anonymous Attribution", the property `Group Key` (`gk`) is required.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th width="361">Smart Mapping Field</th><th width="423">Commanders Act Default Properties</th><th width="393">Exactag Properties</th></tr></thead><tbody><tr><td><code>-</code></td><td><code>Campaign Code</code></td><td><code>campaign</code> <strong>[*]</strong></td></tr><tr><td><code>-</code></td><td><p><code>Event Mapping</code></p><p><code>event_name</code></p></td><td><code>sitegroup</code> <strong>[*][1]</strong></td></tr><tr><td><code>Session Number</code></td><td><code>context.device.lifecycle.session_number</code></td><td><code>sescount</code> <strong>[*][2]</strong></td></tr><tr><td><code>Event Number</code></td><td><code>context.event_id</code></td><td><code>sesevent</code> <strong>[*][3]</strong></td></tr><tr><td><code>Partner User Identifier</code></td><td><code>user.consistent_anonymous_id</code></td><td><code>euk</code> <strong>[4]</strong></td></tr><tr><td><code>Exactag User Key</code></td><td><code>partners.exactag.user_key</code></td><td><code>uk</code> <strong>[4][5]</strong></td></tr><tr><td><code>Device Mobile Identifier</code></td><td><code>context.device.advertising_id</code></td><td><code>did</code> <strong>[4]</strong></td></tr><tr><td><code>Group Key</code></td><td><code>partners.exactag.group_key</code></td><td><code>gk</code> <strong>[6]</strong></td></tr><tr><td><code>Optout</code></td><td><code>partners.exactag.optout</code></td><td><code>optout</code> <strong>[7]</strong></td></tr><tr><td><code>Optin</code></td><td><code>partners.exactag.optin</code></td><td><code>optin</code> <strong>[8]</strong></td></tr><tr><td><code>Transaction Id</code></td><td><code>id</code></td><td><code>orderid</code> <strong>[9]</strong></td></tr><tr><td><code>Commission Level</code></td><td><code>partners.exactag.level</code></td><td><code>level</code></td></tr><tr><td><code>User Identifier</code></td><td><code>user.id</code></td><td><code>customerid</code> <strong>[10]</strong></td></tr><tr><td><code>Transaction Value</code></td><td><code>value</code></td><td><code>totalprice</code></td></tr><tr><td><code>Page URL</code></td><td><code>context.page.url</code></td><td><p><code>protocol</code> <strong>[11]</strong></p><p><code>host</code> <strong>[11]</strong></p><p><code>site</code> <strong>[11]</strong></p><p><code>search</code> <strong>[11]</strong></p></td></tr><tr><td><code>Page Referrer</code></td><td><code>context.page.referrer</code></td><td><code>referrer</code> <strong>[12]</strong></td></tr><tr><td><code>Device IP</code></td><td><code>context.device.ip</code></td><td><code>ipaddress</code> <strong>[13]</strong></td></tr><tr><td><code>Device User Agent</code></td><td><code>context.device.user_agent</code></td><td><code>useragent</code> <strong>[14]</strong></td></tr><tr><td><code>Session Identifier</code></td><td><code>context.device.lifecycle.session_id</code></td><td><code>sessionid</code> <strong>[15]</strong></td></tr><tr><td><code>Consent</code></td><td><code>partners.exactag.consent</code></td><td><code>consent</code> <strong>[16]</strong></td></tr><tr><td><code>IAB GDPR Consent</code></td><td><code>partners.exactag.consent_string</code></td><td><code>consent_string</code> <strong>[17]</strong></td></tr><tr><td><code>Browser</code></td><td><code>partners.exactag.browser</code></td><td><code>browser</code> <strong>[18]</strong></td></tr><tr><td><code>Operating System</code></td><td><code>partners.exactag.os</code></td><td><code>os</code> <strong>[18]</strong></td></tr><tr><td><code>Operating System Version</code></td><td><code>partners.exactag.os_ver</code></td><td><code>os_ver</code> <strong>[18]</strong></td></tr><tr><td><code>Language</code></td><td><code>partners.exactag.lang</code></td><td><code>lang</code> <strong>[18]</strong></td></tr><tr><td><code>Device Type</code></td><td><code>partners.exactag.device_type</code></td><td><code>device_type</code> <strong>[18]</strong></td></tr><tr><td><code>Device Name</code></td><td><code>partners.exactag.device_name</code></td><td><code>device_name</code> <strong>[18]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\*** Mandatory property.\
**1.** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](exactag.md#configuration) to change the standard mapping base on your needs.\
**2.** Session number from <mark style="color:blue;">`1`</mark> to <mark style="color:blue;">`x`</mark>  (<mark style="color:blue;">`1`</mark> : new visitor, <mark style="color:blue;">`>1`</mark> : recurring visitor).\
**3.** Event number from <mark style="color:blue;">`1`</mark> to <mark style="color:blue;">`x`</mark> (<mark style="color:blue;">`1`</mark> : first page impression in this session).\
**4.** See [Fields mappings](exactag.md#field-mappings) for more details on how Exactag identifies users.\
**5.** Exactags unique identifier for the person or device. This value must be a valid md5 hash.\
**6.** A unique identifier for an anonymous group of multiple users. This value must be a valid md5 hash combined with the group expire timestamp (urlencoded or base64url encoded value). Mandatory for "Anonymous Attribution".\
**7.** If set to <mark style="color:blue;">`0`</mark> or missing, the request will be treated as the user has opted in. Set with <mark style="color:blue;">`1`</mark> if the user has opted out.\
**8.** If the campaign requires an optin, as internal configuration, then <mark style="color:blue;">`optin=0`</mark> or no parameter passed will be treated as an optout. <mark style="color:blue;">`optin=1`</mark> is required for normal processing. If the campaign has no setting, then optin can be ignored and <mark style="color:blue;">`optin=1`</mark> will be assumed.\
**9.** Used for deduplication.\
**10.** Used for cross device.\
**11.** Value retrieved from <mark style="color:blue;">`Page URL`</mark> .\
**12.** Can be anonymized by sending only the referral domain.\
**13.** Required for geo location information. Optional, for for opted out users, if geo location information is not neede.\
**14.** Optional if device information is not desired. It can be anonymized by sending only extracted values. See "Smart Mapping" fields: <mark style="color:blue;">`Browser`</mark> , <mark style="color:blue;">`Operating System`</mark> , <mark style="color:blue;">`Operating System Version`</mark> , <mark style="color:blue;">`Language`</mark> , <mark style="color:blue;">`Device Type`</mark> and <mark style="color:blue;">`Device Name`</mark> .\
**15.** Optional for opted out users.\
**16.** JSON object for type or partner based consent.\
**17.** IAB GDPR consent string.\
**18.** This can be used to send anonymized extracted values instead of setting a value in <mark style="color:blue;">`Device User Agent`</mark>  .
{% endhint %}
