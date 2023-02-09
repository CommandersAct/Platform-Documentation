# Source Live Event Inspector

Live event inspector is a great way to visualize in real-time all your incoming events, coming from a specific source (tab Event Inspector when you click on a source) or coming from all sources (Live Events Inspector link in Sources menu).

It is the easiest way to help you to debug what is received, you can check all properties and filter on specific events or properties.

![](<../../.gitbook/assets/Capture d’écran 2022-08-03 à 14.47.30.png>)

### Intelligent sampling

During your test phase, you'll see 100% of your ingoing events in the event inspector, thanks to the _intelligent sampling_ mechanism.

When you'll start to send more real data with millions of events, you'll see only a portion of ingoing events, based on these rules :&#x20;

* 6 requests per minute for each event type
* a bonus of 30 requests per hour for each event type

{% hint style="info" %}
You can visualize data up to 7 days
{% endhint %}

{% hint style="info" %}
IP addresses are automatically obfuscated (the last octet is replaced by 0)
{% endhint %}

To go further, you can also inspect the data sent to each destination in real time, by going to the Event Inspector tab of your destinations:

{% content-ref url="../destinations/live-event-inspector.md" %}
[live-event-inspector.md](../destinations/live-event-inspector.md)
{% endcontent-ref %}
