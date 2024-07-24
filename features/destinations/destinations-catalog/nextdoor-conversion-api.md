# Nextdoor Conversion API

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Nextdoor](https://nextdoor.com) operates a hyperlocal social networking service for neighborhoods.\
Using this destination you can send marketing data in the form of events or conversions to Nextdoor and get a more complete picture of their advertising outcomes on Nextdoor. This is based on [Nextdoor Conversion API](https://adsmanager.help.nextdoor.com/namhelpcenter/s/article/About-the-Nextdoor-Conversion-API?language=en\_US).

## Key features

The Nextdoor Conversion API destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) matches [Nextdoor events](https://adsmanager.help.nextdoor.com/namhelpcenter/s/article/Conversion-API-request-parameters?language=en\_US), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Event mapping**: change standard mapping between Nextdoor events and yours or add new mappings.&#x20;
* **Support for multi-item data**: information included in the [item](https://doc.commandersact.com/developers/tracking/events-reference#item) array is dispatched to Nextdoor.
* **Automatic hashing**: information is automatically hashed matching Nextdoor specifications.

## Destination setup

{% hint style="info" %}
Before configuring this destination, you need access to [Nextdoor Ads Manager](https://ads.nextdoor.com).
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><em><strong><code>Required</code></strong></em>  <br>Your NAM advertiser identifier in <a href="https://ads.nextdoor.com/v2/login">Nextdoor Ads Manager</a>. More details are available by following this <a href="https://adsmanager.help.nextdoor.com/namhelpcenter/s/article/Conversion-API-request-parameters?language=en_US">LINK</a> (See <code>client_id</code>).</td></tr><tr><td><code>Access Token</code></td><td><em><strong><code>Required</code></strong></em>  <br>Your access token identifier as generated by accessing <a href="https://ads.nextdoor.com/v2/login">Nextdoor Ads Manager</a>. More details are available by following this <a href="https://adsmanager.help.nextdoor.com/namhelpcenter/s/article/About-the-Nextdoor-Conversion-API?language=en_US&#x26;parentTab=Campaign-performance">LINK</a>.</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping between Nextdoor's events and yours or add new mappings. Nextdoor event names must be one of the following: <code>conversion</code>, <code>lead</code>, <code>purchase</code>, <code>sign_up</code> and <code>custom_conversion_X</code>, where <code>X</code> is a number from 1 to 10.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Nextdoor Events                |
| --------------------- | ------------------------------ |
| `purchase`            | `purchase`                     |
| `generate_lead`       | `lead`                         |
| `sign_up`             | `sign_up`                      |
| `[Any Event]`         | `[Any Allowed Event]` **\[1]** |

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](nextdoor-conversion-api.md#configuration) for more details.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table><thead><tr><th width="440.6685580062746">Commanders Act Properties</th><th>Nextdoor Properties</th></tr></thead><tbody><tr><td><code>Advertiser Id</code></td><td><code>client_id</code></td></tr><tr><td>(<code>event_name</code>)</td><td><code>event_name</code> <strong>[1]</strong></td></tr><tr><td><code>context.event_id</code></td><td><code>event_id</code></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>event_time</code> <strong>[2]</strong></td></tr><tr><td><code>partners.nextdoor.event_timezone</code></td><td><code>event_timezone</code></td></tr><tr><td><code>partners.nextdoor.action_source</code></td><td><code>action_source</code> <strong>[3]</strong></td></tr><tr><td><code>context.page.url</code></td><td><code>action_source_url</code></td></tr><tr><td><code>partners.nextdoor.delivery_optimization</code></td><td><code>delivery_optimization</code></td></tr><tr><td><code>partners.nextdoor.test_event</code></td><td><code>test_event</code></td></tr><tr><td><code>user.email</code></td><td><code>email</code> <strong>[4][5][6]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>phone_number</code> <strong>[4][6][7]</strong></td></tr><tr><td><code>user.firstname</code></td><td><code>first_name</code> <strong>[4][5][6]</strong></td></tr><tr><td><code>user.lastname</code></td><td><code>last_name</code> <strong>[4][5][6]</strong></td></tr><tr><td><code>user.birthdate</code></td><td><code>date_of_birth</code> <strong>[4][6][8]</strong></td></tr><tr><td><code>user.street</code></td><td><code>street_address</code> <strong>[4][6]</strong></td></tr><tr><td><code>user.city</code></td><td><code>city</code> <strong>[4][6][9]</strong></td></tr><tr><td><code>user.state_short</code></td><td><code>state</code> <strong>[4][6][10]</strong></td></tr><tr><td><code>user.zipcode</code></td><td><code>zip_code</code> <strong>[4][6][11]</strong></td></tr><tr><td><code>user.country</code></td><td><code>country</code> <strong>[4][6][12]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>client_ip_address</code> <strong>[4]</strong></td></tr><tr><td><code>partners.nextdoor.pixel_id</code></td><td><code>pixel_id</code> <strong>[4][13]</strong></td></tr><tr><td><code>partners.nextdoor.click_id</code></td><td><code>click_id</code> <strong>[4][14]</strong></td></tr><tr><td><code>id</code></td><td><code>order_id</code> <strong>[15]</strong></td></tr><tr><td><code>currency</code> + <code>value</code></td><td><code>order_value</code> <strong>[15]</strong></td></tr><tr><td><code>partners.nextdoor.delivery_category</code></td><td><code>delivery_category</code> <strong>[15]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>id</code>  <strong>[16]</strong></td></tr><tr><td><code>items.X.product.name</code></td><td><code>content_name</code> <strong>[16]</strong></td></tr><tr><td><code>items.X.product.price</code></td><td><code>item_price</code> <strong>[16]</strong></td></tr><tr><td><code>items.X.quantity</code></td><td><code>quantity</code> <strong>[16]</strong></td></tr><tr><td><code>context.app.namespace</code></td><td><code>app_id</code> <strong>[17]</strong></td></tr><tr><td><code>context.device.ad_tracking_enabled</code></td><td><code>app_tracking_enabled</code> <strong>[17]</strong></td></tr><tr><td><code>context.device.os.name</code></td><td><code>platform</code> <strong>[17]</strong></td></tr><tr><td><code>context.app.version</code></td><td><code>app_version</code> <strong>[17]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](nextdoor-conversion-api.md#configuration) for more details.\
**\[2]** Automatically converted in [ISO 8601 format](https://en.wikipedia.org/wiki/ISO\_8601).\
**\[3]** When Smart Mapping  <mark style="color:blue;">Action Source</mark> is not set, this value is automatically set by using the following information in the presented priority order: 1. Smart Mapping field <mark style="color:blue;">`Experience Type`</mark>  2. property <mark style="color:blue;">`context.app`</mark>  3. Smart Mapping field <mark style="color:blue;">`Conversion Type`</mark> .\
**\[4]** Set in <mark style="color:blue;">`customer`</mark>  object.\
**\[5]** Pre-hashed format in lower case.\
**\[6]** Automatically hashed via SHA256 when provided in clear text.\
**\[7]** Pre-hashed format should consist of exactly ten digits, devoid of any special characters or international country codes.\
**\[8]** Pre-hashed format <mark style="color:blue;">`YYYYMMDD`</mark> .\
**\[9]** Pre-hashed format in lower case, no special characters.\
**\[10]** Pre-hashed format in lowercase and as [two letter ANSI abbreviation code](https://en.wikipedia.org/wiki/Federal\_Information\_Processing\_Standard\_state\_code).\
**\[11]** Pre-hashed format with five digits for US.\
**\[12]** Pre-hashed format as [two-character ISO 3166-1 alpha-2 code](https://en.wikipedia.org/wiki/ISO\_3166-1\_alpha-2).\
**\[13]** Allows Nextdoor to deduplicate events for an advertiser that sends events via both the CAPI and the pixel making it soft required for multiple pixel implementation.\
**\[14]** This is the same as <mark style="color:blue;">`ndclid`</mark>  parameter attached to clickthrough URL.\
**\[15]** Set in <mark style="color:blue;">`custom`</mark> .\
**\[16]** Set in <mark style="color:blue;">`custom.product_context.X`</mark> .\
**\[17]** Set in <mark style="color:blue;">`app`</mark> .
{% endhint %}