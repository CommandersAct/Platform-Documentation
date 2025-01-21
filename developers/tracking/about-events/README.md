# About events

Events are triggered as users interact with your site or app.

The data you can see in your server side data comes from events that are triggered as users interact with your website and/or app. For example, a `page_view` event is triggered each time a user views a page on your website

You can implement two types of events:

* **Recommended standard events** are events that you implement yourself, but that have Commanders Act-predefined names and parameters. Recommended events unlock existing and future features/reporting/automatic-mapping/automatic-QA-alerting capabilities not available for custom events (events that you name yourself). Here are the events recommended for [all sectors](../events-reference/common-events.md), [Retail/E-commerce/Travel/Real estate](ecommerce-retail-events.md) and [Bank/Assurances](../events-reference/common-events.md).
* **Custom events** are events that you name and implement yourself. Before implementing a custom event, check that there is not a recommended event that already provides what you need. With custom events, best practice is to use recommended properties that you can find in our [event references](../events-reference/) (ex: revenue, currency, ...) beside your custom properties.

{% hint style="info" %}
Inside a standard events, you can add custom properties beside standard properties
{% endhint %}

{% hint style="info" %}
Inside custom events, it is recommended to put standard properties. Of course, custom properties can also be added
{% endhint %}
