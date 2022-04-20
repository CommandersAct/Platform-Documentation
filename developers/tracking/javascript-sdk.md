# Javascript SDK

## Getting Started

Overview on the Commanders Act onsite API.

The onsite API is used to interact with Commanders Act features with JavaScript.

There are different commands available within `cact()`: `config` is used to set general properties,  `trigger` event is used to send data, and other specific `get/update/revoke` commands are used to interract with platform features (ex : get user consent)

## How to use <a href="#how-to-use" id="how-to-use"></a>

The onsite API consists of a single function, `cact()`, with the following strict signature:

```
cact(command, [options,], [config,], [callback])
```

| Argument   | Descriptions                                                                                                        | Required |
| ---------- | ------------------------------------------------------------------------------------------------------------------- | -------- |
| `command`  | A string identifier used to select the desired method.                                                              | Required |
| `options`  | A JavaScript object that includes data passed to the method.                                                        | Optional |
| `config`   | A javascript object that is used to override the default settings like `siteId` , `collectionDomain` or `sourceKey` | Optional |
| `callback` | A JavaScript callback function that is used to receive information or events from the onsite API.                   | Optional |

Onsite API is included in each containers and privacy banners.

## Initialize global settings with config <a href="#config" id="config"></a>

Use the `config` command to initialize and configure settings for a particular workspace.

{% hint style="info" %}
This command is optional, you can also set custom settings directly inside a[ `trigger` command](javascript-sdk.md#send-event), through the config object parameter.
{% endhint %}

The config command takes the following format:

```javascript
cact('config', {<config_object>});
```

Config object accept **3 parameters**, they are optional if you use a web container on your page :&#x20;

* `siteId` : if not set, the default value is the site id of the last web container loaded (`tC.id_site`)
* `sourceKey`: if not set, the default value is derivative from you web container id. If you don't have a web container, the sourceKey is mandatory and correspond to your JS SDK source.
* `collectionDomain`: if not set, the default value is `collect.commander1.com`\
  ``This parameter is used to set your first party domain

Example :

```javascript
cact('config', { siteId: 1234, sourceKey: 'abcd' });
```

## Send event <a href="#send-event" id="send-event"></a>

To send event data to the serverside Commanders Act platform, use this command:

```javascript
cact('trigger', '<event_name>', {<event_params>});
```

Example : to send a purchase event :

```javascript
cact('trigger', 'purchase', {   id:'1234',  currency: 'EUR',  //...});
```

Example : to send a purchase event, overriding the default tracking domain / workspace / sourcekey :

```javascript
cact('trigger', 'purchase', {   id:'1234',  currency: 'EUR',  //...},{
    collectionDomain: "my.firstdomain.com",
    siteId: "1234", 
    sourceKey: "abcd"
});
```

## Get information <a href="#get-information" id="get-information"></a>

To get various values from Commanders Act, use this command:

```
cact(get command, [callback])
```

Example : to get consent from TrustCommander, you can call the `consent.get` API like this:

```
cact('consent.get', function(result) {    if (result.consent.status === "all-on") {                // Consent available for all categories.            }});
```

The onsite API methods are called asynchronously. In case e.g. you need information synchronous in the `<head>` of the document it is recommended to cache and retrieve the result of the API in `localStorage`.

## Error handling <a href="#error-handling" id="error-handling"></a>

You can handle errors through error property in the callback object. Example:

```
cact('consent.get', function(result) {​    if (result.error) {            // Manage the error        }    else if (result.consent.status === "all-on") {                // Consent available for all categories.            }});
```

## API Stub (optional) <a href="#api-stub-optional" id="api-stub-optional"></a>

For advance usage, we provide also an API stub that can be added when you need to interact with the API before containers or banners have loaded. This stub is already included in containers and privacy banners, so you do not have to add in most use cases. The stub is used to buffer all methods in a JavaScript array until Commanders Act JavaScript is loaded and ready to process the methods. This allows for example to use the onsite API before TrustCommander JavaScript was loaded.

```
window.caReady = window.caReady || []; window.cact = function() { window.caReady.push(arguments); };
```

`window.caReady` is a JavaScript array that buffers the interactions with the API. `window.cact` is a JavaScript function used to interact with the onsite API.

In case you work in a big team and are unsure the stub was already installed it is ok to install the JavaScript stub multiple times.
