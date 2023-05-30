# Common events

## page\_view <a href="#page_view" id="page_view"></a>

The `page_view` call lets you record whenever a user sees a page of your website, along with any optional properties about the page.

**Parameters (required and recommended)**

<table><thead><tr><th width="144">Name</th><th width="99">Type</th><th width="82">Required</th><th width="160">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>page_type</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>product_list</td><td><p>Page category. Recommanded predefined types:</p><ul><li>home</li><li>landing</li><li>product_list</li><li>product</li><li>content_list</li><li>content</li><li>search</li><li>funnel</li><li>success</li><li>funnel_confirmation</li><li>account</li><li>cart</li><li>legal (e.g. Privacy Policy)</li></ul><p>Equivalent to <code>tc_vars.env_template</code></p></td></tr><tr><td><code>page_name</code></td><td><code>string</code></td><td>No</td><td>Suggestion for Mother's Day</td><td>Name of the page.</td></tr><tr><td><code>user</code></td><td><a href="common-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Automatically added parameters by cact API for web sources**

<table><thead><tr><th width="133">Name</th><th width="103">Type</th><th width="81">Required</th><th width="161">Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>user</code></td><td><a href="common-events.md#user">Object &#x3C;User></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr><tr><td><code>title</code></td><td><code>string</code></td><td>No</td><td>Products - MySite.com</td><td>Title of the page :<a href="https://developer.mozilla.org/en-US/docs/Web/API/Document/title"><code>document.title</code></a> from the DOM API</td></tr><tr><td><code>url</code></td><td><code>string</code></td><td>No</td><td><a href="http://www.mysite.com">http://www.mysite.com</a></td><td>Full URL of the page. Equivalent to<a href="https://developer.mozilla.org/en-US/docs/Web/API/Location"><code>location.href</code></a> from the DOM API.</td></tr><tr><td><code>path</code></td><td><code>string</code></td><td>No</td><td>/products/mothers</td><td>Path portion of the URL of the page : <a href="https://developer.mozilla.org/en-US/docs/Web/API/Location"><code>location.pathname</code></a> from the DOM API.</td></tr><tr><td><code>referrer</code></td><td><code>string</code></td><td>No</td><td><a href="http://www.example.com">http://www.example.com</a></td><td>Full URL of the previous page : <a href="https://developer.mozilla.org/en-US/docs/Web/API/Document/referrer"><code>document.referrer</code></a> from the DOM API.</td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="Javascript" %}
```javascript
cact('trigger','page_view', {
  page_type: 'product_list',
  page_name: 'Best sellers',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCPageViewEvent("product_list")
event.pageName = "Best sellers"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```java
// Some code
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCPageViewEvent *event = [[TCPageViewEvent alloc] init];
event.pageType = @"product_list";
event.pageName = @"Best sellers";
[TCS execute: event];

