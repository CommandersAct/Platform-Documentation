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

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

## 2. Setup the tag

If you choose the _builder_ version of the tag, you can go to the next step, you just have to follow the instructions.\
If you choose the _custom_ one, here is how it works:\
\
The `cact('trigger')` function is what allows you to record any actions your users perform, along with any properties that describe the action.\
Each action is known as an [event](../concepts/#event).

Here’s the format of a typical `trigger` call:

<pre class="language-javascript"><code class="lang-javascript"><strong>cact('trigger', '&#x3C;event_name>', {&#x3C;event_data>}, [config], [callback]);
</strong></code></pre>

Each event has a name, like **page\_view**, and properties. For example, a **page\_view** event might have properties like `page_name` or `page_type`.

Here is an example&#x20;

```javascript
cact('trigger','page_view', {
  page_type: 'product_list',
  page_name: 'Best sellers', 
  //...
});
```

{% hint style="info" %}
`config` and `callback` parameters are optional
{% endhint %}

### Standard events and custom events

You can implement two types of events:

* **Recommended** [_**standard events**_](../../developers/tracking/events-reference/) are events that you implement yourself, but that have Commanders Act-predefined names and parameters.

{% hint style="warning" %}
**We strongly recommend the use of standard events**, as it allows you to benefit from plug\&play features, automatic-mapping, automatic-QA-alerting, etc. but also future features/reporting.
{% endhint %}

* _**Custom events**_ are events that you name and implement yourself. Before implementing a custom event, check that there is not a [recommended event](../../developers/tracking/events-reference/) that already provides what you need. With custom events, best practice is to use recommended properties that you can find in our [event references](../../developers/tracking/events-reference/) (ex: revenue, currency, ...) beside your custom properties.

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

`consent_categories` is the user's consents list and is mandatory to manage consents in each destinations (aka server-side consent) See [how work server-side consent management](onetag-tutorial.md#how-work-server-side-consent-management).

### Advanced options: Overriding default parameters

There are 3 default parameters that you can override if needed:

* `collectionDomain`: if not set, the default value correspond to your first party domain (if you setup one) or `collect.commander1.com`
* `sourceKey`: if not set, the default value is the [source key](../../features/sources/#source-key) of the currently running web container.
* `siteId` : if not set, the default value is the site id of the last web container loaded (`tC.id_site`)

To override a parameter, you can add a config object to your cact('trigger') function (4th parameter) like this:

```javascript
cact('trigger', 'purchase', {   id:'1234',  currency: 'EUR',  //...},{
    collectionDomain: "my.firstdomain.com",
    siteId: "1234",
    sourceKey: "abcd"
});
```

You can also set globally these parameters for all triggered events with the `cact('config')` method. See the [Javascript API documentation](../../features/sources/sources-catalog/web/js-sdk/) for more information.

## 3. Check that everything is working

After configuring your OneTag (at lease one event triggered) and deploying your web container, you can refer to the [Event Inspector](../../features/sources/live-event-inspector.md) tab for the Source to verify that it generates the expected event data.

The Source Event Inspector serves as a live tool that aids in validating the arrival of events originating from your website, mobile application, or servers to your Commanders Act Source. This enables you to promptly examine the reception of calls by your source and troubleshoot without the need to await data processing.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

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

## FAQ

### How work server-side consent management

When you add a destination (aka serverside tag), you manage the user consent by selecting the appropriate consent categories for that destination (for example "Advertising" category for Facebook CAPI). \
\
As a result, since each event entering the platform contains information about the user's consent, **the event will only be sent to the destination if there is a match between the categories consented by the user and the consent's category associated to the destination.**

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

