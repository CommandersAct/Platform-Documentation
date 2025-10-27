# Salesforce Marketing Cloud - Data Extension Upsert Row

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Salesforce ](https://www.salesforce.com)is a cloud-based software company providing customer relationship management (CRM) software and applications focused on sales, customer service, marketing automation, analytics, and application development. Using this integration and your [segments](https://doc.commandersact.com/features/customers/segment) you can create or update (upsert) a row in a [data extension](https://help.salesforce.com/s/articleView?id=data.c360_a_data_extensions.htm\&type=5) using Salesforce Marketing Cloud Engagement synchronous REST API and enable a multitude of data activation flows like the abandoned cart.

## Key features

The Salesforce Marketing Cloud - Data Extension Upsert Row destination provides the following key features:

* **Data activation**: upserting [data extensions](https://help.salesforce.com/s/articleView?language=en_US\&id=data.c360_a_data_extensions.htm\&type=5) can be used to enable various data activation flows based on the user behaviour.
* **Two versions**: See section [Available versions](salesforce-marketing-cloud-data-extension-upsert-row.md#available-versions) for more details.
* **Easy setup:** select your data variables, in [segments](https://doc.commandersact.com/features/customers/segment), from a drop-down menu.&#x20;

## Available versions

This integration is provided in the form of two separate destination versions:

1. **Standard**
2. **Batch**

With the **Batch** version, multiple records are sent to your data extension with a single request while with the **Standard** version each request includes only one record.\
Both versions have their benefits and drawbacks that are inherited from the associated Salesforce API: [upsertRowByKey](https://developer.salesforce.com/docs/marketing/marketing-cloud/references/mc-data_extension_rows_sync?meta=upsertRowByKey) and [upsertRowsetByKey](https://developer.salesforce.com/docs/marketing/marketing-cloud/references/mc-data_extension_rows_sync?meta=upsertRowsetByKey) respectively - See the following table for more details:

<table><thead><tr><th width="167">Version</th><th>Benefits</th><th>Drawbacks</th></tr></thead><tbody><tr><td><strong>Standard</strong></td><td>• Real-time requests.<br>• Better error management.</td><td>• More  susceptible to <a href="salesforce-marketing-cloud-data-extension-upsert-row.md#salesforce-api-limits">Salesforce API limits</a>.</td></tr><tr><td><strong>Batch</strong></td><td>• Less susceptible to <a href="salesforce-marketing-cloud-data-extension-upsert-row.md#salesforce-api-limits">Salesforce API limits</a>.</td><td>• Slightly postponed requests.<br>• On error, all records are discarded.</td></tr></tbody></table>

## Destination setup

{% hint style="info" %}
Ensure you have access to [Salesforce Marketing Cloud](https://mc.exacttarget.com/) with administrator or "Manage Connected Apps" user privileges. After authenticating, take note of the following information:\
• <mark style="color:blue;">`Client ID`</mark>\
• <mark style="color:blue;">`Client Secret`</mark>\
• <mark style="color:blue;">`Tenant-Specific Subdomain`</mark>\
You can find these values by clicking your user name in the top right corner and select <mark style="color:blue;">`Setup`</mark> . In the left-side menu, navigate to <mark style="color:blue;">`Apps`</mark>  → <mark style="color:blue;">`Installed Packages`</mark> and select the package you want to use or create one by clicking <mark style="color:blue;">`New`</mark>  and add a new <mark style="color:blue;">`API Integration`</mark>  component.\
This information is required to set your <mark style="color:blue;">`Credentials`</mark> . See the next section [Configuration](salesforce-marketing-cloud-data-extension-upsert-row.md#configuration) for more details.
{% endhint %}

### Configuration

<table><thead><tr><th width="331">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Credentials</code></td><td><em><strong><code>Required</code></strong></em> <br>Your credentials with Salesforce Marketing Cloud as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Salesforce Marketinng</code> .</td></tr><tr><td><code>Data Extension Id</code></td><td><em><strong><code>Required</code></strong></em> <br>The unique identifier for the data extension.</td></tr><tr><td><code>Primary Key Mapping</code></td><td><em><strong><code>Required</code></strong></em> <br>Select the <mark style="color:blue;"><code>Data variable</code></mark>  holding the primary key value to be looked up to find the record to update/insert and input the <mark style="color:blue;"><code>Salesforce column</code></mark>  representing the primary key column name. One entry is required.</td></tr><tr><td><code>Record Field Mapping</code></td><td><em><strong><code>Required</code></strong></em> <br>Select the <mark style="color:blue;"><code>Data variable</code></mark>  holding the value to update/insert and input the <mark style="color:blue;"><code>Salesforce column</code></mark>  representing the related field name.</td></tr></tbody></table>

## Field mappings

Created data extension records include the following properties:

<table><thead><tr><th width="275">Property Name</th><th width="586">Property Value</th></tr></thead><tbody><tr><td><code>Salesforce column</code> <strong>[1]</strong></td><td><code>Data variable</code> <strong>[1]</strong></td></tr></tbody></table>

## Salesforce API limits

Salesforce protects their services [by placing limits on API usage](https://app.gitbook.com/u/TyQmmynWMvMlk9NdUinevOT5XTl2), resulting in the following soft limits for this integration:

* Maximum API request volume. The limit depends on your edition:
  * **Pro**: 2 million requests per year
  * **Corporate**: 6 million requests per year
  * **Enterprise**: 200 million requests per year
* Maximum request rate for synchronous API requests: 2500 requests per minute across all endpoints.
* Maximum number of concurrent connections: 100 connections.

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Record Field Mapping`</mark>  in [Configuration](salesforce-marketing-cloud-data-extension-upsert-row.md#configuration) for more details.
{% endhint %}
