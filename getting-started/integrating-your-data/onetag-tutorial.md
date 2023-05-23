# OneTag Tutorial

Sending an event from a [web container](../../features/sources/sources-catalog/web/containers/) is as easy as adding a tag : the OneTag.

## 1.Add the OneTag from the tag library

From your web container, add a tag from the tag library, searching **Commanders Act OneTag**

You will find 2 tags to choose from :&#x20;

1. The _**OneTag - Builder**_: it will guide you without having to write code
2. The _**OneTag - Custom**: for those who prefer to manually write it using in javascript_

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
