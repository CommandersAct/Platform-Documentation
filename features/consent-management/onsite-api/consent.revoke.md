---
description: Method to revoke Commanders Act consent OnSite via JavaScript.
---

# consent.revoke

{% hint style="info" %}
The Commanders Act [OnSite API stub](getting-started.md) has to be installed before using any of the OnSite API functions.
{% endhint %}

```javascript
cact('consent.revoke')
```

`consent.revoke` is called with no options and no callback function. It resets the consent, consent id and initiates two `consen.onUpdate` events, one with the `updateEvent` set to `changed`, and a second one set to`revoked` that allows to perform cleanup tasks like removing cookie identifiers.
