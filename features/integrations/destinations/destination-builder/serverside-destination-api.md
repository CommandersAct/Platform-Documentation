---
description: This article describes the server-side destination APIs.
---

# Serverside destination API

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
request.sendHttpGet('https://example.com/collect', function(statusCode, headers, body) {
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
request.sendHttpRequest('https://example.com/collect', function(statusCode, headers, body) {
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
