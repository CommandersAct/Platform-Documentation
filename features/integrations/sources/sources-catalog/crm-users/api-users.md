# API users

{% swagger baseUrl="https://api.commander1.com/v1.0" path="/engage/visitors/" method="get" summary="Visitor" %}
{% swagger-description %}
This endpoint allows you to 

**get properties for one specific visitor**

. When you create the token, you can define which properties to return.

\


This API is more designed to be called from a tag in each user's browser.
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

{% swagger-parameter in="query" name="tcid" type="string" %}
Cookie id. If empty (recommanded) it will read the tcid in the user's cookie.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.commander1.com" path="/engage/user/" method="get" summary="User" %}
{% swagger-description %}
This endpoint allows you to 

**get properties for one specific user**

 based on a 

`user_id`

. When you create the token, you can define which properties to return.
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
    "user_age": 39,
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

##

{% swagger baseUrl="https://api.commander1.com" path="/engage/user/" method="put" summary="User" %}
{% swagger-description %}
Insert or update a user
{% endswagger-description %}

{% swagger-parameter in="query" name="site" type="string" %}
Id of the site (account)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="user_id" type="string" %}
Id of the user. Required if tc_id parameter is not set
{% endswagger-parameter %}

{% swagger-parameter in="query" name="tc_id" type="string" %}
Optional. Cookie id of the user
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

#### Example Request <a href="#example-request" id="example-request"></a>

`PUT`

https://api.commander1.com/engage/user/?site=1234\&user\_id=1234\&tc\_id=1234\&token=WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA

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

| NAME              | REQUIREMENT    | EXAMPLE VALUES                    | DESCRIPTION       |
| ----------------- | -------------- | --------------------------------- | ----------------- |
| site              | d+             |  1234                             | Id of the site    |
| user\_id          | d+             |  1234                             | Id of the user    |
| tc\_id (optional) | d+             |  1234                             | Id of the visitor |
| token             | \[a-zA-Z0-9]\* |  WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA | Security token    |

#### Example Request <a href="#example-request" id="example-request"></a>

`DELETE`

https://api.commander1.com/engage/user/?site=1234\&user\_id=1234\&tc\_id=1234\&token=WvNIX8955cnZ7WF0f632s0Wb99Ql3rtA

#### Response <a href="#example-request" id="example-request"></a>

```
{"success":true}
```
