# API users

## Visitor

<mark style="color:blue;">`GET`</mark> `https://api.commander1.com/v1.0/engage/visitors/`

This endpoint allows you to

**get properties for one specific visitor**

. When you create the token, you can define which properties to return.

\\

This API is more designed to be called from a tag in each user's browser.

#### Query Parameters

| Name     | Type    | Description                                                                   |
| -------- | ------- | ----------------------------------------------------------------------------- |
| callback | string  | (optional) Callback for jsonp request                                         |
| token    | string  | Security token                                                                |
| site     | integer | ID of the site                                                                |
| tcid     | string  | Cookie id. If empty (recommanded) it will read the tcid in the user's cookie. |

{% tabs %}
{% tab title="200 " %}
```
{
    "user_age": 39,
    "user_privacy_categories": [
      "11",
      "12",
      "13"
    ]
}
```
{% endtab %}
{% endtabs %}

## User

<mark style="color:blue;">`GET`</mark> `https://api.commander1.com/engage/user/`

This endpoint allows you to

**get properties for one specific user**

based on a

`user_id`

. When you create the token, you can define which properties to return.

#### Query Parameters

| Name     | Type    | Description    |
| -------- | ------- | -------------- |
| token    | string  | Security token |
| user\_id | string  | ID of the user |
| site     | integer | ID of the site |

{% tabs %}
{% tab title="200 Consent successfully retrieved." %}
```javascript
{
    "user_age": 39,
    "user_privacy_categories": [
      "11",
      "12",
      "13"
    ]
}
```
{% endtab %}

{% tab title="404 Could not find a user matching this query." %}
```javascript
{
    "message": "Person not found"
}
```
{% endtab %}
{% endtabs %}

## User

<mark style="color:orange;">`PUT`</mark> `https://api.commander1.com/engage/user/`

Insert or update a user

#### Query Parameters

| Name     | Type   | Description              |
| -------- | ------ | ------------------------ |
| site     | string | Id of the site (account) |
| user\_id | string | Id of the user.          |
| token    | string | Security token           |

{% tabs %}
{% tab title="200 " %}
```
{"success":true}
```
{% endtab %}
{% endtabs %}

#### Example Request <a href="#example-request" id="example-request"></a>

`PUT`

https://api.commander1.com/engage/user/?site=1234\&user\_id=1234\&token=WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA

```
{
"preferences.channel":"email",
"preference.frequency":"30d",
...
}
```

## DELETE user

Delete a user

#### Resource URL <a href="#resource-url" id="resource-url"></a>

https://api.commander1.com/engage/user/

#### Resource Information <a href="#resource-information" id="resource-information"></a>

| Response formats         | JSON        |
| ------------------------ | ----------- |
| Requires authentication? | Yes (token) |

#### Parameters

| NAME              | REQUIREMENT    | EXAMPLE VALUES                   | DESCRIPTION       |
| ----------------- | -------------- | -------------------------------- | ----------------- |
| site              | d+             | 1234                             | Id of the site    |
| user\_id          | d+             | 1234                             | Id of the user    |
| tc\_id (optional) | d+             | 1234                             | Id of the visitor |
| token             | \[a-zA-Z0-9]\* | WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA | Security token    |

#### Example Request <a href="#example-request" id="example-request"></a>

`DELETE`

https://api.commander1.com/engage/user/?site=1234\&user\_id=1234\&tc\_id=1234\&token=WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA

#### Response <a href="#example-request" id="example-request"></a>

```
{"success":true}
```
