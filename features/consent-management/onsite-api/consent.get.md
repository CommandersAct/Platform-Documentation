---
description: >-
  Method to receive Commanders Act consent and consent metadata OnSite via
  JavaScript.
---

# consent.get

{% hint style="info" %}
The Commanders Act [OnSite API stub](getting-started.md) has to be installed before using any of the OnSite API functions.
{% endhint %}

`cact('consent.get', function (result) { ... });`

The `consent.get` method takes one callback JavaScript function as an argument that gets called with the [Consent Object](../knowledge-base/consent-object.md) that is currently stored on the browser. The callback is called once after Commanders Act CMP JavaScript loaded and validated the stored consent.

{% hint style="info" %}
The OnSite API works asynchronous. In case you need the consent synchronous (e.g. in the `<head>` of a document for AB Testing or personalisation solutions) it is recommended to cache the object in the `localStorage` of the browser. In this case it is crucial to implement the `consent.onUpdate` method to keep the cached consent in sync.
{% endhint %}

### Examples <a href="#examples" id="examples"></a>

#### Executing code based on the consent setting of a category <a href="#executing-code-based-on-the-consent-setting-of-a-category" id="executing-code-based-on-the-consent-setting-of-a-category"></a>

In this example the Analytics category was configured with the consent category id 2 in Commanders Act banner.

```
cact('consent.get', function (result) {

   const ANALYTICS_ID = 2;
   const analyticsCategory = result.consent.categories[ANALYTICS_ID] || {};
   
   if (analyticsCategory.status === 'on') {
         
      // Consent was provided for the category. 
      
   } else {
      
      // Consent was not provided for the category.
   
   }
        
});
```

#### Executing code based on the consent setting of a category and vendor <a href="#executing-code-based-on-the-consent-setting-of-a-category-and-vendor" id="executing-code-based-on-the-consent-setting-of-a-category-and-vendor"></a>

In this example the Analytics category was configured with the consent category id 2 and the vendor Google with vendor id 5 in Commanders Act CMP.

```
cact('consent.get', function (result) {
   
   const ANALYTICS_ID = 2;
   const analyticsCategory = result.consent.categories[ANALYTICS_ID] || {};

   const GOOGLE_ID = 5;
   const googleVendor = result.consent.vendors[GOOGLE_ID] || {};
   
   if (analyticsCategory.status === 'on' && googleVendor.status === 'on') {
         
      // Consent was provided for the category. 
      
   } else {
      
      // Consent was not provided for the category.
   
   }
        
});
```

#### Check if consent was already set by the visitor <a href="#check-if-consent-was-already-set-by-the-visitor" id="check-if-consent-was-already-set-by-the-visitor"></a>

```
cact('consent.get', function (result) {
   
   if (result.consent.status === 'unset') {
         
      // Consent was not yet provided.
      
   } else {
      
      // Consent was accepted or refused.
   
   }
        
});
```

#### Checking when the current consent expires <a href="#checking-when-the-current-consent-expires" id="checking-when-the-current-consent-expires"></a>

```
cact('consent.get', function (result) {

    const dateExpires = result.meta.dateExpires;
                
});
```
