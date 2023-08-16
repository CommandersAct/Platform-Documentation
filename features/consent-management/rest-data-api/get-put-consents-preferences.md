---
description: Get/put user consent stored in DataCommander
---

# GET/PUT Consents / preferences

{% swagger baseUrl="https://api.commander1.com" path="/engage/user/" method="get" summary="User Consents" %}
{% swagger-description %}
This endpoint allows you to get categorie's consent for one specific user
{% endswagger-description %}

{% swagger-parameter in="query" name="token" type="string" %}
Security token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="user_id" type="string" %}
ID of the user
{% endswagger-parameter %}

{% swagger-parameter in="query" name="site" type="integer" %}
ID of the site
{% endswagger-parameter %}

{% swagger-response status="200" description="Consent successfully retrieved." %}
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
{% endswagger-response %}

{% swagger-response status="404" description="Could not find a user matching this query." %}
```javascript
{
    "message": "Person not found"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.commander1.com/v1.0" path="/engage/visitors/" method="get" summary="Visitor Consents" %}
{% swagger-description %}
This endpoint allows you to get categorie's consent for one specific visitor
{% endswagger-description %}

{% swagger-parameter in="query" name="callback" type="string" %}
(optional) Callback for jsonp request
{% endswagger-parameter %}

{% swagger-parameter in="query" name="token" type="string" %}
Security token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="site" type="integer" %}
ID of the site
{% endswagger-parameter %}

{% swagger-parameter in="query" name="tc_id" %}
Optional. Cookie id of the user
{% endswagger-parameter %}

{% swagger-response status="200" description="Example with optin response" %}
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
{% endswagger-response %}

{% swagger-response status="202" description="Example with optout response" %}
```
{
    "user_privacy_optin": 0,
    "user_privacy_categories": []
}
```
{% endswagger-response %}

{% swagger-response status="404" description="" %}
```
{
    "message": "visitor not found"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.commander1.com" path="/engage/user/" method="put" summary="User" %}
{% swagger-description %}
Insert or update a preference in the database (require to have the DataCommander module activated)
{% endswagger-description %}

{% swagger-parameter in="query" name="site" type="string" %}
Id of the site (account)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="user_id" type="string" %}
Id of the user. Required if tc_id parameter is not set
{% endswagger-parameter %}

{% swagger-parameter in="query" name="token" type="string" %}
Security token
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{"success":true}
```
{% endswagger-response %}
{% endswagger %}

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
