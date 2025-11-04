# Report analysis

In order to be able to visualize TagPerformance reports, you have to request the activation of this module, not included in the basic Commanders Act offer. If you are interested in using TagPerformance, please get in touch with your account manager or our Support Department ([support@commandersact.com](mailto:support@tagcommander.com)).

To access the reports,

* Log in to the **Commanders Act** Interface and click the Health > Website Monitoring > TagPerformance menu

<figure><img src="../../../../../../../.gitbook/assets/image (322).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../.gitbook/assets/image (323).png" alt=""><figcaption></figcaption></figure>

## Dashboard

The “Dashboard” report provides an overview of tags’ performance on your site:

You will find below a detailed explanation of the report’s analysis windows.

**1)-The three** main indicators **(Start Render, DOM Ready, DOM Loaded):**

<figure><img src="../../../../../../../.gitbook/assets/image (324).png" alt=""><figcaption></figcaption></figure>

* **Average Start Render (First Paint)**: average loading time on site of the Start Render event.
* **Average DOM Ready**: average loading time on site of the DOM Ready event.
* **Average Page loading time (on load)**: average loading time on site of the DOM Loaded event.

Note: These three metrics consider the following filters “page type”, “container”, “device”, “OS” or “browser”.

Example: These three pages are loaded on your site:

<figure><img src="../../../../../../../.gitbook/assets/image (325).png" alt=""><figcaption></figcaption></figure>

The three metrics would take the following values:

* “**Average Start Render (First Paint)**”: **5 sec** (700ms, 500ms and 300ms on average)
* “**Average DOM Ready**”: **8** **sec** (2000ms, 2200ms and 1100ms on average)
* “**Average Page loading time (on load)**”: **6** **sec** (2800ms, 2800ms and 2100ms on average)

**2)-The Pie Chart:**

<figure><img src="../../../../../../../.gitbook/assets/image (326) (1).png" alt=""><figcaption></figcaption></figure>

The pie chart highlights tags that take longer to load in terms of the selected level of analysis in the available filters: **Start Render, DOM Ready, DOM Loaded** or Cumulated loading time.

Example: the pie chart above appears once the “Tags impacting start render (First Paint)” level of analysis is selected. It shows that the “Lengow lead validation” tag is the tag that delays the most the Start Render event, because it takes about 17% of total time preceding the Start Render event.

By clicking the “Others” part, you will be able to obtain more details about the remaining tags affecting your site’s loading time.

Note: the pie chart that appears next provides the proportion of each tag in relation with the “Other”’s total.

Example: Here below, the “Effiliation” tag takes about 14% of the “Other”’s total loading time (14% of the 21% of global loading time, which “Others” account for).

<figure><img src="../../../../../../../.gitbook/assets/image (328).png" alt=""><figcaption></figcaption></figure>

**3)-Main Tag Variations:**

The “Main Tag Variations” graphs allow you to identify tags whose loading time has varied (+/-10%) over a selected period of time in terms of the selected level of analysis in the available filters: Start Render, DOM Ready, DOM Loaded or Cummulated loading time.

<figure><img src="../../../../../../../.gitbook/assets/image (329).png" alt=""><figcaption></figcaption></figure>

The tag’s variation measures gaps in tags’ loading times in relation with the median (and not the average, in order for it to be less sensitive to extreme values). Calculation is based on the six previous identical periods.

Example:

We wish to analyze the variation of tags affecting the Start Render event on May 22nd.

In the screenshot below, we can see a 65% increase in AB Tasty’s loading time for that day. The tag does indeed take 61.96ms to load, whereas the median for the six previous days was of 37.65ms. (May 16th: 48.05ms /May 17th: 30.30ms / May 18th: 35.77ms / May 19th: 27.44ms / May 20th: 64.11 ms / May 21st: 39.53ms).

<figure><img src="../../../../../../../.gitbook/assets/image (330) (1).png" alt=""><figcaption></figcaption></figure>

**4)-Main Page Type Variations:**

