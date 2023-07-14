---
description: >-
  How to migrate to the old platform sdk (Platform 7) to the new platform
  (Platform X)
---

# Migrate from old mobile sdk

To track mobile app on the new platform, you can either install our new SDK ([Android](../../../features/sources/sources-catalog/android.md) and [iOS](../../../features/sources/sources-catalog/ios.md)) or use our [HTTP tracking API](https://community.commandersact.com/platform-x/features/integrations/sources/sources-catalog/http-tracking-api).

## Steps to follow for migration from SDK v4 to SDK v5

### Create your Mobile Source(s)

In the Sources Catalog, create your new Sources. \
`Sources > Overview > Add Source`

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

At the last step of the Source setup, you will obtain a Source Key, required for the initialization methods of our SDK

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### Replace SDK Modules

Our SDK files have changed. You must replace the old ones. Please upload our latest versions :

Android : [https://github.com/CommandersAct/AndroidV5#latest-available-versions](https://github.com/CommandersAct/AndroidV5#latest-available-versions)\
iOS : [https://github.com/CommandersAct/iOSV5#latest-available-versions](https://github.com/CommandersAct/iosV5#latest-available-versions)

{% hint style="info" %}
Some names of our modules have also evolved, here are their correspondences :

TCSDK -> TCServerSide&#x20;

TCPrivacy -> TCConsent
{% endhint %}

### Modify initialization methods

The way you initialize our SDK is now different, your old methods will not be recognized anymore.

* You don't need container ID anymore, all is on the same site ID. Instead of a container ID you'll need a specific key to define the source.
* You don't need to put any TCServerSide instance in your Consent implementation anymore.
* You might need to use the TCUser class to forward relevant information about your users.

{% hint style="info" %}
There’s a code example you can check here:

[https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#example\
https://github.com/CommandersAct/iosV5/tree/master/TCServerSide#example](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#examplehttps://github.com/CommandersAct/iosV5/tree/master/TCServerSide#example)[](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#examplehttps://github.com/CommandersAct/iosV5/tree/master/TCServerSide#example)
{% endhint %}

{% hint style="success" %}
If your mobile app use our SDK modules only for Privacy your migration is done at this point.

\
If you want to benefit of all the advantages of tracking with server-side destinations, or if you was using server-side v1 containers to send data to your partners, please follow the next steps!
{% endhint %}

### Replace container calls by events

With the old platform, you was used to send a container call, with all the variables. It's not compatible anymore.\
Instead, you have to send events with properties.

Here’s a code example of how to execute an event:

```swift
let event = TCPageViewEvent(type: "product list")
	event?.pageName = "Best sellers"
	serverside?.execute(event)
```

{% hint style="info" %}
You can have a look on all events code's examples [here](https://doc.commandersact.com/developers/tracking/events-reference)\
For more information about events specificity, please refer to [this page](https://doc.commandersact.com/developers/tracking/about-events/mobile-sdk-event-specificity#fields-details) of our documentation.
{% endhint %}

For technical documentation about how integrating events, please visit to our GitHub:\
[https://github.com/CommandersAct/iOSV5/tree/master/TCServerSide#executing-events](https://github.com/CommandersAct/iOSV5/tree/master/TCServerSide#executing-events)\
[https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#executing-an-event](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#executing-an-event)

### Upgrade your data layer

The new platform is using standard properties, so we recommend to upgrade your mobile application’s data layer by using our standard properties as much as possible

### Create your destinations

You can now use our platform to [create new destinations](https://doc.commandersact.com/features/destinations/add-destination) and send data to your partners

### Test & validation

A Quality Assurance Test & validation is strongly recommended before launch in production ! Here’s a few references to help you on this point:

*   Testing => tips how to test

    [https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#testing](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide)

    [https://github.com/CommandersAct/iosV5/tree/master/TCServerSide#testing](https://github.com/CommandersAct/iosV5/tree/master/TCServerSide)
* Debugging => list of methods to display logs in your app\
  [https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#debugging](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide)\
  [https://github.com/CommandersAct/iosV5/tree/master/TCServerSide#debugging](https://github.com/CommandersAct/iosV5/tree/master/TCServerSide)
*   Common errors list

    [https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#common-errors](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide)

    [https://github.com/CommandersAct/iosV5/tree/master/TCServerSide#common-errors](https://github.com/CommandersAct/iosV5/tree/master/TCServerSide)



{% hint style="success" %}
Your migration is done !

Maybe you have some specific needs ? Don’t forget to check the following FAQ
{% endhint %}

## FAQ

### Is my data layer must be identical for my website & my app ?

It’s a good practice !\
We strongly recommend to have the same data layer for web & mobile application\
Main benefit: setup only 1 destination for both sources! \
Your destination’s setup will be recognized by web and mobile

### How can I obtain the IDFA/AAID ?

Our SDK doesn’t collect automatically the IDFA/AAID anymore, but we offer a simple method to track this information:

[Android](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#getting-aaid) `ServerSideInstance.addAdvertisingIDs());`\
[iOS](https://github.com/CommandersAct/iosV5/tree/master/TCServerSide#getting-idfa) `[ServerSideInstance addAdvertisingIDs];`

### Can I create custom events ?

Yes it’s possible !

For further information, have a look to this part of our documentation:\
[https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#custom-events](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide)\
[https://github.com/CommandersAct/iosV5/tree/master/TCServerSide#custom-events](https://github.com/CommandersAct/iosV5/tree/master/TCServerSide)

### Can I use additional parameters ?

Yes it’s possible ! If you need to send more data then just the required properties, simply use the "additional property" method, as follow:

[Android example:](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#customising-events)

```
TCPageViewEvent pageViewEvent = new TCPageViewEvent("Consent");
pageViewEvent.pageName = "Configuration";
pageViewEvent.addAdditionalProperty("currentConsent", "refused");
```

[iOS example:](https://github.com/CommandersAct/iosV5/tree/master/TCServerSide#customising-events)

```
TCPageViewEvent *pageViewEvent = [[TCPageViewEvent alloc] initWithType: @"Consent"];
pageViewEvent.pageName = @"Configuration";
[pageViewEvent addAdditionalProperty: @"currentConsent" withStringValue: @"refused"];
```

### Can I add Persisting variables ?

Yes it’s possible !

If you need to set a persistent variable, please refer to this doc:\
[https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide#persisting-variables](https://github.com/CommandersAct/AndroidV5/tree/master/TCServerSide)[https://github.com/CommandersAct/iosV5/tree/master/TCServerSide#persisting-variables](https://github.com/CommandersAct/iosV5/tree/master/TCServerSide)

{% hint style="info" %}
Persisting variable’s definition: it’s a key/value which will remains the same forever\
(example : Google account ID)
{% endhint %}

### Do I need to change/update my Json file ?

It’s not required !\
Your current json is still valid for our new SDK

### Do I need to change/update my callbacks for consent statistics ?

It’s not required !\
Your current setup is still valid for our new SDK
