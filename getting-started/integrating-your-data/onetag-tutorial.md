# OneTag Tutorial

Sending an event from a [web container](../../features/sources/sources-catalog/web/containers/) is as easy as adding a tag : the OneTag.

{% hint style="info" %}
If you haven’t already, you should read the [platform explanations](../concepts/)!
{% endhint %}

## 1. Add the OneTag from the tag library

From your web container, add a tag from the tag library, searching **Commanders Act OneTag**

You will find 2 tags to choose from :&#x20;

1. The _**OneTag - Builder**_: it will guide you without having to write code
2. The _**OneTag - Custom**:_ for those who prefer to manually write complex event data using javascript

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## 2. Setup the tag

If you choose the _builder_ version of the tag, you can go to the next step, you just have to follow the instructions.\
If you choose the _custom_ one, here is how it works:\
\
The `cact('trigger')` function is what allows you to record any actions your users perform, along with any properties that describe the action.\
Each action is known as an [event](../concepts/#event).

<pre class="language-javascript"><code class="lang-javascript"><strong>cact('trigger', '&#x3C;event_name>', {&#x3C;event_data>}, );
</strong></code></pre>

Each event has a name, like **page\_view**, and properties. For example, a **page\_view** event might have properties like `page_name` or `page_type`.\
\
Here’s the payload of a typical `trigger` call with most common fields removed:\
To send event data to the Commanders Act platform, you will use the `cact('trigger')` function following this format:

Example : to send a purchase event :

```javascript
cact('trigger', 'purchase', { id:'1234',  currency: 'EUR', ... });
```

### Standard events and custom events

You can implement two types of events:

* **Recommended standard events** are events that you implement yourself, but that have Commanders Act-predefined names and parameters. **Recommended events unlock existing plug\&play features/automatic-mapping/automatic-QA-alerting capabilities, but also future features/reporting** Here are the [events recommended](../../developers/tracking/events-reference/) by industries.
* **Custom events** are events that you name and implement yourself. Before implementing a custom event, check that there is not a recommended event that already provides what you need. With custom events, best practice is to use recommended properties that you can find in our [event references](../../developers/tracking/events-reference/) (ex: revenue, currency, ...) beside your custom properties.

{% hint style="info" %}
Inside a standard events, you can add custom properties beside standard properties
{% endhint %}

{% hint style="info" %}
Inside custom events, it is recommanded to put standard properties. Of course, custom properties can also be added
{% endhint %}

### User Consent in each events

If you use Commanders Act CMP, the user consent is automatically retrieved and **put inside all events** in the `user` property.

If you use another CMP, you will have to add manually a property `consent_categories` inside a `user` property, following this example :&#x20;

```javascript
cact('trigger','sign_up', {
  method: 'email', 
  user: {
      consent_categories: [1,3,4,6]
  }
});
```

`consent_categories` is the user's consents list and is mandatory to manage consents in each destinations (aka server-side consent)

### How work server-side consent management

When you add a destination (aka serverside tag), you manage the user consent by selecting the appropriate consent categories for that destination (for example "Advertising" category for Facebook CAPI).&#x20;

![](../../.gitbook/assets/image.png)\
As a result, since each event entering the platform contains information about the user's consent at the time the event took place, **the event will only be sent to the destination if there is a match between the categories consented by the user and the consent's category associated to the destination.**

### Advanced : Overrinding default parameters

If you want to force a parameter (for example the collection domain), you have 2 ways to do it : \
1\. First you can add it as a third parameter.\
Example : to send a purchase event, overriding the default tracking domain / workspace / sourcekey :

```javascript
cact('trigger', 'purchase', {   id:'1234',  currency: 'EUR',  //...},{
    collectionDomain: "my.firstdomain.com",
    siteId: "1234", 
    sourceKey: "abcd"
});
```

## 3. Check that everything is working

After configuring your OneTag (at lease one event triggered) and deploying your web container, you can refer to the [Event Inspector](../../features/sources/live-event-inspector.md) tab for the Source to verify that it generates the expected event data.

The Source Event Inspector serves as a live tool that aids in validating the arrival of API requests originating from your website, mobile application, or servers to your Commanders Act Source. This enables you to promptly examine the reception of calls by your source and troubleshoot without the need to await data processing.

![](<../../.gitbook/assets/image (1) (1).png>)

## 4. Setup your first destination

Once you have verified the inflow of data from your fresh source, it's the perfect moment to create your first destination:

* Navigate to your Commanders Act platform, click on Destinations-> Overview, and select 'Add Destination' to list all the available destinations in the catalog.
* Look for the destination of your preference. For example Facebook Conversion API.
* Click on the card representing the destination to obtain more information about it.
* Initiate the configuration by clicking on 'Configure'
* Choose the source that you had previously setup, or select all sources.
* In the settings screen, name your destination, choose an environment and enter required information.
* Then in the filter tab, manage the user consent by selecting the appropriate consent categories for that destination (for example "Advertising" category for Facebook CAPI)
* Save and go checking that everything is going well in the Event Delivery and/or Event Inspector tab, or directly in your tool.
