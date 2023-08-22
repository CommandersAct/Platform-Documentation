# APIs

## GET Tags List

Returns the tags list

#### Call URL <a href="#resource-url" id="resource-url"></a>

GET api.commander1.com/api/1.0/manage/container/tags/list?**id\_site**=X&**access\_token**=Y&**id\_container**=Z

#### Call parameters <a href="#resource-information" id="resource-information"></a>

<table data-header-hidden><thead><tr><th>URL PARAMETER</th><th width="151">TYPE</th><th width="163">MANDATORY</th><th>DESCRIPTION</th></tr></thead><tbody><tr><td>URL PARAMETER</td><td>TYPE</td><td>MANDATORY</td><td>DESCRIPTION</td></tr><tr><td>id_site</td><td>Integer</td><td>Yes</td><td>Client site identifier</td></tr><tr><td>access_token</td><td>Alphanum</td><td> Yes</td><td>Caller’s security identifier</td></tr><tr><td>id_container</td><td>Integer</td><td> No</td><td>Container identifier</td></tr></tbody></table>

#### Return code: <a href="#example-request" id="example-request"></a>

| HTTP CODE | MESSAGE               | DESCRIPTION                                                         |
| --------- | --------------------- | ------------------------------------------------------------------- |
| 200       | OK                    | The request went through, the result is in the answer’s body        |
| 400       | Bad Request           | The parameters are not ok or mandatory parameters are missing       |
| 401       | Unauthorized          | The security token does not match the site\_id or the container\_id |
| 404       | Not Found             | A container identifier for the site\_id parameter was not found     |
| 500       | Internal Server Error | Internal server error                                               |

#### Response format : <a href="#example-request" id="example-request"></a>

The response is in JSON format.

<table data-header-hidden><thead><tr><th width="213">FIELD</th><th width="150">TYPE</th><th width="187">ALWAYS PRESENT ?</th><th>DESCRIPTION</th></tr></thead><tbody><tr><td>FIELD</td><td>TYPE</td><td>ALWAYS PRESENT ?</td><td>DESCRIPTION</td></tr><tr><td>idSite</td><td>Integer</td><td>Yes</td><td>Site identifier</td></tr><tr><td>containers</td><td>Array</td><td>Yes</td><td>Array containing the container list and their label</td></tr><tr><td>containers/id</td><td>Integer</td><td>Yes</td><td>Container identifier</td></tr><tr><td>containers/label</td><td>String</td><td>Yes</td><td>Container label</td></tr><tr><td>containers/is_active</td><td>Boolean</td><td>Yes</td><td>Container status (active=true, deleted=false)</td></tr><tr><td>tags</td><td>Array</td><td>Yes</td><td>Array containing the tag list and container label</td></tr><tr><td>tags/id</td><td>Integer</td><td>No</td><td>Tag identifier</td></tr><tr><td>tags/label</td><td>String</td><td>No</td><td>Tag label</td></tr></tbody></table>

`GET`

#### Response example <a href="#example-result" id="example-result"></a>

```
{  
    "idSite":26,
    "containers":[  
        {  
            "id":1,
            "label":"Container1",
            "is_active": true,
            "tags":[  
                {  
                    "id":1,
                    "label":"Click&Site Tracking"
                },
                {  
                    "id":3,
                    "label":"commanders act"
                }
            ]
        }
    ]
```

## Get Users

Get platform users.

{% swagger baseUrl="https://api.commander1.com" path="/v2/{siteId}/users" method="get" summary="Users" %}
{% swagger-description %}
Two usages :

\


GET 

**/users/**

 : Returns a list of user properties (depending on the parameters requested) linked to the users of a site.

\


GET 

**/users/123**

 : Return properties of one user (id 

**123**

) on one site.

\




\


Click below to download complete API documentation
{% endswagger-description %}

{% swagger-parameter in="query" name="id" type="integer" %}
The user id
{% endswagger-parameter %}

{% swagger-parameter in="query" name="include" type="string" %}
`permissions`

 or 

`roles`

 or both separated by a comma
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}
