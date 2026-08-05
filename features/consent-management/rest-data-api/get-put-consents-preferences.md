---
description: Get/put user consent stored in DataCommander
---

# GET/PUT Consents / preferences

## User Consents

<mark style="color:blue;">`GET`</mark> `https://api.commander1.com/engage/user/`

This endpoint allows you to get categorie's consent for one specific user

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
    "user_privacy_optin": 1,
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

## Visitor Consents

<mark style="color:blue;">`GET`</mark> `https://api.commander1.com/v1.0/engage/visitors/`

This endpoint allows you to get categorie's consent for one specific visitor

#### Query Parameters

| Name     | Type    | Description                           |
| -------- | ------- | ------------------------------------- |
| callback | string  | (optional) Callback for jsonp request |
| token    | string  | Security token                        |
| site     | integer | ID of the site                        |
| tc\_id   | String  | Optional. Cookie id of the user       |

{% tabs %}
{% tab title="200 Example with optin response" %}
```javascript
{
    "user_privacy_optin": 1,
    "user_privacy_categories": [
      "11",
      "12",
      "13"
    ]
}
```
{% endtab %}

{% tab title="202 Example with optout response" %}
```
{
    "user_privacy_optin": 0,
    "user_privacy_categories": []
}
```
{% endtab %}

{% tab title="404 " %}
```
{
    "message": "visitor not found"
}
```
{% endtab %}
{% endtabs %}

## User Preferences

<mark style="color:orange;">`PUT`</mark> `https://api.commander1.com/engage/user/`

Insert or update a preference in the database (require to have the DataCommander module activated)

#### Query Parameters

| Name     | Type   | Description                                             |
| -------- | ------ | ------------------------------------------------------- |
| site     | string | Id of the site (account)                                |
| user\_id | string | Id of the user. Required if tc\_id parameter is not set |
| token    | string | Security token                                          |

{% tabs %}
{% tab title="200 " %}
```
{"success":true}
```
{% endtab %}
{% endtabs %}

**Syntax and limitations**

* The json playload is represented by a key/value for each preference.
* Each preference property (key) start with "preferences." followed by the preference name : `preferences.your_preference_name`
* The preference name should not contain white space, dot or special characters. Its format is `[A-Za-z0-9_-]`
* The preference value can contain white space, dot but not special characters.
* The API accepts a **maximum of 20 preferences**

**Example Request**

`PUT`

https://api.commander1.com/engage/user/?site=1234\&user\_id=1234\&token=WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA

```
{
  "preferences": {
    "news_monthly": true,
    "news_sales": true
  }
}
```
