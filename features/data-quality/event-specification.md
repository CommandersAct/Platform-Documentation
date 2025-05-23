# Event Specification

In the _Event Specification_ interface, you will be able to define the **schema of your data** and determine the [actions ](event-specification.md#validation-rule-actions)to be taken if an event does not conform your **event specifications** (aka validation rules)

Adding event specifications allows you to define the payload and what is expected, so that you can see if the data is meeting those specifications, in case there are any errors.

Then, in the [Source data quality](data-quality.md) view, you are able to define an automatic alert or see the summary of all specification violations, so that you fix it at your source or with the live [Data Cleansing](data-cleansing/) feature

<figure><img src="../../.gitbook/assets/NDL1.png" alt=""><figcaption></figcaption></figure>

You can choose to add a [standard event](../../developers/tracking/events-reference/) (from the event catalog) or a custom specification.

The schema of standard events is already defined, but you can modify it by adding more properties (standard or custom properties).

<figure><img src="../../.gitbook/assets/ndl2.png" alt=""><figcaption></figcaption></figure>

### Create custom property

You can create custom properties and add it to your event specification.

<figure><img src="../../.gitbook/assets/ndl3.png" alt=""><figcaption></figcaption></figure>

#### Precise the data type

* String: most used type, it corresponds to a text format (ex: name = 'ABC')
* Number: corresponds to a number (float, entire) (ex: value = '12')
* Boolean: the property can take only 2 values, true or false (ex: paid = 'true')
* Object: corresponds to an array of values (ex: items = shirt, pant, shoes)

#### Precise the structure type

* Default (simple value): most used structure, corresponds to a single value. (ex: name = 'ABC')
* List (array of values): list of all values on the property (ex: items = shirt, pant, pant)
* Set (array of unique values): list of unique values (ex: items = shirt, pant)

#### PII option

You can define your property as 'Personal Identifiable Information (PII)', meaning this property contains personal information that could identify a user (email address, postal address, Customer ID...).

If this option is set to true, the property will be considered as PII.

If this property is stored and set as PII, it will be automatically encrypted in AES-256 before being written to the database.

### Validation Rule Actions

<figure><img src="../../.gitbook/assets/ndl4.png" alt=""><figcaption></figcaption></figure>

You can define bespoke responses to data validation scenarios:

* **Missing Required Property:** Choose to either accept or reject events entirely when a required property is missing.
* **Unexpected Value Format:** Configure the system either to omit properties that don’t match the expected format or to accept/reject event entirely.
* **Unspecified Events:** You have the option to accept events that are not predefined in your schema. You can also decide if this action should trigger a warning in the Source Data Quality report.
* **Unspecified Properties:** Decide whether to omit undefined properties or to accept them, with or without warnings.
