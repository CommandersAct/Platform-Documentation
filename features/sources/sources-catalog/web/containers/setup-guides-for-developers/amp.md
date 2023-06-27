---
description: Installation Instructions for Web container on AMP.
---

# AMP

{% hint style="info" %}
Accelerated Mobile Pages (AMP) use the Server-Side version of our TMS
{% endhint %}

## AMP Definition

AMP, which stands for Accelerated Mobile Pages, is a technology issued from the open source Digital News Initiative (DNI) between Google and European publishers. AMP is a format allowing the creation of optimized mobile content in a bid to improve user experience.

If you wish to learn more about AMPs, click the following links:

\[FR] [https://www.ampproject.org/fr/learn/about-amp/](https://www.ampproject.org/fr/learn/about-amp/)

\[EN] [https://www.ampproject.org/learn/about-amp/](https://www.ampproject.org/learn/about-amp/)

## Implementing Commanders Act on AMPs

AMP blocks synchronous JavaScript files called on your websites in order to increase mobile pages’ loading speed. For your Commanders Act container to be compatible, you need to adapt the way you set it up to be compliant with AMP’s requirements.

Below, you will find an example showing how to set up a Commanders Act container on your AMP pages. We recommend using the \<amp-analytics> tag ([https://www.ampproject.org/docs/reference/components/amp-analytics](https://www.ampproject.org/docs/reference/components/amp-analytics)) to define your data layer and the container.

**Important**: This operation calls for Commanders Act’s API and thus requires that a server-side container be setup in Commanders Act’s user interface.&#x20;

### **Setup example with analytics tag**

```
<!doctype html>
<html amp lang=”en”>
<head>
<meta charset=”utf-8″>
<title>Commanders Act – AMP Analytics</title>
<link rel=”canonical” href=”http://example.ampproject.org/article-metadata.html” />
<meta name=”viewport” content=”width=device-width,minimum-scale=1,initial-scale=1″>
<!– Mandatory execution of the AMP Analytics Script “https://cdn.ampproject.org/v0/amp-analytics-0.1.js” –> 
<script async custom-element=”amp-analytics”
src=”https://cdn.ampproject.org/v0/amp-analytics-0.1.js“></script>
<style>body {opacity: 0}</style><noscript><style>body {opacity: 1}</style></noscript>
<script async src=”https://cdn.ampproject.org/v0.js”></script>
</head>
<body
<amp-analytics id=”commandersact”>
<!– JSON data structure containing the TagCommander data layer –> 
<script type=”application/json”>
{
“vars”: {
“tC_SiteID”: “3503”,
“tC_ContainerID”: “1”,
“env_template” : “homepage”,
“env_work” : “prod”,
“env_device” : “m”,
“env_country” : “IT”,
“page_name” : “amp_homepage”,
“user_id” : “”,
“user_newcustomer” : “”,
“order_id” : “”
},
<!– Call to Commanders Act’s API (server-side) –> 
“requests”: {
“tC_BaseURL“: “//serverside${tC_SiteID}.tagcommander.com/${tC_ContainerID}/”,
<!– Page variables mentioned in the “tC_PageTrack” element –> 
“tC_PageTrack“: “${tC_BaseURL}?&env_template=${template}&env_work=${work_environment}&env_device=${device}&env_country=${country}&page_name=${page_name}&user_id=${user_id}&user_newcustomer=${newcustomer}&order_id=${order_id}”,
<!– Event variables mentioned in the “tC_EventTrack” element. Note: “scroll” and other such variables are natively proposed in AMP pages–> 
“tC_EventTrack“: “${tC_PageTrack}&scrollY=${scrollTop}&scrollX=${scrollLeft}&height=${availableScreenHeight}&width=${availableScreenWidth}&scrollBoundV=${verticalScrollBoundary}&scrollBoundH=${horizontalScrollBoundary}${eventLabel}”
},
<!– Additional parameters mentioned in the “extraUrlParams” element. Note: the clientId function creates a unique ID per visitor (different from the regular TCIDs)–> 
“extraUrlParams”: {
“TCID_AMP”: “${clientId(TCID_AMP)}”,
“path”: “${ampdocUrl}”,
“type”: “${type|default:page}”,
“platform”: “AMP”,
“r”: “${random}”
},
<!– Execution of Commanders Act hits on the “triggers” element. “Pageview” sends the hit to the page viewed, the “clickPings” trigger sends the hit to an event defined in the “selector” –>
“triggers”: {
“pageview”: {
“on”: “visible”,
“request”: “tC_PageTrack”,
“vars”: {
“type”: “page”
}
},
“clickPings”: {
“on”: “click”,
“selector”: “.tC_events”,
“request”: “tC_EventTrack”,
“vars”: {
“type”: “event”
}
}
}
}
</script>
</amp-analytics>
<h1 id=”header”>AMP Page</h1>
<!– data-vars-event-label2 allows to collect additional variables, such as event variables –>
<span id=”event-test” class=”tC_events” data-vars-event-label2=”22″>
Click here to generate an event
</span>
</body>
```

AMPs also allow you to set up your tag management tool through an iframe. Please note that if the iframe has not loaded within 5 seconds, it will not be called. You will find below an a setup example through an iframe:

**Setup example with iframe**

```
<!doctype html>
<html amp lang=”en”>
<head>
<meta charset=”utf-8″>
<title>Commanders ACT – Serverside – AMP Analytics</title>
<link rel=”canonical” href=”http://example.ampproject.org/article-metadata.html” />
<meta name=”viewport” content=”width=device-width,minimum-scale=1,initial-scale=1″>
<!– Mandatory execution of the AMP iframe script “https://cdn.ampproject.org/v0/amp-iframe-0.1.js ” –>
<script async custom-element=”amp-iframe” src=”https://cdn.ampproject.org/v0/amp-iframe-0.1.js”></script>
<style>body {opacity: 0}</style><noscript><style>body {opacity: 1}</style></noscript>
<script async src=”https://cdn.ampproject.org/v0.js”></script>
</head>
<body>
<!– Call to the TagCommander iframe “https://academy.commandersact.com/AMP/iframe.php” containing the data layer variables. Note: the iframe must belong to a different domain from that of the website (except if the allow-same-origin parameter is added) and be https –>
<amp-iframe width=1 height=1 src=”https://academy.commandersact.com/AMP/iframe.php? env_template=homepage&env_work=prod&env_device=m&env_country=IT&page_name=amp_homepage&user_id=&user_newcustomer=&order_id=” sandbox=”allow-scripts allow-same-origin” layout=”fixed” frameborder=”0″>
<!– Adding content to the iframe is mandatory (a pixel in this case)–>
<amp-img src=”https://academy.commandersact.com/AMP/pixel.gif” height=1 width=1 layout=”fill” placeholder></amp-img>25
</amp-iframe>
<h1 id=”header”>AMP Page</h1>
<span id=”event-test” class=”tC_events” data-vars-event-label2=”22″>
Click here to generate an event
</span>
</body>
</html>
```