The “**Main Page Type Variations**” graphs allow you to identify the page types whose loading time has varied (+/-10%) over a selected period of time in terms of the DOM Loaded event only (the page’s loading time is defined with the arrival of the DOM Loaded event).

Note: The page type corresponds to the default “page type” filter available on the interface.

<figure><img src="../../../../../../../.gitbook/assets/image (332).png" alt=""><figcaption></figcaption></figure>

The page type variation measures gaps in pages’ loading times depending on their type and in relation with the median (and not the average). Calculation is based on the six previous identical periods.

Example:

We wish to analyze variations in types on May 2nd.

In the screenshot below, we see a 31% reduction in loading times for the “newsletter” page type on that day. It takes 5.23ms to load whereas the median in the six preceding days was of 7.6ms (April 26th: 7.58 ms / April 27th: 5.31 ms / April 28th: 8.16 ms /April 29th: 7.62 ms / April 30th: 7.84 ms / May 1st: 6.02 ms).

<figure><img src="../../../../../../../.gitbook/assets/image (333).png" alt=""><figcaption></figcaption></figure>

## Report by tag

**1)-The four main metrics**

<figure><img src="../../../../../../../.gitbook/assets/image (334).png" alt=""><figcaption></figcaption></figure>

* **Average page loading time**: average loading time of your website’s pages (= DOM Loaded). This loading time is compared to that of the previous period (ex: the previous day or week according to the selected period).
* **Average tag loading time**: average loading time of the tags on your website according to the level of analysis that you selected in the filtering options (Start Render, DOM Ready, DOM Loaded, Cumulated loading time). This loading time is compared to that of the previous period (ex: the previous day or week according to the selected period).
* **Lowest impact tag**: tag that takes the least time to load according to the level of analysis that you selected in the filtering options (Start Render, DOM Ready, DOM Loaded, Cumulated loading time).
* **Highest impact tag**: tag that takes the most time to load according to the level of analysis that you selected in the filtering options (Start Render, DOM Ready, DOM Loaded, Cumulated loading time).

Note: These four metrics consider the selected filters among “page type”, “container”, “device”, “OS” or “browser”.

**2)-TagPerformance by tags**

<figure><img src="../../../../../../../.gitbook/assets/image (335) (1).png" alt=""><figcaption></figcaption></figure>

The graph shows information about tags’ loading time on your website.

To select tags to analyze with the graph (1), check the corresponding tag in the “Tags” report (2) and reload (3).

<figure><img src="../../../../../../../.gitbook/assets/image (337).png" alt=""><figcaption></figcaption></figure>

You can compare this data to generic information about the page’s context. To do so, select the indicators you are interested in from the dropdown menu above the graph.

Metrics related to the analyzed tags:

* **Tag Loading time**: tags’ loading time according to the level of analysis that you selected in the filtering options (Start Render, DOM Ready, DOM Loaded, Cumulated loading time).
* **Tag firing**: number of times tags are loaded on the site (this metric is independent from the filters).

Metrics related to the page’s context:

* **Tag number**: number of tags present in the last generated version(s) of a container.
* **Average start render (First paint)**: average loading time of the tart Render on the site.
* **Average page structure building (DOM Ready)**: average loading time of the DOM Ready on the site.
* **Average page loading time (OnLoad)**: average loading time of the DOM Loaded on the site.

Note: These six metrics consider the selected filters among “page type”, “container”, “device”, “OS” or “browser”.

Example:

You wish to know if a tag loading during the Start Render event has an impact on the site’s global Start Render.

* Use the “Tags impacting Start Render (First Paint)” filter on your report:

<figure><img src="../../../../../../../.gitbook/assets/image (338).png" alt=""><figcaption></figcaption></figure>

*   Select the tag to analyze:

    <figure><img src="../../../../../../../.gitbook/assets/image (339).png" alt=""><figcaption></figcaption></figure>
*   Select the following metrics from your graph: “Tag Loading Time” (the tag’s loading time) and “Average Start Render (First Paint)” (average loading time of the Start Render):\\

    <figure><img src="../../../../../../../.gitbook/assets/image (340).png" alt=""><figcaption></figcaption></figure>

