# Destination filters

{% hint style="info" %}
Please note that the interface of this feature is going to evolve to provide the best filtering experience.
{% endhint %}

With filters, you have the possibility to define some conditions. As a result, some events will be sent and some don't, according to your conditions.

Example: you want to only send events with property 'country' is equal to France ('FR') AND property 'currency' is equal to Euro ('EUR').

On the destination configuration wizard, filter step, you can define your filter like that:

![](<../../../.gitbook/assets/Capture d’écran 2022-03-04 à 11.39.01.png>)

You can type directly the property's name and write the formula according to allowed characters:

Supported operators:

* `= (equals to)`
* `> (smaller than)`
* `< (greater than)`
* `!= (different from)`

Supported conditions:

* `AND`
* `OR`

{% hint style="info" %}
Input is parsing using those operators and rules like : \
\- characters like `123` or `123.45` are cast to number \
\- characters with simple or double quotes are cast to string
{% endhint %}

{% hint style="info" %}
Event metadata can be access using the relevant prefix like _`page.*`_ , `device.*` , app.\* or `event_*`\
`Ex: page.title=search OR event_name=search OR app.name=MySearchApp`&#x20;

\
For event properties you can either write `properites.myPropertyName` or just `myPropertyName`. Both are supported.\
Ex: `revenue=12 AND properties.currency=EUR`
{% endhint %}
