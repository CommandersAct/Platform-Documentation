# Salesforce Marketing Cloud - Data Extension Upsert Row

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Salesforce ](https://www.salesforce.com)is a cloud-based software company providing customer relationship management (CRM) software and applications focused on sales, customer service, marketing automation, analytics, and application development. Using this destination and your [segments](https://doc.commandersact.com/features/customers/segment) you can create create or update (upsert) a row in a [data extension](https://help.salesforce.com/s/articleView?id=data.c360_a_data_extensions.htm\&type=5) using Salesforce [upsertRowByKey](https://developer.salesforce.com/docs/marketing/marketing-cloud/references/mc-data_extension_rows_sync?meta=upsertRowByKey) API and enable a multitude of data activation flows like the abandoned cart.

## Key features

The Salesforce Marketing Cloud - Data Extension Upsert Row destination provides the following key features:

* **Data activation**: upserting data extensions can be used to enable various data activation flows based on the user behaviour.

## Destination setup

{% hint style="info" %}
Ensure you have access to [Salesforce Marketing Cloud](https://mc.exacttarget.com/).
{% endhint %}

### Configuration

<table><thead><tr><th width="331">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Credentials</code></td><td><em><strong><code>Required</code></strong></em> <br>Your credentials with Salesforce Marketing Cloud as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Salesforce Marketing</code>.   </td></tr><tr><td><code>Subdomain</code></td><td><em><strong><code>Required</code></strong></em> <br>The unique API subdomain for your Marketing Cloud Engagement tenant. You can find this value in the Installed Packages section of Marketing Cloud Engagement Setup.</td></tr><tr><td><code>Data Extension Id</code></td><td><em><strong><code>Required</code></strong></em> <br>The unique identifier for the data extension.</td></tr><tr><td><code>Primary Key Mapping</code></td><td><em><strong><code>Required</code></strong></em> <br>Input the name of a primary key inside your data extension in <mark style="color:blue;">Primary key name</mark>  and the value to be looked up to find the record to update in <mark style="color:blue;">Primary key value</mark>  . If the value is not found, a new record is created. One entry is required.</td></tr><tr><td><code>Record Field Mapping</code></td><td><em><strong><code>Required</code></strong></em> <br>Input the name of a field in your data extension in <mark style="color:blue;">Record field name</mark>  and the value to be updated in <mark style="color:blue;">Record field value</mark>  . One entry is required.</td></tr></tbody></table>

## Field mappings

Created data extension records include the following properties:

<table><thead><tr><th width="275">Property Name</th><th width="586">Property Value</th></tr></thead><tbody><tr><td><code>Record field name</code> <strong>[1]</strong></td><td><code>Record field value</code> <strong>[1]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\[1]** See <mark style="color:blue;">`Record Field Mapping`</mark>  in [Configuration](salesforce-marketing-cloud-data-extension-upsert-row.md#configuration) for more details.
{% endhint %}
