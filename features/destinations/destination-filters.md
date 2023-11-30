# Destination filters

With filters, you have the possibility to define some conditions. As a result, some events will be sent and some don't, according to your conditions.

## SIMPLE FILTER

Use the dropdown to select the property on which you want to filter, then select the operator and the value to filter on.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-03-15 à 10.48.32.png" alt=""><figcaption></figcaption></figure>

Available operators:

* is
* isn't
* match regex _(see also '_[_About regex_](destination-filters.md#about-regex)_' section)_
* doesn't match the regex _(see also '_[_About regex_](destination-filters.md#about-regex)_' section)_
* contains
* doesn't contain
* starts with
* doesn't start with
* ends with
* doesn't end with
* exists
* doesn't exist
* is empty

## ADVANCED FILTER

An "Advanced" filter can be used when a simple one is not sufficient.

The simple filter will be automatically transcribed into the advanced one, but the opposite is not possible, as advanced functions are not supported by the simple filter.

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-03-15 à 10.50.15.png" alt=""><figcaption><p>From simple filter...</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-03-15 à 10.50.31.png" alt=""><figcaption><p>...to advanced filter</p></figcaption></figure>

With Advanced filter, you can use formula and advanced [functions](../data-quality/data-cleansing/supported-transformation-functions/), simply click on the button on the right of the field to see all available functions.

Supported operators:

* `= (equals to)`
* `> (smaller than)`
* `< (greater than)`
* `!= (different from)`

Supported conditions:

* `AND`
* `OR`

Supported functions:

{% content-ref url="../data-quality/data-cleansing/supported-transformation-functions/" %}
[supported-transformation-functions](../data-quality/data-cleansing/supported-transformation-functions/)
{% endcontent-ref %}

{% hint style="info" %}
Always use " " to enter a value in advanced mode. \
All values entered without " " will be treated as a number.
{% endhint %}

### About Regex

Both simple and advanced filter can manage regex:

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-03-15 à 17.07.25.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Capture d’écran 2023-03-15 à 17.07.44.png" alt=""><figcaption></figcaption></figure>

To know how to build a regex, please refer to [regular expression documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular\_Expressions).
