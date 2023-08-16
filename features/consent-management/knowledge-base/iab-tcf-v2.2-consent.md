---
description: Description of how to interact with IAB consent API
---

# IAB TCF V2.2 Consent

If you are using IAB TCF option (see [this page](https://www.doc.commandersact.com/consent-management/user-guides/settings#iab-tcf-compliancy) to setup IAB TCF on your account), you will be able to use IAB TCF's `__tcfapi` where your privacy banner is deployed.

That function is defined in your container and in your privacy banner so that you can use it before your privacy banner has finished loading. It is sometimes referred by IAB as the `TCF API stub`.

IAB TCF consent is encoded in a format called the `Consent-String`.

### How to use the TCF API

The recommended way of getting the value of TCF's consent-string (`tcData.tcString` in the example below) is by using the `addEventListener` command.

```javascript
__tcfapi('addEventListener', 2, (pingReturn, success) =>{
 if(success &&
    (pingReturn.eventStatus === 'tcloaded' || pingReturn.eventStatus === 'useractioncomplete')) {
 
    // do something with pingReturn.tcString

  } else {

    // do something else

  }
});
```

Sometimes you do not want to be notified of consent updates. You can achieve this by using the more advanced code below:

```javascript
__tcfapi('addEventListener', 2, function(pingReturn, success) {
  if(success &&
    (pingReturn.eventStatus === 'tcloaded' || pingReturn.eventStatus === 'useractioncomplete')) {

    // do something with pingReturn.tcString

    // remove ourselves to not get called more than once
    __tcfapi('removeEventListener', 2, pingReturn.listenerId);

  } else {

    // do something else

  }
});
```

* Reference: [IAB TCF commands](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20CMP%20API%20v2.md#what-required-api-commands-must-a-cmp-support)

### How to decode the Consent-String

You can use this copy-paste a `Consent-String` on this page: [https://iabtcf.com/#/decode](https://iabtcf.com/#/decode).

* Reference: [IAB TCF Consent-String format](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/IAB%20Tech%20Lab%20-%20Consent%20string%20and%20vendor%20list%20formats%20v2.md)

### Google Additional Consent Mode

This an optional extension to IAB TCF.\
\
Once setup in Consent Management Settings, an additional `addtlConsent` property will be available on the `tcData` object.

```javascript
__tcfapi('addEventListener', 2, function(pingResult, success) {
  if(success &&
    (pingResult.eventStatus === 'tcloaded' || pingResult.eventStatus === 'useractioncomplete')) {

    // do something with pingResult.addtlConsent

  } else {

    // do something else

  }
});
```

* Reference: [Google Additional Consent Mode Technical Specification](https://support.google.com/admanager/answer/9681920?hl=en)
