# Clinch Conversions API

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Clinch's platform](https://www.clinch.co/) is used for omnichanel content orchestration. Using this destination you can activate server-to-server tracking to send events to Clinch.

## Key features

The Clinch Conversions API destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) model covers Clinch's event types, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Event mapping**: change standard mapping between Clinch events and yours.
* **Support for multi-item data**: information included in the [item](https://doc.commandersact.com/developers/tracking/events-reference#item) array is dispatched to Clinch.

## Destination setup

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Client Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your encoded client identifier (cid). You can find this value in Clinch interface by following <code>Accounts</code> → <code>Data Sources</code> after creating a <code>Website Pixel</code>. Here you can find the <code>Advertiser ID (cid)</code>.</td></tr><tr><td><code>Data Source Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your encoded data source identifier (dsid). You can find this value in Clinch interface by following <code>Accounts</code> → <code>Data Sources</code> after creating a <code>Website Pixel</code>. Here you can find the <code>Pixel ID (dsid)</code>.</td></tr><tr><td><code>Event Mapping</code></td><td>Change the standard mapping between Clinch event types and your events or add new mappings. Accepted value for <code>Clinch event type</code>: <code>PageView</code>, <code>HomePage</code>, <code>Landing</code>, <code>Search</code>, <code>Category</code>, <code>Details</code>, <code>DetailsExit</code>, <code>AddToCart</code>, <code>RemFromCart</code>, <code>CartPage</code>, <code>AddToWishList</code>, <code>Checkout</code>, <code>conv</code>, <code>Registration</code> and <code>OfflineConv</code>.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Clinch Event Types                                                                                                            |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `page_view`           | <p><code>HomePage</code> <strong>[1]</strong></p><p><code>Landing</code> <strong>[2]</strong></p><p><code>PageView</code></p> |
| `search`              | `Search`                                                                                                                      |
| `view_item_list`      | `Category`                                                                                                                    |
| `view_item`           | `Details`                                                                                                                     |
| `add_to_cart`         | `AddToCart`                                                                                                                   |
| `remove_from_cart`    | `RemFromCart`                                                                                                                 |
| `view_cart`           | `CartPage`                                                                                                                    |
| `add_to_wishlist`     | `AddToWishList`                                                                                                               |
| `begin_checkout`      | `Checkout`                                                                                                                    |
| `purchase`            | <p><code>OfflineConv</code> <strong>[3]</strong></p><p><code>conv</code></p>                                                  |
| `generate_lead`       | `Registration`                                                                                                                |
| `[Any Other Event]`   | `Other`                                                                                                                       |
| `[Any Event]`         | `[Any Event]` **\[4]**                                                                                                        |

{% hint style="info" %}
**1.** Set if property <mark style="color:blue;">`page_type`</mark> is <mark style="color:blue;">`home`</mark> .\
**2.** Set if property <mark style="color:blue;">`page_type`</mark> is <mark style="color:blue;">`landing`</mark> .\
**3.** Set if property <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`offline`</mark> .\
**4.** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](clinch-conversions-api.md#configuration).
{% endhint %}

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th width="361">Smart Mapping Field</th><th width="423">Commanders Act Default Properties</th><th width="393">Clinch Properties</th></tr></thead><tbody><tr><td><code>-</code></td><td><code>Client Id</code></td><td><code>cid</code> <strong>[*]</strong></td></tr><tr><td><code>-</code></td><td><code>Data Source Id</code></td><td><code>dsid</code> <strong>[*]</strong></td></tr><tr><td><code>Device IP</code></td><td><code>context.device.ip</code></td><td><code>user_ip</code> <strong>[*]</strong></td></tr><tr><td><code>Device User Agent</code></td><td><code>context.device.user_agent</code></td><td><code>user_agent</code> <strong>[*]</strong></td></tr><tr><td><code>Page URL</code></td><td><code>context.page.url</code></td><td><code>referrer</code> <strong>[*]</strong></td></tr><tr><td><code>Event Timestamp</code></td><td><code>context.event_timestamp</code></td><td><code>timestamp</code></td></tr><tr><td><code>Vendor Partner Id</code></td><td><code>partners.clinch.partner</code></td><td><code>partner</code></td></tr><tr><td><code>Clinch Cookie Id</code></td><td><code>partners.clinch.clinch_sid</code></td><td><code>clinch-sid</code> <strong>[1]</strong></td></tr><tr><td><code>Clinch Click Id</code></td><td><code>partners.clinch.click_id</code></td><td><code>clinchClickId_[Client Id]</code> <strong>[2]</strong></td></tr><tr><td><code>User Email</code></td><td><code>user.email</code></td><td><code>hem</code> <strong>[3]</strong></td></tr><tr><td><code>Device Mobile Identifier</code></td><td><code>context.device.advertising_id</code></td><td><code>did</code></td></tr><tr><td><code>Liveramp ATS Envelope</code></td><td><code>partners.clinch.ats_envelop</code></td><td><code>atsEnvelop</code></td></tr><tr><td><code>Uid2</code></td><td><code>partners.clinch.uid2</code></td><td><code>uid2</code></td></tr><tr><td><code>-</code></td><td><code>(event_name)</code></td><td><code>type</code> <strong>[4]</strong></td></tr><tr><td><code>Event Secondary Type</code></td><td><code>partners.clinch.stype</code></td><td><code>stype</code> <strong>[5]</strong></td></tr><tr><td><code>Product Type</code></td><td><code>partners.clinch.product</code></td><td><code>product</code> <strong>[6]</strong></td></tr><tr><td><code>Item List</code></td><td><code>items</code></td><td><code>-</code></td></tr><tr><td><code>Item Id</code></td><td><code>items.X.id</code></td><td><code>ids</code> <strong>[7]</strong></td></tr><tr><td><code>Product Category</code></td><td><code>partners.clinch.category</code></td><td><code>category</code></td></tr><tr><td><code>Recommended Item Id</code></td><td><code>items.X.rec_id</code></td><td><code>recommended</code> <strong>[7]</strong></td></tr><tr><td><code>Search Term</code></td><td><code>search_term</code></td><td><code>term</code></td></tr><tr><td><code>Origin City/Airport IATA Code</code></td><td><code>partners.clinch.from</code></td><td><code>from</code></td></tr><tr><td><code>Destination City/Airport IATA Code</code></td><td><code>partners.clinch.to</code></td><td><code>to</code></td></tr><tr><td><code>Departure</code></td><td><code>partners.clinch.departure</code></td><td><code>depart</code></td></tr><tr><td><code>Return</code></td><td><code>partners.clinch.return</code></td><td><code>return</code></td></tr><tr><td><code>City Code</code></td><td><code>partners.clinch.city</code></td><td><code>city</code></td></tr><tr><td><code>Transaction Id</code></td><td><code>id</code></td><td><code>orderId</code></td></tr><tr><td><code>Transaction Value</code></td><td><code>value</code></td><td><code>amount</code></td></tr><tr><td><code>Currency</code></td><td><code>currency</code></td><td><code>currency</code></td></tr><tr><td><code>TCF String</code></td><td><code>partners.clinch.tcf_string</code></td><td><code>tcf_string</code></td></tr><tr><td><code>US Privacy String</code></td><td><code>partners.clinch.usp_string</code></td><td><code>usp_string</code></td></tr><tr><td><code>Global Privacy Platform</code></td><td><code>partners.clinch.gpp_string</code></td><td><code>gpp_string</code></td></tr><tr><td><code>GPP Enforced Section Ids</code></td><td><code>partners.clinch.gpp_sid</code></td><td><code>gpp_sid</code></td></tr><tr><td><code>User Tags</code></td><td><code>partners.clinch.utags</code></td><td><code>utags</code></td></tr></tbody></table>

{% hint style="info" %}
**\*** Mandatory property.\
**1.** Default value: from cookie <mark style="color:blue;">`clinch-sid`</mark> .\
**2.** Default value: from parameter <mark style="color:blue;">`clinchClickId_[Client Id]`</mark> in <mark style="color:blue;">`Page URL`</mark> or cookie with the same name.\
**3.** Automatically hashed if passed in clear text.\
**4.** See [Quick reference](clinch-conversions-api.md#quick-reference).\
**5.** Default value: from property <mark style="color:blue;">`event_name`</mark> .\
**6.** Accepted values: <mark style="color:blue;">`Ecommerce`</mark>, <mark style="color:blue;">`Flight`</mark>, <mark style="color:blue;">`Hotel`</mark> and <mark style="color:blue;">`Car`</mark>.\
**7.** Comma-separated string with all product identifiers.
{% endhint %}
