# Econda

[Econda](https://www.dymatrix.de/en) is web analytics tool under the [DYMATRIX brand](https://www.dymatrix.de/en/econda-is-now-dymatrix). Using this destination, you can implement server-side tracking.

## Key features

The Econda destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports Econda event types, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to Econda.
* **Connection management**: events are sent again in case of congestion or network issues.

## Destination setup

### Configuration

| Settings                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Client Key`              | <p><em><strong><code>Required</code></strong></em><br>Your client key as reported in Econda interface under <code>Configuration</code> → <code>Analytics JS Library</code> .</p>                                                                                                                                                                                                                                                                                                                                                                           |
| `Custom Event Mapping`    | Change the standard mapping between Econda event types and your events or add new mappings. See [Quick reference](econda.md#quick-reference) for more details.                                                                                                                                                                                                                                                                                                                                                                                             |
| `Custom Event Properties` | Map your custom event properties by setting their field names in `Econda property name` and adding the values in `Your value` . In the column `Your value path` you should keep the default value `Default (root)` as it better fits most scenarios. In case you select either `In "items" {items.X}` or `In "product" {items.X.product}` , the `Your value` must be set with a property name and this destination will look for the provided property name starting from the items or product level respectively and set the value in Econda `ec_Event` . |

## Quick reference

| Commanders Act Events | Econda Event Types         |
| --------------------- | -------------------------- |
| `add_to_cart`         | `c_add`                    |
| `add_to_wishlist`     | `wlist_add`                |
| `purchase`            | `buy`                      |
| `view_item`           | `view`                     |
| `[Any other event]`   | `[No event type]` **\[1]** |

{% hint style="info" %}
**\[1]** Other events are supported and no specific Econda event type is set.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
For Econda, visits and sessions are the same and they are based on the distinct value count for the property <mark style="color:blue;">`sid`</mark>. Additionally, Econda has a timeout set by default with 30 minutes, which can be changed, so even with the same <mark style="color:blue;">`sid`</mark> the session counter will increase after the timeout has passed.\
Visitors are based on the property <mark style="color:blue;">`vid`</mark> and its distinct count.\
An additional custom property <mark style="color:blue;">`retry_count`</mark> is set with the number of send retries due to Econda endpoint congestion or connection interruptions.
{% endhint %}

<table><thead><tr><th width="391.6685580062746">Commanders Act Properties</th><th>Econda Properties</th></tr></thead><tbody><tr><td><code>context.event_id</code></td><td><code>rid</code> <strong>[*]</strong></td></tr><tr><td><code>context.device.lifecycle.session_id</code></td><td><code>sid</code> <strong>[*]</strong></td></tr><tr><td><code>user.consistent_anonymous_id</code></td><td><code>vid</code> <strong>[*]</strong></td></tr><tr><td><code>context.page.location.hostname</code></td><td><code>host</code> <strong>[*][1]</strong></td></tr><tr><td><code>partners.econda.site_id</code></td><td><code>siteid</code> <strong>[2]</strong></td></tr><tr><td><code>partners.econda.category_path</code></td><td><code>content</code> <strong>[3]</strong></td></tr><tr><td><code>partners.econda.country_id</code></td><td><code>countryid</code> <strong>[4]</strong></td></tr><tr><td><code>context.device.lang</code></td><td><code>langid</code></td></tr><tr><td><code>partners.econda.order_process</code></td><td><code>orderProcess</code> <strong>[5]</strong></td></tr><tr><td><code>partners.econda.source</code></td><td><code>source</code></td></tr><tr><td><code>partners.econda.campaign</code></td><td><code>camp</code></td></tr><tr><td><code>partners.econda.privacy_mode</code></td><td><code>prv</code> <strong>[6]</strong></td></tr><tr><td><code>id</code></td><td><code>billing.0</code> <strong>[7]</strong></td></tr><tr><td><code>user.id</code></td><td><code>billing.1</code> <strong>[7]</strong></td></tr><tr><td><code>user.country</code><br><code>user.city</code><br><code>user.zipcode</code></td><td><code>billing.2</code> <strong>[7][8]</strong></td></tr><tr><td><code>value</code></td><td><code>billing.3</code> <strong>[7]</strong></td></tr><tr><td>See <code>Econda Event Types</code> in <a href="econda.md#quick-reference">Quick Reference</a></td><td><code>ec_Event.0.type</code></td></tr><tr><td><code>items.X.id</code></td><td><code>ec_Event.0.pid</code></td></tr><tr><td><code>items.X.product.id</code></td><td><code>ec_Event.0.sku</code></td></tr><tr><td><code>items.X.product.name</code></td><td><code>ec_Event.0.name</code></td></tr><tr><td><code>items.X.product.price</code></td><td><code>ec_Event.0.price</code></td></tr><tr><td><code>partners.econda.category_path</code> <strong>[9]</strong><br><code>items.X.product.category_1</code> <strong>[10]</strong></td><td><code>ec_Event.0.group</code></td></tr><tr><td><code>items.X.quantity</code></td><td><code>ec_Event.0.count</code></td></tr><tr><td><code>search_term</code></td><td><code>search.0.0</code> <strong>[11]</strong></td></tr><tr><td><code>search_results_number</code></td><td><code>search.0.1</code> <strong>[11]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>ip</code></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>ua</code></td></tr><tr><td><code>user.email</code></td><td><code>hashedvalue</code> <strong>[12]</strong></td></tr><tr><td><code>Cookie TCAUDIENCE</code> <strong>[13]</strong><br><code>DataSegments</code></td><td><code>usertype</code> <strong>[14]</strong></td></tr><tr><td><code>partners.econda.recipient_id</code></td><td><code>newsuid</code> <strong>[15]</strong></td></tr><tr><td><code>partners.econda.newsmid</code></td><td><code>newsmid</code> <strong>[16]</strong></td></tr><tr><td><code>partners.econda.target_group</code></td><td><code>Target.0</code> <strong>[17]</strong></td></tr><tr><td><code>partners.econda.target_name</code></td><td><code>Target.1</code></td></tr><tr><td><code>partners.econda.target_value</code></td><td><code>Target.2</code></td></tr><tr><td><code>partners.econda.target_rule</code></td><td><code>Target.3</code></td></tr><tr><td><code>partners.econda.marker_name</code></td><td><code>marker</code> <strong>[18]</strong></td></tr><tr><td><code>partners.econda.onsite_cmp_seen1</code></td><td><code>icampv.0</code> <strong>[19]</strong></td></tr><tr><td><code>partners.econda.onsite_cmp_seen2</code></td><td><code>icampv.1</code> <strong>[19]</strong></td></tr><tr><td><code>partners.econda.onsite_cmp_seen3</code></td><td><code>icampv.2</code> <strong>[19]</strong></td></tr><tr><td><code>partners.econda.onsite_cmp_click1</code></td><td><code>icampc.0</code> <strong>[20]</strong></td></tr><tr><td><code>partners.econda.onsite_cmp_click2</code></td><td><code>icampc.1</code> <strong>[20]</strong></td></tr><tr><td><code>partners.econda.onsite_cmp_click3</code></td><td><code>icampc.2</code> <strong>[20]</strong></td></tr><tr><td><code>context.device.screen.width</code><br><code>context.device.screen.height</code><br><code>context.device.screen.zoom_factor</code></td><td><code>swsh</code> <strong>[21]</strong></td></tr><tr><td><code>user.id</code></td><td><code>login.0.0</code></td></tr><tr><td><code>user.login_success</code></td><td><code>login.0.1</code> <strong>[22]</strong></td></tr><tr><td><code>video_title</code></td><td><code>media.0</code></td></tr><tr><td><code>event_name</code></td><td><code>media.1</code> <strong>[23]</strong></td></tr><tr><td><code>cursor_position</code></td><td><code>media.3</code></td></tr><tr><td><code>total_length</code></td><td><code>media.4</code></td></tr><tr><td><code>partners.econda.tspageload</code></td><td><code>media.5</code></td></tr><tr><td><code>partners.econda.video_index_position</code></td><td><code>media.6</code></td></tr><tr><td><code>context.page.url</code></td><td><code>media.7</code></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
\&#xNAN;**\[1]** If it's not provided, the "Smart Mapping" field <mark style="color:blue;">`Page URL (host)`</mark> is used to retrieve the hostname.\
\&#xNAN;**\[2]** the name of the website to be measured, as configured by DYMATRIX Support. This is usually the main domain, without the leading "www.".\
\&#xNAN;**\[3]** A unique identifier for the content of the current website. By entering forward slashes ( <mark style="color:blue;">`/`</mark> ), the website context (E.g. the path) can be transferred and analyzed in a summarized form at a later time.\
\&#xNAN;**\[4]** The country identifier allows you to differentiate your website for different countries.\
\&#xNAN;**\[5]** Here you can monitor the purchase process. A typical purchase process in an online store consists of several steps that the customer must complete before the purchase is completed. These include filling the shopping cart, entering billing information, etc. (E.g. <mark style="color:blue;">`02_login`</mark> ).\
\&#xNAN;**\[6]** Privacy mode as defined in Econda.\
\&#xNAN;**\[7]** Set when the Econda event type is `buy` . See [Quick reference](econda.md#quick-reference) for more details.\
\&#xNAN;**\[8]** Set with the value of the fields on the left and separated by the character forward slash ( <mark style="color:blue;">`/`</mark> ).\
\&#xNAN;**\[9]** Property used when Econda event types is <mark style="color:blue;">`view`</mark> .\
\&#xNAN;**\[10]** Property used when Econda event types is <mark style="color:blue;">`buy`</mark> .\
\&#xNAN;**\[11]** Set when a [search event](../../../developers/tracking-and-integrations/) is triggered.\
\&#xNAN;**\[12]** If provided in clear text, it's automatically hashed via SHA256.\
\&#xNAN;**\[13]** More details are available following this [LINK](https://doc.commandersact.com/configure/cookies#data).\
\&#xNAN;**\[14]** This two-dimensional array is set with the user segments provided. Priority on the left side. `DataSegments` must be a single dimension array with the user segment names provided at the index `0` and separated by the comma character. (E.g. <mark style="color:blue;">`["USER_SEGMENT_NAME_1,USER_SEGMENT_NAME_2...."]`</mark> ).\
\&#xNAN;**\[15]** Newsletter recipient identifier as used in the ESP.\
\&#xNAN;**\[16]** Newsletter identifier.\
\&#xNAN;**\[17]** Target/goal group (E.g. <mark style="color:blue;">`newsletter subscription`</mark> )\
\&#xNAN;**\[18]** Markers are measurement tools that allow you to place "light barriers" on a website. As soon as a visitor passes a light barrier, the contribution of this measurement point to achieving the defined goal is recorded and thus made transparent (E.g. <mark style="color:blue;">`SubscriptionClick`</mark>).\
\&#xNAN;**\[19]** With on-site campaigns, you use relevant areas of your website for sales-promoting marketing campaigns, e.g., in the form of on-site banners. Send the names of on-site campaign banners being seen (E.g. <mark style="color:blue;">`Summer Sale`</mark>): you can send up to three names.\
\&#xNAN;**\[20]** Send the names of on-site campaign banners being clicked (E.g. <mark style="color:blue;">`Summer Sale`</mark> ): you can send up to three names.\
\&#xNAN;**\[21]** E.g. <mark style="color:blue;">`1280x1024|1.5`</mark> .\
\&#xNAN;**\[22]** Set with `0` on sucessful login, otherwise <mark style="color:blue;">`1`</mark> . Default value: <mark style="color:blue;">`0`</mark> .\
\&#xNAN;**\[23]** Supported video events [Video Playback Started](../../../developers/tracking/events-reference/video-event-reference.md), [Video Playback Paused](../../../developers/tracking/events-reference/video-event-reference.md), and [Video Playback Completed](../../../developers/tracking/events-reference/video-event-reference.md): this property is set with either <mark style="color:blue;">`play`</mark>, <mark style="color:blue;">`pause`</mark> or <mark style="color:blue;">`ended`</mark> respectively.
{% endhint %}
