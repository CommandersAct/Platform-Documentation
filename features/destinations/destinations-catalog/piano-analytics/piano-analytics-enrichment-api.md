# Piano Analytics Enrichment API

Piano Analytics is the successor of AT Internet Analytics Suite 2 (AS2) and a user-centric tool that simplifies product & marketing analytics, while ensuring data quality.\
Using this destination you can connect your catalogs to your behavioral data in Piano Analytics by using [Piano Catalogs API](https://developers.piano.io/analytics/data-collection/import/catalogs/).

{% hint style="info" %}
Catalogs are the natural evolution of Piano Analytics's enrichments. If you have already configured enrichments, these were seamlessly migrated to catalogs.&#x20;
{% endhint %}

## Key features

The Piano Analytics Enrichment API destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model supports [Piano Analytics catalog's data structure](https://developers.piano.io/analytics/data-collection/import/catalogs/#payload), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.

## Destination setup

Before you get started with this destination, ensure your user has administrator or data supervisor rights and you have created and configured an catalog/enrichment.

{% hint style="info" %}
You can create/access catalogs by going to Piano Analytics interface following ![](<../../../../.gitbook/assets/1 (3).png>) ➜ <mark style="color:blue;">`SETTINGS`</mark> ➜ <mark style="color:blue;">`Data Management`</mark> ➜ <mark style="color:blue;">`Catalogs`</mark>.
{% endhint %}

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Access Key</code></td><td><em><strong><code>Required</code></strong></em><br>Your access key. This can be found or created by following this <a href="https://user-profile.atinternet-solutions.com/#/apikeys">LINK</a>.</td></tr><tr><td><code>Secret Key</code></td><td><em><strong><code>Required</code></strong></em><br>Your secret key. This can be created by following this <a href="https://user-profile.atinternet-solutions.com/#/apikeys">LINK</a> and it's only shown at creation time.</td></tr><tr><td><code>Catalog Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your catalog (import) identifier. This can be found in Piano Analytics interface following <img src="../../../../.gitbook/assets/1 (3).png" alt=""> ➜ <code>SETTINGS</code>➜ <code>Data Management</code> ➜ <code>Catalogs</code> (left menu) <strong>→</strong> Click you catalog in the list <strong>→</strong> Click the <code>Import data</code> tab <strong>→</strong> <code>Catalog ID</code>.</td></tr><tr><td><code>Catalog Key</code></td><td><em><strong><code>Required</code></strong></em><br>Your catalog (reconciliation) key. This can be found in Piano Analytics interface following <img src="../../../../.gitbook/assets/1 (3).png" alt=""> ➜ <code>SETTINGS</code>➜ <code>Data Management</code> ➜ <code>Catalogs</code> (left menu) ➜ Click you catalog in the list ➜ Click the <code>Structure</code> tab ➜ look for the line with <code>Role</code> equals to <code>Reconciliation key</code> and use the value in the column <code>Property key</code>.</td></tr><tr><td><code>One Hit for Each Item</code></td><td>This will instruct the destination to send one hit for each item in your "Item list". This is usefull when using the Piano Analytics <code>E-COMMERCE/product_id</code> template.</td></tr><tr><td><code>Enrichment Configuration</code></td><td>Map your properties to be updated/enriched. Your <code>Catalog Key</code> must me included and mapped.<br>In <code>Your value path</code>, when selecting a value different from "Default (root)", you need to set a property name in <code>Your value</code>.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Piano Analytics Templates |
| --------------------- | ------------------------- |
| `[Any Event]`         | `[Any Template]` **\[1]** |

{% hint style="info" %}
> **1.** Use [Destination filters](https://doc.commandersact.com/features/destinations/destination-filters) to match your events with Piano Analytics' templates.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

{% hint style="warning" %}
Your selected catalog key must me included and mapped.
{% endhint %}

| Commanders Act Properties | Piano Analytics Properties |
| ------------------------- | -------------------------- |
| `[Any Property]`          | `[Any Property]` **\[1]**  |

{% hint style="info" %}
> **1.** See [Enrichment Configuration](piano-analytics-enrichment-api.md#configuration) for more details.
{% endhint %}
