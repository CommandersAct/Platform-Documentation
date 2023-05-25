---
description: Strategies to improve the onsite performance of TagCommander.
---

# Performance Optimization

Onsite performance of a website is one of the most important KPIs for SEO. Therefore more and more businesses are interested in optimizing onsite performance via TagCommander. This post collects topics to make TagCommander itself more performant.

## Reduce File Size of TagCommander

### **Remove unused Data Layer Properties**

Each Data Layer property that is configured in the options in the interface creates a bit of JavaScript code in the Container to initialise the variable in case it was not present in the onsite Data Layer `tc_vars`. Removing unused/old variables will therefore make the Container file a bit smaller (and as a side effect also improve transparency of the Container setup).

### **Remove Unused Internal Variables**

Each internal variable that is configured in the options in the interface is a JavaScript snippet, so removing internal variables allows to make a Container file smaller. This can be done by removing unused internal variables and also by specifying which variables are used in which Container. This is especially important for clients with a `<head>` and `<body>` Container and clients that have multiple Containers for different websites.

### **Do Not Repeat Yourself**

Sometimes the same functionality of a Tag is duplicated in multiple Tags. In these cases it is possible to save a good amount of JavaScript code and Container file size by refactoring the common functionality into an internal variable or into a common Tag. For example many Tags exist of two parts. One part loads an external JavaScript library of the vendor and one part sends the actual event to the vendor. Per default the code that loads the JavaScript library is often duplicated in every event. So extracting the first part into a _base Tag_ allows to remove the duplicated JavaScript.

### **Split Large Container Files**

Many Tags are deployed on every page of a website even so they are not triggered. For example many vendors have separate Tags for collecting information and only one Tag that is played out on the confirmation page. Therefore it might make sense to split the Container in two parts—one for catalogue pages and one for funnel pages. Therefore both Containers have a smaller size as they only include Tags that are relevant for their part of the website.&#x20;

Also make sure to only implement Tags in `<head>` Container if necessary as those Tags usually have a greater impact on onpage performance than Tags in \`\<body>\` Container.

### **Implement Hybrid TagCommander Setup**

A hybrid setup allows to move onsite performance impact into the Server-Side TagCommander infrastructure.

## Make TagCommander asynchronous

### **Load Container Asynchronous**

Many onsite page speed crawlers measure the time until the browser event _onload_. So in case the IT team loads the TagCommander Container asynchronous on the _onload_ event it is possible to make the TagCommander file _invisible_ for some page speed metrics. This is usually only possible for `<body>` Containers as `<head>` Containers need to be executed synchronously for A/B testing and personalisation Tags that have an impact on the visual content of the website.&#x20;

{% hint style="danger" %}
Tags in asynchronous `<body>` Container that use synchronous `document.write` (e.g. some advertising solutions) will break the website in case the Container is loaded asynchronously. These Tags need to be avoided in case a Container is installed asynchronously.
{% endhint %}

### **Load Tags Asynchronous**

JavaScript is for the most part a single thread language, this means that long running JavaScript (like a long process in a loop) can block other parts of the JavaScript that should be executed right away. It is possible to put long running JavaScript on an _execute later with a lower priority stack_ by wrapping it inside of a setTimeout with a delay of 0 ms.

```javascript
setTimeout(function() {
    // My Tag Code
}, 0);
```

This needs to be tested with each individual Tag as some might not be compatible with this approach.