The result below shows that the selected tag has little impact on the site’s Start Render, as the increase in the tag’s loading time at 13h (1) did not cause the Start Render’s average loading time to increase as well at that very moment.\\

<figure><img src="../../../../../../../.gitbook/assets/image (341).png" alt=""><figcaption></figcaption></figure>

**3)-Tags**

<figure><img src="../../../../../../../.gitbook/assets/image (342).png" alt=""><figcaption></figcaption></figure>

The “Tags” section of the report provides deeper insight about the tags that are loaded on your site, according to the level of analysis you selected from the filters on the top left-hand side (Start Render, DOM Ready, DOM Loaded, Cumulated loading time) and top right-hand side of the page (“page type”, “container”, “device”, “OS” and “browser”).

You can analyze the following elements for each tag:

* **“Tag loading time” (ms**): Loading time in milliseconds
*   **“Tag firing”**: Number of times a tag is loaded\
    \\

    <figure><img src="../../../../../../../.gitbook/assets/image (343).png" alt=""><figcaption></figcaption></figure>

If you click a tag’s name, a graph appears showing these items:

* The tag’s loading time compared to the previous period (ex: previous day if the analysis is done by day).
* The tags’ average loading time compared to the previous period.
* The number of times a tag is loaded compared to the previous period (ex: previous day if the analysis is done by day).
* The number of times tags are loaded on the site compared to the previous period.

Note: The current period is always displayed in green and the period of comparison in blue.\\

<figure><img src="../../../../../../../.gitbook/assets/image (344).png" alt=""><figcaption></figcaption></figure>

## Piggybacking

“Piggybacking”, consisting in triggering a tag with another, has widespread exponentially with the appearance of programmatic. The subsequent data leakage has generated legal issues and financial losses for companies.

Amid this context, the “Tag Hierarchy” report provides a global insight of requests happening while your website and its content load. You can thus better control calls issued from your website and exchanged data.

**Report Structure:**

1/Page type filter:

This report is filtered by page type (“page\_type” option on the segmentation menu). The default selected page type is the first one appearing on the list (1) and is displayed on the top, left-hand side of the report (2):\
\\

<figure><img src="../../../../../../../.gitbook/assets/image (346).png" alt=""><figcaption></figcaption></figure>

You can at all times apply filters on different page types or deselect enabled filters to have an overview of your site (please note that in this case, the report might take a little longer to load, as it will combine all domains called on your website).

2/Request type (script/iframe/pixel)

The report highlights the request’s nature/type:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2018/01/piggybacking_doc_2.png)

* Script (URL called with \<script> tag)
* Iframe (URL called with an \<iframe> tag)
* Pixel (URL called with an \<img> tag)
* “Other” (in case the request type is not identified)

<figure><img src="../../../../../../../.gitbook/assets/image (347).png" alt=""><figcaption></figcaption></figure>

3/Request Detail

The “Tag Hierarchy” report allows you to visualize all domains called from your main domain and all other domains they call on different levels:\\

<figure><img src="../../../../../../../.gitbook/assets/image (348).png" alt=""><figcaption></figcaption></figure>

On the diagram above, sub-domain 2 (“sub-domain 2”) is called from your site’s main domain. It is a JavaScript file (blue circle) that in turn calls two pixels (green circles) and a JavaScript file. Waterfall calls stop here for this request, but this is not the case for sub- domain 1 (“Sub-domain 1”), which calls JavaScript files which in turn issue new requests.

In order to provide you with better readability, same-type “childless” requests (script/iframe/pixel) coming from the same domain are gathered under the same domain name, and a number between brackets next to the domain’s name indicates how many calls were issued from it:\\

<figure><img src="../../../../../../../.gitbook/assets/image (349).png" alt=""><figcaption></figcaption></figure>

By hovering over any of these domains (ex: ) you will see, with greater detail, which URLs are called by them:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2018/01/2018-01-29_12h13_27.png)

