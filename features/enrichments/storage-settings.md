---
description: >-
  A Data Store holds data that the platform looks up later to enrich your
  events. Each record is retrieved through its matching key.
---

# Data Stores

## Choosing the type

You pick the type when you create the Data Store, and **it cannot be changed afterwards**.

|                             | Linked to a user                                                  | No user                                                                        |
| --------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Holds                       | Data attached to a visitor, identified or not                     | Reference data that exists on its own: product catalog, store list, price list |
| Stored data is described as | Properties of an event                                            | Fields of a row                                                                |
| Fed by                      | Events collected by your sources                                  | A file import                                                                  |
| Matching key                | A field that leads to a visitor: `email`, `user_id`, `session_id` | A field unique to each row: `product_id`, `store_code`                         |
| Consent                     | Applies                                                           | Not applicable                                                                 |
| Retention                   | Up to 730 days                                                    | None, no expiry                                                                |
| Filters                     | Available                                                         | Not available                                                                  |

<figure><img src="../../.gitbook/assets/image (582).png" alt=""><figcaption></figcaption></figure>

The type describes what the data is, not how it arrives. A file can contain events — the CSV Conversions Importer works that way — and those belong in a Data Store linked to a user.

\
The sources you are offered are filtered to match the type. If a source you expect is missing from a list, this is why.

{% hint style="warning" %}
A Data Store holds one kind of data, not both. To cross browsing data with a reference table, use two Data Stores and two enrichments.
{% endhint %}

## **Creating a Data Store**

Data Governance > Data Stores > Add Data Store. Name it, choose the type, then fill in the fields that appear.

### Linked to a user

* **Sources and environment** — which sources feed it.
* **Consent category** — the consent scope under which the data is stored. Ensure compliance with data privacy regulations.
* **Event** — which event the properties are taken from.
* **Properties** — click Add/Edit Properties to open the side panel, or turn on the top toggle to store everything.

{% hint style="success" %}
Nested formats are allowed, see [Check Properties format](storage-settings.md#check-properties-format) below.
{% endhint %}

* **Matching key** — must be present and identical on both the stored event and the event to be enriched.
* **Filters (optional)** — store only the events meeting a condition.
* **Retention period** — how long stored events are kept, up to 730 days.

{% hint style="success" %}
Retention affects credit consumption. Choose a duration that matches your use case rather than the maximum.
{% endhint %}

### **No user**

* **Fields** — the columns stored for each row.
* **Matching key** — tick the one field that identifies a row. Exactly one, and it is required.<br>

Consent, event, filters and retention don't apply here. Records never expire, which also means an obsolete entry stays until a later import overwrites it.\
You can create the Data Store empty and connect a source later, or let the import wizard create it. See [CSV Products Importer](../sources/sources-catalog/product-catalog/products-file-importer.md).

### Editing and deleting

<figure><img src="../../.gitbook/assets/image (604).png" alt=""><figcaption></figcaption></figure>

#### Editing

**Linked to a user**: properties can be added or removed at any time.\
**No user**: fields can be added, renamed or removed at any time, from the Data Store. Existing records only carry a new field once they are imported again.<br>

In both cases the matching key is modified from the Data Store, not from the source: the sources feeding it pick up the change.

{% hint style="danger" %}
Changing the matching key of a Data Store that already holds records does not reindex them.&#x20;

Records written afterwards use the new key, alongside the old ones, which stay in place and will never be matched or updated again. Prefer creating a new Data Store over changing the key of one already in use — all the more so without user scope, where records have no expiry and cannot be deleted individually.
{% endhint %}

#### Deleting

Deleting a Data Store is possible for both types, and **does not delete the sources that feed it.** For an import source, this leaves it with no target: reconnect it to a Data Store before using it again.&#x20;

If an enrichment stops finding data with no other explanation, check that its Data Store still exists.



## **Tips and tricks**

{% hint style="info" %}
The following section applies only to the Data Stores of the type: **linked to a user**.&#x20;
{% endhint %}

### Check if the property already exist

Natively, a Storage Settings will not enrich a property if it does already exists in the event to be enriched.\
\
If the property already exists, but you really need to change the value with your enrichment, don't forget to check the "override" option in your [enrichment configuration](https://app.commandersact.com/en/4452/sources/privacy-banners/?p=/en/4452/containers/privacy/settings/1/demo-iab-ii).

This override feature can also be applied to arrays values.

### Check Properties format

It is not possible to enrich a property with a different type other than the standard one expected in your enrichment.\
Basic example:\
Sending a Number value to enrich a String type property\
`storage > "items.product.quantity": 2 >> enrich >> "items.product.color": N/A`\
This won't work, you'll get a [warning error](storage-settings.md#errors) instead of an enriched property. You can easily identify it, with the following message in "details": `'type error, number cannot replace a string'`

### **Consent properties**

Avoid any enrichment of the `user.consent_categories` property.\
This relates to the user's legal choice about the collection/tracking of personal data.\
Enriching this property may create a risk of non-compliance.

### Warnings Errors

If there's an anomaly in your storage, you may see a "warnings" property in the Live Event Inspector.

Located within the event that should have been enriched, if the enrichment doesn't apply as expected you'll see this "warnings" property, including details for an easy understanding

```json
            warnings: [
                {
                    type: 'enrichment',
                    step: 'saveHit',
                    path: 'event.items',
                    detail: {
                        message: 'type error, object cannot replace array',
                    },
                },
            ],
```

### **Specific cases - Objects**

You can store an entire Object, (example: `items.product`) but you can also store only single key(s) extracted from an Object (example: `items.product.price`).\
If you are saving single keys, be sure that the destination event has already the Object defined.\
Otherwise the single key will not enrich anything.\
The warnings message will contain the following detail:\
`message:` '`should merge object properties that do not exist in target'`

#### **Multiple Objects reconciliation**

If you store a property that occurs in several objects, be careful!\
Our matching mechanism is based on ID's.\
As an example, you have many `items.product` objects and you need to store `items.product.brand` property.\
We will use the `items.product.id` as matching key to fill the different `items.product` objects.\
If there's no "ID" property inside your object, we will simply fed in the same order then it was stored.\
In this case, the following "warnings" details will be added to your enrichment\
`message: 'No ID field found, falling back to index-based merge',`

#### Override usage

Be careful when using the Override option!\
Overriding an entire object will block the "non-override" of a single key\
Example of a bad practice:

`items.product.color` << _override: false_ >> `items.product.defaultColor`\
`items` << _override: true_ >> `items`

The data from the `items.product.color` value is overridden because the second line has priority.

### Best Practice : filter's usage

Of course, the filters set in your destinations will be applied.\
So why should you use the Storage Settings filters?\
We provide the filters at this level simply to save you Storage fees (credit consumption), and to simplify the processing on your destinations.

Same quality of enrichment, for lower fees!
