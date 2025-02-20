# Reddit Conversions API

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Reddit](https://redditinc.com/) is a social news aggregation, content rating, and forum social network.\
[Reddit Conversions API](https://ads-api.reddit.com/docs/v2/#tag/Conversions) (CAPI) is a server-side solution to share your web conversion data directly with Reddit so you can measure and optimize your performance campaigns.

## Key features

The Reddit Conversions API destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) model covers [Reddit's event types and custom events](https://ads-api.reddit.com/docs/v2/#tag/Conversions/paths/~1api~1v2.0~1conversions~1events~1{account_id}/post), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Event mapping**: change standard mapping between Reddit events and yours or add new mappings.
* **Support for multi-item data**: information included in the [item](https://doc.commandersact.com/developers/tracking/events-reference#item) array is dispatched to Reddit.

## Destination setup

{% hint style="info" %}
Before configuring this destination, you need access to [Reddit Ads Manager](https://ads.reddit.com/).
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Authentication</code></td><td><em><strong><code>Required</code></strong></em> <br>Your credentials with Reddit Campaign Manager as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>RedditAds</code></td></tr><tr><td><code>Access Token</code></td><td><em><strong><code>Required</code></strong></em>  <br>Your access token identifier as generated by accessing <a href="https://ads.nextdoor.com/v2/login">Nextdoor Ads Manager</a>. More details are available by following this <a href="https://adsmanager.help.nextdoor.com/namhelpcenter/s/article/About-the-Nextdoor-Conversion-API?language=en_US&#x26;parentTab=Campaign-performance">LINK</a>.</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping between Reddit's events and yours or add new mappings.</td></tr><tr><td><code>Test Mode</code></td><td>Enable this only while testing your settings. <strong>Disable in production!</strong></td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Reddit Events          |
| --------------------- | ---------------------- |
| `add_to_cart`         | `AddToCart`            |
| `add_to_wishlist`     | `AddToWishlist`        |
| `generate_lead`       | `Lead`                 |
| `page_view`           | `PageVisit`            |
| `purchase`            | `Purchase`             |
| `search`              | `Search`               |
| `sign_up`             | `SignUp`               |
| `view_item`           | `ViewContent`          |
| `[Any Event]`         | `[Any Event]` **\[1]** |

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](reddit-conversions-api.md#configuration) for more details.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
All Reddit properties are set in the path <mark style="color:blue;">`events[0]`</mark> <mark style="color:blue;"></mark><mark style="color:blue;">.</mark>
{% endhint %}

{% hint style="warning" %}
At least one of the following Reddit properties is required:\
• <mark style="color:blue;">`click_id`</mark> \*\
• <mark style="color:blue;">`uuid`</mark> \*\
• <mark style="color:blue;">`email`</mark> \*\
• <mark style="color:blue;">`ip_address`</mark> + <mark style="color:blue;">`user_agent`</mark> + <mark style="color:blue;">`width`</mark> + <mark style="color:blue;">`height`</mark> \*\
• <mark style="color:blue;">`idfa`</mark> or <mark style="color:blue;">`aaid`</mark> \
• <mark style="color:blue;">`external_id`</mark>\
Sending more properties will improve attribution accuracy and performance.\
\* Recommended properties.
{% endhint %}

<table><thead><tr><th width="396.6685580062746">Commanders Act Properties</th><th>Reddit Properties</th></tr></thead><tbody><tr><td><code>context.event_timestamp</code></td><td><code>event_at</code> <strong>[1]</strong></td></tr><tr><td><code>Event Mapping</code></td><td><code>event_type.custom_event_name</code></td></tr><tr><td><code>partners.reddit.click_id</code></td><td><code>click_id</code> <strong>[2]</strong></td></tr><tr><td><code>id</code></td><td><code>conversion_id</code> <strong>[3]</strong></td></tr><tr><td><code>value</code></td><td><code>value_decimal</code> <strong>[3]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code> <strong>[3]</strong></td></tr><tr><td><code>items</code></td><td><code>item_count</code> <strong>[3][4]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>products.X.id</code> <strong>[3]</strong></td></tr><tr><td><code>items.X.product.name</code></td><td><code>products.X.name</code> <strong>[3]</strong></td></tr><tr><td><p><code>items.X.product.category_1</code></p><p><code>items.X.product.category_2</code></p><p><code>items.X.product.category_3</code></p><p><code>items.X.product.category_4</code></p><p><code>items.X.product.category_5</code></p></td><td><code>products.X.category</code> <strong>[3][5]</strong></td></tr><tr><td><code>context.device.advertising_id</code></td><td><p><code>idfa</code> <strong>[6][7][8]</strong></p><p><code>aaid</code> <strong>[6][7][8]</strong></p></td></tr><tr><td><code>user.email</code></td><td><code>email</code> <strong>[6][8]</strong></td></tr><tr><td><code>user.id</code></td><td><code>external_id</code> <strong>[6][8]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>ip_address</code> <strong>[6][8]</strong></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>user_agent</code> <strong>[6]</strong></td></tr><tr><td><code>parters.reddit.uuid</code></td><td><code>uuid</code> <strong>[6]</strong></td></tr><tr><td><code>context.device.ad_tracking_enabled</code></td><td><code>opt_out</code> <strong>[6]</strong></td></tr><tr><td><code>user.country</code></td><td><code>country</code> <strong>[9]</strong></td></tr><tr><td><code>user.region</code></td><td><code>region</code> <strong>[9]</strong></td></tr><tr><td><code>parters.reddit.data_proc_mode</code></td><td><code>modes[0]</code> <strong>[9][10]</strong></td></tr><tr><td><code>context.device.screen.width</code></td><td><code>width</code> <strong>[11]</strong></td></tr><tr><td><code>context.device.screen.height</code></td><td><code>height</code> <strong>[11]</strong></td></tr><tr><td><code>Test Mode</code></td><td><code>test_mode</code> <strong>[12]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Timestamp is converted to the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format.\
&#xNAN;**\[2]** If a value is not provided, this is retrieved from the page URL by parsing the parameter <mark style="color:blue;">`rdt_cid`</mark> .\
&#xNAN;**\[3]** Set in the <mark style="color:blue;">`event_metadata`</mark>  field.\
&#xNAN;**\[4]** Based on the length of the provided "Smart Mapping" field <mark style="color:blue;">`Item List`</mark>  .\
&#xNAN;**\[5]** All provided categories are separated by the "greater than" character ( `>` ).\
&#xNAN;**\[6]** Set in the <mark style="color:blue;">`user`</mark>  field.\
&#xNAN;**\[7]** These properties require a proper value, <mark style="color:blue;">`iOS`</mark>  or <mark style="color:blue;">`Android`</mark> , for the "Smart Mapping" field <mark style="color:blue;">`Device Platform`</mark>  .\
&#xNAN;**\[8]** Automatically hashed via SHA256 when provided in clear text.\
&#xNAN;**\[9]** Set in the <mark style="color:blue;">`user.data_processing_options`</mark>  field.\
&#xNAN;**\[10]** Supported value: <mark style="color:blue;">`LDU`</mark> .\
&#xNAN;**\[11]** Set in the <mark style="color:blue;">`user.screen_dimensions`</mark>  field.\
&#xNAN;**\[12]** Set in the base path.
{% endhint %}
