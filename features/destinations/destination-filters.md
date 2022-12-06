# Destination filters

{% hint style="info" %}
Please note that the interface of this feature is going to evolve to provide the best filtering experience.
{% endhint %}

With filters, you have the possibility to define some conditions. As a result, some events will be sent and some don't, according to your conditions. In the drop-down list, you will find predefined filters and a custom filter.

### PREDEFINED FILTERS

Below is the list of the predefined filters and the CA event property it corresponds to :

* Currency --> currency
* Event Type --> event\_name _(root property of the event)_
* Country --> country
* Coupon --> coupon
* Method --> method _(e.g.: method used to login)_
* Name --> name _(name usually refers to a product and is valued with the product name)_
* Path --> path _(path of the page url where the event occurs)_
* Payment Method --> payment\_method
* Referrer --> referrer _(referrer of the page where the event occurs)_
* Title --> title _(title of the page where the event occurs)_
* Type --> type _(the type of conversion usually valued with "online", "offline", "call" and so on)_
* URL --> url _(url of the page where the event occurs)_

### CUSTOM FILTER

A "Custom" filter can be use when predefined ones are not sufficient. It can be either used to filter events based on a specific property or even to combine several properties.

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
