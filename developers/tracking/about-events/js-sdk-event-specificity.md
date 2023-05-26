# Web event specificity

## Fields automatically added to event&#x20;

The [JS SDK](../../../features/sources/sources-catalog/web/js-sdk/), [Web container](../../../features/sources/sources-catalog/web/containers/) and [GTM bridge](../../../features/sources/sources-catalog/web/gtm.md) add autmatically specific properties in the event regarding the browser.\
Here is a complete event payload example :

```json
{
   "event_name": "search",
   "search_term": "t-shirts",
   "url": "https://www.mywebsite.com/path1/path2/", //Automatically added if missing
   "path": "/path1/path2/", //Automatically added
   "referrer": "https:///www.google.fr", //Automatically added
   "title": "My page title", //Automatically added if missing
   "user": {
      "id": "12345",
      "email": "toto@domain.fr",
      "consent_categories": ["1","3"] //Automatically added if you use Commanders Act CMP
   },
   "context": {
      "event_id": "202110130000000000", //Automatically added
      "generatorVersion": "10.0", //Automatically added
      "containerVersion": "3.1", //Automatically added
      "event_timestamp": "1639044446636", //Automatically added
      "page": { //Automatically added
         "title": "Search page", //Automatically added
         "url": "https://shop.com/search?q=...", //Automatically added
         "lang": "en", //Automatically added
         "referrer": "https:///www.google.fr", //Automatically added
         "viewport": { //Automatically added
            "width": 320, //Automatically added
            "height": 568 //Automatically added
         }
      },
      "device": { //Automatically added
         "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.86 Safari/537.36",//Automatically added
         "ip": "102.3.4.56",//Automatically copied from the request header
         "lang": "fr",//Automatically added
         "cookie": "_fbp=123; _fbc=456; _ga=789",//Automatically added
         "timezone": "Europe/Paris"//Automatically added
      }
   }
}
```

## Fields automatically added

| Field name                 | Example value                                                                                                           | Description                                    |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| context.event\_id          | <pre><code>202110130000000000
</code></pre>                                                                             | Id of the event                                |
| context.event\_timestamp   | <pre><code>1639044446636
</code></pre>                                                                                  | Timestamp of the event sending time.           |
| context.device.user\_agent | Mozilla/5.0 (Macintosh; Intel Mac OS X 10\_15\_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.0.0 Safari/537.36 | The browser's user agent                       |
| context.device.lang        | fr                                                                                                                      | Browser language                               |
| path                       | /path1/path2/                                                                                                           | Path of the current url (only on page\_view)   |
| referrer                   | [https:///www.google.fr](https://www.google.fr)                                                                         | Referer url (only on page\_view)               |
| title                      | My page title                                                                                                           | Title of the current page (only on page\_view) |
| url                        | [https:///www.mywebsite.fr](https://www.google.fr)                                                                      | Url of the current page                        |
| page.\*                    |                                                                                                                         | pages information                              |

{% hint style="info" %}
IP Address is not collected by our libraries, but instead filled in by our servers when it receives a message for **client side events only**. Copying it from the request header containing the IP Address.
{% endhint %}
