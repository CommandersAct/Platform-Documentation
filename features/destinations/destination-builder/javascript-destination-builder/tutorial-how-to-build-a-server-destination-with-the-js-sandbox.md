---
description: Example of destination created with the J0 sandbox in the Destination Builder
---

# Tutorial -  How to build a server destination with the JS sandbox

The Destination builder allows you to create custom server-side destinations using server-side **javascript** (aka Node.js), but with an **easy and simplified** subset of Node.js : the [_**Javascript Sandbox**_](./#javascript-sandbox).

This tutorial will teach you the basics of writing your own server-side destination template and publish it in your own destination catalog(s).

{% hint style="success" %}
A server-side destination receive incoming event data from your sources, transform it, and send the data wherever you want. As long as the destination tool accepts HTTP requests, it can accept data from a server-side destination.
{% endhint %}

## Basic example: Slack

In this tutorial, you will create a destination that sends event data to Slack using a single `webhook_url` parameter. Slack is a messaging and collaboration tool that supports webhook integration. The Use cas can be : "I want to receive on a Slack channel a message each time an event "sign\_up" is received"

### Destination Configuration

To begin, create the destination template by navigating to the **Destination** section in the menu and clicking **New** in the **Destination Builder** section. Then, give your destination a name, a logo, a category and a description.

<figure><img src="../../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Now, we can go to the _Code_ tab, starting to write the code of our destination template.\


<figure><img src="../../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

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

