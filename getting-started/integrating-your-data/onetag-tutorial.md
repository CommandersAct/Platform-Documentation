# OneTag Tutorial

Sending an event from a [web container](../../features/sources/sources-catalog/web/containers/) is as easy as adding a tag : the OneTag.

## 1.Add the OneTag from the tag library

From your web container, add a tag from the tag library, searching **Commanders Act OneTag**

You will find 2 tags to choose from :&#x20;

1. The _**OneTag - Builder**_: it will guide you without having to write code
2. The _**OneTag - Custom**:_ for those who prefer to manually write complex event data using javascript

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

## 2. Setup the tag

If you choose the _builder_ version of the tag, you can stop here, you just have to follow the instructions.\
If you choose the _custom_ one, you will find below helpfull information:

To send event data to the Commanders Act platform, you will use the `cact()` function following this format:

```javascript
cact('trigger', '<event_name>', {<event_data>}, );
```

Example : to send a purchase event :

```javascript
cact('trigger', 'purchase', { id:'1234',  currency: 'EUR', ... });
```

### Consent management

If you use Commanders Act CMP, the user consent is automatically retrieved and put inside all events.

If you use another CMP, you will have to add manually a property `consent_categories` inside a `user` property, following this example :&#x20;

```javascript
cact('trigger','sign_up', {
  method: 'email', 
  user: {
      consent_categories: [1,3]
  }
});
```

`consent_categories` is the user's consents list and is mandatory to manage consents. It is automatically filled from web sources .

### Overrinding default parameters

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

![](<../../.gitbook/assets/image (1).png>)

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
