---
description: Example of destination created with the J0 sandbox in the Destination Builder
---

# Tutorial - How to build a server destination with the JS sandbox

The Destination builder allows you to create custom server-side destinations using server-side **javascript** (aka Node.js), but with an **easy and simplified** subset of Node.js : the [_**Javascript Sandbox**_](./#javascript-sandbox).

This tutorial will teach you the basics of writing your own server-side destination template and publish it in your own destination catalog(s).

{% hint style="success" %}
A server-side destination receive incoming event data from your sources, transform it, and send the data wherever you want. As long as the destination tool accepts HTTP requests, it can accept data from a server-side destination.
{% endhint %}

## Basic example: Slack

In this tutorial, you will create a destination that sends event data to Slack using a single `webhook_url` parameter. Slack is a messaging and collaboration tool that supports webhook integration. The Use cas can be : "I want to receive on a Slack channel a message each time an event "sign\_up" is received"

### Destination Configuration

To begin, create the destination template by navigating to the **Destination** section in the menu and clicking **New** in the **Destination Builder** section. Then, give your destination a name, a logo, a category and a description.

<figure><img src="../../../../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption></figcaption></figure>

Then, go to the **Fields** section of the editor to add settings options for your destination. You have three options for building your destination:

1. **Total Configuration**: Create a configuration field for every parameter, allowing the user to set everything explicitly.
2. **No Configuration**: Do not include any options for configuring the destination. Instead, all data is taken directly from the event.
3. **Some Configuration**: Include fields for some parameters but not others.

While having a field for every parameter is flexible, it can result in a lot of duplicated work for the user. Therefore, it is best to have the code handle the configuration of unambiguous and universal data. \
For example, if you are building an analytics destination, you don't want to ask to the user to enter the URL of the analytics API every time he will setup this destination. You will prefer to hardcode the URL inside your code without to ask user to enter it.\
\
On the other hand, if you build your destination to get the data only from the event, without adding any field in the settings for the user, the user will not be able to personnalize the destination.\
For example, if the destination required a token, this token may vary according to the context (prod, dev, country...), so if you hardcode one token in the code...\
Or, perhaps the assumptions made by the destination regarding the structure of the incoming event data do not align with the actual reality for custom events/properties. In both scenarios, the user is unable to proceed.

In conclusion, some data should always be extracted from the event while other data needs to be configured by the user. It is up to you to decide so that the end result is user-friendly.

In the case of our Slack destination, we will want to add one field so that the user can copy/paste its Slack's webhook url. We choose a text input like this:

<figure><img src="../../../../.gitbook/assets/image (10) (3).png" alt=""><figcaption></figcaption></figure>

Now, we can go to the _Code_ tab, starting to write the code of our destination template.\


<figure><img src="../../../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

### How to get the data in your code ?

You may want to get 2 types of data :&#x20;

1. user-entered data (fields filled in the settings tab)
2. event data (some properties of your event that you want to send to the partner)

#### 1. User-entered data

All data filled in the differents fields by the user are accessible in the `data` object in your code.\
In your example, we have only one field named "url", and the value that the end-user will enter will be accessible via `data.url`

#### 2. Event data

You will want to get some properties of your events to send them to the partner server. You can use one of this 2 functions to get your event data :&#x20;

* [getAllEventData() ](serverside-js-helpers.md#getalleventdata-2)=> will return an object will all the event properties
* [getEventData(myProperty)](serverside-js-helpers.md#geteventdata) =>will return the value of a specific property in your event

### Destination implementation

After setting up the destination configuration, you can proceed to implement its behavior in the JavaScript Sandbox.

The Slack example requires the following four steps:

1. Obtain the webhook URL from the destination's settings.
2. Create the message that will be sent to the Slack API.
3. Send a request to the Slack collection server to transmit the data.
4. Test your code, to make sure that the destination will behave appropriately in production.

It's important to note that the code should not perform certain actions, as they are the responsibility of the filter tab. Specifically, the code should not:

* Manage the consent to determine wether the event should be send or not.\
  It is the responsability of the consent category dropdown in the Filter tab. It is important not to override this feature, to not break the Data Governance reports
* Analyze the event properties to determine whether it should be executed. \
  Don't forget that the user will be able to choose in the _Filter tab_ wich event will be sent to the destination. You may want to restrict your code to some event's type, but you should not remove the user's ability to filter his events on certain properties (ex : the user may want to send only events with property "country" equals to "UK")
* Return an global error (`data.onFailure()`) when some event's type does not fit the destination. Prefer to use silent error with `data.onFailure({ status: 'filtered'})`

If you create a destination template that performs any of these actions, it can cause confusion for users of your destination. For instance, a destination that sends errors to Event Delivery whenever unsupported events are detected can lead to unnecessary warnings in Health reports. This would violate users' expectations regarding the expected behavior of the destination.

With this in mind, here is an annotated example of the tag implementation in JavaScript sandbox:

```javascript
const sendHttpRequest = require('sendHttpRequest');
const getAllEventData = require('getAllEventData');

//We get the event data (all event's properties)
const eventModel = getAllEventData();

if (eventModel.event_name == 'sign_up') {
    //get the url from what the user wrote in the webhook url field
    //Settings data comes into the sandboxed code as a predefined 
    //variable called 'data'.
    const url = data.url; 
    //Construct the body message, concatening the user name inside the sentence to send
    const postBody = '{"text": "' + eventModel.user.firstname + ' ' + eventModel.user.lastname + 'just signed up!"}';

    // Send the data to the Slack server
    //The sendHttpRequest function takes a URL,a result callback, optionally a header, a method and a body.
    sendHttpRequest(url, (statusCode, headers, body) => {
        if (statusCode >= 200 && statusCode < 300) {
            //send a success information to the Event Delivery report
            data.onSuccess();
        } else {
           //send an error to the Event Delivery report
            data.onFailure();
        }
    }, { headers: { 'Content-Type': 'application/json' }, method: 'POST', timeout: 1000 }, postBody);
}
else {
    //silent failure that will not send an error in the Event Delivery report
    data.onFailure({ status: 'filtered', detail: 'unsupported_event' });
}
```
