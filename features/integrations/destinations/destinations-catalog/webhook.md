# Webhook

Webhook destination allows you to send event data to APIs that accept receiving JSON data.&#x20;

POST, PATCH, GET, DELETE, and PUT are all HTTP request methods that can be used to send data. Select or modify the data that will be sent with each request, as well as the format in which it will be sent.

In the settings step, configure first the destination URL, where you want to send data.

![](<../../../../.gitbook/assets/Capture d’écran 2022-06-30 à 14.49.50.png>)

## Request Body (JSON)

Then, you can build the request body (JSON), you can choose to send all events, all events + specific ones or only specific events.&#x20;

For specific events, you can use the key/value fields to provide data to build the JSON body. Value can be an event property name, a static value or a combination of both (ex : "Hi, \{{event\_name\}} was received with value equals \{{value\}} ").

![](<../../../../.gitbook/assets/Capture d’écran 2022-06-30 à 14.50.24.png>)

## Request Headers

You can add here headers with key/value fields.

![](<../../../../.gitbook/assets/Capture d’écran 2022-06-30 à 14.50.59.png>)

## Additional options

You can select the request method: GET, POST, PUT, PATCH, DELETE

Define the timeout in milliseconds.

Use flatten keys: if checked, all nested objects will flatten with "_" and symbol "-" changed to "_" in keys.

Do not use dot notation: by default, you can use dot notation to create a nested request object. But in case you need to create a property that contains a dot, then you can use this option for that.

![](<../../../../.gitbook/assets/Capture d’écran 2022-06-30 à 14.51.41.png>)

