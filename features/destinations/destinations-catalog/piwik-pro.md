# Piwik PRO

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Piwik PRO](https://piwik.pro/) "Analytics Suite" is a privacy-focused platform for tracking and analyzing user behavior on websites and other digital products. Their product is an alternative to Google Analytics, geared towards compliance with strict security policies and privacy regulations.\
Using this destination, you can leverage Piwik PRO [Tracking HTTP API](https://developers.piwik.pro/en/latest/data\_collection/api/http\_api.html) to send events. The data sent to this API will be processed and eventually appear in Analytics reports.

## Key features

The Piwik PRO destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model matches [Piwik PRO's event types](https://developers.piwik.pro/en/latest/data\_collection/api/http\_api.html#/paths/\~1ppms.php/get) (See query parameter `e_t`), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.&#x20;
* **Event mapping**: change standard mapping between your partners' events and yours or add new mappings.&#x20;
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to Piwik PRO.

## Destination setup

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Instance Name</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Your instance name as provided by Piwik PRO (E.g. for https://<strong>InstanceName</strong>.piwik.pro/ppms.php, include the <strong>bold string</strong> only).</p></td></tr><tr><td><code>Application Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your application identifier (Previously "Website Id") as provided by Piwik PRO.</td></tr><tr><td><code>Goal Identifiers</code></td><td>Map your goal identifiers by setting the ids in <code>Piwik PRO goal identifiers</code> and adding event names in <code>Your event name</code>. Goal Id "0" is reserved for E-commerce cart tracking.</td></tr><tr><td><code>Custom Dimensions</code></td><td><p>Map your custom dimensions by setting their field names in <code>Piwik PRO dimension name</code> and adding its value in <code>Your value</code>. E.g. if you input<code>size</code>in the <code>Piwik PRO dimension name</code> and <code>items.0.product.size</code> in <code>Your value</code>, you'll have a custom dimension in Piwik PRO called<code>size</code>with a value based on the content of the field <code>items.0.product.size</code> <strong>[1]</strong>.</p><p><br>In the column <code>Your value path</code> you should keep the default value <code>Default (root)</code> as this will add a custom dimension at the base request level which better fits most scenarios. In case you select either <code>In "items" {items.X}</code> or <code>In "product" {items.X.product}</code> this destination will look for the input event property starting from the <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#item">items </a>or <a href="https://community.commandersact.com/platform-x/developers/tracking/events-reference#product">product </a>level respectively and add it as a custom product dimension. In this scenario, <code>Piwik PRO dimension name</code> must be a numeric string identifier (E.g. <code>1</code>, <code>2</code>, ..., <code>N</code>). More details are available following this <a href="https://developers.piwik.pro/en/latest/data_collection/api/http_api.html#/paths/~1ppms.php/get">LINK</a> (See query parameter named <code>ec_products</code>).</p></td></tr><tr><td><code>Custom Session Variables</code></td><td>Map your custom session variables by setting their field names in <code>Piwik PRO variable name</code> and adding its value in <code>Your value</code>. E.g. if you input<code>size</code>in the <code>Piwik PRO variable name</code> and <code>items.0.product.size</code> in <code>Your value</code>, you'll have a custom session variable in Piwik PRO called<code>size</code>with a value based on the content of the field <code>items.0.product.size</code> <strong>[1]</strong>. More details are available following this <a href="https://developers.piwik.pro/en/latest/data_collection/api/http_api.html#/paths/~1ppms.php/get">LINK</a> (See query parameter named <code>_cvar</code>).</td></tr><tr><td><code>Custom Event Variables</code></td><td>Map your custom event variables by setting their field names in <code>Piwik PRO variable name</code> and adding its value in <code>Your value</code>. E.g. if you input<code>size</code>in the <code>Piwik PRO variable name</code> and <code>items.0.product.size</code> in <code>Your value</code>, you'll have a custom event variable in Piwik PRO called<code>size</code>with a value based on the content of the field <code>items.0.product.size</code> <strong>[1]</strong>. More details are available following this <a href="https://developers.piwik.pro/en/latest/data_collection/api/http_api.html#/paths/~1ppms.php/get">LINK</a> (See query parameter named <code>cvar</code>).</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping between Piwik PRO's events and yours or add new mappings.</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.
{% endhint %}

## Quick reference

| Commanders Act Events | Piwik PRO Event Types  |
| --------------------- | ---------------------- |
| `add_to_cart`         | `add-to-cart`          |
| `purchase`            | `order`                |
| `remove_from_cart`    | `remove-from-cart`     |
| `update_cart`         | `cart-update`          |
| `[Any Event]`         | `[Any Event]` **\[1]** |

{% hint style="info" %}
&#x20;**\[1]** See [Event Mapping](piwik-pro.md#configuration) for more details.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
It's recommended to include the visitor identifier in your requets - See Piwik Pro property <mark style="color:blue;">`_id`</mark> for more details.
{% endhint %}

<table><thead><tr><th width="451">Commanders Act Properties</th><th>Piwik Pro Properties</th></tr></thead><tbody><tr><td><code>Application Id</code></td><td><code>idsite</code> <strong>[*]</strong></td></tr><tr><td><code>context.page.url</code></td><td><p><code>url</code></p><p><code>link</code></p></td></tr><tr><td><code>event_name</code></td><td><code>action_name</code></td></tr><tr><td><code>user.id</code></td><td><code>uid</code> <strong>[1]</strong></td></tr><tr><td><code>partners.piwik_pro.visitor_id</code></td><td><code>_id</code> <strong>[2]</strong></td></tr><tr><td><code>partners.piwik_pro.config_id</code></td><td><code>cid</code> <strong>[3]</strong></td></tr><tr><td><code>partners.piwik_pro.anon_tracking</code></td><td><code>uia</code> <strong>[4]</strong></td></tr><tr><td><code>context.page.referrer</code></td><td><code>urlref</code></td></tr><tr><td><code>Custom Session Variables</code></td><td><code>_cvar</code> <strong>[5]</strong></td></tr><tr><td><code>Custom Event Variables</code></td><td><code>cvar</code> <strong>[6]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>cip</code></td></tr><tr><td><code>context.device.screen.width</code>x<br><code>context.device.screen.height</code></td><td><code>res</code> <strong>[7]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>h</code> <strong>[8]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>m</code> <strong>[8]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>s</code> <strong>[8]</strong></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>ua</code></td></tr><tr><td><code>context.device.lang</code></td><td><code>lang</code></td></tr><tr><td><code>user.country</code></td><td><code>country</code></td></tr><tr><td><code>user.city</code></td><td><code>city</code></td></tr><tr><td><code>Custom Dimensions</code></td><td><code>[Custom Dimension]</code> <strong>[9]</strong></td></tr><tr><td><code>search_term</code></td><td><code>search</code></td></tr><tr><td><code>Goal Identifiers</code></td><td><code>idgoal</code> <strong>[10]</strong></td></tr><tr><td><code>revenue</code></td><td><p><code>revenue</code></p><p><code>ec_st</code></p></td></tr><tr><td>See <a href="piwik-pro.md#quick-reference">Quick reference</a></td><td><code>e_t</code></td></tr><tr><td><code>id</code></td><td><code>ec_id</code></td></tr><tr><td>[[<code>items.X.id</code>,<code>items.X.product.name</code>,[<code>items.X.product.category_1</code>, <code>...</code>, <code>items.X.product.category_5</code>], <code>items.X.product.price</code>,<code>items.X.quantity</code>,<code>items.X.product.brand</code>,<code>items.X.variant</code>, { <code>[Custom Product Dimension Id Y]</code>: <code>[Custom Product Dimension Value Y]</code>, <code>...</code>, <code>[Custom Product Dimension Id Y+N]</code>: <code>[Custom Product Dimension Value Y+N]</code>}]]</td><td><code>ec_products</code> <strong>[11]</strong></td></tr><tr><td><code>tax_amount</code></td><td><code>ec_tx</code></td></tr><tr><td><code>shipping_amount</code></td><td><code>ec_sh</code></td></tr><tr><td>(<code>items.X.discount</code>)</td><td><code>ec_dt</code> <strong>[12]</strong></td></tr><tr><td><code>partners.piwik_pro.page_view_id</code></td><td><code>pv_id</code> <strong>[13]</strong></td></tr><tr><td><code>partners.piwik_pro.force_new_visit</code></td><td><code>new_visit</code> <strong>[14]</strong></td></tr><tr><td><code>partners.piwik_pro.visit_counter</code></td><td><code>_idvc</code> <strong>[15]</strong></td></tr><tr><td><code>partners.piwik_pro.prev_visit</code></td><td><code>_viewts</code> <strong>[16]</strong></td></tr><tr><td><code>partners.piwik_pro.first_visit</code></td><td><code>_idts</code> <strong>[17]</strong></td></tr><tr><td><code>partners.piwik_pro.download_url</code></td><td><code>download</code> <strong>[18]</strong></td></tr><tr><td><code>partners.piwik_pro.search_categories</code></td><td><code>search_cats</code></td></tr><tr><td><code>partners.piwik_pro.search_count</code></td><td><code>search_count</code></td></tr><tr><td><code>partners.piwik_pro.last_order_timestamp</code></td><td><code>_ects</code> <strong>[19]</strong></td></tr><tr><td><code>partners.piwik_pro.custom_event_category</code></td><td><code>e_c</code> <strong>[20]</strong></td></tr><tr><td><code>partners.piwik_pro.custom_event_action</code></td><td><code>e_a</code> <strong>[21]</strong></td></tr><tr><td><code>partners.piwik_pro.custom_event_value</code></td><td><code>e_v</code> <strong>[22]</strong></td></tr><tr><td><code>partners.piwik_pro.content_name</code></td><td><code>c_n</code> <strong>[23]</strong></td></tr><tr><td><code>partners.piwik_pro.content_piece</code></td><td><code>c_p</code> <strong>[24]</strong></td></tr><tr><td><code>partners.piwik_pro.content_target</code></td><td><code>c_t</code> <strong>[25]</strong></td></tr><tr><td><code>partners.piwik_pro.content_interaction</code></td><td><code>c_i</code> <strong>[26]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** Can be used to identify visitor by the application (e.g. login name, email address or internal user ID). More details are available following: [Recognizing Visitors](https://help.piwik.pro/analytics/recognizing-visitors/?pk\_vid=16986795055e8adf).\
**\[2]** This allows you to use the application identifier of a visitor instead of a default identifier generated by Piwik PRO analytics. More details are available following: [Recognizing Visitors](https://help.piwik.pro/analytics/recognizing-visitors/?pk\_vid=16986795055e8adf). If you don't pass a value, this destination tries to recover it from the cookie named <mark style="color:blue;">`_pk_id.[Application Id].`</mark>More details are available following this [LINK](https://help.piwik.pro/support/privacy/cookies-created-for-visitors-by-piwik-pro/).\
**\[3]** Semi-unique hash generated for the visitor's browser (based on configuration and installed plugins). This parameter overwrites visitor identifier sent with <mark style="color:blue;">`_id`</mark> property.\
**\[4]** Whether the user should be tracked anonymously: <mark style="color:blue;">`1`</mark>all IP bytes will be masked (0.0.0.0), GeoIP data below country level will be anonymized, <mark style="color:blue;">`0`</mark>available visitor data will be added to the session.\
**\[5]** See [Custom Session Variables](piwik-pro.md#configuration) for more details.\
**\[6]** See [Custom Event Variables](piwik-pro.md#configuration) for more details.\
**\[7]** Screen resolution (E.g. 1920x1080).\
**\[8]** Hour, minute and second when the request was made.\
**\[9]** See [Custom Dimensions](piwik-pro.md#configuration) for more details.\
**\[10]** See [Goal Identifiers](piwik-pro.md#configuration) for more details.\
**\[11]** <mark style="color:blue;">`[Custom Product Dimension Id Y]`</mark> must be a numeric identifier starting from `1` and must be incremented for every new custom product dimension being set in [Custom Dimensions](piwik-pro.md#configuration).\
**\[12]** Sum of all product discounts.\
**\[13]** Unique page view identifier generated when the page is loaded.\
**\[14]** Force start of new visit when value is <mark style="color:blue;">`1`</mark>. Allowed values: <mark style="color:blue;">`0`</mark> or <mark style="color:blue;">`1`</mark>.\
**\[15]** Visit counter.\
**\[16]** Time of previous visit in UNIX timestamp format: number of seconds.\
**\[17]** Time of first visit.\
**\[18]** URL of downloaded file.\
**\[19]** Time of the last ecommerce order in UNIX timestamp format: number of seconds.\
**\[20]** Custom event category. More details are available following this [LINK](https://help.piwik.pro/support/reports/custom-event-report/).\
**\[21]** Custom event action. More details are available following this [LINK](https://help.piwik.pro/support/reports/custom-event-report/).\
**\[22]** Content event value. More details are available following this [LINK](https://help.piwik.pro/support/reports/custom-event-report/).\
**\[23]** Content name. More details are available following this [LINK](https://help.piwik.pro/support/reports/content-performance-report/).\
**\[24]** Content piece. More details are available following this [LINK](https://help.piwik.pro/support/reports/content-performance-report/).\
**\[25]** Content target. More details are available following this [LINK](https://help.piwik.pro/support/reports/content-performance-report/).\
**\[26]** Content interaction. More details are available following this [LINK](https://help.piwik.pro/support/reports/content-performance-report/).
{% endhint %}
