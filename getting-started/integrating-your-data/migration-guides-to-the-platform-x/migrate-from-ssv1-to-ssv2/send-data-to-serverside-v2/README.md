# Send data to serverside v2

## 1. New concepts

On the new platform (aka Platform X), everything is Source/Event/Destination.\
\
[Sources](./#source) (your website, app or server) collect your user actions by sending [events](./#event).\
These events are sent to the platform servers and are then enriched, normalized and translated in each tool ([Destination](./#destinations)) format, so that they can be sent to your chosen destinations.\
\
You can learn more in the [Concepts ](../../../../concepts/)section.

## 2.How to send events (standard / custom)

* From a **server**, use our [HTTP tracking API](../../../../../features/sources/sources-catalog/http-tracking-api.md).

{% hint style="info" %}
Your data has to be sent to a [new url](../../../../../features/sources/sources-catalog/http-tracking-api.md#track), following a [new format](./#3.-format-events).
{% endhint %}

* From a **mobile application**, you can either use one of our SDK ([Android](../../../../../features/sources/sources-catalog/android.md), [IOS](../../../../../features/sources/sources-catalog/ios.md), ...) or use our  [HTTP tracking API](https://community.commandersact.com/platform-x/features/integrations/sources/sources-catalog/http-tracking-api) if you don't want to use a SDK.

## 3. Format events

* Events are the new format of your data. As explain in the [event documentation](../../../../../developers/tracking/about-events/), common events have to be sent in the **standard format** (name and properties) to benefit from plug\&play features.

{% hint style="info" %}
For specific events, **custom events** name is possible. Nevertheless, please use **standard properties** in custom events, as far as possible, to benefit from automatic mapping, automatic QA, and plug\&play features.
{% endhint %}

* Standard event format can be found in our [event reference documentation](https://community.commandersact.com/platform-x/developers/tracking/events-reference)
* Go through this [**example,** ](purchase-event-example-ssv1-to-ssv2.md)**based on the ssv1 format** :  [purchase event example](purchase-event-example-ssv1-to-ssv2.md)
