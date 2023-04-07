# Snapchat

[Snapchat ](https://www.snapchat.com/)is a multimedia instant messaging app and service. \
The [Snapchat Conversions API](https://marketingapi.snapchat.com/docs/conversion.html#introduction) allows you to bridge web and app events to Snapchat via a server-side integration.

## Key features

The Snapchat destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) fits [Snapchat's one](https://marketingapi.snapchat.com/docs/conversion.html#parameters-for-event-type-platform), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Custom events**: you can freely push custom events based on your specific needs.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to Snapchat.

## Destination setup

Before you get started with this destination, make sure you can access the [Snapchat Ads Manager](https://ads.snapchat.com).

### Configuration

| Settings                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Authentication`          | <p><em><strong><code>Required</code></strong></em><br>Your credentials with Snapchat as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Snapchat</code></p>                                                                                                                                                                                                        |
| `Pixel Id (WEB)`          | <p><em><strong><code>Required</code></strong></em> for <a href="https://marketingapi.snapchat.com/docs/conversion.html#web-parameters">WEB events</a>.</p><p>Your <a href="https://businesshelp.snapchat.com/s/article/pixel-website-install?language=en_US">Pixel Id</a> as provided by Snapchat for "Web" type events. For more details, you can check the following <a href="https://businesshelp.snapchat.com/s/article/pixel-website-install?language=en_US">LINK</a>.</p>     |
| `Snap App Id (APP)`       | <p><em><strong><code>Required</code></strong></em> for <a href="https://marketingapi.snapchat.com/docs/conversion.html#mobile_app-parameters">MOBILE APP</a> events.</p><p>Your <a href="https://businesshelp.snapchat.com/s/article/snap-app-id?language=en_US">Snap App Id</a> as provided by Snapchat for "Mobile App" type events. For more details, you can check the following <a href="https://businesshelp.snapchat.com/s/article/snap-app-id?language=en_US">LINK</a>.</p> |
| `Custom Event Mapping`    | Snapchat allows up to five (5) custom events to be tracked. In `Commanders Act Event Name` input an event name, while in `Snapchat Event Name` set a name as follows: `CUSTOM_EVENT_X`, where `X` is a number between`1`and`5`, both included (E.g. `CUSTOM_EVENT_1`).                                                                                                                                                                                                              |
| `Custom Event Properties` | Map your custom event properties by setting their field names in `Event property name` and adding the field name holding the value in `Commanders Act event property`. E.g. if you input`size`in the `Event property name` and`properties.items.0.product.size` **\[1]** in `Commanders Act event property`, you will have a custom event property in Snapchat called`size`with a value based on the content of the field`properties.items.0.product.size`.                         |

{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

| Commanders Act Events       | Snapchat Events           |
| --------------------------- | ------------------------- |
| `add_payment_info`          | `ADD_BILLING`             |
| `add_to_cart`               | `ADD_CART`                |
| `add_to_wishlist`           | `ADD_TO_WISHLIST`         |
| `begin_checkout`            | `START_CHECKOUT`          |
| `generate_lead`             | `SUBSCRIBE`               |
| `login`                     | `LOGIN`                   |
| `page_view`                 | `PAGE_VIEW`               |
| `purchase`                  | `PURCHASE`                |
| `search`                    | `SEARCH`                  |
| `sign_up`                   | `SIGN_UP`                 |
| `view_item`                 | `VIEW_CONTENT`            |
| `view_item_list`            | `LIST_VIEW`               |
| `Commanders Act Event Name` | `CUSTOM_EVENT_X` **\[1]** |

{% hint style="info" %}
**\[1]** Where<mark style="color:blue;">`X`</mark>is a number between`1`and`5`, both included. See <mark style="color:blue;">Custom Event Mapping</mark> in [Configuration](snapchat-conversions-api.md#configuration) for more details on how you can track custom events with Snapchat.
{% endhint %}

## Field Mappings

{% hint style="info" %}
This destination will set the unique visitor identifier, which you can provide if you're using Snapchat Pixel SDK, as value for the Snapchat<mark style="color:blue;">`uuid_c1`</mark>property by looking for<mark style="color:blue;">`partners.snapchat.uuid_c1`</mark>property. If it's not present, the cookie <mark style="color:blue;">**\_scid**</mark> is used.
{% endhint %}

| Commanders Act Properties                                                                         | Snapchat Properties              |
| ------------------------------------------------------------------------------------------------- | -------------------------------- |
| `context.event_timestamp`                                                                         | `timestamp` **\[1]**             |
| `Pixel Id (WEB)`                                                                                  | `pixel_id`                       |
| `Snap App Id (APP)`                                                                               | `snap_app_id`                    |
| <p><code>partners.snapchat.event_conversion_type</code></p><p><code>(context.app.name)</code></p> | `event_conversion_type` **\[2]** |
| `context.page.url`                                                                                | `page_url`                       |
| `context.app.namespace`                                                                           | `app_id`                         |
| `id`                                                                                              | `client_dedup_id` **\[3]**       |
| `items.X.id`                                                                                      | `item_ids.X`                     |
| `items.length`                                                                                    | `number_items`                   |
| `items.X.id`                                                                                      | `item_ids` **\[4]**              |
| `items.X.product.category_1`                                                                      | `item_category` **\[4]**         |
| `value`                                                                                           | `price`                          |
| `currency`                                                                                        | `currency`                       |
| `id`                                                                                              | `transaction_id`                 |
| `method`                                                                                          | `sign_up_method`                 |
| `search_term`                                                                                     | `search_string`                  |
| `user.email`                                                                                      | `hashed_email` **\[5]**          |
| `user.phone`                                                                                      | `hashed_phone_number` **\[6]**   |
| `context.device.ip`                                                                               | `hashed_ip_address` **\[5]**     |
| `context.device.user_agent`                                                                       | `user_agent`                     |
| `context.device.advertising_id`                                                                   | `hashed_mobile_ad_id`            |
| `context.device.idfv`                                                                             | `hashed_idfv`                    |
| `context.device.model`                                                                            | `device_model`                   |
| `context.device.os.version`                                                                       | `os_version`                     |
| `partners.snapchat.uuid_c1`                                                                       | `uuid_c1` **\[7]**               |
| `partners.snapchat.click_id`                                                                      | `click_id`                       |
| `partners.snapchat.att_status`                                                                    | `att_status`                     |

{% hint style="info" %}
**\[1]** Field automatically generated when it's not set.\
**\[2]** Priority order is listed in the left column. If<mark style="color:blue;">`context.app.name`</mark>is defined then this field is set with<mark style="color:blue;">`MOBILE_APP`</mark>, otherwise,<mark style="color:blue;">`WEB`</mark>.\
**\[3]** If you are reporting events using multiple methods (E.g. Snap Pixel and Conversions API) you should use the same`client_dedup_id`across all of them. This will be used within a 48 hour scope of the first occurrence.\
**\[4]** Each item information is pushed in the related array.\
**\[5]** Field automatically hashed if provided in clear text.\
**\[6]** Field automatically hashed and [normalized](https://marketingapi.snapchat.com/docs/conversion.html#data-hygiene).\
**\[7]**<mark style="color:blue;">`partners.snapchat.uuid_c1`</mark>has priority over cookie <mark style="color:blue;">**\_scid**</mark>.
{% endhint %}
