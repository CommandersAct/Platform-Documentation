# Snapchat Conversions API

[Snapchat ](https://www.snapchat.com/)is a multimedia instant messaging app and service. \
This destination leverages the [Snapchat Conversions API](https://marketingapi.snapchat.com/docs/conversion.html#introduction) to push web and app events to Snapchat.

## Key features

The Snapchat destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) fits [Snapchat event types](https://marketingapi.snapchat.com/docs/conversion.html#conversion-parameters), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Custom events**: you can freely push custom events based on your specific needs.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to Snapchat.

## Destination setup

Before you get started with this destination, make sure you can access the [Snapchat Ads Manager](https://ads.snapchat.com).

### Configuration

<table><thead><tr><th width="150">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Credentials</code></td><td><em><strong><code>Required if API Token is not set</code></strong></em><br>Your credentials with Snapchat as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Snapchat</code></td></tr><tr><td><code>API Token</code></td><td><em><strong><code>Required if Credentials is not set</code></strong></em> <br>Input your "API Token", also known as "Static long lived token", as generated in Snapchat <a href="https://business.snapchat.com/">Business Manager</a> → "Business Details" by following this <a href="https://marketingapi.snapchat.com/docs/conversion.html#static-long-lived-tokens">LINK</a>. This field has priority over <code>Credentials</code>.</td></tr><tr><td><code>Pixel Id (WEB)</code></td><td><em><strong><code>Required</code></strong></em> for <a href="https://marketingapi.snapchat.com/docs/conversion.html#web-parameters">WEB events</a>. <br>Your <a href="https://businesshelp.snapchat.com/s/article/pixel-website-install?language=en_US">Pixel Id</a> as provided by Snapchat for "Web" type events. For more details, you can check the following <a href="https://businesshelp.snapchat.com/s/article/pixel-website-install?language=en_US">LINK</a>.</td></tr><tr><td><code>Snap App Id (APP)</code></td><td><em><strong><code>Required</code></strong></em> for <a href="https://marketingapi.snapchat.com/docs/conversion.html#mobile_app-parameters">MOBILE APP</a> events. <br>Your <a href="https://businesshelp.snapchat.com/s/article/snap-app-id?language=en_US">Snap App Id</a> as provided by Snapchat for "Mobile App" type events. For more details, you can check the following <a href="https://businesshelp.snapchat.com/s/article/snap-app-id?language=en_US">LINK</a>.</td></tr><tr><td><code>Custom Event Mapping</code></td><td>Snapchat allows up to five (5) custom events to be tracked. In <code>Commanders Act Event Name</code>  input an event name, while in <code>Snapchat Event Name</code>  set a name as follows: <code>CUSTOM_EVENT_X</code> , where <code>X</code>  is a number between <code>1</code> and <code>5</code> , both included (E.g. <code>CUSTOM_EVENT_1</code> ).  </td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>Event property name</code>  and adding the field name holding the value in <code>Commanders Act event property</code> . E.g. if you input <code>size</code> in the <code>Event property name</code>  and <code>items.0.product.size</code>  <strong>[1]</strong> in <code>Commanders Act event property</code> , you will have a custom event property in Snapchat called <code>size</code> with a value based on the content of the field <code>items.0.product.size</code> .</td></tr></tbody></table>



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
| `invite`                    | `INVITE`                  |
| `login`                     | `LOGIN`                   |
| `page_view`                 | `PAGE_VIEW`               |
| `purchase`                  | `PURCHASE`                |
| `reserve`                   | `RESERVE`                 |
| `search`                    | `SEARCH`                  |
| `sign_up`                   | `SIGN_UP`                 |
| `view_item`                 | `VIEW_CONTENT`            |
| `view_item_list`            | `LIST_VIEW`               |
| `Commanders Act Event Name` | `CUSTOM_EVENT_X` **\[1]** |

{% hint style="info" %}
**\[1]** Where <mark style="color:blue;">`X`</mark> is a number between `1` and `5` , both included. See <mark style="color:blue;">Custom Event Mapping</mark> in [Configuration](snapchat-conversions-api.md#configuration) for more details on how you can track custom events with Snapchat.
{% endhint %}

## Field Mappings

{% hint style="info" %}
This destination will set the unique visitor identifier, which you can provide if you're using Snapchat Pixel SDK, as value for the Snapchat <mark style="color:blue;">`uuid_c1`</mark> property by looking for <mark style="color:blue;">`partners.snapchat.uuid_c1`</mark> property. If it's not present, the cookie <mark style="color:blue;">**\_scid**</mark> is used.
{% endhint %}

<table><thead><tr><th width="441">Commanders Act Properties</th><th>Snapchat Properties</th></tr></thead><tbody><tr><td><code>context.event_timestamp</code></td><td><code>timestamp</code> <strong>[1]</strong></td></tr><tr><td><code>Pixel Id (WEB)</code></td><td><code>pixel_id</code></td></tr><tr><td><code>Snap App Id (APP)</code></td><td><code>snap_app_id</code></td></tr><tr><td><p><code>partners.snapchat.event_conversion_type</code></p><p><code>(context.app.name)</code></p></td><td><code>event_conversion_type</code> <strong>[2]</strong></td></tr><tr><td><code>context.page.url</code></td><td><code>page_url</code></td></tr><tr><td><code>context.app.namespace</code></td><td><code>app_id</code></td></tr><tr><td><code>id</code></td><td><code>client_dedup_id</code> <strong>[3]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>item_ids.X</code></td></tr><tr><td><code>items.length</code></td><td><code>number_items</code></td></tr><tr><td><code>items.X.id</code></td><td><code>item_ids</code> <strong>[4]</strong></td></tr><tr><td><code>items.X.product.category_1</code></td><td><code>item_category</code> <strong>[4]</strong></td></tr><tr><td><code>value</code></td><td><code>price</code></td></tr><tr><td><code>currency</code></td><td><code>currency</code></td></tr><tr><td><code>id</code></td><td><code>transaction_id</code></td></tr><tr><td><code>method</code></td><td><code>sign_up_method</code></td></tr><tr><td><code>search_term</code></td><td><code>search_string</code></td></tr><tr><td><code>user.email</code></td><td><code>hashed_email</code> <strong>[5]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>hashed_phone_number</code> <strong>[6]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>hashed_ip_address</code> <strong>[5]</strong></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>user_agent</code></td></tr><tr><td><code>context.device.advertising_id</code></td><td><code>hashed_mobile_ad_id</code></td></tr><tr><td><code>context.device.idfv</code></td><td><code>hashed_idfv</code></td></tr><tr><td><code>context.device.model</code></td><td><code>device_model</code></td></tr><tr><td><code>context.device.os.version</code></td><td><code>os_version</code></td></tr><tr><td><code>partners.snapchat.uuid_c1</code></td><td><code>uuid_c1</code> <strong>[7]</strong></td></tr><tr><td><code>partners.snapchat.click_id</code></td><td><code>click_id</code></td></tr><tr><td><code>partners.snapchat.att_status</code></td><td><code>att_status</code></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Field automatically generated when it's not set.\
&#xNAN;**\[2]** Priority order is listed in the left column. If <mark style="color:blue;">`context.app.name`</mark> is defined then this field is set with <mark style="color:blue;">`MOBILE_APP`</mark> , otherwise, <mark style="color:blue;">`WEB`</mark> .\
&#xNAN;**\[3]** If you are reporting events using multiple methods (E.g. Snap Pixel and Conversions API) you should use the same <mark style="color:blue;">`client_dedup_id`</mark> across all of them. This will be used within a 48 hour scope of the first occurrence.\
&#xNAN;**\[4]** Each item information is pushed in the related array. \
&#xNAN;**\[5]** Field automatically hashed if provided in clear text.\
&#xNAN;**\[6]** Field automatically hashed and [normalized](https://marketingapi.snapchat.com/docs/conversion.html#data-hygiene).\
&#xNAN;**\[7]** <mark style="color:blue;">`partners.snapchat.uuid_c1`</mark> has priority over cookie <mark style="color:blue;">**\_scid**</mark>.
{% endhint %}
