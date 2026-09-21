---
description: >-
  Import a product catalog, or any other reference table, from a file into a
  Data Store.
---

# CSV Products Importer

{% hint style="info" %}
If you want to import a product catalog into our CDP, please see the [Product catalog files importer](product-catalog-files-importer-ftp.md) page.
{% endhint %}

## What it's for

Your events carry a `product_id`, but not the margin, the price or the category. Those live in your back office. Import that catalog as a file, then use an enrichment to attach the missing attributes to your events before they reach your destinations.&#x20;

The same applies to any reference table that isn't attached to a visitor: store list, price list, mapping table.

{% hint style="info" %}
This source only fills the Data Store. Attaching the data to your events is a separate step, configured in Enrichments. All enrichment types can read from the Data Store.
{% endhint %}

This CSV importer is **not to be confused with the** **CSV Conversions Importer**, which imports `purchase` events attached to a visitor.

## Before you start

* A CSV file with a header row, one row per item, and one column that uniquely identifies each row (for example `product_id`).
* An FTP connection configured in Connector credentials.&#x20;
* Permission to create Data Stores, if you want to create one during setup rather than reuse an existing one.

## Setting up

**Sources** > **Sources catalog** > **File import** > **CSV Products Importer**.

### 1. Settings

Name and environment.

### 2. File settings

The sample file you provide here is used only to **build the mapping**. Its rows are not imported, the file is not kept, and dropping it does not count as an import. A short extract with the right headers is enough.

### 3. Data Store

Choose the Data Store that will receive your data, or create one from here.\
Only Data Stores **without user scope** are listed: this source imports reference data, not visitor data. See [Data Stores](../../../enrichments/storage-settings.md).\
Nothing is saved until the last step. A Data Store created here does not exist anywhere until you save the source.

### 4. Fields

Declare what gets stored: the field name on the left, the column of your file that feeds it on the right.\
**One field must be the matching key**. It is what makes each import an update rather than a duplicate: a row whose key already exists overwrites that record, a new key creates one. Records absent from the file are left untouched — importing a shorter file deletes nothing.

<figure><img src="../../../../.gitbook/assets/image (579).png" alt=""><figcaption></figcaption></figure>

\
If you reuse an existing Data Store, the fields are pre-filled by matching your column names against the ones already declared. Review them before activating: this is a name match, not a check of the content. The matching key and the field types come from the Data Store and cannot be changed from the source; typing a new field name adds it to the Data Store.

\
Later files are read with this same configuration: it is not asked again at each import. You can adjust it afterwards from the Fields tab of the source, for instance to change which column feeds a field.

### 5. File retrieval

Where the file is picked up, and when.

* Only run once — a single import.
* Run periodically — on a recurring schedule, optionally limited to a start and end date. Match the frequency to how often your catalog actually changes.

\
**Enable deleting the file after process** removes the file from the FTP once read. Use it if your system drops a new file each time; leave it off if the same file is overwritten in place.\
Set the alert addresses under **Notifications**: a failed import is otherwise silent until someone notices missing data downstream.

## What happens on each import

| Situation                            | Result                                                     |
| ------------------------------------ | ---------------------------------------------------------- |
| Row with no value in the key column  | Row skipped, import continues                              |
| Same key twice in one file           | The last row wins                                          |
| Malformed row                        |  The import stops there; rows already written stay written |

## Checking that it works

The contents of a Data Store cannot be browsed record by record. Two things to look at:

* the Records (24h) column in the Data Stores list, which shows what came in over the last 24 hours;
* the Live Event Inspector, which shows whether a live event was actually enriched. This is the real test.

\
If an event arrives without the expected attributes, three causes are possible and worth distinguishing: the import did not run, the value of the key on the event doesn't exist in your catalog, or the enrichment isn't configured to add that field.

## Limitations

* One matching key per Data Store, changed from the Data Store itself, never from the source. To reconcile on a second key, use a second Data Store.
* Changing the matching key of a Data Store that already holds records creates a duplicate set on the next import: existing records are not reindexed. Create a new Data Store instead.
* Records cannot be viewed, edited or deleted individually.
* Update only: replacing the whole catalog or appending without updating is not available.
* Records never expire. An obsolete entry stays until a later import overwrites it.
* Deleting the Data Store does not delete the source, but the source then has no target and must be reconnected before it produces anything.
