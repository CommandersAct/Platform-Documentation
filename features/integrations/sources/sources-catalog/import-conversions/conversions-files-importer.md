# Conversions files importer

If you wish to share your data via flat file feed integration, please use a CSV feed format, following the structure below.

{% hint style="info" %}
The CSV format is based on the comma-separated value. The header must be declared in the first row of the file, it is recommended that headers are provided in the lower case and don't contain spaces.
{% endhint %}

Files can be uploaded to the Commandersact FTP or downloaded from your own FTP by CommandersAct. Get in touch with your Account Manager to agree the integration method that is best for you.

Use our CSV conversion importer connector to configure the FTP import.

### Structure of the file:

#### 1 file with 1 line per product (conversion item)

Each line in the file should be a distinct product (conversion item) with their unit price and quantity. Transactions that include several products should be split into multiple lines, sharing the same conversion\_id.&#x20;

Example:\
conversion\_ID\_1, conversion\_item\_1, \
conversion\_ID\_1, conversion\_item\_2, \
conversion\_ID\_1, conversion\_item\_3,&#x20;

{% hint style="danger" %}
Be sure you are using exactly the same headers as in this example CSV file:&#x20;
{% endhint %}

{% file src="../../../../../.gitbook/assets/csv_conversions_import_one_file.csv" %}
Template CSV conversions import
{% endfile %}

{% hint style="danger" %}
Some columns are **required**, please check this [link](api-conversions-and-product-catalog.md) to see which fields are required or not.
{% endhint %}

{% hint style="warning" %}
Please sort your file and group it by conversion ID (all conversion items related to conversion\_ID\_1 then all conversion items related to conversion\_ID\_2 etc...)
{% endhint %}
