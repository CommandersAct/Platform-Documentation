# Branch Events

[Branch](https://www.branch.io/) (formerly known as Branch Metrics) is a mobile software company focused on mobile deep linking and attribution. This integration allows [server-side event tracking](https://help.branch.io/developers-hub/reference/events-api).

## Key features

The Branch Events destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) matches Branch [standard](https://help.branch.io/developers-hub/reference/logstandardevents) and [custom events](https://help.branch.io/developers-hub/reference/logcustomevents), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Refined data**: you can freely push additional information based on your specific needs (E.g. adding custom events and custom event properties).
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Event mapping**: change standard mapping between your partners' events and yours or add new mappings.
* **Support for multi-item data**: information included in the [item](https://doc.commandersact.com/developers/tracking/events-reference#item) array is dispatched to Branch.

## Destination setup

{% hint style="info" %}
Before configuring this destination, you need to create a [Branch Dashboard](https://dashboard.branch.io/).
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Branch Key</code></td><td><em><strong><code>Required</code></strong></em><br>Branch Key of the originating app and obtained by accessing your <a href="https://help.branch.io/using-branch/docs/profile-settings">Account Settings</a>.</td></tr><tr><td><code>Content Schema</code></td><td>Category/Schema for the included content.</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>Branch property name</code> and adding the field name holding the value in <code>Your event property</code>.</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping (See <a href="branch-events.md#quick-reference">Quick reference</a>) between Branch's events and yours or add new mappings.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | Branch Events           |
| ---------------------- | ----------------------- |
| `achieve_level`        | `ACHIEVE_LEVEL`         |
| `add_payment_info`     | `ADD_PAYMENT_INFO`      |
| `add_to_cart`          | `ADD_TO_CART`           |
| `add_to_wishlist`      | `ADD_TO_WISHLIST`       |
| `begin_checkout`       | `INITIATE_PURCHASE`     |
| `click_ad`             | `CLICK_AD`              |
| `complete_stream`      | `COMPLETE_STREAM`       |
| `complete_tutorial`    | `COMPLETE_TUTORIAL`     |
| `generate_lead`        | `COMPLETE_REGISTRATION` |
| `initiate_stream`      | `INITIATE_STREAM`       |
| `invite`               | `INVITE`                |
| `login`                | `LOGIN`                 |
| `purchase`             | `PURCHASE`              |
| `rate`                 | `RATE`                  |
| `search`               | `SEARCH`                |
| `share`                | `SHARE`                 |
| `start_trial`          | `START_TRIAL`           |
| `spend_credits`        | `SPEND_CREDITS`         |
| `subscribe`            | `SUBSCRIBE`             |
| `unlock_achievement`   | `UNLOCK_ACHIEVEMENT`    |
| `view_ad`              | `VIEW_AD`               |
| `view_cart`            | `VIEW_CART`             |
| `view_item`            | `VIEW_ITEM`             |
| `view_items`           | `VIEW_ITEMS`            |
| `[Any Event]` **\[1]** | `[Any Event]` **\[1]**  |

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](branch-events.md#configuration) for more details.
{% endhint %}

## Field mappings

{% hint style="warning" %}
At least one of the following must be included:\
• <mark style="color:blue;">`developer_identity`</mark>\
• <mark style="color:blue;">`browser_fingerprint_id`</mark>\
• <mark style="color:blue;">`idfa`</mark> OR <mark style="color:blue;">`idfv`</mark> (IF <mark style="color:blue;">`os`</mark> = <mark style="color:blue;">`iOS`</mark> )\
• <mark style="color:blue;">`aaid`</mark> OR <mark style="color:blue;">`android_id`</mark> (IF <mark style="color:blue;">`os`</mark> = <mark style="color:blue;">`Android`</mark> )
{% endhint %}

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

<table><thead><tr><th width="404.6685580062746">Commanders Act Properties</th><th>Branch Properties</th></tr></thead><tbody><tr><td><code>Branch Key</code></td><td><code>branch_key</code></td></tr><tr><td><code>partners.branch.event_alias</code></td><td><code>customer_event_alias</code></td></tr><tr><td><code>context.device.os.name</code></td><td><code>os</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.os.version</code></td><td><code>os_version</code> <strong>[1]</strong></td></tr><tr><td><code>partners.branch.env</code></td><td><code>environment</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.advertising_id</code></td><td><p><code>idfa</code> <strong>[1][5]</strong></p><p><code>aaid</code> <strong>[1][6]</strong></p></td></tr><tr><td><code>partners.branch.hardware_id</code></td><td><code>android_id</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.idfv</code></td><td><code>idfv</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.ad_tracking_enabled</code></td><td><code>limit_ad_tracking</code> <strong>[1][7]</strong></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>user_agent</code> <strong>[1]</strong></td></tr><tr><td><code>partners.branch.fingerprint_id</code></td><td><code>browser_fingerprint_id</code> <strong>[1]</strong></td></tr><tr><td><code>context.page.url</code></td><td><code>http_origin</code> <strong>[1]</strong></td></tr><tr><td><code>context.page.referrer</code></td><td><code>http_referrer</code> <strong>[1]</strong></td></tr><tr><td><code>user.id</code></td><td><code>developer_identity</code> <strong>[1]</strong></td></tr><tr><td><code>user.country</code></td><td><code>country</code> <strong>[1]</strong></td></tr><tr><td><code>context.page.lang</code></td><td><code>language</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>ip</code> <strong>[1]</strong></td></tr><tr><td><code>partners.branch.local_ip</code></td><td><code>local_ip</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.manufacturer</code></td><td><code>brand</code> <strong>[1]</strong></td></tr><tr><td><code>partners.branch.device_token</code></td><td><code>randomized_device_token</code> <strong>[1]</strong></td></tr><tr><td><code>context.app.version</code></td><td><code>app_version</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.model</code></td><td><code>model</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.screen.density</code></td><td><code>screen_dpi</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.screen.width</code></td><td><code>screen_width</code> <strong>[1]</strong></td></tr><tr><td><code>context.device.screen.height</code></td><td><code>screen_height</code> <strong>[1]</strong></td></tr><tr><td><code>partners.branch.dma_eea</code></td><td><code>dma_eea</code> <strong>[1]</strong></td></tr><tr><td><code>partners.branch.dma_ad_pers</code></td><td><code>dma_ad_personalization</code> <strong>[1]</strong></td></tr><tr><td><code>partners.branch.dma_ad_user_data</code></td><td><code>dma_ad_user_data</code> <strong>[1]</strong></td></tr><tr><td><code>id</code></td><td><code>transaction_id</code> <strong>[2]</strong></td></tr><tr><td><code>revenue</code></td><td><code>revenue</code> <strong>[2]</strong></td></tr><tr><td><code>currency</code></td><td><code>currency</code> <strong>[2]</strong></td></tr><tr><td><code>shipping_amount</code></td><td><code>shipping</code> <strong>[2]</strong></td></tr><tr><td><code>tax_amount</code></td><td><code>tax</code> <strong>[2]</strong></td></tr><tr><td><code>coupon</code></td><td><code>coupon</code> <strong>[2]</strong></td></tr><tr><td><code>type</code></td><td><code>affiliation</code> <strong>[2]</strong></td></tr><tr><td><code>event_name</code></td><td><code>description</code> <strong>[2]</strong></td></tr><tr><td><code>search_query</code></td><td><code>search_term</code> <strong>[2]</strong></td></tr><tr><td><code>Content Schema</code></td><td><code>$content_schema</code> <strong>[3]</strong></td></tr><tr><td><code>item_title</code> <strong>[4]</strong></td><td><code>$og_title</code> <strong>[3]</strong></td></tr><tr><td><code>product.image_url</code> <strong>[4]</strong></td><td><code>$og_image_url</code> <strong>[3]</strong></td></tr><tr><td><code>product.canonical_identifier</code> <strong>[4]</strong></td><td><code>$canonical_identifier</code> <strong>[3]</strong></td></tr><tr><td><code>product.publicly_indexable</code> <strong>[4]</strong></td><td><code>$publicly_indexable</code> <strong>[3]</strong></td></tr><tr><td><code>product.locally_indexable</code> <strong>[4]</strong></td><td><code>$locally_indexable</code> <strong>[3]</strong></td></tr><tr><td><code>product.price</code> <strong>[4]</strong></td><td><code>$price</code> <strong>[3]</strong></td></tr><tr><td><code>quantity</code> <strong>[4]</strong></td><td><code>$quantity</code> <strong>[3]</strong></td></tr><tr><td><code>id</code> <strong>[4]</strong></td><td><code>$sku</code> <strong>[3]</strong></td></tr><tr><td><code>product.name</code> <strong>[4]</strong></td><td><code>$product_name</code> <strong>[3]</strong></td></tr><tr><td><code>product.brand</code> <strong>[4]</strong></td><td><code>$product_brand</code> <strong>[3]</strong></td></tr><tr><td><code>product.category_1</code> <strong>[4]</strong></td><td><code>$product_category</code> <strong>[3]</strong></td></tr><tr><td><code>variant</code> <strong>[4]</strong></td><td><code>$product_variant</code> <strong>[3]</strong></td></tr><tr><td><code>product.rating_average</code> <strong>[4]</strong></td><td><code>$rating_average</code> <strong>[3]</strong></td></tr><tr><td><code>product.rating_count</code> <strong>[4]</strong></td><td><code>$rating_count</code> <strong>[3]</strong></td></tr><tr><td><code>product.rating_max</code> <strong>[4]</strong></td><td><code>$rating_max</code> <strong>[3]</strong></td></tr><tr><td><code>product.creation_timestamp</code> <strong>[4]</strong></td><td><code>$creation_timestamp</code> <strong>[3]</strong></td></tr><tr><td><code>product.exp_date</code> <strong>[4]</strong></td><td><code>$exp_date</code> <strong>[3]</strong></td></tr><tr><td><code>product.keywords</code> <strong>[4]</strong></td><td><code>$keywords</code> <strong>[3]</strong></td></tr><tr><td><code>product.address_street</code> <strong>[4]</strong></td><td><code>$address_street</code> <strong>[3]</strong></td></tr><tr><td><code>product.address_city</code> <strong>[4]</strong></td><td><code>$address_city</code> <strong>[3]</strong></td></tr><tr><td><code>product.address_region</code> <strong>[4]</strong></td><td><code>$address_region</code> <strong>[3]</strong></td></tr><tr><td><code>product.address_country</code> <strong>[4]</strong></td><td><code>$address_country</code> <strong>[3]</strong></td></tr><tr><td><code>product.address_postal_code</code> <strong>[4]</strong></td><td><code>$address_postal_code</code> <strong>[3]</strong></td></tr><tr><td><code>product.latitude</code> <strong>[4]</strong></td><td><code>$latitude</code> <strong>[3]</strong></td></tr><tr><td><code>product.longitude</code> <strong>[4]</strong></td><td><code>$longitude</code> <strong>[3]</strong></td></tr><tr><td><code>product.image_captions</code> <strong>[4]</strong></td><td><code>$image_captions</code> <strong>[3]</strong></td></tr><tr><td><code>product.condition</code> <strong>[4]</strong></td><td><code>$condition</code> <strong>[3]</strong></td></tr></tbody></table>

{% hint style="info" %}
&#x20;**\[1]** in <mark style="color:blue;">`user_data`</mark> .\
&#x20;**\[2]** in <mark style="color:blue;">`event_data`</mark> .\
&#x20;**\[3]** in <mark style="color:blue;">`content_items.X`</mark> .\
&#x20;**\[4]** in <mark style="color:blue;">`items.X`</mark> .\
&#x20;**\[5]** property set when <mark style="color:blue;">`context.device.os.name`</mark> is <mark style="color:blue;">`iOS`</mark> (case insensitive).\
&#x20;**\[6]** property set when <mark style="color:blue;">`context.device.os.name`</mark> is <mark style="color:blue;">`Android`</mark> (case insensitive).\
&#x20;**\[7]** boolean opposite of <mark style="color:blue;">`context.device.ad_tracking_enabled`</mark> .
{% endhint %}
