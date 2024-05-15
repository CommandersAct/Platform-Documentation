---
description: >-
  Method to subscribe to Commanders Act consent status updates OnSite via
  JavaScript.
---

# consent.onUpdate

{% hint style="info" %}
Method to subscribe to Commanders Act consent updates OnSite via JavaScript.The Commanders Act [OnSite API stub](getting-started.md) has to be installed before using any of the OnSite API functions.
{% endhint %}

```javascript
cact('consent.onUpdate', function (result) { ... })
```

The `consent.onUpdate` method allow to subscribe a callback function for consent updates. The callback function will be called with the updated Consent Object. It is called whenever the consent is changed via a Commanders Act banner interaction or the `consent.update` method of the OnSite API.&#x20;

The `consentObject` argument will also be enriched with an additional property `updateEvent` to signal how the update happened. It can have following values:

| Value     | Description                                                                               |
| --------- | ----------------------------------------------------------------------------------------- |
| `set`     | The consent was set.                                                                      |
| `changed` | Consent was already established and then changed.                                         |
| `revoked` | Consent was revoked by the user. Used for cleanup tasks like deleting cookie identifiers. |

{% hint style="info" %}
When consent is revoked it fires two events: One changed followed by one revoked.
{% endhint %}

## Examples

### Example to react to consent changes of a specific category

In this example the Analytics category was configured with the consent category id 2 in Commanders Act Consent settings.

```javascript
cact('consent.onUpdate', function (result) { 
    
    var ANALYTICS_ID = 2;
    var analyticsCategory = result.consent.categories[ANALYTICS_ID] || {};
     
    if (analyticsCategory.status === 'on') {
    
        // Consent was provided for the category. 
    
    } else {
        
        // Consent was not provided for the category. 
           
    }
    
});
```

### Example only react to consent changes of a specific category after the initial consent was given

In this example the Analytics category was configured with the consent category id 2 in TrustCommander.

```javascript
cact('consent.onUpdate', function (result) { 

    var ANALYTICS_ID = 2;
    var analyticsCategory = result.consent.categories[ANALYTICS_ID] || {};

    if (result.updateEvent === "changed" && analyticsCategory.status === 'on') {
    
        // Consent was provided for the category during an update.
    
    } 
    
});
```
