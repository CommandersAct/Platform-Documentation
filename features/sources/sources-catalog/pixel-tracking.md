# Pixel Tracking

Pixel Tracking, also known as 1x1 gifs, or clear gifs, lets you record data from any website (or application) where JavaScript or POST requests are not allowed, but where you can insert an image (aka GET hit)

Example `event` call:

{% code fullWidth="false" %}
```c
GET  https://collect.commander1.com/events?tc_s={siteId}&token={yourSourceKey}&event_name=page_view&prop1=value1
```
{% endcode %}
