# Destination filters

With filters, you have the possibility to define some conditions. As a result, some events will be sent and some don't, according to your conditions.

### SIMPLE FILTER

Use the dropdown to select the property on which you want to filter, then select the operator and the value to filter on.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-03-15 à 10.48.32.png" alt=""><figcaption></figcaption></figure>

Available operators:

* is
* isn't
* match regex
* doesn't match the regex
* contains
* doesn't contain
* starts with
* doesn't start with
* ends with
* doesn't end with
* exists
* doesn't exist
* is empty

### ADVANCED FILTER

An "Advanced" filter can be use when a simple one is not sufficient.

The simple filter will be automatically transcribed into the advanced one, but the opposite is not possible, as advanced functions are not supported by the simple filter.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-03-15 à 10.50.15.png" alt=""><figcaption><p>From simple filter...</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-03-15 à 10.50.31.png" alt=""><figcaption><p>...to advanced filter</p></figcaption></figure>

Supported operators:

* `= (equals to)`
* `> (smaller than)`
* `< (greater than)`
* `!= (different from)`

Supported conditions:

* `AND`
* `OR`

Supported functions:

{% content-ref url="../data-quality/data-cleansing/supported-transformation-functions.md" %}
[supported-transformation-functions.md](../data-quality/data-cleansing/supported-transformation-functions.md)
{% endcontent-ref %}

{% hint style="info" %}
Always use " " to enter a value
{% endhint %}

{% hint style="info" %}
Input is parsing using those operators and rules like :\
\- characters like `123` or `123.45` are cast to number\
\- characters with simple or double quotes are cast to string
{% endhint %}

{% hint style="info" %}
Event **metadata** can be accessed using the relevant prefix like _`page.*`_ , `device.*` , app.\* or `event_*`\
`Ex: page.title=search OR event_name=search OR app.name=MySearchApp`
{% endhint %}

{% hint style="info" %}
For **event properties** you can either write `properties.myPropertyName` or just `myPropertyName`. Both are supported.\
Ex: `revenue=12 AND properties.currency=EUR`
{% endhint %}
