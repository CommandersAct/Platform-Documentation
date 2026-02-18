# Snapchat Conversions API v3

[Snapchat](https://www.snapchat.com/) is a multimedia instant messaging app and service.\
This destination leverages the latest [Snapchat Conversions API v3](https://developers.snap.com/api/marketing-api/Conversions-API/Introduction) to push web and app events to Snapchat leading to optimized ad campaigns, improved targeting, and measure the conversions that resulted from your Snapchat campaigns.

## Key features

The Snapchat destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [Snapchat events](https://developers.snap.com/api/marketing-api/Conversions-API/Parameters#server-parameters), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Custom events**: you can freely push custom events based on your specific needs.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to Snapchat.

## Destination setup

### Configuration

<table><thead><tr><th width="242">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Credentials</code></td><td><em><strong><code>Required if API Token is not set</code></strong></em><br>Your credentials with Snapchat as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Snapchat</code></td></tr><tr><td><code>API Token</code></td><td><em><strong><code>Required if Credentials is not set</code></strong></em><br>Input your "API Token", also known as "Static long lived token", as generated in Snapchat <a href="https://business.snapchat.com/">Business Manager</a> → "Business Details" by following this <a href="https://marketingapi.snapchat.com/docs/conversion.html#static-long-lived-tokens">LINK</a>. This field has priority over <code>Credentials</code>.</td></tr><tr><td><code>Pixel Id (WEB)</code></td><td><em><strong><code>Required</code></strong></em> for <a href="https://marketingapi.snapchat.com/docs/conversion.html#web-parameters">WEB events</a>.<br>Your <a href="https://businesshelp.snapchat.com/s/article/pixel-website-install?language=en_US">Pixel Id</a> as provided by Snapchat for "Web" type events. For more details, you can check the following <a href="https://businesshelp.snapchat.com/s/article/pixel-website-install?language=en_US">LINK</a>.</td></tr><tr><td><code>Snap App Id (APP)</code></td><td><em><strong><code>Required</code></strong></em> for <a href="https://marketingapi.snapchat.com/docs/conversion.html#mobile_app-parameters">MOBILE APP</a> events.<br>Your <a href="https://businesshelp.snapchat.com/s/article/snap-app-id?language=en_US">Snap App Id</a> as provided by Snapchat for "Mobile App" type events. For more details, you can check the following <a href="https://businesshelp.snapchat.com/s/article/snap-app-id?language=en_US">LINK</a>.</td></tr><tr><td><code>Send IP Address</code></td><td>Flag this option to send the IP address as set in the <code>Smart Mapping</code>  field <code>Device IP</code> .</td></tr><tr><td><code>Custom Event Mapping</code></td><td>Snapchat allows up to five (5) custom events to be tracked. In <code>Commanders Act Event Name</code> input an event name, while in <code>Snapchat Event Name</code> set a name as follows: <code>CUSTOM_EVENT_X</code> , where <code>X</code> is a number between <code>1</code> and <code>5</code> , both included (E.g. <code>CUSTOM_EVENT_1</code> ).</td></tr><tr><td><code>Custom Event Properties</code></td><td>Map your custom event properties by setting their field names in <code>Snapchat property name</code> and adding the value in <code>Your value event</code> . </td></tr></tbody></table>

## Quick reference

| Commanders Act Events                                            | Snapchat Events           |
| ---------------------------------------------------------------- | ------------------------- |
| `achievement_unlocked`                                           | `ACHIEVEMENT_UNLOCKED`    |
| `ad_click`                                                       | `AD_CLICK`                |
| `ad_view`                                                        | `AD_VIEW`                 |
| <p><code>add_payment_info</code><br><code>add_billing</code></p> | `ADD_BILLING`             |
| `add_to_cart`                                                    | `ADD_CART`                |
| `add_to_wishlist`                                                | `ADD_TO_WISHLIST`         |
| `app_open`                                                       | `APP_OPEN`                |
| `begin_checkout`                                                 | `START_CHECKOUT`          |
| `complete_tutorial`                                              | `COMPLETE_TUTORIAL`       |
| `generate_lead`                                                  | `SUBSCRIBE`               |
| `invite`                                                         | `INVITE`                  |
| `level_complete`                                                 | `LEVEL_COMPLETE`          |
| `login`                                                          | `LOGIN`                   |
| `page_view`                                                      | `PAGE_VIEW`               |
| `purchase`                                                       | `PURCHASE`                |
| `rate`                                                           | `RATE`                    |
| `reserve`                                                        | `RESERVE`                 |
| `save`                                                           | `SAVE`                    |
| `search`                                                         | `SEARCH`                  |
| `share`                                                          | `SHARE`                   |
| `sign_up`                                                        | `SIGN_UP`                 |
| `spent_credits`                                                  | `SPENT_CREDITS`           |
| `start_trial`                                                    | `START_TRIAL`             |
| `view_item`                                                      | `VIEW_CONTENT`            |
| `view_item_list`                                                 | `LIST_VIEW`               |
| `[ANY EVENT]`                                                    | `CUSTOM_EVENT_X` **\[1]** |

{% hint style="info" %}
> **\[1]** Where <mark style="color:blue;">`X`</mark> is a number between `1` and `5` , both included. See <mark style="color:blue;">Custom Event Mapping</mark> in [Configuration](snapchat-conversions-api-v3.md#configuration) for more details on how you can track custom events with Snapchat.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
All Snapchat properties are set in the base path `data.0` .
{% endhint %}

<table><thead><tr><th width="374">Commanders Act Properties</th><th>Snapchat Properties</th></tr></thead><tbody><tr><td><code>context.event_timestamp</code></td><td><code>event_time</code></td></tr><tr><td><code>(event_name)</code></td><td><code>event_name</code> <strong>[1]</strong></td></tr><tr><td><code>partners.snapchat.event_conversion_type</code> <br><code>(context.app.name)</code></td><td><code>action_source</code> <strong>[2]</strong></td></tr><tr><td><code>context.page.url</code></td><td><code>event_source_url</code></td></tr><tr><td><code>id</code></td><td><code>event_id</code> <strong>[3]</strong></td></tr><tr><td><code>partners.snapchat.dpo</code></td><td><code>data_processing_options</code></td></tr><tr><td><code>partners.snapchat.test_code</code></td><td><code>test_event_code</code></td></tr><tr><td><code>items.X.id</code></td><td><code>custom_data.content_ids</code> <strong>[4]</strong></td></tr><tr><td><code>items.X.product.category_1</code></td><td><code>custom_data.content_category</code> <strong>[5]</strong></td></tr><tr><td><code>context.page.title</code></td><td><code>custom_data.content_name</code></td></tr><tr><td><code>partners.snapchat.content_type</code></td><td><code>custom_data.content_type</code> <strong>[6]</strong></td></tr><tr><td><code>items.X.id</code></td><td><code>custom_data.contents.X.id</code></td></tr><tr><td><code>items.X.quantity</code></td><td><code>custom_data.contents.X.quantity</code></td></tr><tr><td><code>items.X.product.price</code></td><td><code>custom_data.contents.X.item_price</code></td></tr><tr><td><code>items.X.product.delivery_category</code></td><td><code>custom_data.contents.X.delivery_category</code></td></tr><tr><td><code>items.length</code></td><td><code>custom_data.num_items</code></td></tr><tr><td><code>value</code></td><td><code>custom_data.value</code></td></tr><tr><td><code>currency</code></td><td><code>custom_data.currency</code></td></tr><tr><td><code>id</code></td><td><code>custom_data.order_id</code></td></tr><tr><td><code>partners.snapchat.predicted_ltv</code></td><td><code>custom_data.predicted_ltv</code></td></tr><tr><td><code>search_term</code></td><td><code>custom_data.search_string</code></td></tr><tr><td><code>partners.snapchat.checkin_date</code></td><td><code>custom_data.checkin_date</code> <strong>[7]</strong></td></tr><tr><td><code>partners.snapchat.travel_end</code></td><td><code>custom_data.travel_end</code></td></tr><tr><td><code>partners.snapchat.travel_start</code></td><td><code>custom_data.travel_start</code></td></tr><tr><td><code>partners.snapchat.suggest_dest</code></td><td><code>custom_data.suggested_destinations</code> <strong>[8]</strong></td></tr><tr><td><code>partners.snapchat.dest_airport</code></td><td><code>custom_data.destination_airport</code> <strong>[9]</strong></td></tr><tr><td><code>partners.snapchat.dest_country</code></td><td><code>custom_data.country</code> <strong>[10]</strong></td></tr><tr><td><code>partners.snapchat.dest_city</code></td><td><code>custom_data.city</code> <strong>[11]</strong></td></tr><tr><td><code>partners.snapchat.dest_region</code></td><td><code>custom_data.region</code> <strong>[12]</strong></td></tr><tr><td><code>partners.snapchat.dest_neigh</code></td><td><code>custom_data.neighborhood</code> <strong>[13]</strong></td></tr><tr><td><code>method</code></td><td><code>custom_data.sign_up_method</code></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>user_data.client_user_agent</code></td></tr><tr><td><code>context.app.namespace</code></td><td><code>app_data.app_id</code><br><code>extinfo.1</code></td></tr><tr><td><code>context.device.advertising_id</code></td><td><code>user_data.madid</code></td></tr><tr><td><code>context.device.idfv</code></td><td><code>user_data.idfv</code> <strong>[14]</strong></td></tr><tr><td><code>(context.device.os.name)</code></td><td><code>extinfo.0</code> <strong>[15]</strong></td></tr><tr><td><code>context.app.version</code></td><td><code>extinfo.2</code> </td></tr><tr><td><code>context.app.version_long</code></td><td><code>extinfo.3</code> </td></tr><tr><td><code>context.device.os.version</code></td><td><code>custom_data.os_version</code><br><code>extinfo.4</code> </td></tr><tr><td><code>context.device.model</code></td><td><code>custom_data.device_model</code><br><code>extinfo.5</code> </td></tr><tr><td><code>context.device.language</code></td><td><code>extinfo.6</code> </td></tr><tr><td><code>context.device.timezone_short</code></td><td><code>extinfo.7</code> </td></tr><tr><td><code>context.device.network.carrier</code></td><td><code>extinfo.8</code> </td></tr><tr><td><code>context.device.screen.width</code></td><td><code>extinfo.9</code> </td></tr><tr><td><code>context.device.screen.height</code></td><td><code>extinfo.10</code> </td></tr><tr><td><code>context.device.screen.density</code></td><td><code>extinfo.11</code> </td></tr><tr><td><code>context.device.cpu_core</code></td><td><code>extinfo.12</code> </td></tr><tr><td><code>context.device.storage</code></td><td><code>extinfo.13</code> </td></tr><tr><td><code>context.device.ex_storage</code></td><td><code>extinfo.14</code> </td></tr><tr><td><code>context.device.timezone</code></td><td><code>extinfo.15</code> </td></tr><tr><td><code>context.device.ad_tracking_enabled</code></td><td><code>app_data.advertiser_tracking_enabled</code></td></tr><tr><td><code>user.email</code></td><td><code>user_data.em</code> <strong>[16]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>user_data.ph</code> <strong>[16]</strong></td></tr><tr><td><code>user.firstname</code></td><td><code>user_data.fn</code> <strong>[16]</strong></td></tr><tr><td><code>user.lastname</code></td><td><code>user_data.ln</code> <strong>[16]</strong></td></tr><tr><td><code>user.gender</code></td><td><code>user_data.ge</code> <strong>[16]</strong></td></tr><tr><td><code>user.city</code></td><td><code>user_data.ct</code> <strong>[16]</strong></td></tr><tr><td><code>user.state_short</code></td><td><code>user_data.st</code> <strong>[16]</strong></td></tr><tr><td><code>user.zipcode</code></td><td><code>user_data.zp</code> <strong>[16]</strong></td></tr><tr><td><code>user.country</code></td><td><code>user_data.country</code> <strong>[16]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>user_data.client_ip_address</code></td></tr><tr><td><code>user.id</code></td><td><code>user_data.external_id</code></td></tr><tr><td><code>partners.snapchat.sub_id</code></td><td><code>user_data.subscription_id</code></td></tr><tr><td><code>partners.snapchat.lead_id</code></td><td><code>user_data.lead_id</code></td></tr><tr><td><code>partners.snapchat.app_install_id</code></td><td><code>user_data.anon_id</code></td></tr><tr><td><code>partners.snapchat.download_id</code></td><td><code>user_data.download_id</code></td></tr><tr><td><code>partners.snapchat.partner_id</code></td><td><code>user_data.partner_id</code></td></tr><tr><td><code>partners.snapchat.uuid_c1</code> <br><code>Cookie _scid</code></td><td><code>user_data.sc_cookie1</code> <strong>[17]</strong></td></tr><tr><td><code>partners.snapchat.click_id</code></td><td><code>user_data.sc_click_id</code></td></tr></tbody></table>

{% hint style="info" %}
> **\[1]** See [Quick reference](snapchat-conversions-api-v3.md#quick-reference) for more details.\
> &#xNAN;**\[2]** Priority on the left side. If `context.app.name`  is set `MOBILE_APP`  is returned. Allowed values: `OFFLINE` , `MOBILE_APP`  and `WEB` . Default value: `WEB` .\
> &#xNAN;**\[3]** If you are reporting events via more than one method (Snap Pixel, App Ads Kit , Conversions API) you should use the same event identifier across all methods. If using [Snap Pixel](https://businesshelp.snapchat.com/s/article/snap-pixel-about?language=en_US), this must match the `client_dedup_id`  for the matching event.\
> &#xNAN;**\[4]** All item identifier are included.\
> &#xNAN;**\[5]** All categories are included.\
> &#xNAN;**\[6]** Indicates what the keys in `content_ids`  or `contents`  represent. Set with `product`  for individual items or `product_group`  for items that have multiple options in either size, color or any other variation. Default value: `product` .\
> &#xNAN;**\[7]** The desired hotel check-in date in the hotel's time-zone. Accepted formats are: `YYYYMMDD` , `YYYY-MM-DD` , `YYYY-MM-DDThh:mmTZD`  and `YYYY-MM-DDThh:mm:ssTZD` .\
> &#xNAN;**\[8]** Suggested Destinations. Comma-separated or list of destinations (E.g. `destination1,destination2`  or `["destination1", "destination2"]` ).\
> &#xNAN;**\[9]** IATA code.\
> &#xNAN;**\[10]** The country based on the location the user intends to visit.\
> &#xNAN;**\[11]** The city based on the location the user intends to visit.\
> &#xNAN;**\[12]** This could be the state, district, or region of interest to the user.\
> &#xNAN;**\[13]** The neighborhood the user is interested in.\
> &#xNAN;**\[14]** iOS IDFV. If it's passed in clear text, it's automatically hashed via SHA256.\
> &#xNAN;**\[15]** Set with `a2`  if `context.device.os.name`  is `Android`  (case insensitive) or `i2`  if `context.device.os.name`  is `iOS` (case insensitive).\
> &#xNAN;**\[16]** If it's passed in clear text, it's normalized and automatically hashed via SHA256.\
> &#xNAN;**\[17]** Priority on the left side.
{% endhint %}
