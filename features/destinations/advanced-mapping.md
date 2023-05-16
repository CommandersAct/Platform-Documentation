# Mapping and Properties transformation

## Transform data before it gets to the destination.

In some case, you would need, for a specific destination, to transform your event before it is sent to the destination.\
\
_Properties transformation_ support currently renaming or deleting properties.

Enter on the left the property name you want to add or delete. Then enter on the right the property name to map (or leave empty to remove the property)

<figure><img src="../../.gitbook/assets/image (2) (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Smart mapping

{% hint style="info" %}
Deployment in progress for all destinations
{% endhint %}

The smart mapping feature shows the mapping between standard events/properties and destination partner properties.

Ex: Standard property: value ⇒ Partner property: revenue

If needed, you can modify this mapping, with custom properties for example.

## Text input

On settings configuration, you can simply enter values with the text input.

Use brackets button \{{ \}} to enter a dynamic value, like a property name.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-05-16 à 17.40.20.png" alt=""><figcaption></figcaption></figure>

If you click on the _T_ icon, you can switch to formulas mode.

## Formulas

Use no-code formulas to transform properties. You can use more than 25 formulas (list [here](../data-quality/data-cleansing/supported-transformation-functions.md)) to transform properties.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-05-16 à 17.40.51.png" alt=""><figcaption></figcaption></figure>

For example, if a destination requires MD5 email, you can select the email in clear and apply the MD5 formula to turn the clear email into a MD5 email, only for this destination (if it is for all destinations, please use our [Data Cleansing](../data-quality/data-cleansing/) feature).

Other example, if a destination requires a price with "." (ex: 12.30), but in your database prices are stored with a "," (ex: 12,30), you can transform the data with a dedicated formula to turn the "," into a "."&#x20;

