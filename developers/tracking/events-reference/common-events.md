# Common events

## page\_view <a href="#page_view" id="page_view"></a>

The `page_view` call lets you record whenever a user sees a page of your website, along with any optional properties about the page.

**Parameters (required and recommended)**

| Name        | Type                                    | Required | Example Value                                                                                                                                                 | Description                                                                                                                                                                                                                                                                                                                                                          |
| ----------- | --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `page_type` | `string`                                | **Yes**  | product\_list                                                                                                                                                 | <p>Page category. Recommanded predefined types:</p><ul><li>home</li><li>landing</li><li>product_list</li><li>product</li><li>content_list</li><li>content</li><li>search</li><li>funnel</li><li>success</li><li>funnel_confirmation</li><li>account</li><li>cart</li><li>legal (e.g. Privacy Policy)</li></ul><p>Equivalent to <code>tc_vars.env_template</code></p> |
| `page_name` | `string`                                | No       | Suggestion for Mother's Day                                                                                                                                   | Name of the page.                                                                                                                                                                                                                                                                                                                                                    |
| `user`      | [`Object<User>`](common-events.md#user) | Yes      | <p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p> | <p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p>                                                                                                       |

**Automatically added parameters by cact API for web sources**

| Name       | Type                                    | Required | Example Value                                                                                                                                                 | Description                                                                                                                                                                                                                                                    |
| ---------- | --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `user`     | [Object \<User>](common-events.md#user) | Yes      | <p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p> | <p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p> |
| `title`    | `string`                                | No       | Products - MySite.com                                                                                                                                         | Title of the page :[`document.title`](https://developer.mozilla.org/en-US/docs/Web/API/Document/title) from the DOM API                                                                                                                                        |
| `url`      | `string`                                | No       | [http://www.mysite.com](http://www.mysite.com)                                                                                                                | Full URL of the page. Equivalent to[`location.href`](https://developer.mozilla.org/en-US/docs/Web/API/Location) from the DOM API.                                                                                                                              |
| `path`     | `string`                                | No       | /products/mothers                                                                                                                                             | Path portion of the URL of the page : [`location.pathname`](https://developer.mozilla.org/en-US/docs/Web/API/Location) from the DOM API.                                                                                                                       |
| `referrer` | `string`                                | No       | [http://www.example.com](http://www.example.com)                                                                                                              | Full URL of the previous page : [`document.referrer`](https://developer.mozilla.org/en-US/docs/Web/API/Document/referrer) from the DOM API.                                                                                                                    |

**Example**

```javascript
cact('trigger','page_view', {
  page_type: 'product_list',
  page_name: 'Best sellers'
});
```

## login <a href="#login" id="login"></a>

Send this event to signify that a user has logged in.

#### Parameters <a href="#parameters_14" id="parameters_14"></a>

| Name     | Type                                    | Required | Example                                                                                                                                                       | Description                                                                                                                                                                                                                                                    |
| -------- | --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `method` | `string`                                | No       | LinkedIn                                                                                                                                                      | The method used to login.                                                                                                                                                                                                                                      |
| `user`   | [`Object<User>`](common-events.md#user) | Yes      | <p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p> | <p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p> |

**Example**

```javascript
cact('trigger', 'login', {
  method: 'LinkedIn'
});
```

## &#x20;<a href="#page_view" id="page_view"></a>

## search

Use this event to contextualize search operations. This event can help you identify the most popular content in your app.

#### Parameters <a href="#parameters_21" id="parameters_21"></a>

| Name          | Type                                    | Required | Example value                                                                                                                                                 | Description                                                                                                                                                                                                                                                    |
| ------------- | --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `search_term` | `string`                                | **Yes**  | t-shirts                                                                                                                                                      | The term that was searched for.                                                                                                                                                                                                                                |
| `user`        | [`Object<User>`](common-events.md#user) | Yes      | <p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p> | <p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p> |

#### Example <a href="#example_30" id="example_30"></a>

```javascript
cact('trigger','search', {
  search_term: 't-shirts'
});
```

## select\_content

This event signifies that a user has selected some content of a certain type. This event can help you identify popular content and categories of content in your app or click on internal promotion.

#### Parameters <a href="#parameters_22" id="parameters_22"></a>

| Name           | Type                                    | Required | Example value                                                                                                                                                 | Description                                                                                                                                                                                                                                                    |
| -------------- | --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `content_type` | `string`                                | No       | product                                                                                                                                                       | The type of selected content.                                                                                                                                                                                                                                  |
| `item_id`      | `string`                                | No       | I\_12345                                                                                                                                                      | An identifier for the item that was selected.                                                                                                                                                                                                                  |
| `user`         | [`Object<User>`](common-events.md#user) | Yes      | <p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p> | <p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p> |

#### Example <a href="#example_32" id="example_32"></a>

```javascript
cact('trigger','select_content', {
  content_type: 'product',
  item_id: 'I_12345'
});
```

## sign\_up <a href="#sign_up" id="sign_up"></a>

This event indicates that a user has signed up for an account.

#### Parameters **(required and recommended)** <a href="#parameters_27" id="parameters_27"></a>

| Name     | Type                                    | Required | Example                                                                                                                                                       | Description                                                                                                                                                                                                                                                    |
| -------- | --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `method` | `string`                                | No       | Facebook                                                                                                                                                      | The method used for sign up.                                                                                                                                                                                                                                   |
| `user`   | [`Object<User>`](common-events.md#user) | Yes      | <p><code>{</code><br><code>id: '12345',</code><br><code>email: 'toto@domain.fr',</code></p><p><code>consent_categories: [1,3]</code></p><p><code>}</code></p> | <p><code>consent_categories</code> is the user's consents list. It is automatically filled from web sources if you use Commanders Act CMP.</p><p>You should also add all user's properties in this user object, especially reconciliation key (id, email).</p> |

**Example**

```javascript
cact('trigger','sign_up', {
  method: 'email'
});
```

## - COMMON SCHEMAS -

### User

When you send an event, it needs to carry enough information to identify which user made it. We can link events together using cookies. But destination partners require accurate identifiers to take actions.

`id` and `email` are usually the most useful parameters. Though some destination partners also use `firstname`, `lastname`, `birthdate`, `city`, ...

You won't always have all of those parameters. But it is recommended to send them as soon as you can during user's browsing.

#### Parameters **(required and recommended)** <a href="#parameters_17" id="parameters_17"></a>

| Name                 | Type     | Required | Example Value        | Description                                                                                                                                                                |
| -------------------- | -------- | -------- | -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                 | `string` | No\*     | 845454               | <p>User's main identifier (e.g. CRM id)</p><p>(*) required for many destinations and internal processing.</p>                                                              |
| `email`              | `string` | Yes\*    | john.doe@example.com | <p>Email (plain value)</p><p>(*) required for many destinations and internal processing. Not required if <code>email_sha256</code> is provided</p>                         |
| `email_md5`          | `string` | No\*     | 8eb1b52... (size 32) | Email, hashed using [MD5 algorithm](https://en.wikipedia.org/wiki/MD5). Not required if `email` is provided (see below)                                                    |
| `email_sha256`       | `string` | No\*     | 836f82d... (size 64) | Email, hashed using [SHA-256 algorithm](https://en.wikipedia.org/wiki/SHA-2). Not required if `email` is provided (see below)                                              |
| `phone`              | `string` | No\*     | +33612345678         | <p>Phone number, <a href="https://en.wikipedia.org/wiki/E.164">E.164</a> format<br>(*) required for some destinations.</p>                                                 |
| `firstname`          | `string` | No       | John                 | First name                                                                                                                                                                 |
| `lastname`           | `string` | No       | Doe                  | Last name                                                                                                                                                                  |
| `gender`             | `string` | No       | m                    | <p>Gender</p><ul><li><code>f</code> for Female</li><li><code>m</code> for Male</li></ul>                                                                                   |
| `birthdate`          | `string` | No       | 1970-01-01           | Birth date, `YYYY-MM-DD` format                                                                                                                                            |
| `city`               | `string` | No       | Boston               | City                                                                                                                                                                       |
| `state`              | `string` | No       | Massachusetts        | State                                                                                                                                                                      |
| `zipcode`            | `string` | No       | 02108                | Zip code                                                                                                                                                                   |
| `country`            | `string` | No       | USA                  | Country code, ISO 3166-1 [2-letter](https://en.wikipedia.org/wiki/ISO\_3166-1\_alpha-2) or [3-letter](https://en.wikipedia.org/wiki/ISO\_3166-1\_alpha-3) formats          |
| `consent_categories` | `Array`  | **Yes**  | \[1,2,3]             | <p>User's consent categories.<br>Necessary to grant data sharing with destination partners. It is automatically filled from web sources if you use Commanders Act CMP.</p> |

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
