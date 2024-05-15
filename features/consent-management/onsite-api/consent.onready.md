---
description: Method to obtain Commanders Act consent when it becomes available.
---

# consent.onReady

{% hint style="info" %}
Method to obtain consent when it becomes available.The Commanders Act [OnSite API stub](getting-started.md) has to be installed before using any of the OnSite API functions.
{% endhint %}

```javascript
cact('consent.onReady', function (result) { ... })
```

The `consent.onReady` method allow to subscribe a callback function for when consent is set. The callback function will be called only once, with the updated Consent Object. It is called whenever the consent is set via a consent banner interaction or when a consent cookie is already set.

Like in the command `consent.onUpdate`, the `consentObject` argument will be enriched with the property `updateEvent`, but only with the value '`set`'.&#x20;

## Example

### Example to wait for consent availability and do something on a specific category

In this example, the code is waiting for the user's interaction with the consent banner. The Analytics category was configured with the consent category id 2 on privacy banner.

```javascript
cact('consent.onReady', function (result) { 
    
    var ANALYTICS_ID = 2;
    var analyticsCategory = result.consent.categories[ANALYTICS_ID] || {};
     
    if (analyticsCategory.status === 'on') {
    
        // Consent was provided for the category. 
    
    } else {
        
        // Consent was not provided for the category. 
           
    }
    
});
```
