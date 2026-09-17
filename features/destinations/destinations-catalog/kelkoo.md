---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Kelkoo

[Kelkoo](https://www.kelkoo.com) is a price comparison service. Using this destination you can activate server-side tracking as a fallback method to increase coverage.

## Key features

The Kelkoo destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) matches [Kelkoo conversion tracking](https://developers.kelkoogroup.com/app/documentation/navigate/_merchant/salesTrackingWS/_/_Installation_Advanced/ServerToServer), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://doc.commandersact.com/developers/tracking/events-reference#item) array is dispatched to Kelkoo.

## Destination setup

### Configuration

<table data-header-hidden="false" data-header-sticky><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Shop Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your unique shop identifier within the Kelkoo Group system (<code>comId</code>).</td></tr><tr><td><code>Country</code></td><td><em><strong><code>Required</code></strong></em><br>The 2-letter country code for the country on which your products are listed on Kelkoo Group (E.g. <code>fr</code>).</td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | Kelkoo Tracking    |
| ---------------------- | ------------------ |
| `[Any Event]` **\[1]** | `[Any Conversion]` |

{% hint style="info" %}
**1.** Use [Destination filters](https://doc.commandersact.com/features/destinations/destination-filters) to refine events matching your specific needs.
{% endhint %}

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Smart Mapping Fields</th><th>Commanders Act Default Properties</th><th>Kelkoo Properties</th></tr></thead><tbody><tr><td><code>-</code></td><td><code>Country</code></td><td><code>country</code></td></tr><tr><td><code>-</code></td><td><code>Shop Id</code></td><td><code>comId</code></td></tr><tr><td><code>Transaction Id</code></td><td><code>id</code></td><td><code>orderId</code></td></tr><tr><td><p><code>Item Name</code></p><p><code>Item Id</code></p><p><code>Item Price</code></p><p><code>Item Quantity</code></p></td><td><code>items.X.product.name</code> <br><code>items.X.id</code> <br><code>items.X.product.price</code> <br><code>items.X.quantity</code></td><td><code>productsInfos</code> <strong>[1]</strong></td></tr><tr><td><code>Kelkoo Id</code></td><td><code>partners.kelkoo.id</code></td><td><code>kelkooId</code></td></tr><tr><td><code>Google Click Id</code></td><td><code>partners.kelkoo.gclid</code></td><td><code>gclid</code></td></tr><tr><td><code>Microsoft Click Id</code></td><td><code>partners.kelkoo.msclkid</code></td><td><code>msclkid</code></td></tr><tr><td><code>User Status</code></td><td><code>user.status</code> <strong>[2]</strong></td><td><code>returningUser</code></td></tr></tbody></table>

{% hint style="info" %}
**1.** Automatically encoded in base64url. More details are available by following this [LINK](https://developers.kelkoogroup.com/app/documentation/navigate/_merchant/salesTrackingWS/_/_Installation_Advanced/ServerToServer).\
**2.** Supported values: <mark style="color:blue;">`New`</mark> or <mark style="color:blue;">`Existing`</mark> (case insensitive).
{% endhint %}
