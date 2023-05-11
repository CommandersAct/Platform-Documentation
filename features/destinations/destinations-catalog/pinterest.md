# Pinterest

[Pinterest](https://www.pinterest.com) is an image sharing and social media service designed to enable saving and discovery of information on the internet using images, animated GIFs and videos, in the form of pinboards.\
Using this destination, you can leverage [Pinterest API](https://developers.pinterest.com/docs/conversions/conversion-management/#Tracking%20conversions%20with%20the%20Pinterest%20API) to send events via server-side hits. More technical details are available following this [LINK](https://developers.pinterest.com/docs/api/v5/#tag/conversion\_events).

## Key features

The Pinterest destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model covers Pinterest's events, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.&#x20;
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to Pinterest.

## Destination setup

{% hint style="info" %}
Ensure you have access to a [Pinterest Ads account](https://ads.pinterest.com) before configuring this destination.
{% endhint %}

### Configuration

| Settings                 | Description                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Advertiser ID`          | <p><em><strong><code>Required</code></strong></em></p><p>Pinterest Advertiser ID. More details are available following this <a href="https://developers.pinterest.com/docs/conversions/3rd-party-api-integrations/#Getting%20your%20Access%20Token%20and%20Advertiser%20ID">LINK</a>.</p>                                                                       |
| `API Access Token`       | <p><em><strong><code>Required</code></strong></em><br>The Pinterest Conversions API needs an access token to authenticate your activities. More details are available following this <a href="https://developers.pinterest.com/docs/conversions/3rd-party-api-integrations/#Getting%20your%20Access%20Token%20and%20Advertiser%20ID">LINK</a>.</p>              |
| `Send as a test-request` | If checked, the event will not be recorded in Pinterest Ads, but the API will still return the same response messages. Use this mode to verify your requests and if your events are constructed correctly. More details are available following this [LINK](https://developers.pinterest.com/docs/conversions/conversion-management/#Testing%20your%20request). |

## Quick reference

| Commanders Act Events                                                                                                                                                                                                                                                                                                                                                                                                                  | Pinterest Events |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| `page_view`                                                                                                                                                                                                                                                                                                                                                                                                                            | `page_visit`     |
| <p><code>purchase</code></p><p><code>buy</code></p><p><code>pay</code></p><p><code>payment</code></p>                                                                                                                                                                                                                                                                                                                                  | `checkout`       |
| <p><code>add_to_cart</code></p><p><code>addtocart</code></p>                                                                                                                                                                                                                                                                                                                                                                           | `add_to_cart`    |
| <p><code>search</code></p><p><code>find_location</code></p>                                                                                                                                                                                                                                                                                                                                                                            | `search`         |
| <p><code>generate_lead</code></p><p><code>submit_application</code></p><p><code>contact</code></p>                                                                                                                                                                                                                                                                                                                                     | `lead`           |
| <p><code>sign_up</code><br><code>signup</code></p><p><code>completeregistration</code></p>                                                                                                                                                                                                                                                                                                                                             | `signup`         |
| <p><code>view_item_list</code></p><p><code>viewcategory</code></p><p><code>viewcontent</code></p>                                                                                                                                                                                                                                                                                                                                      | `view_category`  |
| <p><code>watch_video</code></p><p><code>watchvideo</code></p>                                                                                                                                                                                                                                                                                                                                                                          | `watch_video`    |
| <p><code>add_payment_info</code></p><p><code>add_shipping_info</code></p><p><code>add_to_wishlist</code></p><p><code>begin_checkout</code></p><p><code>login</code></p><p><code>refund</code></p><p><code>remove_from_cart</code></p><p><code>select_content</code></p><p><code>select_item</code></p><p><code>view_cart</code></p><p><code>view_item</code></p><p><code>select_promotion</code></p><p><code>view_promotion</code></p> | `custom`         |

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
At least one of the following statement must be fulfilled:\
• <mark style="color:blue;">`user_data.em`</mark>is set.\
• <mark style="color:blue;">`user_data.hashed_maids`</mark>is set.\
• <mark style="color:blue;">`user_data.client_ip_address`</mark>and<mark style="color:blue;">`user_data.client_user_agent`</mark>are set.\
The property<mark style="color:blue;">`event_id`</mark>is required and used for deduplication. More information are available following this [LINK](https://developers.pinterest.com/docs/conversions/conversions/) (See section "How deduplication works").&#x20;
{% endhint %}

| Commanders Act Properties          | Pinterest Properties                |
| ---------------------------------- | ----------------------------------- |
| `partners.pinterest.event_id`      | `event_id` **\[\*]**                |
| `partners.pinterest.action_source` | `action_source` **\[1]**            |
| `context.event_timestamp`          | `event_time`                        |
| `context.page.url`                 | `event_source_url` **\[2]**         |
| `partners.pinterest.opt_out`       | `opt_out` **\[3]**                  |
| `context.app.namespace`            | `app_id`                            |
| `context.app.name`                 | `app_name`                          |
| `context.app.version`              | `app_version`                       |
| `context.device.manufacturer`      | `device_brand`                      |
| `context.device.network.carrier`   | `device_carrier`                    |
| `context.device.model`             | `device_model`                      |
| `context.device.type`              | `device_type`                       |
| `context.device.os.version`        | `os_version`                        |
| `context.device.network.wifi`      | `wifi` **\[3]**                     |
| `context.device.lang`              | `language`                          |
| `user.email_sha256`                | `user_data.em` **\[4]**             |
| `user.phone`                       | `user_data.ph` **\[4]**             |
| `user.gender`                      | `user_data.ge` **\[4]**             |
| `user.birthdate`                   | `user_data.db` **\[4]**             |
| `user.lastname`                    | `user_data.ln` **\[4]**             |
| `user.firstname`                   | `user_data.fn` **\[4]**             |
| `user.city`                        | `user_data.ct` **\[4]**             |
| `user.state_short`                 | `user_data.st` **\[4]**             |
| `user.zipcode`                     | `user_data.zp` **\[4]**             |
| `user.country`                     | `user_data.country` **\[4]**        |
| `user.id`                          | `user_data.external_id` **\[4]**    |
| `context.device.advertising_id`    | `user_data.hashed_maids` **\[4]**   |
| `context.device.ip`                | `user_data.client_ip_address`       |
| `context.device.user_agent`        | `user_data.client_user_agent`       |
| `id`                               | `custom_data.order_id`              |
| `currency`                         | `custom_data.currency`              |
| `value`                            | `custom_data.value`                 |
| `items.X.id`                       | `custom_data.content_ids` **\[5]**  |
| `items.X.product.price`            | `custom_data.contents.X.item_price` |
| `items.X.quantity`                 | `custom_data.contents.X.quantity`   |
| `items.length`                     | `custom_data.num_items`             |
| `search_term`                      | `custom_data.search_string`         |
| `partners.pinterest.opt_out_type`  | `custom_data.opt_out_type`          |

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** If this property is not provided, a proper<mark style="color:blue;">`action_source`</mark>is retrieved using available data. Default value: <mark style="color:blue;">web</mark>.\
**\[2]** If this property is not provided, a proper<mark style="color:blue;">`event_source_url`</mark>is retrieved using available data.\
**\[3]** Boolean or equivalent string value supported.\
**\[4]** If it's passed in clear text, it's automatically hashed.\
**\[5]** All item identifiers are taken into account.
{% endhint %}
