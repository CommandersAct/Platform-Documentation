# Reddit Conversions API

[Reddit](https://redditinc.com/) is a social news aggregation, content rating, and forum social network.\
Using this destination you can leverage [Reddit Conversions API](https://ads-api.reddit.com/docs/v3/operations/Post%20Conversion%20Events) (CAPI) to share your web conversion data directly with Reddit so you can measure and optimize your performance campaigns.

## Key features

The Reddit Conversions API destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) model covers [Reddit's event types and custom events](https://ads-api.reddit.com/docs/v2/#tag/Conversions/paths/~1api~1v2.0~1conversions~1events~1{account_id}/post), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Event mapping**: change standard mapping between Reddit events and yours or add new mappings.
* **Support for multi-item data**: information included in the [item](https://doc.commandersact.com/developers/tracking/events-reference#item) array is dispatched to Reddit.
* **Support batch mode**: see <mark style="color:blue;">`Enable batch mode`</mark>  in [Configuration](reddit-conversions-api.md#configuration) for mode details.

## Destination setup

{% hint style="info" %}
Before configuring this destination, you need access to [Reddit Ads Manager](https://ads.reddit.com/).\
[Event deduplication](https://business.reddithelp.com/s/article/event-deduplication) is required if you use the [Reddit pixel](https://business.reddithelp.com/s/article/reddit-pixel) together with this destination. Reddit recommends to pass unique conversion identifiers through its pixel and this destination for all events. More details on Reddit deduplication are available following this [LINK](https://business.reddithelp.com/s/article/event-deduplication).
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Access Token</code></td><td><em><strong><code>Required</code></strong></em><br>Input your access token. You can find it in <a href="https://ads.reddit.com">Reddit Ads</a> by following this <a href="https://ads.reddit.com">LINK</a> and, from the left menu, select <code>Event Manager</code> → <code>Conversions API</code> and click <code>Generate Access Token</code> .</td></tr><tr><td><code>Pixel Id</code></td><td><em><strong><code>Required</code></strong></em><br>Input your pixel identifier. You can find it in <a href="https://ads.reddit.com">Reddit Ads</a> by following this <a href="https://ads.reddit.com">LINK</a> and, from the left menu, select <code>Event Manager</code> .</td></tr><tr><td><code>Enable batch mode</code></td><td>When checked, multiple records are sent, with a single request, instead of one at a time.</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping between Reddit events and yours or add new mappings.</td></tr><tr><td><code>Test Mode</code></td><td>Enable this only while testing your settings. <strong>Disable in production!</strong></td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Reddit Events          |
| --------------------- | ---------------------- |
| `add_to_cart`         | `ADD_TO_CART`          |
| `add_to_wishlist`     | `ADD_TO_WISHLIST`      |
| `generate_lead`       | `LEAD`                 |
| `page_view`           | `PAGE_VISIT`           |
| `purchase`            | `PURCHASE`             |
| `search`              | `SEARCH`               |
| `sign_up`             | `SIGN_UP`              |
| `view_item`           | `VIEW_CONTENT`         |
| `[Any Event]`         | `[Any Event]` **\[1]** |

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](reddit-conversions-api.md#configuration) for more details.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
All Reddit properties are set in the path <mark style="color:blue;">`data.events.X`</mark>  .
{% endhint %}

{% hint style="warning" %}
Reddit recommends sending as many identifiers/match keys as possible to help improve attribution accuracy and improve performance. More details are available following this [LINK ](https://business.reddithelp.com/s/article/about-match-keys).
{% endhint %}

<table><thead><tr><th width="396.6685580062746">Commanders Act Properties</th><th>Reddit Properties</th></tr></thead><tbody><tr><td><code>context.event_timestamp</code></td><td><code>event_at</code></td></tr><tr><td><code>event_name</code></td><td><code>type.tracking_type</code> <strong>[1]</strong></td></tr><tr><td><code>Event Mapping</code>   </td><td><code>type.custom_event_name</code> <strong>[2]</strong></td></tr><tr><td><code>partners.reddit.click_id</code></td><td><code>click_id</code> <strong>[3]</strong></td></tr><tr><td><code>id</code></td><td><code>conversion_id</code> <strong>[4]</strong></td></tr><tr><td><code>value</code></td><td><code>value</code> <strong>[4]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code> <strong>[4]</strong></td></tr><tr><td><code>items</code></td><td><code>item_count</code> <strong>[4][5]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>products.X.id</code> <strong>[4]</strong></td></tr><tr><td><code>items.X.product.name</code></td><td><code>products.X.name</code> <strong>[4]</strong></td></tr><tr><td><p><code>items.X.product.category_1</code></p><p><code>items.X.product.category_2</code></p><p><code>items.X.product.category_3</code></p><p><code>items.X.product.category_4</code></p><p><code>items.X.product.category_5</code></p></td><td><code>products.X.category</code> <strong>[4][6]</strong></td></tr><tr><td><code>context.device.advertising_id</code></td><td><p><code>idfa</code> <strong>[7][8][9]</strong></p><p><code>aaid</code> <strong>[7][8][9]</strong></p></td></tr><tr><td><code>user.email</code></td><td><code>email</code> <strong>[7][9]</strong></td></tr><tr><td><code>user.id</code></td><td><code>external_id</code> <strong>[7][9]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>phone_number</code> <strong>[7][9]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>ip_address</code> <strong>[7][9]</strong></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>user_agent</code> <strong>[7]</strong></td></tr><tr><td><code>parters.reddit.uuid</code></td><td><code>uuid</code> <strong>[7]</strong></td></tr><tr><td><code>user.country</code></td><td><code>country</code> <strong>[10]</strong></td></tr><tr><td><code>user.region</code></td><td><code>region</code> <strong>[10]</strong></td></tr><tr><td><code>parters.reddit.data_proc_mode</code></td><td><code>modes[0]</code> <strong>[10][11]</strong></td></tr><tr><td><code>context.device.screen.width</code></td><td><code>width</code> <strong>[12]</strong></td></tr><tr><td><code>context.device.screen.height</code></td><td><code>height</code> <strong>[12]</strong></td></tr><tr><td><code>Test Mode</code></td><td><code>test_mode</code> <strong>[13]</strong></td></tr></tbody></table>

{% hint style="info" %}
> **\[1]** See [Quick reference](reddit-conversions-api.md#quick-reference) for more details on the standard mapping.\
> &#xNAN;**\[2]** See <mark style="color:blue;">`Reddit event name`</mark>  in <mark style="color:blue;">`Event Mapping`</mark> <mark style="color:$primary;">.</mark>\
> **\[3]** If a value is not provided, this is retrieved from the page URL by parsing the parameter <mark style="color:blue;">`rdt_cid`</mark> .  \
> &#xNAN;**\[4]** Set in the <mark style="color:blue;">`metadata`</mark> field.  \
> &#xNAN;**\[5]** Based on the length of the provided "Smart Mapping" field <mark style="color:blue;">`Item List`</mark> .  \
> &#xNAN;**\[6]** All provided categories are separated by the "greater than" character ( `>` ).  \
> &#xNAN;**\[7]** Set in the <mark style="color:blue;">`user`</mark> field.  \
> &#xNAN;**\[8]** These properties require a proper value, <mark style="color:blue;">`iOS`</mark> or <mark style="color:blue;">`Android`</mark> , for the "Smart Mapping" field <mark style="color:blue;">`Device Platform`</mark> .  \
> &#xNAN;**\[9]** Automatically hashed via SHA256 when provided in clear text.  \
> &#xNAN;**\[10]** Set in the <mark style="color:blue;">`user.data_processing_options`</mark> field.  \
> &#xNAN;**\[11]** Supported value: <mark style="color:blue;">`LDU`</mark> .  \
> &#xNAN;**\[12]** Set in the <mark style="color:blue;">`user.screen_dimensions`</mark> field.\
> &#xNAN;**\[13]** Set in the base path.
{% endhint %}