//or you could also use it in a constructor, as follow:
TCPageViewEvent *event = [[TCPageViewEvent alloc] initWithType: @"type"];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let event = TCPageViewEvent(type: "product list")
	event?.pageName = "Best sellers"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCPageViewEvent();
    event.pageName = "event_page_name";
    event.pageType = "event_page_type";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
   "item": [
      {
         "name": "Page_view",
         "request": {
            "method": "POST",
            "header": [],
            "body": {
               "mode": "raw",
               "raw": "{\r\n    \"event\": \"page_view\",\r\n    \"properties\": {\r\n        \"page_type\": \"homepage\",\r\n        \"page_name\": \"welcome\"\r\n    }\r\n}",
               "options": {
                  "raw": {
                     "language": "json"
                  }
               }
            },
            "url": {
               "raw": "https://collect.commander1.com/events?tc_s=#your_site_id#&token=#your_source_key#",
               "protocol": "https",
               "host": [
                  "collect",
                  "commander1",
                  "com"
               ],
               "path": [
                  "events"
               ],
               "query": [
                  {
                     "key": "tc_s",
                     "value": "#your_site_id#"
                  },
                  {
                     "key": "token",
                     "value": "#your_source_key#"
                  }
               ]
            }
         },
         "response": []
      }
   ]
}
```
{% endtab %}
{% endtabs %}

## login <a href="#login" id="login"></a>

Send this event to signify that a user has logged in.

#### Parameters <a href="#parameters_14" id="parameters_14"></a>

<table><thead><tr><th width="119">Name</th><th width="103">Type</th><th width="110">Required</th><th width="224">Example</th><th>Description</th></tr></thead><tbody><tr><td><code>method</code></td><td><code>string</code></td><td>No</td><td>LinkedIn</td><td>The method used to login.</td></tr><tr><td><code>user</code></td><td><a href="common-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="Javascript" %}
```javascript
cact('trigger', 'login', {
  method: 'LinkedIn',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCLoginEvent()
event.method = "LinkedIn"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```
// Some code
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCLoginEvent *event = [[TCLoginEvent alloc] init];
event.method = @"LinkedIn";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let event = TCLoginEvent()
	event.method = "linkedin"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCLoginEvent();
    event.method = "LinkedIn";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
   "item": [
      {
         "name": "Login",
         "request": {
            "method": "POST",
            "header": [],
            "body": {
               "mode": "raw",
               "raw": "{\r\n    \"event\": \"login\",\r\n    \"properties\": {\r\n        \"method\": \"LinkedIn\"\r\n    }\r\n}",
               "options": {
                  "raw": {
                     "language": "json"
                  }
               }
            },
            "url": {
               "raw": "https://collect.commander1.com/events?tc_s=#your_site_id#&token=#your_source_key#",
               "protocol": "https",
               "host": [
                  "collect",
                  "commander1",
                  "com"
               ],
               "path": [
                  "events"
               ],
               "query": [
                  {
                     "key": "tc_s",
                     "value": "#your_site_id#"
                  },
                  {
                     "key": "token",
                     "value": "#your_source_key#"
                  }
               ]
            }
         },
         "response": []
      }
   ]
}
```
{% endtab %}
{% endtabs %}

## search

Use this event to contextualize search operations. This event can help you identify the most popular content in your app.

#### Parameters <a href="#parameters_21" id="parameters_21"></a>

<table><thead><tr><th width="169">Name</th><th width="102">Type</th><th width="82">Required</th><th width="148">Example value</th><th>Description</th></tr></thead><tbody><tr><td><code>search_term</code></td><td><code>string</code></td><td><strong>Yes</strong></td><td>t-shirts</td><td>The term that was searched for.</td></tr><tr><td><code>user</code></td><td><a href="common-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="Javascript" %}
```javascript
cact('trigger','search', {
  search_term: 't-shirts',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCSearchEvent("t-shirts");
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```
// Some code
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCSearchEvent *event = [[TCSearchEvent alloc] init];
event.searchTerm = @"t-shirts";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
<pre class="language-swift"><code class="lang-swift">let event = TCSearchEvent(searchTerm: "t-shirts")
<strong>    serverside.execute(event)
</strong></code></pre>
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCSearchEvent();
    event.searchTerm = "t-shirts";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
   "item": [
      {
         "name": "Search",
         "request": {
            "method": "POST",
            "header": [],
            "body": {
               "mode": "raw",
               "raw": "{\r\n    \"event\": \"search\",\r\n    \"properties\": {\r\n        \"search_term\": \"t-shirts\"\r\n    }\r\n}",
               "options": {
                  "raw": {
                     "language": "json"
                  }
               }
            },
            "url": {
               "raw": "https://collect.commander1.com/events?tc_s=#your_site_id#&token=#your_source_key#",
               "protocol": "https",
               "host": [
                  "collect",
                  "commander1",
                  "com"
               ],
               "path": [
                  "events"
               ],
               "query": [
                  {
                     "key": "tc_s",
                     "value": "#your_site_id#"
                  },
                  {
                     "key": "token",
                     "value": "#your_source_key#"
                  }
               ]
            }
         },
         "response": []
      }
   ]
}
```
{% endtab %}
{% endtabs %}

## select\_content

This event signifies that a user has selected some content of a certain type. This event can help you identify popular content and categories of content in your app or click on internal promotion.

#### Parameters <a href="#parameters_22" id="parameters_22"></a>

<table><thead><tr><th width="175">Name</th><th width="100">Type</th><th width="76">Required</th><th width="159">Example value</th><th>Description</th></tr></thead><tbody><tr><td><code>content_type</code></td><td><code>string</code></td><td>No</td><td>product</td><td>The type of selected content.</td></tr><tr><td><code>item_id</code></td><td><code>string</code></td><td>No</td><td>I_12345</td><td>An identifier for the item that was selected.</td></tr><tr><td><code>user</code></td><td><a href="common-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="Javascript" %}
```javascript
cact('trigger','select_content', {
  content_type: 'product',
  item_id: 'I_12345',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCSelectContentEvent();
event.contentType = "product"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```
// Some code
```
{% endtab %}

{% tab title="Objective-C (iOS)" %}
```objectivec
TCSelectContentEvent *event = [[TCSelectContentEvent alloc] init];
event.contentType = @"product";
event.itemID = @"I_12345";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift (iOS)" %}
```swift
let event = TCSelectContentEvent()
	event.contentType = "product"
	event.itemID = "I_12345"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Dart (Flutter)" %}
```dart
var event = TCSelectContentEvent();
    event.contentType = "product";
    event.itemId = "I_12345";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
   "item": [
      {
         "name": "Select_content",
         "request": {
            "method": "POST",
            "header": [],
            "body": {
               "mode": "raw",
               "raw": "{\r\n    \"event\": \"select_content\",\r\n    \"properties\": {\r\n        \"content_type\": \"product\",\r\n        \"item_id\": \"I_12345\"\r\n    }\r\n}",
               "options": {
                  "raw": {
                     "language": "json"
                  }
               }
            },
            "url": {
               "raw": "https://collect.commander1.com/events?tc_s=#your_site_id#&token=#your_source_key#",
               "protocol": "https",
               "host": [
                  "collect",
                  "commander1",
                  "com"
               ],
               "path": [
                  "events"
               ],
               "query": [
                  {
                     "key": "tc_s",
                     "value": "#your_site_id#"
                  },
                  {
                     "key": "token",
                     "value": "#your_source_key#"
                  }
               ]
            }
         },
         "response": []
      }
   ]
}
```
{% endtab %}
{% endtabs %}

## sign\_up <a href="#sign_up" id="sign_up"></a>

This event indicates that a user has signed up for an account.

#### Parameters **(required and recommended)** <a href="#parameters_27" id="parameters_27"></a>

<table><thead><tr><th width="117">Name</th><th width="102">Type</th><th width="104">Required</th><th width="160">Example</th><th>Description</th></tr></thead><tbody><tr><td><code>method</code></td><td><code>string</code></td><td>No</td><td>Facebook</td><td>The method used for sign up.</td></tr><tr><td><code>user</code></td><td><a href="common-events.md#user"><code>Object&#x3C;User></code></a></td><td>Yes</td><td><p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p></td><td><p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p></td></tr></tbody></table>

**Example**

{% tabs %}
{% tab title="Javascript" %}
```javascript
cact('trigger','sign_up', {
  method: 'email',
  user: {
    id: '12356',
    email:'toto@domain.fr',
    consent_categories: [1,3]
  }
});
```
{% endtab %}

{% tab title="Kotlin (Android)" %}
```kotlin
val event = TCSignUpEvent();
event.method = "email"
serverside.execute(event)
```
{% endtab %}

{% tab title="Java  (Android)" %}
```
// Some code
```
{% endtab %}

{% tab title="iOS" %}
```objectivec
TCSignUpEvent *event = [[TCSignUpEvent alloc] init];
event.method = @"email";
[TCS execute: event];
```
{% endtab %}

{% tab title="Swift" %}
```swift
let event = TCSignUpEvent()
	event.method = "email"
	serverside?.execute(event)
```
{% endtab %}

{% tab title="Flutter" %}
```dart
var event = TCSignUpEvent();
    event.method = "email";
    serverside.execute(event);
```
{% endtab %}

{% tab title="json" %}
```json
{
   "item": [
      {
         "name": "Sign_up",
         "request": {
            "method": "POST",
            "header": [],
            "body": {
               "mode": "raw",
               "raw": "{\r\n    \"event\": \"sign_up\",\r\n    \"properties\": {\r\n        \"method\": \"email\"\r\n    }\r\n}",
               "options": {
                  "raw": {
                     "language": "json"
                  }
               }
            },
            "url": {
               "raw": "https://collect.commander1.com/events?tc_s=#your_site_id#&token=#your_source_key#",
               "protocol": "https",
               "host": [
                  "collect",
                  "commander1",
                  "com"
               ],
               "path": [
                  "events"
               ],
               "query": [
                  {
                     "key": "tc_s",
                     "value": "#your_site_id#"
                  },
                  {
                     "key": "token",
                     "value": "#your_source_key#"
                  }
               ]
            }
         },
         "response": []
      }
   ]
}
```
{% endtab %}
{% endtabs %}

## - COMMON SCHEMAS -

### User

When you send an event, it needs to carry enough information to identify which user made it. We can link events together using cookies. But destination partners require accurate identifiers to take actions.

`id` and `email` are usually the most useful parameters. Though some destination partners also use `firstname`, `lastname`, `birthdate`, `city`, ...

You won't always have all of those parameters. But it is recommended to send them as soon as you can during user's browsing.

#### Parameters **(required and recommended)** <a href="#parameters_17" id="parameters_17"></a>

<table><thead><tr><th width="229">Name</th><th width="118">Type</th><th width="104">Required</th><th>Example Value</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>string</code></td><td>No*</td><td>845454</td><td><p>User's main identifier (e.g. CRM id)</p><p>(*) required for many destinations and internal processing.</p></td></tr><tr><td><code>email</code></td><td><code>string</code></td><td>Yes*</td><td>john.doe@example.com</td><td><p>Email (plain value)</p><p>(*) required for many destinations and internal processing. Not required if <code>email_sha256</code> is provided</p></td></tr><tr><td><code>email_md5</code></td><td><code>string</code></td><td>No*</td><td>8eb1b52... (size 32)</td><td>Email, hashed using <a href="https://en.wikipedia.org/wiki/MD5">MD5 algorithm</a>. Not required if <code>email</code> is provided (see below)</td></tr><tr><td><code>email_sha256</code></td><td><code>string</code></td><td>No*</td><td>836f82d... (size 64)</td><td>Email, hashed using <a href="https://en.wikipedia.org/wiki/SHA-2">SHA-256 algorithm</a>. Not required if <code>email</code> is provided (see below)</td></tr><tr><td><code>phone</code></td><td><code>string</code></td><td>No*</td><td>+33612345678</td><td>Phone number, <a href="https://en.wikipedia.org/wiki/E.164">E.164</a> format<br>(*) required for some destinations.</td></tr><tr><td><code>firstname</code></td><td><code>string</code></td><td>No</td><td>John</td><td>First name</td></tr><tr><td><code>lastname</code></td><td><code>string</code></td><td>No</td><td>Doe</td><td>Last name</td></tr><tr><td><code>gender</code></td><td><code>string</code></td><td>No</td><td>m</td><td><p>Gender</p><ul><li><code>f</code> for Female</li><li><code>m</code> for Male</li></ul></td></tr><tr><td><code>birthdate</code></td><td><code>string</code></td><td>No</td><td>1970-01-01</td><td>Birth date, <code>YYYY-MM-DD</code> format</td></tr><tr><td><code>city</code></td><td><code>string</code></td><td>No</td><td>Boston</td><td>City</td></tr><tr><td><code>state</code></td><td><code>string</code></td><td>No</td><td>Massachusetts</td><td>State</td></tr><tr><td><code>zipcode</code></td><td><code>string</code></td><td>No</td><td>02108</td><td>Zip code</td></tr><tr><td><code>country</code></td><td><code>string</code></td><td>No</td><td>USA</td><td>Country code, ISO 3166-1 <a href="https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2">2-letter</a> or <a href="https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3">3-letter</a> formats</td></tr><tr><td><code>consent_categories</code></td><td><code>Array</code></td><td><strong>Yes</strong></td><td>[1,2,3]</td><td>User's consent categories.<br>Necessary to grant data sharing with destination partners. It is automatically filled from web sources if you use Commanders Act CMP.</td></tr></tbody></table>

**About Hashing**

In some cases, you won't be able to send a parameter **plain** value. It is either unavailable or restricted.

Thus it might be possible to send the **hashed** values. We currently accept 2 algorithm : [`md5`](https://en.wikipedia.org/wiki/MD5) and [`sha256`](https://en.wikipedia.org/wiki/SHA-2).

Every `user.<property>` can be sent under hashed format with algorithm suffix: `_md5` or `_sha256` _(underscore followed by lowercase algorithm name)_

Example :

```
{
  user: {
    email_md5: '8eb1b522f60d11fa897de1dc6351b7e8',                                      // md5('john.doe@example.com')
    email_sha256: '836f82db99121b3481011f16b49dfa5fbc714a0d1b1b9f784a1ebbbf5b39577f',   // sha256('john.doe@example.com')
    phone_md5: '60dd761f55cb17f0532c9fb1679e8ddd',                                      // md5('+33612345678')
    phone_sha256: '42d573cfc315801d4cd8eddd5416b416a0bf298b9b9e12d6b07442c91db42bd8',   // sha256('+33612345678')
  }
}
```

> :information\_source: we only support hex (base16) encoding\
> _(i.e.: **hashed** values are carried by strings with \[0-9a-f] characters)_\
> Other encodings are not supported yet

No need to send both **plain** and **hashed** values :

* if you send **plain** value, the **hashed** values aren't necessary\
  _We can generate **hashed** values on server side using **plain** value_
* if you don't send **plain** value, then you should fill as much **hashed** values as possible\
  _Partners require different hash algorithms and without **plain** value, we can't generate any hash. That's why we need the exact **hashed** value_
