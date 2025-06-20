# Plugin Commanders Act Assistant

## Introduction

We are excited to introduce the latest version of our browser extension, **Commanders Act Assistant (CAA)**! Designed to streamline your testing and debugging processes, CAA is fully compatible with **Google Chrome** and **Microsoft Edge**, offering seamless integration into your workflow.

[Download it now in the Chrome Extension Store](https://chromewebstore.google.com/detail/commanders-act-assistant/lfaifjhjdolnpnlgeohohaalbeidhlpj)

\*Availability in the Microsoft Edge Store is coming soon!

## Key Features &#x20;

### Replace Web Containers easily

With CAA, you can effortlessly **switch between Web Containers versions without a container deployment.** You can test directly on your production website, allowing for quality assurance without disrupting your live environment.\
\
:heart: It's also **compatible with** [**Branches** ](../branches.md)feature! :heart:&#x20;

<figure><img src="../../../../../../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../../.gitbook/assets/Capture d&#x27;écran 2025-02-27 185120.png" alt=""><figcaption></figcaption></figure>

### How to replace your(s) Web Container(s)

You can **test directly using the dedicated buttons** visible on the steps **"Generate," "Test," and "Deploy"** within the Commanders Act platform, making it easier to validate your configurations.

{% hint style="success" %}
Plugin must be active on your browser to see these buttons
{% endhint %}

<figure><img src="../../../../../../../../.gitbook/assets/image (570).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../../.gitbook/assets/image (571).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../../.gitbook/assets/image (572).png" alt=""><figcaption></figcaption></figure>

On click, you will be invited to enter the expected landing page for your test session, then click 'OK' to be redirected to your site.

<figure><img src="../../../../../../../../.gitbook/assets/image (575).png" alt=""><figcaption></figcaption></figure>

### Stop Web Container(s) replacement&#x20;

To **turn off the override**, simply click the **button "stop override" on the plugin**.

<figure><img src="../../../../../../../../.gitbook/assets/image (1) (1) (1) (1).png" alt="" width="408"><figcaption></figcaption></figure>

### Monitor Tags in Action

Easily **view the list of triggered tags** as they fire on your website, giving you a clear overview of your tracking implementation in real time. Simply unfold the "web containers" section to see the list

<figure><img src="../../../../../../../../.gitbook/assets/image (603).png" alt="" width="416"><figcaption></figcaption></figure>

### Reach your Web Container in 1 click

Use the icon aside the Site Name - Container Name to reach in just one click your Web Container on our Platform

<figure><img src="../../../../../../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

### See the full Data Layer state on each page load

On every new page load, you can see the state of the Data Layer!

Simply unfold "External variables" or "Internal variables" to see it.

<figure><img src="../../../../../../../../.gitbook/assets/image (605).png" alt=""><figcaption></figcaption></figure>

### Events tab to watch the triggered events

Open the tab "Events" to see your tags triggered on events.\
The Data Layer state is also visible on this tab.\
If some "event variables" are fed up, you will see them as well

<figure><img src="../../../../../../../../.gitbook/assets/image (606).png" alt=""><figcaption></figcaption></figure>

Customs Events are also visibles, with the proper name of each custom event.

<figure><img src="../../../../../../../../.gitbook/assets/image (608).png" alt=""><figcaption></figcaption></figure>

### Keep a History Across Pages

CAA **records events across multiple pages**, ensuring you have a complete history of tag activations for a comprehensive debugging experience.

<figure><img src="../../../../../../../../.gitbook/assets/image (576).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Need to clear your history ? You can **clear** by stopping the **"record across pages"** option, reloading the page, and turning it on again. \
This process will be improved in an upcoming update!
{% endhint %}

### Login required

To preserve confidentiality, our plugin requires to be logged on our platform.

{% hint style="info" %}
Once you are logged, only the Sites and the Web Containers that you have access are visible through the extension
{% endhint %}

<figure><img src="../../../../../../../../.gitbook/assets/image (12).png" alt="" width="265"><figcaption></figcaption></figure>

### Limitations

While CAA is a powerful tool, here are some current limitations to keep in mind:

* 🌍 **Consistent Web Container URLs:** The Web Containers URLs must remain the same across all pages for the plugin to function correctly.\

* ⚡ **SPA Compatibility:** On **Single Page Applications (SPA)**, the list of triggered tags is only filled on the **first "custom event" hit** collected by the plugin. On each page change, the tags are added to the list\*. \
  The Data Layer is updated on each new "page load"\
  \
  \*This behavior will be improved in an upcoming update, so stay tuned!

### Future Enhancements of our extension

CAA is **continuously evolving**, with new features and improvements planned to further enhance your testing experience. Keep an eye out for future updates that will make debugging and optimization even easier!

Coming soon

* Replace containers versions directly from the drop down (in the plugin)
* Improved SPA website management (for custom events "page load")







