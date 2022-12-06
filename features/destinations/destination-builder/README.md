# Destination builder

If you want to send data to a destination that is not listed in our [destination's catalog](../destinations-catalog/), you can open a destination request, or you can write your own destination.

The destination builder allows you to create your own custom destination, either with a _**no**-code_ approach (Webhook, FTP, API, GTM importer) or with a _javascript sandbox_ aproach (_**low**-code_) :

* Webhook/API/FTP destination builder (no-code experience)
* [JavaScript destination builder](javascript-destination-builder/) (JS sandbox)
* GTM template importer (convert to JS sandbox template out of the box)

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>3 ways to create a new destination</p></figcaption></figure>

## Create and publish a destination

When you publish your work in the destination builder, your destination wil be visible for your team in the destination catalog beside other destinations.

In the destination builder interface, you will be able to set:

* Information about the destination (label, logo, category)
* Destination settings, i.e. questions that will be asked to the user that will add this destination (e.g. token, account id, options ...)
* Connector technical options (url, method, etc.) or JavaScript code

![](<../../../.gitbook/assets/image (3) (2).png>)

Your destination can also be hosted on Github and automatically imported to facilitate updates on your side.

{% hint style="info" %}
The technology for destination's template javascript sandbox in the platform is, to a large extent, compatible with Google Tag manager templates. \
In most cases, templates written for GTM run in Commanders'act with no (or few) changes
{% endhint %}

{% hint style="info" %}
You can also import templates created on GTM inside your catalog in a few clics with a 100% no-code experience.
{% endhint %}
