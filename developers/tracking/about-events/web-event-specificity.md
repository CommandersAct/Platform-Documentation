# JS SDK event specificity  

The JS SDK send specific properties regarding the browser.

```json
{
	"event_name": "search",
	"event_id": "202110130000000000",
	"properties": {
		"search_term": "t-shirts",
        "path": "",
        "referrer": "",
        "title": "",
        "url": "",
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

# Fields

Here are fields automatically added by the js sdk.

(*) IP Address is not collected by our libraries, but instead filled in by our servers when it receives a message for **client side events only**.


| Field name          | Example value                                                                                                         | Description              |
|---------------------|-----------------------------------------------------------------------------------------------------------------------|--------------------------|
| locale              |                                                                                                                       |                          |
| properties.path     |                                                                                                                       |                          |
| properties.referrer |                                                                                                                       |                          |
| properties.title    |                                                                                                                       |                          |
| properties.url      |                                                                                                                       |                          |
| userAgent           | Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36 | The browser's user agent |
