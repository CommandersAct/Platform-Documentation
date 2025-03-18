---
description: Data Layer strategies for common setups.
---

# Common Trigger Strategies

Following you will find common Commanders Act Trigger setups.

## Page View Trigger

In most cases page view events are covered by the inbuilt _Container loaded_ and _DOM ready_ Trigger within Commanders Act. Therefore it is only necessary to setup the Data Layer and the Container to execute Tags on page views. In case of JavaScript driven webpages it is sometimes necessary to further track "virtual page views", e.g. in case the process steps of a sales funnel (log-in, enter shipping details, enter payment details, confirm order, order success) are implemented via JavaScript functionally and not via individual pages with distinct URLs.

In this case it is common to track the initial page view with the _Container loaded_ or _DOM ready_ Trigger and subsequent virtual page views via a custom Trigger. For this scenario it would be necessary to follow these steps on each subsequent virtual page view.

#### **1. Update `tc_vars` Data Layer**

The Data Layer should be updated with the new metadata of the subsequent virtual page view.

```javascript
window.tc_vars = {
    env_template: "homepage",
    env_work: "prod",
    page_name: "Homepage",
    page_keywords: ["homepage", "home", "entrypage", "index"],
    product_name: "",
    (…)
};
```

**2. Reload the Container**

Some internal functionality of the Container (e.g. Internal Variables) are only calculated when the Container was initially loaded. To reload these with the updated Data Layer it is necessary to reload the Container via a JavaScript function.

```javascript
tC.container.reload();
```

**3. Execute Triggers**

After these steps it is then necessary to signal a custom Trigger to execute the related Tags.

```javascript
cact('emit', 'page_view', {});
```

To use event attributes, you can specify the event or the element as first argument.

```html
<a href="/home" onclick="cact('emit', 'pageview', { from: this, some_data: 'some_value' })">Home</a>
```

_**Old Method**_

```javascript
tC.event.pageview({}, {});
```

To use event attributes, you need to specify the event or the element as argument. `event` is a special variable that is always available inside of `onclick` and `on*` attributes.

```html
<a href="/home" onclick="tC.event.pageview(event, {}))">Home</a>
```

{% hint style="info" %}
Steps 2. and 3. are often used in conjunction therefore it is possible to combine them in one call. e.g. `tC.container.reload({ events: { pageview: [{}, {}] } });`
{% endhint %}

## Click Trigger

Click Trigger implementation depends on the scenario. e.g. _Is the user navigated to another site when he clicks an element?_ and _Does the following page open in a new tab?_.

Following you will find a list of common scenarios for click Trigger.

### Scenarios

#### Click Navigates to an Internal Page

Links or interactions that navigate the user to another internal page are difficult to track. The reason for this is that Tags usually need more time to execute than the browser needs to navigate to the next page. This might accidentally cancel Tags execution and therefore its related tracking capabilities.

To successfully track these kind of scenarios it is important to align with the Tag vendor for a solutions. Typical solutions are:

* The Tag delays page navigation until the Tag finishes execution
* The Tag uses the Beacon Browser API, which sends tracking calls in the background

These options typically require configuration of the event Tag code.

#### Click Navigates to an External Page

External links are best opened in another browser tab by using the `target="_blank"` option on anchor links. This allows Tags to finish their work on the old tab, while users can already navigate the new external page in a new tab.

In case external links can not be opened in a new tab this scenario should follow the same advice than the prior scenario.

#### Click Does Not Navigate to Another Page

Some click events do not redirect to a new page. Typical examples are video transport controls or interactions with image carousels.

These click events can usually be tracked with less rissk due to Tags having enough time to execute on the same page.

### Setup

#### With Commanders Act Interface

Commanders Act users can setup common click Triggers with minimal effort via the Web Containers interface by selecting them with a CSS selector path.

This Trigger works in many scenarios but has two downsides:

1. Using a generic CSS selector path to setup a Trigger is unstable and can break on future releases of the website code when the CSS is updated.
2. Commanders Act can only identify elements that are loaded synchronously on the website. Elements that are loaded asynchronously cannot be watched by the predefined Commanders Act Trigger.

Good scenarios for setting up Commanders ActTriggers with the Interface are:

1. Onsite campaign that has to be measured for a short time period (couple of weeks)
2. General click tracking until the web development team can implement a custom Trigger.

#### With Custom Trigger

Technical personnel can implement custom Triggers to track clicks on a website. This approach is more stable compared to setting up a click Trigger with the interface, but usually requires some time until the web development team can implement them. Therefore it is recommended to implement intermediary Triggers with the interface until they are implemented in the site.

Custom Triggers should not be implemented for short term campaigns, but should be favoured for business critical functionalities like _Add to basket_ or _Successful Registration_.

A common way to setup click Trigger is done by setting up `data-attributes` on all elements where clicks should be tracked. These attributes could then be filled by the website CMS with values, so e.g. the marketing team can setup a "Click Trigger" for a new Teaser on their own. In HTML this might look like this:

```markup
<a href="..." class="btn btn--cta" data-tracking-action="click" data-tracking-label="My CTA" data-tracking-value="campaign-1234">Buy now!</a>
```

Inside of Commanders Act Platform it is then possible to catch clicks on these elements to execute a custom Trigger. With jQuery this might look like this:

```javascript
(function(){

    if (!$) {
        console.log("Commanders Act | Error | jQuery not available in Commanders Act Click Trigger!");
        return;
    }

    var eventActionSelector = '[data-tracking-action="click"]';
    var eventLabelAttribute = 'data-tracking-label';
    var eventValueAttribute = 'data-tracking-value';

    var eventHandler = function(event) {

        var eventData = {};
        eventData.event_action = "click";
        eventData.event_label = $(this).attr("data-tracking-label");
        eventData.event_value = $(this).attr("data-tracking-value");

      	if (tC.event && typeof tC.event[triggerName] === "function"){
            // old method
            // tC.event["my_click_trigger"](event, eventData);

            eventData.from = event; // necessary to use event attributes inside the tag
            cact('emit', 'my_click_trigger', eventData);
      	}

    }

    // Setup event handler on body via event delegation to include asynchronous elements
    $("body").on("click", eventElementSelector, eventHandler);

}());
```

{% hint style="info" %}
This approach results in a nice separation of concerns between website code and Commanders Act. The website is responsible to provide tracking data and mark which elements should be trackable. Commanders Act is responsible in bootstrapping the click tracking code and executing the related Tags.
{% endhint %}
