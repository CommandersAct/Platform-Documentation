# Destination filters

{% hint style="info" %}
Please note that the interface of this feature is going to evolve to provide the best filtering experience.
{% endhint %}

With filters, you have the possibility to define some conditions. As a result, some events will be sent and some don't, according to your conditions.

Example: you want to only send events with property 'country' is equal to France ('FR') AND property 'currency' is equal to Euro ('EUR').

On the destination configuration wizard, filter step, you can define your filter like that:

![](<../../../.gitbook/assets/Capture d’écran 2022-03-04 à 11.39.01.png>)

You can type directly the property's name and write the formula according to allowed characters:

Supported operators:&#x20;

* \= (equals to)
* \> (smaller than)
* < (greater than)
* != (different from)

Supported conditions:

* AND
* OR
