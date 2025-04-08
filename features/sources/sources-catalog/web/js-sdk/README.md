# Javascript SDK

## Getting Started

The onsite API is used to interact with Commanders Act features with JavaScript.

There are different commands available within `cact()`: `config` is used to set general options, `trigger` event is used to send data, and other specific `get/update/revoke` commands are used to interract with platform features (ex : get user consent)

{% hint style="info" %}
To use the API, you must have either a web container on the page **or** the JS SDK library script: [https://cdn.tagcommander.com/events/sdk.js](https://cdn.tagcommander.com/events/sdk.js)
{% endhint %}

## How to use <a href="#how-to-use" id="how-to-use"></a>

The onsite API consists of a single function, `cact()`, with the following strict signature:

```
cact(command, [options,], [config,], [callback])
```

| Argument   | Descriptions                                                                                                                     | Required |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------- | -------- |
| `command`  | A string identifier used to select the desired method.                                                                           | Required |
| `options`  | A JavaScript object that includes data passed to the method.                                                                     | Optional |
| `config`   | A javascript object that is used to override the default settings like `siteId` , `collectionDomain` , `eventId`, or `sourceKey` | Optional |
| `callback` | A JavaScript callback function that is used to receive information or events from the onsite API.                                | Optional |

Onsite API is included in each containers and privacy banners.

## Initialize global settings with config <a href="#config" id="config"></a>

Use the `config` command to initialize and configure settings for a particular workspace.

{% hint style="info" %}
This command is optional, you can also set custom settings directly inside a[ `trigger` command](./#send-event), through the config object parameter.
{% endhint %}

The config command takes the following format:

```javascript
cact('config', {<config_object>});
```

Config object accept **4 parameters**, they are optional if you use a web container on your page :

* `siteId` : if not set, the default value is the site id of the last web container loaded (`tC.id_site`)
* `sourceKey`: if not set, the default value is derivative from you web container id. If you don't have a web container, the sourceKey is mandatory and correspond to your JS SDK source.
* `collectionDomain`: if not set, the default value is `collect.commander1.com` (or your first party domain, if you setup one and use a [web container](../containers/))
* `eventId`: if not set, an random id is set for this event and will be put in `context.event_id`

Example :

```javascript
cact('config', { siteId: 1234, sourceKey: 'abcd' });
```

## Send event <a href="#send-event" id="send-event"></a>

{% hint style="info" %}
To use the API, you must have either a web container on the page **or** the JS SDK library script : [https://cdn.tagcommander.com/events/sdk.js](https://cdn.tagcommander.com/events/sdk.js)
{% endhint %}

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

## Meta Properties

The `meta` property includes metadata and context for the consent that was provided on a browser. You can see the list of Meta properties [here](../../../../consent-management/knowledge-base/consent-object.md#meta-properties)

## API Stub (optional) <a href="#api-stub-optional" id="api-stub-optional"></a>

For advance usage, we provide also an API stub that can be added when you need to interact with the API before containers or banners have loaded. This stub is already included in containers and privacy banners, so you do not have to add in most use cases. The stub is used to buffer all methods in a JavaScript array until Commanders Act JavaScript is loaded and ready to process the methods. This allows for example to use the onsite API before TrustCommander JavaScript was loaded.

```
window.caReady = window.caReady || []; window.cact = function() { window.caReady.push(arguments); };
```

`window.caReady` is a JavaScript array that buffers the interactions with the API. `window.cact` is a JavaScript function used to interact with the onsite API.

In case you work in a big team and are unsure the stub was already installed it is ok to install the JavaScript stub multiple times.

## Use Javascript SDK in TMS

***

Our system now includes several new and improved features to help you efficiently manage and implement tags on your website. This guide provides comprehensive information on using our TMS webcontainers and JavaScript SDK, including browser-side events, command references, and tag context variables.

***

### Browser-Side Events

**Introduction**

Our new `cact('emit')` API is a new approach of `tC.event.XXX` functions, ensuring safer and more reliable event handling.&#x20;

Here’s how you can use these events:

```html
<!-- Old method (may cause issues if event does not exist) -->
<a href="mysite.com" onclick="tC.event.my_custom_event(this, { my_event_variable: 'some_value' });">

<!-- New method (safe) -->
<a href="mysite.com" onclick="cact('emit', 'my_custom_event', { from: this, my_event_variable: 'some_value' });">
```

{% hint style="info" %}
Note that hyphens (`-`) in event names will be converted to underscores (`_`). For example, `cact('emit', 'my-custom-event')` will actually call `tC.event.my_custom_event`.
{% endhint %}

### **Available Events**

* **container\_ready**: Fires for every loaded container.
* **container\_**`<siteId>_<containerId>`**\_ready:** Fires a specific  event for each container`container_ready` event (ex: `container_1234_1_ready`)
* **consent-ready**: Fires when the consent cookie is set or the banner is accepted/refused.
* **consent-updated**: Fires when consent is updated.
* **consent-revoke**: Fires when consent is revoked.
* **consent-signal-ready**: Used for Google Consent Mode setups.
* **banner-show**: Fires when the privacy banner is shown.
* **banner-hide**: Fires when the privacy banner is hidden.
* **privacy-center-show**: Fires when the privacy center is shown.
* **privacy-center-hide**: Fires when the privacy center is closed.
* **tag\_trigger\_form\_submission**: Standard form trigger.
* **tag\_trigger\_clicks**: Standard clicks trigger.
* **tag\_trigger\_scroll**: Standard scroll trigger.
* **track\_all\_events**: Server-side event sent with `cact('trigger')` API.
* **track\_\*:** Similar to `track_all_events` but with specific event names (e.g., `track_page_view`, `track_add_to_cart`).
* **privacy-module-loaded**: Internal event fired when `tC.privacy` is initialized.
* **Custom events**: Sent using `cact('emit')`.

#### Trigger example to fire a tag on `consent-update` event

<figure><img src="../../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### **Listening to all Events**

You can listen to all events using the `cact('on', '*')` API.

```javascript
function listen_all_events(event) {
  console.log(event.type); // '*'
  console.log(event.originalEvent.type); // 'page_view'
}

cact('on', '*', listen_all_events);
cact('emit', 'page_view');
```

### **Custom Tag Triggers**

To fire a custom trigger, use the `cact('emit', 'my_custom_event')` command. Note that hyphens will be converted to underscores when launching the trigger.

```javascript
cact('emit', 'my_custom_event');
```

You will be able to use this event as a TMS custom trigger:

<figure><img src="../../../../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### Commands Reference

The container provides a set of commands, some of which trigger browser-side events. To see all commands, type `tC.cact` in your console.

**`config`**

Set various website configurations.

```javascript
cact('config', { siteId: 4242, collectionDomain: 'example.com', sourceKey: 'ABCD-1234-EFGH' });
```

**`setProperty`**

Set properties to be merged with server-side events sent via the trigger API.

```javascript
cact('setProperty', 'page_type', 'homepage');
cact('setProperty', 'user.email', 'user@example.com');
```

**`emit` (Alias: `dispatchEvent`)**

Dispatch a browser-side event for use as a custom tag trigger.

```javascript
cact('emit', 'page_view', { page_type: 'homepage' });
```

**`on` (Alias: `addEventListener`)**

Subscribe to a browser-side event.

```javascript
cact('on', 'page_view', function(event) {
  console.log('event received of type', event.type); // 'page_view'
  console.log('event data is:', event.eventData); // { page_type: 'homepage' }
});

cact('emit', 'page_view', { page_type: 'homepage' });
```

**`once`**

Similar to `on`, but the callback fires only once.

```javascript
cact('once', 'page_view', listener_callback);
```

**`off` (Alias: `removeEventListener`)**

Remove an event listener.

```javascript
cact('off', 'page_view', listener_callback);
```

**`trigger`**

Send a server-side event. Any call to `cact('trigger', ...)` will also dispatch a generic `track_all_events` event.

```javascript
cact('trigger', 'add_to_cart', { value: 42, currency: 'EUR' });
```



***

### Tag Context Variables

The Tag Context provides variables used within a tag. If you need a Tag Context similar to "Container Loaded," consider using the `container_ready` custom trigger.

**`cact_container`**

Contains information about the container.

```javascript
{
  id_container: <containerId>,
  id_site: <siteId>,
  sourceKey: <sourceKey>
}
```

**`cact_event`**

The event that triggered the tag, with a property `cact_event.type`.

```javascript
cact('emit', 'page_view', {});
// cact_event.type will be 'page_view'
```

**`cact_event_vars`**

Contains all event variables from the trigger.

```javascript
cact('emit', 'page_view', { hello: 'world' });
// cact_event_vars will be { hello: 'world' }
```

**`cact_event_attrs`**

Contains event attributes, set using the `from` property in `emit` or `trigger` API.

```html
<a href="/home" onclick="cact('emit', 'page_view', { from: this, hello: 'world' })">Home</a>
```

For more examples and a live demo, refer to the documentation links provided.

***

### Best Practices and Tips

**Resolving Site-ID/Source-Key Conflicts**

In multi-container websites, events were sometimes sent with incorrect site-id or source-key. This issue is fixed for tags using triggers other than native "Container Loaded." Use the new `container_ready` custom trigger for accurate site-id/source-key resolution.

**Privacy-Related Events**

You can use various privacy-related events as custom triggers:

* `consent_ready`
* `consent_updated`
* `consent_revoke`
* `banner_show`
* `banner_hide`
* `privacy_center_show`
* `privacy_center_hide`

**Server-Side Tracking as Custom Triggers**

Need to track an event sent in Server Side ?&#x20;

Our `cact('trigger', ...)` will dispatch a corresponding `track_*` event, that you can use as a custom trigger.

```javascript
cact('trigger', 'page_view', { value: 42, currency: 'EUR' });
```

To use this feature as a TMS custom tag trigger, you'll need to prefix the event name with "track\_\*"\
Example:\


<figure><img src="../../../../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Using `cact('on')` for Event Subscription**

You can subscribe to any event sent using `cact('emit')`.

```javascript
cact('on', 'my_custom_event', function(event) {
  console.log('received an event', event.type); // "my_custom_event"
  console.log('event data:', event.eventData); // { var: "value" }
});
```
