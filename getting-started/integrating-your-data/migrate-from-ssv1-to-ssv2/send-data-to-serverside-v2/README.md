# Send data to serverside v2

## 1. How to send events (standard / custom)

* From a server, use our [HTTP tracking API](https://community.commandersact.com/platform-x/features/integrations/sources/sources-catalog/http-tracking-api)
* From a mobile application, you can either use one of our SDK ([Android](../../../../features/integrations/sources/sources-catalog/android.md), [IOS](../../../../features/integrations/sources/sources-catalog/ios.md), ...) or use our  [HTTP tracking API](https://community.commandersact.com/platform-x/features/integrations/sources/sources-catalog/http-tracking-api)

## 2. Format events

* As explain in the [event documentation](https://community.commandersact.com/platform-x/developers/tracking/about-events), common events have to be sent in the standard format (name and properties) to benefit from plug\&play features.\
  For specific events, custom events name is possible. Nevertheless, please use standard properties in custom events, as far as possible, to benefit from automatic mapping, automatic QA, and plug\&play features.
* Standard event format can be found in our [event reference documentation](https://community.commandersact.com/platform-x/developers/tracking/events-reference)\
  Here is an [example ](purchase-event-example-ssv1-to-ssv2.md)based the ssv1 format :  [purchase event example](purchase-event-example-ssv1-to-ssv2.md)
