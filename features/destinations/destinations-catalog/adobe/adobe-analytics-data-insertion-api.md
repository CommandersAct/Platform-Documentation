# Adobe Analytics Classic

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Adobe](https://www.adobe.com/) is an multinational computer software and web analytics company (See [Adobe Experience Cloud](https://business.adobe.com/)). Using this destination, you can leverage Adobe [Data Insertion API](https://developer.adobe.com/analytics-apis/docs/1.4/guides/data-insertion/) and send data to [Adobe Analytics](https://experienceleague.adobe.com/en/browse/analytics). Instead of using [client-side AppMeasurement](https://experienceleague.adobe.com/en/docs/analytics/implementation/js/overview), this destination collects data based solely on API requests and responses and provides valuable insight into user activity without the overhead associated with attaching JavaScript to every page.

## Key features

The Adobe Analytics Classic provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) supports [Adobe XML tag structure](https://developer.adobe.com/analytics-apis/docs/1.4/guides/data-insertion/variable-reference/), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Support for multi-item data**: information included in the [item](https://community.commandersact.com/platform-x/developers/tracking/events-reference#item) array is bridged to Adobe Analytics.

## Destination setup

Ensure you have access to [Adobe Analytics](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/intro-to-analytics/analytics-basics/logging-in-to-adobe-analytics).&#x20;

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Collection Domain</code></td><td><em><strong><code>Required</code></strong></em><br>Your Adobe Analytics collection domain. (E.g. <code>example.sc.omtrdc.net</code> ).</td></tr><tr><td><code>Report Suite Id</code></td><td><em><strong><code>Required</code></strong></em><br>The <code>Report Suite Id</code>  (RSID) you want to send data to.</td></tr></tbody></table>

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

{% hint style="warning" %}
Requests must include the following Adobe properties:\
• At least one of:\
&#x20;   ◦ `marketingCloudVisitorId`\
&#x20;   ◦ `fallbackVisitorId`\
&#x20;   ◦ `visitorId`\
&#x20;   ◦ `ipAddress` and `userAgent`\
• At least one of:\
&#x20;   ◦ `pageUrl`\
&#x20;   ◦ `pageName`\
&#x20;   ◦ `linkType` with `linkName` or `linkUrl`\
• `reportSuiteId`
{% endhint %}

<table><thead><tr><th width="396.6685580062746">Commanders Act Properties</th><th>Adobe Properties</th></tr></thead><tbody><tr><td><code>Report Suite Id</code></td><td><code>reportSuiteId</code></td></tr><tr><td><code>partners.adobe.marketing_cloud_org_id</code></td><td><code>marketingCloudOrgId</code> <strong>[1]</strong></td></tr><tr><td><code>partners.adobe.marketing_cloud_visitor_id</code></td><td><code>marketingCloudVisitorId</code> <strong>[2]</strong></td></tr><tr><td><code>user.id</code></td><td><code>visitorId</code> <strong>[3]</strong></td></tr><tr><td><code>user.consistent_anonymous_id</code></td><td><code>fallbackVisitorId</code> <strong>[4]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>ipAddress</code></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>userAgent</code></td></tr><tr><td><code>context.page.url</code></td><td><code>pageUrl</code> <strong>[5]</strong> </td></tr><tr><td><code>context.page.title</code></td><td><code>pageName</code> <strong>[6]</strong></td></tr><tr><td><code>page_type</code></td><td><code>pageType</code> <strong>[7]</strong></td></tr><tr><td><code>partners.adobe.link_type</code></td><td><code>linkType</code> <strong>[8]</strong></td></tr><tr><td><code>partners.adobe.link_name</code></td><td><code>linkName</code> <strong>[9]</strong></td></tr><tr><td><code>partners.adobe.link_url</code></td><td><code>linkUrl</code></td></tr><tr><td><code>context.device.screen.width</code><br><code>context.device.screen.height</code></td><td><code>resolution</code> <strong>[10]</strong></td></tr><tr><td><code>context.page.viewport.width</code></td><td><code>browserWidth</code> <strong>[11]</strong></td></tr><tr><td><code>context.page.viewport.height</code></td><td><code>browserHeight</code> <strong>[12]</strong></td></tr><tr><td><code>partners.adobe.campaign</code></td><td><code>campaign</code> <strong>[13]</strong></td></tr><tr><td><code>partners.adobe.channel</code></td><td><code>channel</code> <strong>[14]</strong></td></tr><tr><td><code>partners.adobe.color_depth</code></td><td><code>colorDepth</code> <strong>[15]</strong></td></tr><tr><td><code>partners.adobe.connection_type</code></td><td><code>connectionType</code> <strong>[16]</strong></td></tr><tr><td><code>partners.adobe.cookies_enabled</code></td><td><code>cookiesEnabled</code> <strong>[17]</strong></td></tr><tr><td><code>partners.adobe.customer_perspective</code></td><td><code>customerPerspective</code> <strong>[18]</strong></td></tr><tr><td><code>currency</code></td><td><code>currencyCode</code></td></tr><tr><td><code>partners.adobe.events</code></td><td><code>events</code> <strong>[19]</strong></td></tr><tr><td><code>partners.adobe.ims_region</code></td><td><code>imsRegion</code> <strong>[20]</strong></td></tr><tr><td><code>partners.adobe.java_enabled</code></td><td><code>javaEnabled</code> <strong>[21]</strong></td></tr><tr><td><code>context.device.lang</code></td><td><code>language</code> <strong>[22]</strong></td></tr><tr><td><code>id</code></td><td><code>transactionId</code> <strong>[23]</strong><br><code>purchaseId</code> <strong>[24]</strong></td></tr><tr><td><code>context.page.referrer</code></td><td><code>referrer</code> <strong>[25]</strong></td></tr><tr><td><p><code>partners.adobe.products</code> <br><code>items.X.product.category_1</code></p><p><code>items.X.product.name</code></p><p><code>items.X.quantity</code></p><p><code>items.X.product.price</code></p><p><code>items.X.events</code></p><p><code>items.X.evars</code></p></td><td><code>products</code> <strong>[26]</strong></td></tr><tr><td><code>partners.adobe.server</code></td><td><code>server</code> <strong>[27]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>timestamp</code> <strong>[28]</strong></td></tr><tr><td><code>partners.adobe.architecture</code></td><td><code>architecture</code> <strong>[29]</strong></td></tr><tr><td><code>partners.adobe.bitness</code></td><td><code>bitness</code> <strong>[29]</strong></td></tr><tr><td><code>partners.adobe.model</code></td><td><code>model</code> <strong>[29]</strong></td></tr><tr><td><code>partners.adobe.platform</code></td><td><code>platform</code> <strong>[29]</strong></td></tr><tr><td><code>partners.adobe.platform_version</code></td><td><code>platformVersion</code> <strong>[29]</strong></td></tr><tr><td><code>partners.adobe.wow64</code></td><td><code>wow64</code> <strong>[29]</strong></td></tr></tbody></table>

{% hint style="info" %}
> **\[1]** The Experience Cloud Organization ID. It identifies the organization within the Adobe Experience Cloud.\
> &#xNAN;**\[2]** The unique identifier used with the [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/en/docs/id-service/using/id-service-api/library#/).\
> &#xNAN;**\[3]** The [visitorID](https://experienceleague.adobe.com/en/docs/analytics/implementation/vars/config-vars/visitorid#/) implementation variable.\
> &#xNAN;**\[4]** A fallback cookie <mark style="color:$primary;">`s_fid`</mark>  is set when the primary cookie (<mark style="color:$primary;">`AMCV_`</mark>  or <mark style="color:$primary;">`s_vi`</mark> ) is unavailable. It has a 2 year expiration and is used as the fallback identification method going forward.\
> &#xNAN;**\[5]** The [Page URL](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/page-url#/) dimension.\
> &#xNAN;**\[6]** The [Page](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/page#/) dimension.\
> &#xNAN;**\[7]** The [pageType](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/page#/) implementation variable. Set to the string value <mark style="color:$primary;">`errorPage`</mark>  on any error pages, such as a 404 or 503 error.\
> &#xNAN;**\[8]** The type of link. Defaults to <mark style="color:$primary;">`o`</mark>  if this tag is empty or omitted and <mark style="color:$primary;">`Link Name`</mark>  contains a value. Valid values include: <mark style="color:$primary;">`d`</mark> : Download link <mark style="color:$primary;">`e`</mark> : Exit link <mark style="color:$primary;">`o`</mark> : Custom link\
> &#xNAN;**\[9]** The [Download link](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/download-link#/), [Exit link](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/exit-link#/), or [Custom link](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/custom-link#/) dimension, depending on the value in the <mark style="color:$primary;">`LinkType`</mark>  tag. If this tag contains a value, <mark style="color:$primary;">`Page Name`</mark>  is ignored.\
> &#xNAN;**\[10]** The width and height of the [Monitor resolution](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/monitor-resolution#/) dimension.\
> &#xNAN;**\[11]** The [Browser width](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/browser-width#/) dimension.\
> &#xNAN;**\[12]** The [Browser height](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/browser-height#/) dimension.\
> &#xNAN;**\[13]** The [Tracking code](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/tracking-code#/) dimension.\
> &#xNAN;**\[14]** The [Site section](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/site-section#/) dimension.\
> &#xNAN;**\[15]** The [Color depth](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/color-depth#/) dimension.\
> &#xNAN;**\[16]** The [Connection type](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/connection-type#/) dimension.\
> &#xNAN;**\[17]** The [Cookie support](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/cookie-support#/) dimension.\
> &#xNAN;**\[18]** Integer representing if the hit is considered a background or foreground hit. Valid values include <mark style="color:$primary;">`0`</mark>  (foreground hit, default) and <mark style="color:$primary;">`1`</mark>  (background hit). See [Context-aware](https://experienceleague.adobe.com/en/docs/analytics/components/virtual-report-suites/vrs-mobile-visit-processing#/) sessions.\
> &#xNAN;**\[19]** The [events](https://experienceleague.adobe.com/en/docs/analytics/implementation/vars/page-vars/events/events-overview#/) implementation variable.\
> &#xNAN;**\[20]** Integer that represents the Adobe Audience Manager location hint. Ensures that data is forwarded to the right Audience Manager regional data collection center. The Analytics tracking server/API endpoint must also be set to forward to the correct Audience Manager instance before Analytics data is forwarded to Audience Manager. Use the [getLocationHint](https://experienceleague.adobe.com/en/docs/id-service/using/id-service-api/methods/getlocationhint#/) function of the Adobe Experience Cloud Identity Service API to retrieve the correct <mark style="color:$primary;">`Ims Region`</mark>  value for the user. The <mark style="color:$primary;">`marketingCloudVisitorID`</mark>  tag is also required when using this tag.\
> &#xNAN;**\[21]** The [Java enabled](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/java-enabled#/) dimension.\
> &#xNAN;**\[22]** The [Language](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/language#/) dimension.\
> &#xNAN;**\[23]** The [transactionID](https://experienceleague.adobe.com/en/docs/analytics/implementation/vars/page-vars/transactionid#/) implementation variable.\
> &#xNAN;**\[24]** The [purchaseID](https://experienceleague.adobe.com/en/docs/analytics/implementation/vars/page-vars/purchaseid#/) implementation variable.\
> &#xNAN;**\[25]** The [referrer](https://experienceleague.adobe.com/en/docs/analytics/implementation/vars/page-vars/referrer#/) implementation variable.\
> &#xNAN;**\[26]** The [products](https://experienceleague.adobe.com/en/docs/analytics/implementation/vars/page-vars/products#/) implementation variable. You can set the full products info directly using this field. This has priority over the <mark style="color:$primary;">`Item list`</mark>  and <mark style="color:$primary;">`Item Attributes`</mark> .\
> &#xNAN;**\[27]** The [Server](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/server#/) dimension.\
> &#xNAN;**\[28]** The timestamp related to when the event took place. Both 10 or 13-digit timestamps are supported. If this is not provided the current timestamp is used.\
> &#xNAN;**\[29]** See [User Agent Client Hint fields](https://developer.adobe.com/analytics-apis/docs/1.4/guides/data-insertion/variable-reference/#user-agent-client-hint-fields/).


{% endhint %}
