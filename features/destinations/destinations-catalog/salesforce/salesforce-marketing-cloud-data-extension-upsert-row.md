# Salesforce Marketing Cloud - Profile Sync (API)

[Salesforce ](https://www.salesforce.com)is a cloud-based software company providing customer relationship management (CRM) software and applications focused on sales, customer service, marketing automation, analytics, and application development. Using this destination and your [segments](https://doc.commandersact.com/features/customers/segment) you can create or update (upsert) a row in a [data extension](https://help.salesforce.com/s/articleView?id=data.c360_a_data_extensions.htm\&type=5) using Salesforce Marketing Cloud Engagement synchronous REST API [upsertRowsetByKey](https://developer.salesforce.com/docs/marketing/marketing-cloud/references/mc-data_extension_rows_sync?meta=upsertRowsetByKey) and enable a multitude of data activation flows like the abandoned cart.

## Key features

The Salesforce Marketing Cloud - Profile Sync (API) destination provides the following key features:

* **Data activation**: upserting [data extensions](https://help.salesforce.com/s/articleView?language=en_US\&id=data.c360_a_data_extensions.htm\&type=5) can be used to enable various data activation flows based on the user behaviour.
* **Support batch mode**: see section [Batch mode](salesforce-marketing-cloud-data-extension-upsert-row.md#batch-mode) for more details.
* **Easy setup:** select your data variables, in [segments](https://doc.commandersact.com/features/customers/segment), from a drop-down menu.

## Destination setup

{% hint style="info" %}
Ensure you have access to [Salesforce Marketing Cloud](https://mc.exacttarget.com/) with administrator or "Manage Connected Apps" user privileges. After authenticating, take note of the following information:\
• <mark style="color:blue;">`Client ID`</mark>\
• <mark style="color:blue;">`Client Secret`</mark>\
• <mark style="color:blue;">`Tenant-Specific Subdomain`</mark>\
You can find these values by clicking your user name in the top right corner and select <mark style="color:blue;">`Setup`</mark> . In the left-side menu, navigate to <mark style="color:blue;">`Apps`</mark> → <mark style="color:blue;">`Installed Packages`</mark> and select the package you want to use or create one by clicking <mark style="color:blue;">`New`</mark> and add a new <mark style="color:blue;">`API Integration`</mark> component.\
This information is required to set your <mark style="color:blue;">`Credentials`</mark> in the [Configuration](salesforce-marketing-cloud-data-extension-upsert-row.md#configuration) next section.
{% endhint %}

### Configuration

<table><thead><tr><th width="331">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Credentials</code></td><td><em><strong><code>Required</code></strong></em><br>Your credentials with Salesforce Marketing Cloud as set directly in your destination or, in the left menu, following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Salesforce Marketinng</code> .</td></tr><tr><td><code>Data Extension</code></td><td><em><strong><code>Required</code></strong></em><br>Select your data extension.</td></tr><tr><td><code>Primary Key Mapping</code></td><td><em><strong><code>Required</code></strong></em><br>Select the <mark style="color:blue;"><code>Data variable</code></mark> holding the primary key value to be looked up to find the record to update/insert and the <mark style="color:blue;"><code>Salesforce field</code></mark> representing the primary key column name. One entry is required.</td></tr><tr><td><code>Record Field Mapping</code></td><td><em><strong><code>Required</code></strong></em><br>Select the <mark style="color:blue;"><code>Data variable</code></mark> holding the value to update/insert and the <mark style="color:blue;"><code>Salesforce field</code></mark> representing the related field name. One entry is required.</td></tr><tr><td><code>Enable batch mode</code></td><td>When checked (default), multiple records are sent to your data extension with a single request instead of one at a time. See section <a href="salesforce-marketing-cloud-data-extension-upsert-row.md#batch-mode">Batch mode</a> for more details.</td></tr></tbody></table>

## Field mappings

Created or updated data extension records include the following properties:

<table><thead><tr><th width="275">Property Name</th><th width="586">Property Value</th></tr></thead><tbody><tr><td><code>Salesforce field</code> <strong>[1]</strong></td><td><code>Data variable</code> <strong>[1]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Record Field Mapping`</mark> in [Configuration](salesforce-marketing-cloud-data-extension-upsert-row.md#configuration) for more details.
{% endhint %}

## Batch mode

See <mark style="color:blue;">`Enable batch mode`</mark> in [Configuration](salesforce-marketing-cloud-data-extension-upsert-row.md#configuration) to manage this mode.\
Having batch mode activated has its benefits and drawbacks. See the following table for more details:

<table><thead><tr><th width="209">Activate batch mode</th><th>Benefits</th><th>Drawbacks</th></tr></thead><tbody><tr><td><strong>Not checked</strong></td><td>• Real-time requests.<br>• Better error management.</td><td>• More susceptible to <a href="salesforce-marketing-cloud-data-extension-upsert-row.md#salesforce-api-limits">Salesforce API limits</a>.</td></tr><tr><td><strong>Checked</strong></td><td>• Less susceptible to <a href="salesforce-marketing-cloud-data-extension-upsert-row.md#salesforce-api-limits">Salesforce API limits</a>.</td><td>• Slightly postponed requests.<br>• On error, all records in a single request are discarded. <strong>[1]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** Error response is inherited from the associated Salesforce API [upsertRowsetByKey](https://developer.salesforce.com/docs/marketing/marketing-cloud/references/mc-data_extension_rows_sync?meta=upsertRowsetByKey) which returns limited information for multiple records in a batch request.
{% endhint %}

## Salesforce API limits

Salesforce protects their services by placing [limits on API usage](https://help.salesforce.com/s/articleView?id=mktg.mc_overview_limits_api.htm\&type=5), resulting in the following soft limits for this destination:

* Maximum API request volume. The limit depends on your edition:
  * **Pro**: 2 million requests per year.
  * **Corporate**: 6 million requests per year.
  * **Enterprise**: 200 million requests per year.
* Maximum request rate for synchronous API requests: 2500 requests per minute across all endpoints.
* Maximum number of concurrent connections: 100 connections.
* Maximum batch size for synchronous API requests: 50 objects.
