# Spotify Conversions API

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Spotify](https://open.spotify.com/) is music streaming service provider. Using this destination you can leverage [Spotify Conversions API](https://adshelp.spotify.com/s/article/Spotify-Conversions-API-US?language=en_US) as tagless attribution tool that allows you to pass online and offline conversion events to Spotify. The Conversions API is designed to provide comprehensive, high-fidelity attribution to help you understand the performance of your campaigns on Spotify.

## Key features

The Spotify Conversions API destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) model covers [Spotify's events](https://developer.spotify.com/documentation/ads-api/guides#capi-setup-guide), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Event mapping**: change standard mapping between Spotify events and yours.
* **Support batch mode**: send multiple events in one single request.

## Destination setup

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Access Token</code></td><td><em><strong><code>Required</code></strong></em><br>Your access token. Generate your token in <a href="https://adsmanager.spotify.com">Spotify Ads Manager</a>, by going to <code>Events</code> → <code>Connect Data Source</code> → <code>Conversions API</code> → <code>Generate Token</code> .</td></tr><tr><td><code>Connection Id</code></td><td><em><strong><code>Required</code></strong></em><br>The connection identifier is a unique key assigned to your organization that allows you to access CAPI when used with the access token. Get your identifier in <a href="https://adsmanager.spotify.com">Spotify Ads Manager</a>, by going to <code>Events</code> → <code>Connect Data Source</code> → <code>Conversions API</code> . When you submit the form, the Spotify UI will show the newly created connection identifier (a UUID).</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping between Spotify events and yours. Accepted values for <code>Spotify event name</code> : <code>VIEW</code>, <code>PRODUCT</code>, <code>CHECK_OUT</code>, <code>ADD_TO_CART</code>, <code>PURCHASE</code>, <code>LEAD</code>, <code>SIGN_UP</code>, <code>CUSTOM_EVENT_1</code>, <code>CUSTOM_EVENT_2</code>, <code>CUSTOM_EVENT_3</code>, <code>CUSTOM_EVENT_4</code> and <code>CUSTOM_EVENT_5</code>.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Spotify Events                   |
| --------------------- | -------------------------------- |
| `add_to_cart`         | `ADD_TO_CART`                    |
| `begin_checkout`      | `CHECK_OUT`                      |
| `generate_lead`       | `LEAD`                           |
| `page_view`           | `VIEW`                           |
| `purchase`            | `PURCHASE`                       |
| `sign_up`             | `SIGN_UP`                        |
| `view_item`           | `Details`                        |
| `[Any Event]`         | `[Any Supported Event]` **\[1]** |

{% hint style="info" %}
**1.** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](spotify-conversions-api.md#configuration) for more details on Spotify supported events.
{% endhint %}

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.
{% endhint %}

{% hint style="warning" %}
At least one of the following "Smart Mapping" fields is required:\
• <mark style="color:blue;">`Device IP`</mark>\
• <mark style="color:blue;">`Device Mobile Identifier`</mark>\
• <mark style="color:blue;">`User Email`</mark>\
• <mark style="color:blue;">`User Phone`</mark>
{% endhint %}

<table data-header-hidden="false" data-header-sticky data-search="true"><thead><tr><th width="361">Smart Mapping Fields</th><th width="423">Commanders Act Default Properties</th><th width="393">Spotify Properties</th></tr></thead><tbody><tr><td><code>-</code></td><td><code>Connection Id</code></td><td><code>capi_connection_id</code> <strong>[*][1]</strong></td></tr><tr><td><code>-</code></td><td><p><code>Event Mapping</code></p><p><code>event_name</code></p></td><td><code>event_name</code> <strong>[*][2][3]</strong></td></tr><tr><td><code>Event Id</code></td><td><code>context.event_id</code></td><td><code>event_id</code> <strong>[*][2][4]</strong></td></tr><tr><td><code>Event Timestamp</code></td><td><code>context.event_timestamp</code></td><td><code>event_time</code> <strong>[*][2][5]</strong></td></tr><tr><td><code>Page URL</code></td><td><code>context.page.url</code></td><td><code>event_source_url</code> <strong>[2]</strong></td></tr><tr><td><code>Device IP</code></td><td><code>context.device.ip</code></td><td><code>ip_address</code> <strong>[6]</strong></td></tr><tr><td><code>Device Mobile Identifier</code></td><td><code>context.device.advertising_id</code></td><td><code>device_id</code> <strong>[6]</strong></td></tr><tr><td><code>User Email</code></td><td><code>user.email</code></td><td><code>hashed_emails.0</code> <strong>[6]</strong></td></tr><tr><td><code>User Phone</code></td><td><code>user.phone</code></td><td><code>hashed_phone_number</code> <strong>[6]</strong></td></tr><tr><td><code>Ccurrency</code></td><td><code>currency</code></td><td><code>currency</code> <strong>[7]</strong></td></tr><tr><td><code>Value</code></td><td><code>value</code></td><td><code>amount</code> <strong>[7]</strong></td></tr><tr><td><code>Content Category</code></td><td><code>partners.spotify.content_name</code></td><td><code>content_category</code> <strong>[7]</strong></td></tr><tr><td><code>Content Name</code></td><td><code>partners.spotify.content_name</code></td><td><code>content_name</code> <strong>[7]</strong></td></tr><tr><td><code>Action Source</code></td><td><code>type</code></td><td><code>action_source</code> <strong>[2][8]</strong></td></tr><tr><td><code>Opt-out Targeting</code></td><td><code>partners.spotify.optout_targeting</code></td><td><code>opt_out_targeting</code> <strong>[2][9]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\*** Mandatory property.\
**1.** See <mark style="color:blue;">`Connection Id`</mark> in [Configuration](spotify-conversions-api.md#configuration). Set in <mark style="color:blue;">`conversion_events`</mark> .\
**2.** Set in <mark style="color:blue;">`conversion_events.evennts.X`</mark> .\
**3.** See [Quick reference](spotify-conversions-api.md#quick-reference) for the standard mapping, and <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](spotify-conversions-api.md#configuration) to change the mapping or add new ones.\
**4.** Default: <mark style="color:blue;">`context.event_id`</mark> .\
**5.** Default: event timestamp.\
**6.** Set in <mark style="color:blue;">`conversion_events.events.X.user_data`</mark> .\
**7.** Set in <mark style="color:blue;">`conversion_events.events.X.event_details`</mark> .\
**8.** Default:\
&#x20;   • set to <mark style="color:blue;">`WEB`</mark> if <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`online`</mark> \
&#x20;   • set to <mark style="color:blue;">`APP`</mark> if <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`app`</mark> or <mark style="color:blue;">`mobile_app`</mark>\
&#x20;   • set to <mark style="color:blue;">`OFFLINE`</mark> if <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`offline`</mark>\
&#x20;   • set to <mark style="color:blue;">`WEB`</mark> if none of the above applies.\
**9.** Accepted values: <mark style="color:blue;">`true`</mark> or <mark style="color:blue;">`false`</mark> (boolean)
{% endhint %}
