# Storage Settings

## Setup of Storage Settings

To create a new storage, simply fill all the required fields of the form

* **Name your storage:** give a clear name to your storage
* **Choose Source(s) and Environment**&#x20;
* **Select Consent Category:** Ensure compliance with data privacy regulations.&#x20;

<figure><img src="../../.gitbook/assets/image (583).png" alt=""><figcaption></figcaption></figure>

* **Select Event:** Choose from which event you want to store the properties

<figure><img src="../../.gitbook/assets/image (584).png" alt=""><figcaption></figcaption></figure>

* **Select the properties:** Choose the properties you need for your enrichment. Click on "Add/Edit Properties"

<figure><img src="../../.gitbook/assets/image (585).png" alt=""><figcaption></figcaption></figure>

A side panel will appears, to allow properties selection. \
In some cases, you may need to store all the properties. Just turn on the top button.\
To save your selection, simply click the closing cross

{% hint style="success" %}
Nested format is allowed, see [Check Properties format](storage-settings.md#check-properties-format) section
{% endhint %}

<figure><img src="../../.gitbook/assets/image (586).png" alt=""><figcaption></figcaption></figure>

* **Set a Matching Key:** This unique key have to be present and identical both on the event to be enriched and the event to store.&#x20;

<figure><img src="../../.gitbook/assets/image (587).png" alt=""><figcaption></figcaption></figure>

*   **Add filters (optional):** if needed, you can define some filters to store events on specific conditions\


    <figure><img src="../../.gitbook/assets/image (588).png" alt=""><figcaption></figcaption></figure>
* **Define the retention period:** The storage duration is the period that events stored events are kept in our database (maximum 730 days allowed).

{% hint style="success" %}
In order to avoid an unexpected impact on the consumption of your credit, you should choose a duration that corresponds to your use case.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (589).png" alt=""><figcaption></figcaption></figure>

Congratulations! Your Storage Settings is configured! **Don't forget to Save!**

## **Tips and tricks**

### Check if the property already exist

Natively, a Storage Settings will not enrich a property if it does already exists in the event to be enriched. \
\
If the property already exists, but you really need to change the value with your enrichment, don't forget to check the "override" option in your [enrichment configuration](https://app.commandersact.com/en/4452/sources/privacy-banners/?p=/en/4452/containers/privacy/settings/1/demo-iab-ii).

This override feature can also be applied to arrays values.

### Check Properties format

It is not possible to enrich a property with a different type other than the standard one expected in your enrichment.\
Basic example: \
Sending a Number value to enrich a String type property \
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

### **Specific cases - Objects**&#x20;

You can store an entire Object, (example: `items.product`) but you can also store only single key(s) extracted from an Object (example: `items.product.price`).\
If you are saving single keys, be sure that the destination event has already the Object defined.\
Otherwise the single key will not enrich anything.\
The warnings message will contain the following detail:\
`message:` '`should merge object properties that do not exist in target'`

#### **Multiple Objects reconciliation**

If you store a property that occurs in several objects, be careful!\
Our matching mechanism is based on ID's. \
As an example, you have many `items.product` objects and you need to store `items.product.brand` property. \
We will use the `items.product.id` as matching key to fill the different `items.product` objects.\
If there's no "ID" property inside your object, we will simply fed in the same order then it was stored.\
In this case, the following "warnings" details will be added to your enrichment\
&#x20;`message: 'No ID field found, falling back to index-based merge',`

#### Override usage

Be careful when using the Override option!\
Overriding an entire object will block the "non-override" of a single key\
Example of a bad practice:

`items.product.color` << _override: false_ >> `items.product.defaultColor`\
`items` << _override: true_ >> `items`

The data from the `items.product.color` value is overridden because the second line has priority.

### Best Practice : filter's usage

Of course, the filters set in your destinations will be applied. \
So why should you use the Storage Settings filters? \
We provide the filters at this level simply to save you Storage fees (credit consumption), and to simplify the processing on your destinations.

Same quality of enrichment, for lower fees!
