# Setup guide

The TagPerformance tag must be included in **each and every one of your containers**.

If you have **many containers** on a given page and as many TagPerformance tags, only **one hit** containing information about your tags will be sent.

It is not necessary to place it in a particular order within your containers, as it will automatically execute two seconds after the DOM Loaded event, that is to say, after all the other tags have loaded.

*   In the tag library, select the “Commanders Act – TagPerformance” tag.

    <figure><img src="../../../../../../../.gitbook/assets/image (319).png" alt=""><figcaption></figcaption></figure>
*   There is nothing to configure in the “EDIT” step: Generate a new container version and deploy it.

    <figure><img src="../../../../../../../.gitbook/assets/image (320).png" alt=""><figcaption></figcaption></figure>

**Advanced – Customizing the “TagPerformance” tag:**

*   It is **possible** to **force-measure a tag’s performance** (for example, that of a tag outside the container, that of a custom tag whose URL paths are not recognized by Commanders Act or that of a tag that is not present in the Commanders Act TMS tag library). If you wish to measure a new tag’s performance, place the following code block in the commented line 4 (1) tC.tagPerf.customPatterns.push({label:’Solution A’,p:’domain\\.com.\*js\\.js’})

    <figure><img src="../../../../../../../.gitbook/assets/image (321).png" alt=""><figcaption></figcaption></figure>

_Example:_

_tC.tagPerf.customPatterns.push({label:’exelate’,p:’loadm.exelator.com’});_

* You can also add **additional filters** (in addition to default filters page type, container, device, OS and browser). If you wish to add a custom filter, place the following code block in the commented line: tc\_vars\[“custom\_segment”] = #custom\_segment#;

Note: You can only add **one** additional filter.

_Example: to add a “page category” filter (tc\_vars\[“page\_cat1”]) :_

_tc\_vars\[“custom\_segment”] = tc\_vars\[“page\_cat1”];_

* Finally, you can **change the capturing method of the “Page Type” filter**, which is available in the reports. This filter is based on the tc\_vars\[“env\_template”] variable by default. If this variable is not available on your site, you can rely on a different variable by adding the following code block in the commented line (4) tc\_vars\[“env\_template”] = #page\_type#;

_Example: if you wish to replace tc\_vars\[“env\_template”] with tc\_vars\[“page\_type”] :_

_tc\_vars\[“env\_template”] = tc\_vars\[“page\_type”] ;_
