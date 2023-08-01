# SPA implementation guide

### 1. W**hat is an SPA environment**? <a href="#1.-what-is-an-spa-environment" id="1.-what-is-an-spa-environment"></a>

An SPA (Single Page Application) is a website or a web application that loads elements dynamically according to user actions rather than loading new pages after every interaction. Commanders Act web container offers functions allowing you to load all or a part of the container within an SPA environment, allowing you to call desired tags on every action performed by a user. These functions need to be implemented in your site’s source code by either your technical partner or by your own technical staff.

### 2.**How to implement Commanders Act web container in an SPA environment**? <a href="#2.how-to-implement-tagcommander-in-an-spa-environment" id="2.how-to-implement-tagcommander-in-an-spa-environment"></a>

#### 2.1 Loading containers <a href="#2.1-loading-containers" id="2.1-loading-containers"></a>

Commanders Act web containers are loaded once upon page load within a Single Page Application Environment. In order to reload containers on user actions, you can use the following features:

* tC.container.reload() : this function allows you to reload all the containers on a page. Elements shared by containers (deduplication calculation, external variables initialization, internal variables calculation, calculation of cookies dropped with data storage and the initialization of the Privacy cookie) are only loaded once to optimize performance.

```
tC.container.reload({ exclusions: ["datastorage","deduplication","internalvars","privacy"], events: {label1: [{targeted_element},{event_variables}], label2: [{},{}]}})
```

This function allows to reload all of a page’s containers while excluding some of their elements. Elements to exclude need to be mentioned in the “exclusions” table.\
\
Ex: if you wish to reload the container without recalculating internal variables, you need to call this function: tC.container.reload({exclusions:\["internalvars"]})\
\
This function also allows to call the tC.event function that loads selected tags upon user action. The tC.event function is executed after the container elements reloading. label: specify the name you wish to call your function (ex : "click", "add\_to\_cart"…). targeted\_element: DOM elements on which the event applies. {} if not necessary.\
\
event\_variables: variables specific to the event. {} if not necessary.Ex:&#x20;

`tC.container.reload({events: {label1: [{target: document.getElementById('targeted_element'}, {"page_name":"", "product_id":""}]}})`

* tC.container\_IDS\_IDC.reload() : this function allows loading a single container (to do so, you will have to specify the site’s and the container’s ID) on a page that contains more than one.

IDS : Commanders Act site ID\
IDC : Commanders Act container ID

* `tC.container_IDS_IDC.reload({ exclusions: ["datastorage","deduplication","internalvars","privacy"], events: {label1: [{targeted_element},{event_variables}], label2: [{},{}]} })`

This function allows loading a single container (to do so, you will have to specify the site’s and the container’s ID) on a page that contains more than one while excluding some of their elements. Elements to exclude need to be mentioned in the “exclusions” table, and event functions need to be mentioned in the “events” object, as for the `tC.container.reload({exclusions:["datastorage","deduplication","internalvars","privacy"]})` function.

#### 2.2 Loading tags <a href="#2.2-loading-tags" id="2.2-loading-tags"></a>

To load selected tags upon user action, you will need to implement this function:

* `tC.event.label()` : this function allows loading selected tags upon user action.

label: specify the name you wish to call your function.\
\
Ex: implement the tC.event.step2\_basket function if your wish to call specific tags on the 2nd step in the purchase cart.\
\
You can also set-up a “generic” function like tC.event.all on all of your virtual pages to call tags on all of your SPA sites (Analytics tags, for instance). You will then use perimeters and constraints from the Commanders Act interface to control other tags’ execution.

* `tC.event.label(this, {"page_name":"", "product_id":""})` : this function allows loading selected tags based on user action and to define variables specific to said action (ex : the name of a virtual page, a specific product id …).

#### 2.3 Going further: Structure of a Commanders Act web Ccontainer <a href="#2.3-going-further-structure-of-a-tagcommander-container" id="2.3-going-further-structure-of-a-tagcommander-container"></a>

You will find below a list of all the elements that load inside the Commanders Act web container upon first load, as well as the tC.container.reload,(tC.container\_IDS\_IDC.reload()) and tC.event.XXX() functions that are called.

| Container element                                                                       | Definition                                                                                                                                             | 1st container load | tC.container.rel oad() function | tC.container\_IDS\_IDC.reload() function | tC.event.XXX() function |
| --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------ | ------------------------------- | ---------------------------------------- | ----------------------- |
| Deduplication functions                                                                 | They identify thevisitor’s traffic source                                                                                                              | yes                | Yes (once loaded)               | yes                                      | no                      |
| External variables initialization                                                       | They define all external variables that do not already exist                                                                                           | yes                | yes                             | yes                                      | no                      |
| Dynamic JS 1                                                                            | Calls an external JavaScript file prior to the internal variables’ declaration                                                                         | yes                | no                              | no                                       | no                      |
| Static JS 1                                                                             | Calls custom JavaScript code prior to the internal variables’ declaration                                                                              | yes                | no                              | no                                       | no                      |
| Internal variables                                                                      | Calculates internal variables                                                                                                                          | yes                | yes                             | yes                                      | no                      |
| Dynamic JS 2                                                                            | Calls an external JavaScript file after the external variables’ declaration                                                                            | yes                | no                              | no                                       | no                      |
| Static JS 2                                                                             | Calls an external JavaScript file after the internal variables’ declaration                                                                            | yes                | no                              | no                                       | no                      |
| Data storage                                                                            | Calculates the value of cookies created with the "data storage" module                                                                                 | yes                | yes                             | yes                                      | no                      |
| "Container loaded" & "DOM ready" & "Clicks"& "Form submission " & "Scroll" tags + rules | Executes tags called on the "Container loaded", "DOMready", "Clicks","Form submission" and"Scroll" triggers, as well as on the rules associated to the | yes                | no                              | no                                       | no                      |
| ​                                                                                       | container’s first load.                                                                                                                                | ​                  | ​                               | ​                                        | ​                       |
| "Custom" tags + rules                                                                   | Executes tags called on the "Custom"triggers, as well as on the rules associated to the container’s loading or reloading.                              | yes                | yes                             | yes                                      | yes                     |
| Events + rules                                                                          | Executes events triggered on the previous tc\_events function                                                                                          | yes                | no                              | no                                       | no                      |
| Privacy                                                                                 | Re-initializes the Privacy cookie to take into account users’ choices.                                                                                 | yes                | yes                             | yes                                      | No                      |
| Tag Hierarchy                                                                           | Identifies piggybacked tags (tags sideloaded by other tags in the"TagPerformanc e" module)                                                             | yes                | no                              | no                                       | no                      |
| Event listener                                                                          | Reloads event listeners (which allow to track actions performed by any userbrowsing the site (clicks, scrolls …))                                      | yes                | no                              | no                                       | no                      |
