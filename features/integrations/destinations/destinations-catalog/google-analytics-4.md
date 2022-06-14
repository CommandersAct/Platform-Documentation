# Google Analytics 4

Google Analytics 4 (GA4) is the latest iteration of Google's analytics tool that helps you measure the traffic and engagement across your websites and apps. Using this destination, you can enhance your existing tracking implementation to match your data collection needs with GA4.\
Your data will be sent server-side taking advantage of the [Google Measurement Protocol API](https://developers.google.com/analytics/devguides/collection/protocol/ga4) and in form of [events](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/events).

{% hint style="info" %}
The "Measurement Protocol" is designed to enrich existing events via client-side gtag or Firebase. Sending events to GA4 just by using the "Measurement Protocol" is viable, however, it comes with limitations on available reporting. Some event and parameter names are [reserved](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?#reserved\_names) for use via automatic collection and can't be pushed through the "Measurement Protocol".

The user identifier should be passed in both the client-side gtag and server-side.\
For more information, you can follow these links: [\[GA4\] Measure activity across platforms with User-ID](https://support.google.com/analytics/answer/9213390) and [\[GA4\] Reporting: deduplicate user counts](https://support.google.com/analytics/answer/9355949).

When Google Signals is enabled, same device remarketing is supported. For cross-device remarketing, the user identifier is additionally required.

Geographic information is only available via automatic collection from gtag, Google Tag Manager, or Google Analytics for Firebase.
{% endhint %}

## Key features

The Google Analytics 4 destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model fits [Google's one](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/events), meaning that your data is properly bridged to the expected fields in an optimized and proper way.
* **Prebuilt mappings**: data mapping for events-based destinations happens automatically, which simplifies user inputs.
* **Refined data**: you can freely push additional information based on your specific needs (E.g. adding custom events, custom event and user properties).
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is dispatched to GA4.

## Destination setup

Before you get started with this destination, ensure you have a GA4 property in your Google  Analytics account. You can find more information on this topic following these detailed articles:

* [\[GA4\] Set up Analytics for a website and/or app](https://support.google.com/analytics/answer/9304153)
* [Add a Google Analytics 4 property (to a site that already has Analytics)](https://support.google.com/analytics/answer/9744165?hl=en)

### Getting started

1. From your Commanders Act account, locate the section **INTEGRATIONS** (top-left), then click **Destinations** and **Overview**.
2. Click the button **Add Destination**.
3. Search for "**Google Analytics 4**" and click it.
4. Click **Configure** (top-right).
5. In **Data Source**, **** select your **Sources** and **Events** that will send data to GA4 and click **Next**.
6. In **Settings**, input a **Destination name** and select an **Environment**.
7. Input your **API Secret** and **Measurement ID**.
8. You can map your **Custom Event Properties** and **Custom User Properties** by clicking **Add row**.
9. In **Advanced**, you can set a **Client Id Cookie Name** and **Engagement Time in Milliseconds**.
10. In **Debug View**, you can flag **Enable debug mode**.

### Configuration

| Settings                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| API Secret                      | <p><em><code>Required</code></em></p><p>The <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_query_parameters"><strong>API Secret</strong></a> is generated through Google Analytics. To create this value, navigate in the Google Analytics interface following: <br>Admin > Data Streams > choose your stream > Measurement Protocol > Create.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Measurement Id                  | <p><em><code>Required</code></em></p><p>The <a href="https://support.google.com/analytics/answer/7372977"><strong>Measurement Id</strong></a> identifies a Data Stream. Found in the Google Analytics interface following: <br>Admin > Data Streams > choose your stream > Measurement Id. E.g. "G-XXXXXXXXXX".</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Custom Event Properties         | <p>Map your custom event properties by setting their field names in <strong>Event properties name</strong> and adding the field name holding the <strong>Value</strong> in the related field. E.g. if you input "<em>size</em>" in the <strong>Event properties name</strong> and "<em>properties.items.0.product.size</em>" in <strong>Value</strong>, you will have a custom event property in GA4 called "<em>size</em>" with a value based on the content of the field "<em>properties.items.0.product.size</em>" <strong>[1]</strong>. You also have the option to set a static string/numeric value in <strong>Value</strong>.<br><br>To ensure that custom event properties are picked up by GA4, you must create event-scoped dimensions. You can find more details by following this link: <a href="https://support.google.com/analytics/answer/10075209">[GA4] Custom dimensions and metrics</a>. </p>                                                                                                                                     |
| Custom User Properties          | <p>Map your <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/user-properties">custom user properties</a> by setting their field names in <strong>User properties name</strong> and adding the field name holding the <strong>Value</strong> in the related field.<br>E.g. if you input "<em>customer</em>_<em>zipcode" in</em> <strong>User properties name</strong> <em></em> and "properties.user.zipcode" <em></em> in <strong>Value</strong>, you will have a custom user property in GA4 called "<em>customer_zipcode</em>" with a value based on the content of the field "properties.user.zipcode" <em></em> <strong>[1]</strong>. You also have the option to set a static string/numeric value in <strong>Value</strong>.</p><p></p><p>To ensure that custom user properties are picked up by GA4, you must create user-scoped dimensions. You can find more details by following this link: <a href="https://support.google.com/analytics/answer/10075209">[GA4] Custom dimensions and metrics</a>. </p> |
| Client Id Cookie Name           | <p>Cookie name holding the Google Analytics <a href="https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference?client_type=gtag#payload_query_parameters">Client Id</a> that uniquely identifies a user instance of a web client. You can change its default value: "<em>_ga</em>".</p><p><br>The Client Id is the right most string in the cookie. E.g "GA1.1.<strong>XXXXXXXXXX.XXXXXXXXXX".</strong></p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Engagement Time in Milliseconds | GA4 reports only show active users who engage with your site for a non-zero amount of time. To ensure users are included in reports, you can keep the default value to 1. If you track the actual engagement time with your events, you can set the [**Engagement Time in Milliseconds**](https://developers.google.com/analytics/devguides/collection/protocol/ga4/sending-events?client\_type=gtag#optional\_parameters\_for\_reports) with an actual value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Enable debug mode               | Under Debug View, you can flag this option to enable [Debug Mode](https://developers.google.com/analytics/devguides/collection/ga4/debug?technology=websites), sending the field "_debug\_mode_" set to "_true_" on each event. It enables GA4 [DebugView](https://support.google.com/analytics/answer/7201382) monitoring feature.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |



{% hint style="info" %}
**\[1]** Using "dots" (".") you can navigate deeper to the specific field you want to get the value of. See [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) for more details on the standard field names by event. You can also freely set custom fields: there are no boundaries.&#x20;
{% endhint %}

## Mapping to GA4 events

This destination provides automatic mapping between our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model and GA4 events. In this section, you will learn what properties are set so you can expect to see those details in GA4 reporting.

{% hint style="info" %}
Properties reported in **bold** are required.

More details on GA4 standard events are available following this [LINK](https://developers.google.com/analytics/devguides/collection/protocol/ga4/reference/events).

To ensure that custom event properties are picked up by GA4, you must create event-scoped dimensions. You can find more details by following this link: [\[GA4\] Custom dimensions and metrics](https://support.google.com/analytics/answer/10075209).
{% endhint %}

### add\_payment\_info

| Property       | Description                                                                         | Field           | Mapped with                  |
| -------------- | ----------------------------------------------------------------------------------- | --------------- | ---------------------------- |
| **Currency**   | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_      | _properties.currency_        |
| **Value**      | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_         | _properties.value_           |
| Coupon         | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                   | _coupon_        | _properties.coupon_          |
| Payment Method | <p>Type: <em><code>String</code></em><br>The payment method.</p>                    | _payment\_type_ | _properties.payment\_method_ |
| Revenue        | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>              | _revenue_       | _properties.revenue_         |
| **Items**      | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_         | _properties.items_           |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### add\_shipping\_info

| Property      | Description                                                                                                                    | Field            | Mapped with               |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------ | ---------------- | ------------------------- |
| **Currency**  | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                            | _currency_       | _properties.currency_     |
| **Value**     | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                                                           | _value_          | _properties.value_        |
| Coupon        | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                                                              | _coupon_         | _properties.coupon_       |
| Shipping Tier | <p>Type: <em><code>String</code></em><br>The shipping tier (E.g. <code>Next-day</code>) selected for delivery of the item.</p> | _shipping\_tier_ | properties.shipping\_tier |
| **Items**     | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>                                                 | _items_          | _properties.items_        |

####

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### add\_to\_cart

| Property     | Description                                                                         | Field      | Mapped with           |
| ------------ | ----------------------------------------------------------------------------------- | ---------- | --------------------- |
| **Currency** | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| **Value**    | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| **Items**    | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### add\_to\_wishlist

| Property     | Description                                                                         | Field      | Mapped with           |
| ------------ | ----------------------------------------------------------------------------------- | ---------- | --------------------- |
| **Currency** | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| **Value**    | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| **Items**    | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### begin\_checkout

| Property     | Description                                                                         | Field      | Mapped with           |
| ------------ | ----------------------------------------------------------------------------------- | ---------- | --------------------- |
| **Currency** | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| **Value**    | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| Coupon       | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                   | _coupon_   | _properties.coupon_   |
| Revenue      | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>              | _revenue_  | _properties.revenue_  |
| **Items**    | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### generate\_lead

| Currency       | Description                                                                         | Field      | Mapped with           |
| -------------- | ----------------------------------------------------------------------------------- | ---------- | --------------------- |
| **Currency**   | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| **Value**      | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| Transaction Id | <p>Type: <em><code>String</code></em><br>The transaction identifier.</p>            | _id_       | _properties.id_       |

### login

| Property | Description                                                    | Field    | Mapped with         |
| -------- | -------------------------------------------------------------- | -------- | ------------------- |
| Method   | <p>Type: <em><code>String</code></em><br>The login method.</p> | _method_ | _properties.method_ |

### page\_view

| Property      | Description                                                           | GA4 field        | Mapped with             |
| ------------- | --------------------------------------------------------------------- | ---------------- | ----------------------- |
| Page Location | <p>Type: <em><code>String</code></em></p><p>The current page URL.</p> | _page\_location_ | _properties.url_        |
| Page Referrer | <p>Type: <em><code>String</code></em><br>The previous page URL.</p>   | _page\_referrer_ | _properties.referrer_   |
| Page Title    | <p>Type: <em><code>String</code></em><br>The current page title.</p>  | _page\_title_    | _properties.title_      |
| Page Name     | <p>Type: <em><code>String</code></em><br>The current page name.</p>   | _page\_name_     | _properties.page\_name_ |
| Page Type     | <p>Type: <em><code>String</code></em><br>The current page type.</p>   | _page\_type_     | _properties.page\_type_ |
| Page Path     | <p>Type: <em><code>String</code></em><br>The current page path.</p>   | _page\_path_     | _properties.path_       |

### purchase

| Property           | Description                                                                         | Field                | Mapped with                  |
| ------------------ | ----------------------------------------------------------------------------------- | -------------------- | ---------------------------- |
| **Currency**       | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_           | _properties.currency_        |
| **Value**          | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_              | _properties.value_           |
| **Transaction Id** | <p>Type: <em><code>String</code></em><br>The transaction identifier.</p>            | _id_                 | _properties.id_              |
| Affiliation        | <p>Type: <em><code>String</code></em><br>Affiliation information.</p>               | affiliation          | _properties.affiliation_     |
| Coupon             | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                   | _coupon_             | _properties.coupon_          |
| Shipping           | <p>Type: <em><code>Number</code></em><br>Shipping cost.</p>                         | _shipping_           | properties.shipping\_amount  |
| Tax                | <p>Type: <em><code>Number</code></em><br>Tax amount.</p>                            | _tax_                | properties.tax\_amount       |
| Revenue            | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>              | _revenue_            | _properties.revenue_         |
| Conversion Type    | <p>Type: <em><code>String</code></em><br>The conversion type.</p>                   | _conversion\_type_   | _properties.type_            |
| Conversion Status  | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                 | _conversion\_status_ | _properties.status_          |
| Conversion Url     | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                 | _conversion\_url_    | _properties.url_             |
| Payment Method     | <p>Type: <em><code>String</code></em><br>The payment method.</p>                    | _payment\_type_      | _properties.payment\_method_ |
| **Items**          | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_              | _properties.items_           |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### refund

| Property           | Description                                                                         | Field                | Mapped with                 |
| ------------------ | ----------------------------------------------------------------------------------- | -------------------- | --------------------------- |
| **Currency**       | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_           | _properties.currency_       |
| **Value**          | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_              | _properties.value_          |
| **Transaction Id** | <p>Type: <em><code>String</code></em><br>The transaction identifier.</p>            | _id_                 | _properties.id_             |
| Affiliation        | <p>Type: <em><code>String</code></em><br>Affiliation information.</p>               | affiliation          | _properties.affiliation_    |
| Coupon             | <p>Type: <em><code>String</code></em><br>Coupon code applied.</p>                   | _coupon_             | _properties.coupon_         |
| Shipping           | <p>Type: <em><code>Number</code></em><br>Shipping cost.</p>                         | _shipping_           | properties.shipping\_amount |
| Tax                | <p>Type: <em><code>Number</code></em><br>Tax amount.</p>                            | _tax_                | properties.tax\_amount      |
| Revenue            | <p>Type: <em><code>Number</code></em><br>The revenue of the event.</p>              | _revenue_            | _properties.revenue_        |
| Conversion Type    | <p>Type: <em><code>String</code></em><br>The conversion type.</p>                   | _conversion\_type_   | _properties.type_           |
| Conversion Status  | <p>Type: <em><code>String</code></em><br>The conversion status.</p>                 | _conversion\_status_ | _properties.status_         |
| Conversion Url     | <p>Type: <em><code>String</code></em><br>The conversion url.</p>                    | _conversion\_url_    | _properties.url_            |
| Payment Method     | <p>Type: <em><code>String</code></em><br>The payment method.</p>                    | _payment\_type_      | properties.payment\_method  |
| Items              | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_              | _properties.items_          |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### remove\_from\_cart

| Property     | Description                                                                         | Field      | Mapped with           |
| ------------ | ----------------------------------------------------------------------------------- | ---------- | --------------------- |
| **Currency** | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| **Value**    | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| **Items**    | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### search

| Property         | Description                                                                  | Field          | Mapped with               |
| ---------------- | ---------------------------------------------------------------------------- | -------------- | ------------------------- |
| **Search Term**  | <p>Type: <em><code>String</code></em><br>The term that was searched for.</p> | _search\_term_ | _properties.search\_term_ |

### select\_content

| Property     | Description                                                                                | Field           | Mapped with                |
| ------------ | ------------------------------------------------------------------------------------------ | --------------- | -------------------------- |
| Content Type | <p>Type: <em><code>String</code></em><br>The term that was searched for.</p>               | _content\_type_ | _properties.content\_type_ |
| Item Id      | <p>Type: <em><code>String</code></em><br>An identifier for the item that was selected.</p> | _item\_id_      | properties.item\_id        |

### select\_item

| Property       | Description                                                                                                    | Field              | Mapped with                   |
| -------------- | -------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------- |
| Item List Name | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p> | _item\_list\_name_ | _properties.item\_list\_name_ |
| **Items**      | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>                                 | _items_            | _properties.items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### sign\_up

| Property    | Description                                                               | Field    | Mapped with         |
| ----------- | ------------------------------------------------------------------------- | -------- | ------------------- |
| **Method**  | <p>Type: <em><code>String</code></em><br>The method used for sign up.</p> | _method_ | _properties.method_ |

### view\_cart

| Property     | Description                                                                         | Field      | Mapped with           |
| ------------ | ----------------------------------------------------------------------------------- | ---------- | --------------------- |
| **Currency** | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| **Value**    | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| **Items**    | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### view\_item

| Property     | Description                                                                         | Field      | Mapped with           |
| ------------ | ----------------------------------------------------------------------------------- | ---------- | --------------------- |
| **Currency** | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p> | _currency_ | _properties.currency_ |
| **Value**    | <p>Type: <em><code>Number</code></em><br>The value of the event.</p>                | _value_    | _properties.value_    |
| **Items**    | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>      | _items_    | _properties.items_    |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### view\_item\_list

| Property       | Description                                                                                                    | Field              | Mapped with                   |
| -------------- | -------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------- |
| Item List Name | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p> | _item\_list\_name_ | _properties.item\_list\_name_ |
| **Items**      | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>                                 | _items_            | _properties.items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

### \[Custom Event]

You have the option to send custom events to better fit your specific needs.

{% hint style="info" %}
More details on how you can create and manage custom events are available following this link: [\[GA4\] Modify and create events via the user interface](https://support.google.com/analytics/answer/10085872)
{% endhint %}

| Property          | Description                                                                                                                                          | Field                | Mapped with                   |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | ----------------------------- |
| Currency          | <p>Type: <em><code>String</code></em><br><em><code></code></em>Currency, in 3-letter ISO 4217 format.</p>                                            | _currency_           | _properties.currency_         |
| Value             | <p>Type: <em><code>Number</code></em><br><em><code></code></em>The value of the event.</p>                                                           | _value_              | _properties.value_            |
| Transaction Id    | <p>Type: <em><code>String</code></em><br><em><code></code></em>The transaction identifier.</p>                                                       | _id_                 | _properties.id_               |
| Content Type      | <p>Type: <em><code>String</code></em><br><em><code></code></em>The transaction identifier.</p>                                                       | _content\_type_      | _properties.content\_type_    |
| Conversion Type   | <p>Type: <em><code>String</code></em><br><em><code></code></em>The conversion type.</p>                                                              | _conversion\_type_   | _properties.type_             |
| Conversion Status | <p>Type: <em><code>String</code></em><br><em><code></code></em>The conversion status.</p>                                                            | _conversion\_status_ | _properties.status_           |
| Conversion Url    | <p>Type: <em><code>String</code></em><br><em><code></code></em>The conversion url.</p>                                                               | _conversion\_url_    | _properties.url_              |
| Coupon            | <p>Type: <em><code>String</code></em><br><em><code></code></em>Coupon code applied.</p>                                                              | _coupon_             | _properties.coupon_           |
| Item Id           | <p>Type: <em><code>String</code></em><br><em><code></code></em>An identifier for the item that was selected.</p>                                     | _item\_id_           | _properties.item\_id_         |
| Item List Name    | <p>Type: <em><code>String</code></em><br><em><code></code></em>The name of the list in which the item was presented to the user.</p>                 | _item\_list\_name_   | _properties.item\_list\_name_ |
| Method            | <p>Type: <em><code>String</code></em><br><em></em> Method used.</p>                                                                                  | _method_             | _properties.method_           |
| Page Location     | <p>Type: <em><code>String</code></em><br><em><code></code></em>The current page URL.</p>                                                             | _page\_location_     | _properties.url_              |
| Page Referrer     | <p>Type: <em><code>String</code></em><br><em><code></code></em>The previous page URL.</p>                                                            | _page\_referrer_     | _properties.referrer_         |
| Page Title        | <p>Type: <em><code>String</code></em><br><em><code></code></em>The current page title.</p>                                                           | _page\_title_        | _properties.title_            |
| Page Name         | <p>Type: <em><code>String</code></em><br><em><code></code></em>The current page name.</p>                                                            | _page\_name_         | _properties.page\_name_       |
| Page Type         | <p>Type: <em><code>String</code></em><br><em><code></code></em>The current page type.</p>                                                            | _page\_type_         | _properties.page\_type_       |
| Page Path         | <p>Type: <em><code>String</code></em><br><em><code></code></em>The current page type.</p>                                                            | _page\_path_         | _properties.path_             |
| Payment Method    | <p>Type: <em><code>String</code></em><br><em></em>The payment method.</p>                                                                            | _payment\_type_      | _properties.payment\_method_  |
| Revenue           | <p>Type: <em><code>Number</code></em><br><em><code></code></em>The revenue of the event.</p>                                                         | _revenue_            | _properties.revenue_          |
| Search Term       | <p>Type: <em><code>String</code></em><br><em></em>The term that was searched for.</p>                                                                | _search\_term_       | _properties.search\_term_     |
| Shipping Tier     | <p>Type: <em><code>String</code></em><br><em><code></code></em>The shipping tier (E.g. <code>Next-day</code>) selected for delivery of the item.</p> | _shipping\_tier_     | _properties.shipping\_tier_   |
| Shipping          | <p>Type: <em><code>Number</code></em><br><em><code></code></em>Shipping cost.</p>                                                                    | _shipping_           | properties.shipping\_amount   |
| Tax               | <p>Type: <em><code>Number</code></em><br><em><code></code></em>Tax amount.</p>                                                                       | _tax_                | properties.tax\_amount        |
| Items             | <p>Type: <em><code>Array</code></em><br>The list of products of the event.</p>                                                                       | _items_              | _properties.items_            |

#### Items

| Property        | Description                                                                                                                             | Field              | Mapped with                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------ | ----------------------------------------- |
| **Item Id**     | <p>Type: <em><code>String</code></em><br>The ID of the item.</p>                                                                        | _item\_id_         | _properties.items.X.id_                   |
| **Item Name**   | <p>Type: <em><code>String</code></em><br>The name of the item.</p>                                                                      | _item\_name_       | _properties.items.X.product.name_         |
| Affiliation     | <p>Type: <em><code>String</code></em><br>A product affiliation to designate a supplying company or brick and mortar store location.</p> | _affiliation_      | _properties.items.X.product.affiliation_  |
| Coupon          | <p>Type: <em><code>String</code></em><br>The coupon name/code associated with the item.</p>                                             | _coupon_           | _properties.items.X.coupon_               |
| Currency        | <p>Type: <em><code>String</code></em><br>Currency, in 3-letter ISO 4217 format.</p>                                                     | _currency_         | _properties.items.X.product.currency_     |
| Discount        | <p>Type: <em><code>Number</code></em><br>The monetary discount value associated with the item.</p>                                      | _discount_         | _properties.items.X.discount_             |
| Index           | <p>Type: <em><code>Number</code></em><br>The index/position of the item in a list.</p>                                                  | _index_            | _properties.items.X._list\_position       |
| Item Brand      | <p>Type: <em><code>String</code></em><br>The brand of the item.</p>                                                                     | _item\_brand_      | _properties.items.X.product.brand_        |
| Item Category   | <p>Type: <em><code>String</code></em><br>The category of the item.</p>                                                                  | _item\_category_   | _properties.items.X.product.category\_1_  |
| Item Category 2 | <p>Type: <em><code>String</code></em><br>The second category hierarchy or additional taxonomy for the item.</p>                         | _item\_category2_  | _properties.items.X.product.category\_2_  |
| Item Category 3 | <p>Type: <em><code>String</code></em><br>The third category hierarchy or additional taxonomy for the item.</p>                          | _item\_category3_  | _properties.items.X.product.category\_3_  |
| Item Category 4 | <p>Type: <em><code>String</code></em><br>The fourth category hierarchy or additional taxonomy for the item.</p>                         | _item\_category4_  | _properties.items.X.product.category\_4_  |
| Item Category 5 | <p>Type: <em><code>String</code></em><br>The fifth category hierarchy or additional taxonomy for the item.</p>                          | _item\_category5_  | _properties.items.X.product.category\_5_  |
| Item List Id    | <p>Type: <em><code>String</code></em><br>The ID of the list in which the item was presented to the user.</p>                            | _item\_list\_id_   | _properties.items.X.product.list\_id_     |
| Item List Name  | <p>Type: <em><code>String</code></em><br>The name of the list in which the item was presented to the user.</p>                          | _item\_list\_name_ | _properties.items.X.product.list\_name_   |
| Item Variant    | <p>Type: <em><code>String</code></em><br>The item variant or unique code or description for additional item details/options.</p>        | _item\_variant_    | _properties.items.X.variant_              |
| Location Id     | <p>Type: <em><code>String</code></em><br>The location associated with the item.</p>                                                     | _location\_id_     | _properties.items.X.product.location\_id_ |
| Price           | <p>Type: <em><code>Number</code></em><br>The monetary price of the item, in units of the specified currency parameter.</p>              | _price_            | _properties.items.X.product.price_        |
| Quantity        | <p>Type: <em><code>Number</code></em><br>Item quantity.</p>                                                                             | _quantity_         | _properties.items.X.quantity_             |

## Quick reference

| Commanders Act Events | GA4 Events          |
| --------------------- | ------------------- |
| `add_payment_info`    | `add_payment_info`  |
| `add_shipping_info`   | `add_shipping_info` |
| `add_to_cart`         | `add_to_cart`       |
| `add_to_wishlist`     | `add_to_wishlist`   |
| `begin_checkout`      | `begin_checkout`    |
| `generate_lead`       | `generate_lead`     |
| `login`               | `login`             |
| `page_view`           | `page_view`         |
| `purchase`            | `purchase`          |
| `refund`              | `refund`            |
| `remove_from_cart`    | `remove_from_cart`  |
| `search`              | `search`            |
| `select_content`      | `select_content`    |
| `select_item`         | `select_item`       |
| `sign_up`             | `sign_up`           |
| `view_cart`           | `view_cart`         |
| `view_item`           | `view_item`         |
| `view_item_list`      | `view_item_list`    |
| `[Custom Event]`      | `[Custom Event]`    |

## Limitations

Sending events to GA4 has the following limitations:

* Events can have a maximum of 25 parameters.
* Events can have a maximum of 25 user properties.
* User property names must be 24 characters or fewer.
* User property values must be 36 characters or fewer.
* Event names must be 40 characters or fewer, may only contain alpha-numeric characters and underscores, and must start with an alphabetic character.
* Parameter names (including item parameters) must be 40 characters or fewer, may only contain alpha-numeric characters and underscores, and must start with an alphabetic character.
* Parameter values (including item parameter values) must be 100 character or fewer.
* Item parameters can have a maximum of 10 custom parameters.

