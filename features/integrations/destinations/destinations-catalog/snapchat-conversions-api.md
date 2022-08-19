# Snapchat Conversions API

[Snapchat ](https://www.snapchat.com/)is a multimedia instant messaging app and service. \
The [Snapchat Conversions API](https://marketingapi.snapchat.com/docs/conversion.html#introduction) allows you to bridge web and app events to Snapchat via a server-side integration.

## Key features

The Snapchat destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model fits [Snapchat's one](https://marketingapi.snapchat.com/docs/conversion.html#parameters-for-event-type-platform), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Custom events**: you can freely push custom events based on your specific needs.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to Snapchat.

## Destination setup

Before you get started with this destination, make sure you can access the [Snapchat Ads Manager](https://ads.snapchat.com).

### Configuration

| Settings                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Pixel Id (WEB)`          | <p><em><strong><code>Required</code> </strong></em> for <a href="https://marketingapi.snapchat.com/docs/conversion.html#web-parameters">WEB events</a>.</p><p>Your <a href="https://businesshelp.snapchat.com/s/article/pixel-website-install?language=en_US">Pixel Id</a> as provided by Snapchat for "Web" type events. For more details, you can check the following <a href="https://businesshelp.snapchat.com/s/article/pixel-website-install?language=en_US">LINK</a>.</p>                                                                                                                              |
| `Snap App Id (APP)`       | <p><em><strong><code>Required</code></strong></em> for <a href="https://marketingapi.snapchat.com/docs/conversion.html#mobile_app-parameters">MOBILE_APP events</a>.</p><p>Your <a href="https://businesshelp.snapchat.com/s/article/snap-app-id?language=en_US">Snap App Id</a> as provided by Snapchat for "Mobile App" type events. For more details, you can check the following <a href="https://businesshelp.snapchat.com/s/article/snap-app-id?language=en_US">LINK</a>.</p>                                                                                                                           |
| `Custom Event Mapping`    | Snapchat allows up to five (5) custom events to be tracked. In `Commanders Act Event Name` input an event name, while in `Snapchat Event Name` set a name as follows: `CUSTOM_EVENT_[NUMBER]`, where `[NUMBER]` is between 1 and 5, both included (E.g. `CUSTOM_EVENT_1`).                                                                                                                                                                                                                                                                                                                                    |
| `Custom Event Properties` | Map your custom event properties by setting their field names in `Event property name` and adding the field name holding the value in `Commanders Act event property or static value`. E.g. if you input`size`in the `Event property name` and`properties.items.0.product.size` **\[1]** in `Commanders Act event property or static value`, you will have a custom event property in Snapchat called`size`with a value based on the content of the field`properties.items.0.product.size`. You also have the option to set a static string/numeric value in `Commanders Act event property or static value`. |

## Quick reference

| Commanders Act Events | Snapchat Events                 |
| --------------------- | ------------------------------- |
| `add_payment_info`    | `ADD_PAYMENT_INFO` **\[\*]**    |
| `add_shipping_info`   | `ADD_SHIPPING_INFO` **\[\*]**   |
| `add_to_cart`         | `ADD_CART`                      |
| `add_to_wishlist`     | `ADD_TO_WISHLIST`               |
| `begin_checkout`      | `START_CHECKOUT`                |
| `generate_lead`       | `GENERATE_LEAD` **\[\*]**       |
| `login`               | `LOGIN`                         |
| `page_view`           | `PAGE_VIEW`                     |
| `purchase`            | `PURCHASE`                      |
| `refund`              | `REFUND` **\[\*]**              |
| `remove_from_cart`    | `REMOVE_FROM_CART` **\[\*]**    |
| `search`              | `SEARCH`                        |
| `select_content`      | `SELECT_CONTENT` **\[\*]**      |
| `select_item`         | `SELECT_ITEM` **\[\*]**         |
| `sign_up`             | `SIGN_UP` **\[\*]**             |
| `view_cart`           | `VIEW_CART`                     |
| `view_item`           | `VIEW_CONTENT` **\[\*]**        |
| `view_item_list`      | `VIEW_ITEM_LIST` **\[\*]**      |
| `[Custom Event]`      | `[Custom Event]` **\[\*] \[1]** |



{% hint style="info" %}
**\[\*]** Snapchat custom event.\
**\[1]** Commanders Act custom event names are converted to uppercase and sent to Snapchat.
{% endhint %}

## Field Mappings

{% hint style="info" %}
The Snapchat property<mark style="color:blue;">`integration`</mark>is always set as<mark style="color:blue;">`tag-commander`</mark>.
{% endhint %}

| Commanders Act Properties                                 | Snapchat Properties              |
| --------------------------------------------------------- | -------------------------------- |
| `event_timestamp`                                         | `timestamp` **\[1]**             |
| `(app.name)`                                              | `event_conversion_type` **\[2]** |
| `properties.items.X.id`                                   | `item_ids.X`                     |
| `properties.items.length`                                 | `number_items`                   |
| `properties.value`                                        | `price`                          |
| `properties.currency`                                     | `currency`                       |
| `properties.id`                                           | `transaction_id`                 |
| `properties.search_term`                                  | `search_string`                  |
| `device.user_agent`                                       | `user_agent`                     |
| `device.ip`                                               | `hashed_ip_address` **\[3]**     |
| `client_dedup_id`                                         | `client_dedup_id` **\[4]**       |
| `app.namespace`                                           | `app_id`                         |
| `Snap App Id (APP)`                                       | `snap_app_id`                    |
| `device.maid`                                             | `hashed_mobile_ad_id`            |
| `device.idfv`                                             | `hashed_idfv`                    |
| `Pixel Id (WEB)`                                          | `pixel_id`                       |
| `properties.user.email_sha256` or `properties.user.email` | `hashed_email` **\[5]**          |
| `properties.user.phone`                                   | `hashed_phone_number` **\[6]**   |

{% hint style="info" %}
**\[1]** Field automatically generated when it's not set.\
**\[2]** If<mark style="color:blue;">`app.name`</mark>is defined then this field is set with <mark style="color:blue;">`MOBILE_APP`</mark>, otherwise,<mark style="color:blue;">`WEB`</mark>`.`\
``**\[3]** Field automatically hashed.\
**\[4]** If you are reporting events using multiple methods (E.g. Snap Pixel and Conversions API) you should use the same`client_dedup_id`across all of them. This will be used within a 48 hour scope of the first occurrence.\
**\[5]** In case<mark style="color:blue;">`properties.user.email_sha256`</mark>is not provided, <mark style="color:blue;">`properties.user.email`</mark>is hashed and used in its place.\
**\[6]** Field automatically hashed and [normalized](https://marketingapi.snapchat.com/docs/conversion.html#data-hygiene).
{% endhint %}
