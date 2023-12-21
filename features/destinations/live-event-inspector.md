# Destination event inspector

Live event inspector is a great way to visualize in real-time all your outgoing events to a specific destination.

It is the easiest way to help you to debug what is sent to destinations, you can check all properties and filter on specific events or properties.

![](<../../.gitbook/assets/image (1) (2) (1) (1).png>)

### Intelligent sampling

During your test phase, you'll see 100% of your outgoing hits in the event inspector, thanks to the _intelligent sampling_ mechanism.

When you'll start to send more real data with millions of events, you'll see only a portion of outgoing hits, based on these rules :&#x20;

* 6 requests per minute for each event type
* a bonus of 30 requests per hour for each event type

{% hint style="info" %}
You can visualize data up to 48 hours
{% endhint %}

{% hint style="info" %}
IP addresses are automatically obfuscated (the last octet is replaced by 0)
{% endhint %}

### **Debug Mode**

A Debug Mode is available ! Simply add the property `test_code` with any value (string format) in your events.&#x20;

This property will bypass the intelligent sampling mechanism. It's a simple way to be sure your test hits will be available in the Live Event Inspector.\
You will be allowed to send 20 events/minute for each Source.

Here's an example of an event with this property

```
cact('trigger','page_view', {
  page_type: 'product_list',
  page_name: 'Best sellers',
  test_code: 'my_value',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```

In case you cannot modify your events code's you can use our Data Cleansing option to add it in your events. Make sure your setup is based on a single key for reconciliation.&#x20;

Here's an example of setup done with our Data Cleansing tool:

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Note: this method works only for your Destination event inspector, not on the Sources Live event inspector as long as the Data Cleansing modifies the value after collection.
