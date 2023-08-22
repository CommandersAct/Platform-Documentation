# TagPerformance

A Website’s performance is key to **SEO** and **user experience**; however, the increasing amount of tags used on websites nowadays has an impact on loading times.

In this context, tags’ **performance** has become a **strategic** matter.

Commanders Act's “**TagPerformance**” module offers the possibility to measure your site’s performance based on the tags that are placed on it. It acts as a complementary tool to those used by IT departments to measure loading times of websites’ key elements (images, CSS …)

TagPerformance’s main features include:

* A measuring tag executed on the end client’s browser and not by a robot.
* Analysis of the START RENDER, DOM READY and DOM LOADED events to measure performance.
* The possibility to visualize significant variations in tags and page types, free from the noise resulting from the analysis of micro-variations.
* Information on loading times of partner solutions in relation with the average loading times of other solutions to ensure loading times are correct.
* Data segmentation to identify sources of problems, if any, or to focus on a particular segment: container, page type (product, home page), device (mobile, tablet, PC), OS and browser.

TagPerformance is one of the additional modules for the **Commanders Act** product: if you wish to use it on your website(s), please contact your account manager or reach out to our Support Department (support@commandersact.com)

## Metrics

TagPerformance allows you to analyze three events:

* **START RENDER or FIRST PAINT**: This is when the first element is displayed on the page.

This metric is key to bounce rates (if initial visual elements take too long to load, users will most often leave a site) and SEO (“dwell time” metric).

* **DOM READY**: this is when a page’s structure is loaded and analyzed by the browser.
* **PAGE LOADING TIME or ONLOAD or DOM LOADED**: this is when the page’s content has finished loading. This metric is useful for SEO.

Loading order of a web page’s elements:

<figure><img src="../../../../../../../.gitbook/assets/image (316).png" alt=""><figcaption></figcaption></figure>

Example:

Page A and page B take both 12ms to load; DOM loaded is the same for both of them. However, Start Render and DOM Ready events are optimized for page A but not for page B.

<figure><img src="../../../../../../../.gitbook/assets/image (317).png" alt=""><figcaption></figcaption></figure>

## How it works ?

* The page **loads** with the Commanders Act container.
* The Commanders Act container calls the tags placed on the page and loads the “**Commanders Act – TagPerformance**” tag two seconds after the **DOM** **Loaded** event.
* The “Commanders Act – TagPerformance” tag captures information provided by the browser thanks to the **Navigation Timing API**, which is compatible with 88% of existing browsers. The information that is captured includes:
* Generic information about the page: Start Render, DOM Ready and DOM Loaded
* Information about every tag that is executed on the page: hits’ aggregated loading time before **Start Render, DOM Ready** and **DOM Loaded** happen (separately).

Example:

This is the structure of a page from a website:

<figure><img src="../../../../../../../.gitbook/assets/image (318).png" alt=""><figcaption></figcaption></figure>

**“Tag 1” sends 4 hits:**

* One that loads before the Start Render event (300ms)
* One that loads before the DOM Ready event at (400ms)
* One that starts loading before DOM Ready and finishes loading during the DOM Loaded event (600ms)
* One that loads after the DOM Loaded event (100ms)

“**Tag” 2 sends 2 hits:**

* One that loads during the Start Render event (700ms)
* One that loads before the DOM Loaded event (200ms)

**With the “TagPerformance” tag, Commanders Act will count the following loading times for tag 1:**

* Hits’ aggregated loading time before the Start Render event (300ms).
* Hits’ aggregated loading time before the DOM Ready event: 1300ms (the first and second hit’s respective loading times of 300ms and 400ms are stored and added to the 600ms loading time of hit three, which is sent during the DOM Ready event).
* Hits’ aggregated time before the DOM Loaded event: 1300ms (all hits’ loading times are stored: 300ms, 600ms and 600ms for hits one, two and three, respectively).
* Total loading time of tag1 (1400ms)

**The “TagPerformance” tag will count the following loading times for tag 2:**

* Hits’ aggregated loading time before the Start Render event (700ms)
* Hits’ aggregated loading time before the DOM Ready event (700ms)
* Hit’s aggregated loading time before the DOM Loaded event (900ms)
* Total loading time of tag1 (900ms)

**It will also count generic loading times on the page:**

* Start Render (700 ms)
* DOM Ready (2000 ms)
* DOM Loaded (2800 ms)

All this data will populate TagPerformance’s reports.
