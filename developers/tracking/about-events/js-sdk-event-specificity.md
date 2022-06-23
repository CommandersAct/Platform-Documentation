# Web event specificity

## Fields automatically added to event&#x20;

The [JS SDK](../javascript-sdk.md) and [Web container](../../../features/integrations/sources/sources-catalog/containers.md) add specific properties in the event regarding the browser.\
Event example :

```json
{
	"event_name": "search",
	"event_id": "202110130000000000",
	"properties": {
	    "search_term": "t-shirts",
            "url": "https://www.mywebsite.com/path1/path2/",
            "path": "/path1/path2/",
            "referrer": "https:///www.google.fr",
            "title": "My page title",
	    "user": {
			"id": "12345",
			"email": "toto@domain.fr",
			"consent_categories": ["1", "3"]
		}
	},
        "locale": "fr",
        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36",
	"event_timestamp": "1639044446636"
}
```

## Fields autmatically added

| Field name          | Example value                                                                                                           | Description               |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| locale              | fr                                                                                                                      | Browser language          |
| properties.path     | /path1/path2/                                                                                                           | Path of the current url   |
| properties.referrer | [https:///www.google.fr](https://www.google.fr)                                                                         | Referer url               |
| properties.title    | My page title                                                                                                           | Title of the current page |
| properties.url      | [https:///www.mywebsite.fr](https://www.google.fr)                                                                      | Url of the current page   |
| userAgent           | Mozilla/5.0 (Macintosh; Intel Mac OS X 10\_15\_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36 | The browser's user agent  |

{% hint style="info" %}
(\*) IP Address is not collected by our libraries, but instead filled in by our servers when it receives a message for **client side events only**.
{% endhint %}
