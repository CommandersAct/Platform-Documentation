---
description: This article describes the server-side destination APIs.
---

# Serverside javascript helpers

## `decodeURI` <a href="getalleventdata" id="getalleventdata"></a>

Decodes any encoded characters in the provided URI. Returns a **string** that represents the decoded URI. Returns `undefined` when provided with invalid input.

**Syntax**

```javascript
decodeUri(encoded_uri);
```

**Example**

```javascript
const decodeUri = require('decodeUri');

const decodedUrl = decodeUri(data.encodedUrl);
if (decodedUrl) {
  // ...
}
```

| Parameter         | Type     | Description                                                                                                                                         |
| ----------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`encoded_uri`** | _string_ | A URI that has been encoded by [`encodeUri()`](https://developers.google.com/tag-platform/tag-manager/server-side/api#encodeuri) or by other means. |

## `decodeUriComponent` <a href="decodeuricomponent" id="decodeuricomponent"></a>

Decodes any encoded characters in the provided URI component. Returns a **string** that represents the decoded URI component. Returns `undefined` when given invalid input.

**Syntax**

```javascript
decodeUriComponent(encoded_uri_component);
```

**Example**

```javascript
const decodeUriComponent = require('decodeUriComponent');

const decodedQuery = decodeUriComponent(data.query);
if (decodedQuery) {
  // ...
}
```

| Parameter                   | Type     | Description                                                                                                                                                                     |
| --------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`encoded_uri_component`** | _string_ | A URI component that has been encoded by [`encodeUriComponent()`](https://developers.google.com/tag-platform/tag-manager/server-side/api#encodeuricomponent) or by other means. |

## `encodeUri` <a href="getalleventdata" id="getalleventdata"></a>

Returns an encoded Uniform Resource Identifier (URI) by escaping special characters. Returns a **string** that represents the provided string encoded as a URI.

**Syntax**

```javascript
encodeUri(uri);
```

**Example**

```javascript
const encodeUri = require('encodeUri');
const sendHttpGet = require('sendHttpGet');

sendHttpGet('https://www.example.com/' + encodeUri(pathInput));
```

| Parameter | Type     | Description     |
| --------- | -------- | --------------- |
| `uri`     | _string_ | A complete URI. |

## `encodeUriComponent` <a href="encodeuricomponent" id="encodeuricomponent"></a>

Returns an encoded Uniform Resource Identifier (URI) by escaping special characters. Returns a **string** that represents the provided string encoded as a URI.

**Syntax**

```javascript
encodeUriComponent(str);
```

**Example**

```javascript
const encodeUriComponent = require('encodeUriComponent');
const sendHttpGet = require('sendHttpGet');

sendHttpGet('https://www.example.com/?' + encodeUriComponent(queryInput));
```

| Parameter | Type     | Description           |
| --------- | -------- | --------------------- |
| **`str`** | _string_ | A component of a URI. |

## `fromBase64` <a href="frombase64" id="frombase64"></a>

Decodes a base64-encoded string. Returns `undefined` if the input is invalid.

**Syntax**

```javascript
fromBase64(base64EncodedString);
```

**Example**

```javascript
const fromBase64 = require('fromBase64');

const greeting = fromBase64('aGVsbG8=');
if (greeting === 'hello') {
  // ...
}
```

| Parameter                 | Type     | Description            |
| ------------------------- | -------- | ---------------------- |
| **`base64EncodedString`** | _string_ | Base64 encoded string. |

## `generateRandom` <a href="generaterandom" id="generaterandom"></a>

Returns a random **number** (integer) within the given range.

**Syntax**

```javascript
generateRandom(min, max);
```

**Example**

```javascript
const generateRandom = require('generateRandom');

const randomValue = generateRandom(0, 10000000);
```

| Parameter | Type     | Description                                                  |
| --------- | -------- | ------------------------------------------------------------ |
| **`min`** | _number_ | Minimum potential value of the returned integer (inclusive). |
| **`max`** | _number_ | Maximum potential value of the returned integer (inclusive). |

## `getAllEventData` <a href="getalleventdata" id="getalleventdata"></a>

Returns a copy of the event data.

**Syntax**

```javascript
getAllEventData();
```

**Example**

```javascript
const getAllEventData= require('getAllEventData');
const eventModel = getAllEventData();
//build body request from event properties 
const body = {
    crm_id:eventModel.user.id,
    currency:eventModel.currency
};
```

## `getCookieValues` <a href="getcookievalues" id="getcookievalues"></a>

Returns an array containing the values of all cookies with the given name.

**Syntax**

```
getCookieValues(name[, noDecode]);
```

**Example**

```javascript
const getCookieValues = require('getCookieValues');
const facebook_fbp = getCookieValues('fbp')[0];
if (facebook_fbp ) {  // ...}
```

****

**Parameters**

| Parameter      | Type      | Description                                                                                  |
| -------------- | --------- | -------------------------------------------------------------------------------------------- |
| **`name`**     | _string_  | Name of the cookie.                                                                          |
| **`noDecode`** | _boolean_ | If `true`, the cookie values will not be decoded before being returned. Defaults to `false`. |

## `getEventData` <a href="geteventdata" id="geteventdata"></a>

Returns a copy of the value at the given path in the event data. Returns `undefined` if there is no event data or if there is no value at the given path.

**Syntax**

```
getEventData(keyPath);
```

**Example**

```javascript
const getEventData = require('getEventData');

const campaignId = getEventData('campaign.id');
const itemId = getEventData('items.0.id');
const referrer = getEventData('page_referrer');
```

**Parameters**

| Parameter     | Type  | Description                                                                                                                                                                                       |
| ------------- | ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`keyPath`** | _any_ | The path of the key, where path components are separated by dots. The path components can be keys in an object or indices in an array. If `keyPath` is not a string, it is coerced into a string. |

## `getRemoteAddress` <a href="getremoteaddress" id="getremoteaddress"></a>

Returns a **string** representation of the IP address where the request originated, e.g. `62.123.65.780` for IPv4 or `2001:0db8:85a3:0:0:8a2e:0370:1234` for IPv6

**Syntax**

```
getRemoteAddress();
```

## `JSON` <a href="json" id="json"></a>

Returns an object that provides JSON functions.

The `parse()` function parses a JSON string to construct the value or object described by the string. If the value cannot be parsed (malformed JSON), the function will return `undefined`. If the input value is not a string, the input will be coerced to a string.

The `stringify()` function converts the input into a JSON string. If the value cannot be parsed (ex. the object has a cycle), the method will return `undefined`.

**Syntax**

```
JSON.parse(yourString);
JSON.stringify(yourObject);
```

**Example**

```
const JSON = require('JSON');
// The JSON input string is converted to an object.
const object = JSON.parse('{"foo":"bar"}');
// The input object is converted to a JSON string.
const str = JSON.stringify({foo: 'bar'});
```

****

## `Math` <a href="math" id="math"></a>

An object providing `Math` functions.

**Syntax**

```
const Math = require('Math');
// Retrieve the absolute value.
const absolute = Math.abs(-5);
// Round the input down to the nearest integer.
const roundedDown = Math.floor(4.6);
// Round the input up to the nearest integer.
const roundedUp = Math.ceil(2.1);
// Round the input to the nearest integer.
const rounded = Math.round(4.2);
// Return the largest argument.
const biggest = Math.max(1, 4);
// Return the smallest argument.
const smallest = Math.min(4, 5);
// Return the first argument raised to the power of the second argument.
const powerful = Math.pow(4, 2);
// Return the square root of the argument.
const unsquared = Math.sqrt(81);
```

**Parameters**

Math function parameters are converted to numbers.

## `sendHttpGet` <a href="sendhttpget" id="sendhttpget"></a>

Makes an HTTP GET request to the specified URL, and invokes a callback with the response once the request completes or times out.

**Syntax**

```javascript
sendHttpGet(url[, callback[, options]]);
```

**Example**

```javascript
const sendHttpGet = require('sendHttpGet');
// Sends a GET request and nominates response// based on the response from the GET 
sendHttpGet('https://example.com/collect', function(statusCode, headers, body) {
    if (statusCode != 200) {yourCallbackFunction();}
}, {
    headers: {key: 'value'},
    timeout: 500
});
```

**Parameters**

| Parameter      | Type       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`url`**      | _string_   | The request URL.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **`callback`** | _function_ | <p>An optional callback to invoke upon request completion, error, or timeout.<br><br>It is invoked with the <strong>response status code</strong>, the <strong>response headers</strong>, and the <strong>response body</strong> (or undefined if there was no response body).<br>If the request failed (e.g. invalid URL, no route to host, SSL negotiation failure, etc.), the callback will be invoked with a <strong>response status code of zero</strong>, <strong>no headers</strong>, and an <strong>undefined body</strong>.<br>If the <code>'timeout'</code> option was set and the request timed out, the callback will be invoked with a <strong>response status code of -1</strong>, <strong>no headers</strong>, and an <strong>undefined body</strong>.</p> |
| **`options`**  | _object_   | Optional request options. The supported options are **headers**, **timeout**.  Advanced options can be added in **extraOptions**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

#### **Options**

* **headers**: Additional request headers represented as an object.
* **timeout**: The timeout, in milliseconds, before the request is aborted.
* **extraOptions**: Advanced options (ex: {strictSSL:true})

## `sendHttpRequest` <a href="sendhttprequest" id="sendhttprequest"></a>

Makes an HTTP request to the specified URL, and invokes a callback with the response once the request completes or times out.

**Syntax**

```
sendHttpRequest(url[, callback[, options[, body]]]);
```

**Example**

```javascript
const sendHttpRequest = require('sendHttpRequest');
const body = {
    user_type:'vip',
    account:'123'
};
// Sends a POST request 
sendHttpRequest('https://example.com/collect', function(statusCode, headers, body) {
    //your callback code...
}, {
    headers: {
        token: '123456789'
    },
    method: 'POST',
    timeout: 1000
}, body);
```

**Parameters**

| Parameter      | Type       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| -------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **`url`**      | _string_   | The request URL.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **`callback`** | _function_ | <p>An optional callback to invoke upon request completion, error, or timeout.<br><br>It is invoked with the <strong>response status code</strong>, the <strong>response headers</strong>, and the <strong>response body</strong> (or undefined if there was no response body).<br>If the request failed (e.g. invalid URL, no route to host, SSL negotiation failure, etc.), the callback will be invoked with a <strong>response status code of zero</strong>, <strong>no headers</strong>, and an <strong>undefined body</strong>.<br>If the 'timeout' option was set and the request timed out, the callback will be invoked with a <strong>response status code of -1</strong>, <strong>no headers</strong>, and an <strong>undefined body</strong>.</p> |
| **`options`**  | _object_   | Optional request options. The supported options are: **headers**, **method**, and **timeout**. Unknown option keys are ignored. Advanced options can be added in **extraOptions.**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **`body`**     | _string_   | Optional request body.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

**Options**

* **headers**: Additional request headers.
* **method**: The request method, defaults to 'GET'.
* **timeout**: The timeout, in milliseconds, before the request is aborted.
* **extraOptions**: Advanced options (ex: {strictSSL:true})

## `md5Sync`

Calculates and returns the `md5 `digest of the input.

**Syntax**

```
md5Sync(input);
```

**Example**

```javascript
const md5Sync= require('md5Sync');
const email = {};
email.md5 = md5Sync(user.user_email);
sendHttpGet('https://example.com/collect?e5=' + email.md5);
```
