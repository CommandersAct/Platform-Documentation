# Web event specificity

## Fields automatically added to event&#x20;

The [JS SDK](../javascript-sdk.md) and [Web container](../../../features/integrations/sources/sources-catalog/containers.md) add specific properties in the event regarding the browser.\
Event playload example :

```json
{
	"event_name": "search",
	"event_id": "202110130000000000", //Automatically added
	"properties": { // event properties you set
	    "search_term": "t-shirts",
            "url": "https://www.mywebsite.com/path1/path2/",
            "path": "/path1/path2/",
            "referrer": "https:///www.google.fr",
            "title": "My page title",
	    "user": {
			"id": "12345",
			"email": "toto@domain.fr",
			"consent_categories": ["1", "3"] //Automatically added if CA CMP
		}
	},
         "page": { //Automatically added
	    "title": "Search page",
	    "url": "https://shop.com/search?q=...", 
	    "lang": "en",
	    "referrer": "https:///www.google.fr",
            "viewport": {
				"width": 320,
				"height": 568
	 		}
	  },
	  "device": { //Automatically added
	    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.86 Safari/537.36",
	    "ip": "102.3.4.56",
	    "lang": "fr",
	    "cookie": "_fbp=123; _fbc=456; _ga=789", 
	    "timezone": "Europe/Paris"
	 },
	"event_timestamp": "1639044446636", //Automatically added
	"generatorVersion": "10.0", //Automatically added
	"containerVersion": "3.1" //Automatically added
}
```

## Fields automatically added

| Field name          | Example value                                                                                                           | Description                                    |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| device.user\_agent  | Mozilla/5.0 (Macintosh; Intel Mac OS X 10\_15\_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36 | The browser's user agent                       |
| device.lang         | fr                                                                                                                      | Browser language                               |
| properties.path     | /path1/path2/                                                                                                           | Path of the current url (only on page\_view)   |
| properties.referrer | [https:///www.google.fr](https://www.google.fr)                                                                         | Referer url (only on page\_view)               |
| properties.title    | My page title                                                                                                           | Title of the current page (only on page\_view) |
| properties.url      | [https:///www.mywebsite.fr](https://www.google.fr)                                                                      | Url of the current page                        |
| page.\*             |                                                                                                                         | pages information                              |

{% hint style="info" %}
(\*) IP Address is not collected by our libraries, but instead filled in by our servers when it receives a message for **client side events only**.
{% endhint %}
