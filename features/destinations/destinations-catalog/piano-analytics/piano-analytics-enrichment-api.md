# Piano Analytics Enrichment API

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

Piano Analytics is the successor of AT Internet Analytics Suite 2 (AS2).\
It's a user-centric tool that simplifies product & marketing analytics, while ensuring data quality.\
Using this destination you can update and/or enrich your data using [Piano Analytics Enrichment API](https://support.piano.io/hc/en-us/articles/4465975814290-Enrichments).

## Key features

The Piano Analytics Enrichment API destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model covers [Piano Analytics's templates](https://support.piano.io/hc/en-us/articles/4465975814290-Enrichments#Creation), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.&#x20;

## Destination setup

Before you get started with this destination, ensure your user has administrator or data supervisor rights

{% hint style="info" %}
You can access enrichments by going to Piano Analytics interface following<mark style="color:blue;">`Data Management`</mark> ➜ <mark style="color:blue;">`Enrichment`</mark>.
{% endhint %}

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Organization Id</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>Your organization identifier. This can be found in Piano Analytics interface following <img src="../../../../.gitbook/assets/1 (3).png" alt=""> ➜ <code>SETTINGS</code> ➜ <code>Data Management</code> ➜ <code>Enrichment</code> ➜ Edit your enrichment ➜ <code>Import Data</code> then look for the <strong>bold string</strong> in your URL: https://import.atinternet.io/<strong>[ORGANIZATION ID]</strong>/[ENRICHMENT ID]/[ENRICHMENT KEY]</p></td></tr><tr><td><code>Enrichment Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your enrichment identifier. This can be found in Piano Analytics interface following  <img src="../../../../.gitbook/assets/1 (3).png" alt=""> ➜ <code>SETTINGS</code> ➜ <code>Data Management</code> ➜ <code>Enrichment</code> ➜ Edit your enrichment ➜ <code>Import Data</code> then look for the <strong>bold string</strong> in your URL: https://import.atinternet.io/[ORGANIZATION ID]/<strong>[ENRICHMENT ID]</strong>/[ENRICHMENT KEY]</td></tr><tr><td><code>Enrichment Key</code></td><td><em><strong><code>Required</code></strong></em><br>Your enrichment key. This can be found in "Piano Analytics" interface following  <img src="../../../../.gitbook/assets/1 (3).png" alt=""> ➜ <code>SETTINGS</code> ➜ <code>Data Management</code> ➜ <code>Enrichment</code> ➜ Edit your enrichment ➜ <code>Import Data</code> then look for the <strong>bold string</strong> in your URL: https://import.atinternet.io/[ORGANIZATION ID]/[ENRICHMENT ID]/<strong>[ENRICHMENT KEY]</strong></td></tr><tr><td><code>Access Key</code></td><td><em><strong><code>Required</code></strong></em><br>Your access key. This can be found or created by following this <a href="https://user-profile.atinternet-solutions.com/#/apikeys">LINK</a>.</td></tr><tr><td><code>Secret Key</code></td><td><em><strong><code>Required</code></strong></em><br>Your secret key. This can be created by following this <a href="https://user-profile.atinternet-solutions.com/#/apikeys">LINK</a> and it's only shown at creation time.</td></tr><tr><td><code>One Hit for Each Item</code></td><td>This will instruct the destination to send one hit for each item in your "Item list". This is usefull when using the Piano Analytics "E-COMMERCE/product_id" template.</td></tr><tr><td><code>Enrichment Configuration</code></td><td>Map your properties to be enriched. Your <code>Enrichment Key</code> must me included and mapped.<br>In <code>Enrichment property name</code> set your property name in Piano Analytics to be enriched and in <code>Your value</code> your matching value. In <code>Your value path</code> you can select the level where <code>Your value</code> is located. This includes: <code>Default (root)</code>, <code>In "items" {items.X}</code> and <code>In "product" {items.X.product}</code>.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events | Piwik PRO Templates       |
| --------------------- | ------------------------- |
| `[Any Event]`         | `[Any Template]` **\[1]** |

{% hint style="info" %}
&#x20;**\[1]** Use [Destination filters](https://doc.commandersact.com/features/destinations/destination-filters) to match your events with [Piano Analytics' templates](https://support.piano.io/hc/en-us/articles/4465975814290-Enrichments#Creation).
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
Your <mark style="color:blue;">`Enrichment Key`</mark> must me included and mapped.
{% endhint %}

| Commanders Act Properties | Piano Analytics Properties |
| ------------------------- | -------------------------- |
| `[Any Property]`          | `[Any Property]` **\[1]**  |

{% hint style="info" %}
**\[1]** See [Enrichment Configuration](piano-analytics-enrichment-api.md#configuration) for more details.
{% endhint %}
