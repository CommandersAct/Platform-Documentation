# Google BigQuery

[BigQuery](https://cloud.google.com/bigquery/docs/introduction?hl=en) is Google's data warehouse that enables scalable analysis over data. This integration allows pushing your specific input properties, or all of them, to BigQuery.

## Key features

The Google BigQuery destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) feeds BigQuery, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Multi schema support**: store event data following your preferred/existing schema or we can help you creating an [universal one](google-bigquery.md#universal-schema).
* **Data control**: select your properties or just check a box to send them all to BigQuery.

## Destination setup

{% hint style="info" %}
Ensure [BigQuery API](https://console.cloud.google.com/apis/library/bigquery.googleapis.com?project=gtm-mw9cdnc-ntexy) is enabled. More details are available following this [LINK](https://cloud.google.com/bigquery/docs/enable-transfer-service?hl=en#enable-api).\
Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to refine events and/or other properties matching your specific needs.
{% endhint %}

### Configuration

| Settings                          | Description                                                                                                                                                                                                                                                                   |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Authentication`                  | <p><em><strong><code>Required</code></strong></em>   <br>Your credentials with Google as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>BigQuery</code></p> |
| `Project Id`                      | <p><em><strong><code>Required</code></strong></em> <br>Select your project identifier from the dropdown menu as reported in BigQuery console. More details are available following this <a href="https://support.google.com/googleapi/answer/7014113?hl=en">LINK</a>.</p>     |
| `Dataset Id`                      | <p><em><strong><code>Required</code></strong></em> <br>Select your dataset identifier as reported in BigQuery console. More details are available following this <a href="https://cloud.google.com/bigquery/docs/datasets-intro?hl=en">LINK</a>.</p>                          |
| `Table Id`                        | <p><em><strong><code>Required</code></strong></em> <br>Select table identifier as reported in BigQuery console. More details are available following this <a href="https://cloud.google.com/bigquery/docs/tables-intro?hl=en">LINK</a>.</p>                                   |
| `Send all properties to BigQuery` | Flag this option to send all properties to BigQuery following a specific schema: see section [Universal schema](google-bigquery.md#universal-schema) for more details.                                                                                                        |
| `Auto-discover table structure`   | Check this option to enable the auto-discover table structure feature.                                                                                                                                                                                                        |
| `Event property Mapping`          | When `Auto-discover table structure`  is flagged, you can map your BigQuery fields by selecting them in the `BigQuery column` and input the properties holding their value in `Event property` .                                                                              |

## Universal schema

{% hint style="info" %}
The following steps are not required if you checked `Auto-discover table structure` .
{% endhint %}

When flagging `Send all properties to BigQuery` an specific schema is required. See the following subsections to learn how you can create an universal schema. This is not&#x20;

### Dataset

Access [BigQuery console](https://console.cloud.google.com/) to locate your `(1)` project identifier and click `(2)` the `three dots` on the right. Select `(3)` `Create dataset` from the menu or, alternatively, you can use an existing dataset and jump to the [next subsection](google-bigquery.md#table).

<figure><img src="../../../../.gitbook/assets/bigquery_1 (2).png" alt=""><figcaption><p>Dataset creation #1.</p></figcaption></figure>

Input a `(4)` dataset identifier (E.g. "myDatasetId"), select a `(5)` location type and click `(6)` `CREATE DATASET`.

<figure><img src="../../../../.gitbook/assets/bigquery_2.png" alt=""><figcaption><p>Dataset creation #2.</p></figcaption></figure>

### Table

Create a table with the following structure:

| Field name | Type      | Mode     |
| ---------- | --------- | -------- |
| rawDataCa  | String    | Required |
| createdAt  | Timestamp | Required |

The esiest way to create it is to click `(7)` the `plus` button:

<figure><img src="../../../../.gitbook/assets/bigquery_3 (1).png" alt=""><figcaption><p>Compose a new query.</p></figcaption></figure>

copy and paste the following query in `(8)` the input area:

```powerquery
CREATE TABLE IF NOT EXISTS [PROJECT_ID].[DATASET_ID].[TABLE_ID] (rawDataCa STRING NOT NULL, createdAt TIMESTAMP NOT NULL) OPTIONS(description="CA raw event data stored in Google BigQuery")
```

{% hint style="info" %}
Replace `[PROJECT_ID]` , `[DATASET_ID]` and `[TABLE_ID]` with your project, dataset and table identifier respectively. You set your table identifier at this step.
{% endhint %}

and then click the `(9)` `RUN` button.

<figure><img src="../../../../.gitbook/assets/bigquery_4.png" alt=""><figcaption><p>Run table creation query.</p></figcaption></figure>

### Quick reference

| Commanders Act Events   | BigQuery Table Columns             |
| ----------------------- | ---------------------------------- |
| `[Any events]` **\[1]** | `rawDataCa`, `createdAt` **\[2]**  |

{% hint style="info" %}
**\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.\
&#xNAN;**\[2]** Two columns: <mark style="color:blue;">`rawDataCa`</mark> contains your event properties, while <mark style="color:blue;">`createdAt`</mark> is the creation timestamp.
{% endhint %}

