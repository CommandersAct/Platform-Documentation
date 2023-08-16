---
description: Overview on the Commanders Act Consent OnSite API.
---

# Getting Started

The Commanders Act Consent API is used to interact with Commanders Act Consent with JavaScript. It currently only offers methods to receive and update consent, but it will be improved with additional methods in the future.

## API Stub

It is necessary to install a JavaScript stub before any of the OnSite API methods can be used. The stub is used to buffer all methods in a JavaScript array until Commanders Act consent banner JavaScript is loaded and ready to process the methods. This allows to use the OnSite API before Commanders Act Consent Banner (JavaScript file) was loaded.

```javascript
window.caReady = window.caReady || []; 
window.cact = function() { window.caReady.push(arguments); };
```

`window.caReady` is a JavaScript array that buffers the interactions with the API. `window.cact` is a JavaScript function used to interact with the OnSite API.

{% hint style="success" %}
In case you work in a big team and are unsure the stub was already installed it is ok to install the JavaScript stub multiple times.
{% endhint %}

## Methods

After installing the stub it is then possible to use any of the OnSite API methods via the `window.cact` function.

{% hint style="info" %}
The available methods are listed in the documentation under **ONSITE API**.
{% endhint %}

Each method follows a strict signature:

```javascript
cact(command, [options,] [callback])
```

| Argument   | Descriptions                                                                                      | Required |
| ---------- | ------------------------------------------------------------------------------------------------- | -------- |
| `command`  | A string identifier used to select the desired method.                                            | Required |
| `options`  | A JavaScript object that includes data passed to the method.                                      | Optional |
| `callback` | A JavaScript callback function that is used to receive information or events from the OnSite API. | Optional |

Below you will find an example method that is used to receive the Commanders Act consent status with the OnSite API. This example only provides a callback to receive the consent without providing any options.

```javascript
cact('consent.get', function (result) {
    
    if (result.consent.status === "all-on") {
        
        // Consent available for all categories.
        
    }
    
});
```

{% hint style="warning" %}
The OnSite API methods are called asynchronously. In case e.g. you need information synchronous in the `<head>` of the document it is recommended to cache and retrieve the result of the API in `localStorage`.
{% endhint %}
