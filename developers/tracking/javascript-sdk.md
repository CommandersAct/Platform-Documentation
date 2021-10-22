# Javascript SDK

## Getting Started

Overview on the Commanders Act onsite API.

The onsite API is used to interact with Commanders Act features with JavaScript.

## How to use <a href="how-to-use" id="how-to-use"></a>

The onsite API consists of a single function, `cact()`, with the following strict signature:

```
cact(command, [options,], [config,], [callback])
```

| Argument   | Descriptions                                                                                      | Required |
| ---------- | ------------------------------------------------------------------------------------------------- | -------- |
| `command`  | A string identifier used to select the desired method.                                            | Required |
| `options`  | A JavaScript object that includes data passed to the method.                                      | Optional |
| `config`   | A javascript object that is used to override the default settings like `idSite`                   | Optional |
| `callback` | A JavaScript callback function that is used to receive information or events from the onsite API. | Optional |

Onsite API is included in each containers and privacy banners.

## Send event <a href="send-event" id="send-event"></a>

To send event data to the serverside Commanders Act platform, use this command:

```
cact('<event_name>', {<event_params>});
```

Example : to send a purchase event :

```
cact('purchase', {   id:'1234',  currency: 'EUR',  //...});
```

## Get information <a href="get-information" id="get-information"></a>

To get various values from Commanders Act, use this command:

```
cact(get command, [callback])
```

Example : to get consent from TrustCommander, you can call the `consent.get` API like this:

```
cact('consent.get', function(result) {    if (result.consent.status === "all-on") {                // Consent available for all categories.            }});
```

The onsite API methods are called asynchronously. In case e.g. you need information synchronous in the `<head>` of the document it is recommended to cache and retrieve the result of the API in `localStorage`.

## Error handling <a href="error-handling" id="error-handling"></a>

You can handle errors through error property in the callback object. Example:

```
cact('consent.get', function(result) {​    if (result.error) {            // Manage the error        }    else if (result.consent.status === "all-on") {                // Consent available for all categories.            }});
```

## API Stub (optional) <a href="api-stub-optional" id="api-stub-optional"></a>

For advance usage, we provide also an API stub that can be added when you need to interact with the API before containers or banners have loaded. This stub is already included in containers and privacy banners, so you do not have to add in most use cases. The stub is used to buffer all methods in a JavaScript array until Commanders Act JavaScript is loaded and ready to process the methods. This allows for example to use the onsite API before TrustCommander JavaScript was loaded.

```
window.caReady = window.caReady || []; window.cact = function() { window.caReady.push(arguments); };
```

`window.caReady` is a JavaScript array that buffers the interactions with the API. `window.cact` is a JavaScript function used to interact with the onsite API.

In case you work in a big team and are unsure the stub was already installed it is ok to install the JavaScript stub multiple times.
