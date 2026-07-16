# Email export

### 1- Data to export

Select 1 or many segment(s) you want to export.

Select what kind of data you want to export:

* Users
* Page views
* Conversions
* Products
* Views (only available for Campaign Analytics customers)
* Clicks (only available for Campaign Analytics customers)

Select properties you want to export.

For each property, you can choose to apply the following options:

* Hash MD5
* Hash SHA256
* Deduplicate
* Convert Boolean to Integer&#x20;

{% hint style="info" %}
**About deduplication:**

If you enable deduplication on a single property, the export will contain only one occurrence per value of that property.

If you enable deduplication on multiple properties, the export will contain only one occurrence per unique combination of those properties. In other words, two rows are considered duplicates only if they share the same value for every selected property.

**Example**: if you deduplicate on _email_ and _country_, a row with (user@mail.com, France) and another with (user@mail.com, Belgium) will both be kept, since the combination of properties differs.
{% endhint %}

You can add also a static column, meaning you can set a value, and it will be exported as you entered it.

Select the data range:

* All: all stored data corresponding to what you selected
* Pick up where last export left off: differential export, you can export only records which were not exported on the last export
* Last... / Between...: select a precise period for the data range

### 2- Settings

Enter to which email addresses you want to send the raw data export.\
Multiple e-mails can be filled out, separated by commas.

Precise the filename and extension (CSV by default).

Precise if you want to include headers at the top of the file.

Precise the main separator and separator inside a variable (ex: value1,value2;value2a;value2b,value3)