<figure><img src="../../../../../../../.gitbook/assets/image (350).png" alt=""><figcaption></figcaption></figure>

You will also be able to see the URL structure and its parameters for certain requests, hence all the information sent to solutions called on your website:\\

<figure><img src="../../../../../../../.gitbook/assets/image (351).png" alt=""><figcaption></figcaption></figure>

4/Report dates

Displayed data is collected over the past 24 rolling hours.

This export is currently unavailable.

## Filters

**1)-Select your level of analysis:**

<figure><img src="../../../../../../../.gitbook/assets/image (352).png" alt=""><figcaption></figcaption></figure>

* **“Tags impacting start render (First Paint)”**: This corresponds to the aggregated loading time of hits that are sent prior to the Start Render event.
* **“Tags impacting page structure building (DomReady)”**: This corresponds to the aggregated loading time of hits that are sent prior to the DOM Ready event.
* **“Tags impacting page loading time (Onload)”**: This corresponds to the aggregated loading time of hits that are sent before the DOM Loaded event.
* **“Cumulated tag loading time”**: corresponds to the aggregated loading time of all hits (including those sent after the DOM Loaded event).

Example: The following diagram shows an extract of tags present on the site:\\

<figure><img src="../../../../../../../.gitbook/assets/image (318) (1).png" alt=""><figcaption></figcaption></figure>

These are the results you will obtain when you select the following levels of analysis:

*   “Tags impacting start render (First Paint)”: _TAG1 (HIT1) + TAG2 (HIT1)_

    <figure><img src="../../../../../../../.gitbook/assets/image (354).png" alt=""><figcaption></figcaption></figure>
*   “Tags impacting page structure building (DomReady)”: _TAG1 (HIT1) + TAG2 (HIT1) + TAG1 (HIT2) + TAG1 (HIT3)_\\

    <figure><img src="../../../../../../../.gitbook/assets/image (355).png" alt=""><figcaption></figcaption></figure>
*   “Tags impacting page loading time (Onload)”: _TAG1 (HIT1) + TAG2 (HIT1) + TAG1 (HIT2) + TAG1 (HIT3) + TAG2 (HIT2)_

    <figure><img src="../../../../../../../.gitbook/assets/image (356).png" alt=""><figcaption></figcaption></figure>
*   “Cumulated tag loading time”: _TAG1 (HIT1) + TAG2 (HIT1) + TAG1 (HIT2) + TAG1 (HIT3) + TAG2 (HIT2) + TAG1 (HIT4)_

    <figure><img src="../../../../../../../.gitbook/assets/image (318) (1).png" alt=""><figcaption></figcaption></figure>

If you wish to know more about the “Start Render”, “**DOM Ready**” and “**DOM Loaded**” concepts please refer to the Definition of TagPerformance Metrics article.

If you wish to know more about the technical elements that are captured by TagPerformance, please refer to the Advanced: Technical functioning of TagPerformance article.

**2)-Select, if need be, one of the default filters from the interface should you require a more detailed analysis of your site’s performance.**

* **The page type**: This filter allows you to display your tags’ performance in terms of the page template. It is based on the “env\_template” variable’s values, which are automatically captured by TagPerformance.

Note: If you do not have an env\_template variable on your site, you still can capture the values of other variables. Please refer to the Adding the TagPerformance Tag article.

* **The container name**: This filter allows you to display how tags within one or more specific containers are performing.
* **The device**: This filter allows you to display your tags’ performance in terms of the devices your visitors are using. The “device” metric is calculated automatically by our servers, based on the user agent.
* **OS**: This filter allows you to display your tags’ performance in terms of the devices your visitors are using. The “OS” metric is calculated automatically by our servers based on the user agent.
* **The Bowser**: This filter allows you to display your tags’ performance in terms of the browsers your visitors are using. The “browser” metric is calculated automatically by our servers based on the user agent.

Note: if you wish to add an additional filter, please refer to the Adding the TagPerformance Tag article.

**3)-Click “Apply” to obtain filtered results and a different level of analysis.**
