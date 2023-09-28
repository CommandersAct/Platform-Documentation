---
description: Get data from the consent dashboard (aggregated data)
---

# Get statistics

{% swagger baseUrl="https://api-internal.commander1.com" path="/v2/{siteId}/privacy/statistics" method="get" summary="Get Statistics" %}
{% swagger-description %}
This endpoint allows you to get the data from the consent dashboard on a specific date range
{% endswagger-description %}

{% swagger-parameter in="path" name="{siteId}" type="string" %}
Account ID\
example: '12345'
{% endswagger-parameter %}

{% swagger-parameter in="query" name="filter[sup_filters][location][]" type="integer" %}
Data inside and outside of the EU\
0 : Out of EU\
1 : EU
{% endswagger-parameter %}

{% swagger-parameter in="query" name="filter[sup_filters][device][]" type="integer" %}
Typical device types\
0 : others\
1 : mobile\
2 : tablet\
3 : desktop
{% endswagger-parameter %}

{% swagger-parameter in="query" name="token" type="string" %}
Authentication token. Optional if the header "Authorization' parameter is used instead.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="filter[begin_date]" type="string" %}
example: '2021-04-30'
{% endswagger-parameter %}

{% swagger-parameter in="query" name="filter[end_date]" type="string" %}
example: '2021-04-31'
{% endswagger-parameter %}

{% swagger-response status="200" description="Data successfully retrieved." %}
```
{
    "data": [
        {
            "type": "privacy/statistic",
            "id": "1",
            "attributes": {
                "nb_banner_views": 198,
                "nb_banner_clicks_button": 32,
                "nb_optin": 34,
                "nb_optin_all": 33,
                "nb_optin_all_on_click_banner": 23,
                "nb_banner_clicks_links_not_PC": 1,
                "nb_PC_views": 1,
                "nb_optin_all_on_browsing": 10,
                "optin_rate": 0.1717171717171717,
                "optout_rate": 0,
                "nb_optin_category_1": 35,
                "optin_rate_category_1": 0.17676767676767677,
                "nb_optin_category_2": 35,
                "optin_rate_category_2": 0.17676767676767677,
                "nb_optin_category_3": 35,
                "optin_rate_category_3": 0.17676767676767677,
                "nb_optin_category_4": 35,
                "optin_rate_category_4": 0.17676767676767677,
                "nb_optin_category_5": 14,
                "optin_rate_category_5": 0.0707070707070707,
                "nb_optin_category_10001": 7,
                "optin_rate_category_10001": 0.03535353535353535,
                "nb_optin_category_10003": 7,
                "optin_rate_category_10003": 0.03535353535353535,
                "nb_optin_category_10005": 7,
                "optin_rate_category_10005": 0.03535353535353535,
                "nb_optin_category_10007": 7,
                "optin_rate_category_10007": 0.03535353535353535,
                "nb_optin_category_10009": 7,
                "optin_rate_category_10009": 0.03535353535353535,
                "nb_optin_category_10011": 7,
                "optin_rate_category_10011": 0.03535353535353535,
                "nb_optin_category_10013": 7,
                "optin_rate_category_10013": 0.03535353535353535,
                "nb_optin_category_10015": 7,
                "optin_rate_category_10015": 0.03535353535353535,
                "nb_optin_category_10017": 7,
                "optin_rate_category_10017": 0.03535353535353535,
                "nb_optin_category_10019": 7,
                "optin_rate_category_10019": 0.03535353535353535,
                "nb_optin_category_13001": 7,
                "optin_rate_category_13001": 0.03535353535353535,
                "nb_optin_category_13003": 7,
                "optin_rate_category_13003": 0.03535353535353535
            }
        },
        {
            "type": "privacy/statistic",
            "id": "20",
            "attributes": {
                "nb_PC_views": 1,
                "optin_rate": 0,
                "optout_rate": 0
            }
        }
    ]
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Invalid token" %}
```
{
    "errors": [
        {
            "status": 401,
            "title": "Unauthenticated.",
            "detail": "The access token provided is expired, revoked, malformed, or invalid.",
            "context": []
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Example Request" %}
```bash
https://api-internal.commander1.com/v2/siteId/privacy/statistics?token=XXXXXX&filter%5Bbegin_date%5D=YYYY-MM-DD&filter%5Bend_date%5D=YYYY-MM-DD&filter%5Bsup_filters%5D%5Bdevice%5D%5B%5D=1&filter%5Bsup_filters%5D%5Blocation%5D%5B%5D=0&filter%5Bsup_filters%5D%5Blocation%5D%5B%5D=1
```


{% endtab %}
{% endtabs %}

## How to get the token

For each API, you'll have to ask a token to your account manager or support team.



## How to use additional parameters

**Device filters**\
`&filter[sup_filters][device][]=2&filter[sup_filters][device][]=3&filter[sup_filters][device][]=0` \
1 = Mobile \
2 = Tablet \
3 = Desktop \
0 = Others \
(in the example above, mobile device is excluded)\
&#x20;\
**Location filters**\
`&filter[sup_filters][location][]=0` \
1 = EU \
0 = Out of EU\
(in the example above, EU user's location is excluded)

## Result example

```json
{
    "data": [{
        "type": "privacy\/statistic",
        "id": "2",
        "attributes": {
            "nb_visitors_exposed_to_privacy": 11448,
            "nb_banner_views": 11445,
            "nb_banner_clicks_button": 10478,
            "nb_PC_views": 1863,
            "nb_PC_vendor_views": 100,
            "nb_PC_clicks_save": 1089,
            "nb_optin_PC_save": 373,
            "nb_optin": 8724,
            "nb_explicit_optin": 8776,
            "nb_optout": 2769,
            "nb_optout_on_click_banner": 2075,
            "optin_rate": 0.7620545073375262,
            "optout_rate": 0.2418763102725367,
            "nb_optin_category_1": 8718,
            "optin_rate_category_1": 0.7615303983228512,
            "nb_optin_category_3": 8708,
            "optin_rate_category_3": 0.7606568832983928,
            "nb_optin_category_5": 8708,
            "optin_rate_category_5": 0.7606568832983928
           
        }
    }, {
        "type": "privacy\/statistic",
        "id": "4",
        "attributes": {
            "nb_visitors_exposed_to_privacy": 17623,
            "nb_banner_views": 17618,
            "nb_banner_clicks_button": 15029,
            "nb_PC_views": 2377,
            "nb_PC_vendor_views": 465,
            "nb_PC_clicks_save": 1917,
            "nb_optin_PC_save": 713,
            "nb_optin": 13280,
            "nb_explicit_optin": 13460,
            "nb_optout": 3484,
            "nb_optout_on_click_banner": 2282,
            "optin_rate": 0.7535606877376156,
            "optout_rate": 0.19769619247574194,
            "nb_optin_category_1": 13331,
            "optin_rate_category_1": 0.7564546331498609,
            "nb_optin_category_3": 13318,
            "optin_rate_category_3": 0.7557169607898768,
            "nb_optin_category_5": 13302,
            "optin_rate_category_5": 0.7548090563468195,
            "nb_optin_category_7": 13303,
            "optin_rate_category_7": 0.7548658003745106,
            "nb_optin_category_9": 13308,
            "optin_rate_category_9": 0.755149520512966
        }
    }]
}
```
