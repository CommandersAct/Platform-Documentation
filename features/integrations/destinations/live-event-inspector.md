# Live event inspector

Event inspector is a great way to visualize in real-time all your outgoing events to a specific destination.

It is the easiest way to help you to debug what is sent to destinations, you can check all properties and filter on specific events or properties.

![](<../../../.gitbook/assets/image (1) (1).png>)

### Intelligent sampling

During your test phase, you'll see 100% of your outgoing hits in the event inspector, thanks to the _intelligent sampling_ mechanism.

When you'll start to send more real data with millions of events, you'll see only a portion of outgoing hits, based on these rules :&#x20;

* 6 requests per minute for each event type
* a bonus of 30 requests per hour for each event type
