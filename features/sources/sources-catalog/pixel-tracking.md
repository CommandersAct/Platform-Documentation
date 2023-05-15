# Pixel Tracking

Pixel Tracking, also known as 1x1 gifs, or clear gifs, lets you record data from any website (or application) **where JavaScript or POST requests are not allowed**, but where you can insert an image (aka GET hit)

{% hint style="info" %}
When a POST request is possible, please prefer the [http tracking API](http-tracking-api.md), more convenient to use.
{% endhint %}

Example `event` call (basic):

{% code fullWidth="false" %}
```c
GET  https://collect.commander1.com/events?tc_s={siteId}&token={yourSourceKey}&event_name=page_view&prop1=value1
```
{% endcode %}

Example event call with objects and arrays :&#x20;

{% code overflow="wrap" %}
```
GET https://collect.commander1.com/events?tc_s={siteId}&token={yourSourceKey}&event_name=page_view&page_type=product_list&page_name=Best%20sellers&user[id]=12356&user[email]=toto%40domain.fr&user[consent_categories][]=1&user[consent_categories][]=3
```
{% endcode %}
