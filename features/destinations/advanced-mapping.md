# Mapping and Properties transformation

## Transform data before it gets to the destination.

In some case, you would need, for a specific destination, to transform your event before it is sent to the destination.\
\
_Properties transformation_ support currently renaming or deleting properties.

Enter on the left the property name you want to add or delete. Then enter on the right the property name to map (or leave empty to remove the property)

<figure><img src="../../.gitbook/assets/image (429).png" alt=""><figcaption></figcaption></figure>

## Smart mapping

{% hint style="info" %}
Deployment in progress for all destinations
{% endhint %}

The smart mapping feature shows the mapping between standard events/properties and destination partner properties.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-05-23 à 15.55.10.png" alt=""><figcaption></figcaption></figure>

Ex: Standard property: value ⇒ Partner property: revenue

If needed, you can modify this mapping, with custom properties for example.

## Text input (settings)

On settings configuration, you can simply enter values with the text input.

Use brackets button \{{ \}} to enter a dynamic value, like a property name. Without brackets, the value is considered as a string.

Examples:

* `{{price}}`corresponds to the property price, the output will be "12,30" for example.
* `price` corresponds to a static value, the output will be "price".
* `{{price}} excl.taxes` corresponds to the property price concatenated with the string 'excl.taxes', the output will be “12,30 excl.taxes” for example.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-05-16 à 17.40.20.png" alt=""><figcaption></figcaption></figure>

If you click on the _T_ icon, you can switch to functions mode.

## Functions (settings)

Use no-code formulas to transform properties. You can use more than 25 formulas (list [here](../data-quality/data-cleansing/supported-transformation-functions/)).

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-05-16 à 17.40.51.png" alt=""><figcaption></figcaption></figure>

In settings, functions could be useful to define a complex value, for example a concatenation of 2 properties to create a unique ID required by the destination.

## Functions inside smart mapping

{% hint style="info" %}
Coming soon
{% endhint %}

These functions are also available in the [smart mapping feature](advanced-mapping.md#smart-mapping), to easily transform properties before to send to the destination.

For example, if a destination requires MD5 email, you can select the email in clear and apply the MD5 formula to turn the clear email into a MD5 email, only for this destination (if it is for all destinations, please use our [Data Cleansing](../data-quality/data-cleansing/) feature).

Other example, if a destination requires a price with "." (ex: 12.30), but in your database prices are stored with a "," (ex: 12,30), you can transform the data with a dedicated formula to turn the "," into a "."&#x20;

