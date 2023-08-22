# Internal variables

These variables are called **internal variables** because they are created inside the **Commanders** Act web container: They are integrated directly into your site’s container, in contrast with external variables, which are added into the page’s **source code** by the technical staff.

Internal variables are used to **collect data** to enrich data through the external variables. A library of **predefined internal variables is available**, but you can also create **your own**.

**Internal variables** must be created in the **Commanders Act interface** before they can be used in containers. See the rest of the articles in the “internal variables” section to know more about the different options available to create such variables.

All internal variables created can be used:

* To be added to the solutions embedded in the container (linking internal variables and solutions is called **mapping**). See the “Mapping tags’ variables” article to find out how to map your **internal variables** in a tag.
* To create **activation rules** for your tags. See the “Adding Rules” article to find out how to create rules based on your internal variables.

Additional information

Internal variables are all coded in JavaScript, but you **do not need** any **technical knowledge** of **JavaScript** in order to use the “**Predefined**” variables or the “**Builder**” modes,  since the code is generated **automatically** by the **Commanders Act**. However, you will **need to know JavaScript** or seek help from the **Commanders Act support** team in order to create your own **custom internal variables**.

Here are some examples of predefined internal variables:

*   Internal variable for retrieving the URL of the page:\


    | <pre><code>tC.internalvars.tc_url = document.location.href;
    </code></pre> |
    | ------------------------------------------------------------------------- |
*   Internal variable for retrieving the URL of the previous page/site:\


    | <pre><code>tC.internalvars.tc_referrer = document.referrer;
    </code></pre> |
    | ------------------------------------------------------------------------- |
*   Internal variable for retrieving what comes between the first “/” and second “/” of the URL:\


    ```
    tC.internalvars.tc_url_1 =(function(){
    tC.internalvars.tc_url_1_tmp = document.location.href.split('?');
    tC.internalvars.tc_url_1_tmp2 = tC.internalvars.tc_url_1_tmp[0].split('/');
    return tC.internalvars.tc_url_1_tmp2[3];
    })();
    ```





## When to add an internal variable

There are several situations in which you may need to create an **internal variable** using the internal **variable management** interface:

* You want to **retrieve elements** available on your web pages, but they **do not** have **external variables** implemented by technical staff (for example: the value of a cookie, HTML tag, URL, etc.).
* You want to **create a new variable** based on the values of **external variables already implemented** by technical staff (for example: calculating the cart’s total before tax using the external variable that returns the cart’s total including tax).
* You want to create a lookup table based on an external variable (for example: when the external “country” variable is “FR”, you send an account number to your analytics tool that is different from when the variable is “IT”).
* Etc.

The link created between the internal variables and the solutions is called “**mapping**“. This is performed in the “**EDIT**” tab during the container deployment process.

## Types of internal variables

There are **two types** of internal variables: **predefined** and **custom**.

* Predefined internal variables, have already been created and are ready to use (e.g. variables that retrieve URL fragments).
* You can also configure your own internal variables, using pre-existing variables (e.g. external variables) or retrieving elements available on your sites’ pages (e.g. cookies).

To declare a predefined internal variable, click "**Data Management**” > "**Web Datalayer**" > “**Internal Variables**” > “**ADD PREDEFINED VARIABLE**”:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/ADD\_PREDEFINED\_INT\_VAR.png)

<figure><img src="../../../../../../../.gitbook/assets/image (244).png" alt=""><figcaption></figcaption></figure>

You will then be prompted to select a predefined variable universe.\


<figure><img src="../../../../../../../.gitbook/assets/image (245).png" alt=""><figcaption></figcaption></figure>

The “**add variable**” window contains various fields:

<figure><img src="../../../../../../../.gitbook/assets/image (246).png" alt=""><figcaption></figcaption></figure>

“**Predefined universe**“: Selection of predefined internal variable categories

“**Name**“: Variable’s name

“**Description**“: Variable’s description

“**Code**“: Variable’s code

**Checkbox**: The selection of predefined internal variables to add to the container (it is futile to include variables you do not wish to use).

**Four predefined variable universes (“Predefined universe”) are available:**

* **Common variables**: The most used variables by both Commanders Act consultants and customers.
* **Customer journey variables**: Variables that exploit the visitor’s customer journey (prerequisite: the "deduplication" module must be activated).
* **AT Internet plugin:** Variables that exploit data collected by the AT Internet digital analytics solution (prerequisite: the AT Internet solution must be present on your site).
* **Partner tags:** Code snippets adapted and adaptable to partner tags to increase their potential and perform additional actions.

## Add build-in internal common variable

You will find below a list of the variables available in the “**Common variables**” category and their description

**Page title:** it stores the title of the page (from the \<title> html tag).[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/PAGE\_TITLE\_INTERNAL\_VAR.png)

_Example:_

_The value of this variable (on the http://www.tagcommander.com/fr/) page will be “Commanders Act – Tag Universel – Tag Management – Commanders Act”. It takes the value of the html \<title> tab._

\*\*\*

**Page URL:** it stores the URL of the current page.[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/PAGE\_URL\_INTERNAL\_VAR.png)

_Example:_

_The value of this variable for the “http://www.tagcommander.com/fr/” page will be “http://www.tagcommander.com/fr/”_

\*\*\*

**Previously Visited URL:** it stores the URL of the previous page

_Example:_

_If the visitor arrives at the Commanders Act site via the Google search engine, the value of this variable will contain “google.fr”_

\*\*\*

**Page URL without query string:** it stores the URL of the current page without the tracking parameters (Commanders Act will remove the “?” from the URL and everything after it.

_Example:_

_If the visitor is on the page “https://www.google.fr/webhp**?**tab=ww\&ei=-ATjVPTyFaWqywOpqoHYDw\&ved=0CAcQ1S4#q=inurl\&start=10″, the value of this variable will be “https://www.google.fr/webhp”_

\*\*\*

**Page query string only**:  it stores the the current page’s URL parameters (Commanders Act a will save everything that follows the “?” without including it).

_Example:_

_If the visitor is on the page “https://www.google.fr/webhp**?**tab=ww\&ei=-ATjVPTyFaWqywOpqoHYDw\&ved=0CAcQ1S4#q=inurl\&start=10″, the value of this variable will be “tab=ww\&ei=-ATjVPTyFaWqywOpqoHYDw\&ved=0CAcQ1S4#q=inurl\&start=10”_

\*\*\*

**URL parameters:** it stores the current page’s array of URL parameters.

_Example:_

_If the visitor is on the page “https://www.google.fr/webhp?**tab**=ww&**ei**=-ATjVPTyFaWqywOpqoHYDw&**ved**=0CAcQ1S4#q=inurl\&start=10″, this variable will contain the value of these three parameters: “tab”, “ei” and “ved”, and their values will be accessible in the following manner: “tc\_array\_url\_vars\[‘tab’]”, “tc\_array\_url\_vars\[‘ei’]” and “tc\_array\_url\_vars\[‘ved’]”_

\*\*\*

**Folder #1 in URL:** it stores the First “folder” in the current page’s URL

_Example:_

_If the visitor is on the page “http://www.tagcommander.com/**fr**/fonctionnalites/tag-management”, the value of this variable will be “fr”._

\*\*\*

**Folder #2 in URL:** it stores the second “folder” in the current page’s URL

_Example:_

_If the visitor is on the page “http://www.tagcommander.com/fr/**fonctionnalites**/tag-management”, the value of this page will be “fonctionnalites”_

\*\*\*

**Folder #3 in URL:** it stores Third “folder” in the current page’s URL

_Example:_

_If the visitor is on the page “http://www.tagcommander.com/fr/fonctionnalites/**tag-management**“, the value of this variable will be “tag-management”_

\*\*\*

**Random value(integer 9 digits):** it creates and stores a random number composed of 9 digits

_Example:_

_With each pageview/loading of this variable, the variable will return a random 9-digit number; for example, “255103492”_

\*\*\*

**URL pathname without query string /…/…/….html:**  it stores the current page’s URL without the parameters (including the “/”)

_Example:_

_If the visitor is on the page “https://www.google.fr**/webhp**?tab=ww\&ei=-ATjVPTyFaWqywOpqoHYDw\&ved=0CAcQ1S4#q=inurl\&start=10″, the value of this variable will be “/webhp”_

\*\*\*

**Https protocol? “yes”/”no”:** Sends “yes” if the page uses the “https” protocol and “no” if it does not

_Example:_

_If the visitor is on the page “**https**://www.google.fr/webhp?tab=ww\&ei=-ATjVPTyFaWqywOpqoHYDw\&ved=0CAcQ1S4#q=inurl\&start=10″, the value of this variable will be “yes”_

\*\*\*

**Current domain name (www.domain.com):** it stores the current page’s domain name

_Example:_

_If the visitor is on the page “http://www.tagcommander.com/fr/fonctionnalites/tag-management”, the value of this variable will be “www.tagcommander.com”_

\*\*\*

**Main domain name without subdomains:** it stores the current page’s domain name without the subdomains

_Example:_

_If the visitor is on the page “http://www.tagcommander.com/fr/fonctionnalites/tag-management”, the value of this variable will be “tagcommander.com”_

\*\*\*

**Unix timestamp:** Current UNIX time  (the number of seconds since January 1, 1970 00:00:00)

_Example:_

_The current UNIX time when this document was written was “142166467”_

\*\*\*

**Device:** This variable provides information regarding a user’s device based on their screen resolution.

## Adding built-in customer journey internal variables

You will find below a list of the variables available in the “**Customer journey variables**” category and their corresponding description:

Last touch name (channel): Channel of the last touchpoint saved (prerequisite: deduplication must be active on your site).

_Example:_

_For customer journey “SEO/Google -> SEM/Bing -> **Display**/Criteo” the value of this variable will be “Display”._

\*\*\*

Last touch name (source): Source of the last touchpoint saved (prerequisite: deduplication must be active on your site).

_Example :_

_For customer journey “SEO/Google -> SEM/Bing -> Display/**Criteo**” the value of this variable will be “Criteo”._

## Adding customer internal variables

You can create your own internal variable in **two** ways:

* Via the “**Builder**” tab: The “**Builder**” mode assists you in creating customized internal variables without any technical knowledge or expertise;
* Via the “**Custom**” tab: “**Custom**” is a completely customized mode used to write your own JavaScript code. This method requires technical knowledge and expertise (but your **Commanders Act consultant** or **support** team can create custom variables for you if necessary).

To create your own internal variable, click "**Data Management**” > "**Web Datalayer**" > “**Internal Variables**” > “**ADD VARIABLE**”:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/ADD\_CUSTOM\_INT\_VAR.png)

<figure><img src="../../../../../../../.gitbook/assets/image (247).png" alt=""><figcaption></figcaption></figure>

The “**add variable**” window contains various fields:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/CUSTOM\_INTERNAL\_VINT\_CONFIG.png)

<figure><img src="../../../../../../../.gitbook/assets/image (248).png" alt=""><figcaption></figcaption></figure>

“**tC.internalvars.**“: The variable’s name (caution: it must not contain any accents or special characters, especially “-“).

_Note: The variable’s name is always prefixed by “tC.internalvars.” in order to avoid conflict with other variables on your site. For example, to see the content of an internal variable directly on your site or use a variable on another site, do not forget to specify the full name of the variable, which includes the prefix “tC.internalvars.” along with the variable’s name._

“**Builder**“/”**Custom**“: Select “Builder” or “Custom” creation mode

Area to create the variable (see details below for the Builder and Custom modes)

“**Type**“: The type of variable. Please refer to the article “Managing Variable Types“.

“**Description**“: A description of the variable, to clarify the variable’s name (e.g. “Product IDs separated by a /” can be the description of the variable named “tC.internalvars.concatid”)

“**Detailed description**“: A detailed description of the variable, to further clarify its name (e.g. “ID1/ID1/ID2…” can be the description of the variable named “tC.internalvars.concatid”)

### Builder mode

The “**Builder**” mode offers you three types of operations (1) that we describe below:

* “Join internal and/or external variable(s)”;
* “Join two-dimensional array variable(s)”;
*   “Variable mapping”.

    <figure><img src="../../../../../../../.gitbook/assets/image (249).png" alt="" width="563"><figcaption></figcaption></figure>

#### **Join internal and/or external variable(s)**

This operation allows you to **join** internal or external **variables** with the **separator** of your choice.

_Example:_

_If you wish to join an external variable returning the order ID with another external variable returning the order amount, with everything separated by a “-“, select the “order\_id” variable in the “External variables” tab to the left and then enter and add your separator in the “add separator” field in order to finish the “order\_amount” variable in the “External variables” tab._

<figure><img src="../../../../../../../.gitbook/assets/image (250).png" alt=""><figcaption></figcaption></figure>

#### **Join two-dimensional array variable(s)**

This operation allows you to join the array keys of a “**Two dimensional array**” variable.

_Example:_

_Your retargeting provider wants you to send all the prices of the products added to the cart separated by “|”. Begin by selecting the variable that contains the product information on the cart page (here the “user\_id” variable) (1), then the “order id” variable (here the “order\_confirmation\_id” key)  and the separator “|”. For example, the value obtained might be: “user@mail.com|123456789AB”._

#### **Variable mapping**

This operation allows you to create a lookup table for an input value (via an already existing internal or external variable) and an expected output value.

_Example:_

_You want to send a different account ID to your Digital Analytics solution depending on the work environment (pre-prod or prod). Select your reference variable (here the external variable “env\_work”), add its different input values in the “INPUT” field (e.g. “pre-prod” et “prod”) and then add the output account IDs of your analytics solution in the “OUTPUT” field. You can also add a default value if none of the values entered in the “INPUT” field have been foundj,yècr èuc._

<figure><img src="../../../../../../../.gitbook/assets/image (252).png" alt=""><figcaption></figcaption></figure>

_This operation allows you to automatically send the correct account ID to your analytics solution depending on the work environment._

### Full custom mode

The “**Custom**” mode allows you to write your **own JavaScript** code to create the internal variable of your choice:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/CUSTOM\_VAR.png)

<figure><img src="../../../../../../../.gitbook/assets/image (253).png" alt=""><figcaption></figcaption></figure>

Note: make sure that the variable’s JavaScript code always has the following syntax:\
`tC.internalvars.nameVariable = "yourCode";`

Also, make sure that **nameVariable** has the same name as the variable entered in the “**tC.internalvars**” field (see first screenshot with the variable **tC.internalvars.my\_custom\_var**):

Note: To avoid potential errors when the internal variable’s code is included, the “**TEST**” step of the container deployment process will test your internal variable on multiple browsers/operating systems.

## Managing variable types

The variable “**type**” (also called “**processing function**“) allows you to modify the variable format on the fly when mapping your tags.

They are useful when one of your solutions requests a variable format different from the format that you return in your **internal variable**. For example, if your “order\_discount” variable contains three decimal places, the processing functions will allow you to correct this so that your solutions receive the value with only 2 decimal places.

The most commonly used types are:

* **Order amount**: this allows you to modify the number format (amount) on the fly.

You can change separating commas into periods (e.g. “12,50” becomes “12.50”), choose the number of decimal places to retain (e.g. “12.50 becomes “12.5”), or convert the amount into pennies (“12.50 becomes “1250”).

* **Alphanumeric & Special chars**: this allows you to modify the character string format on the fly.

You can replace special characters with “\_” (e.g. “the company\&its values” changes to “the company\_its values”) or truncate a character string (e.g. limiting the variable’s value to 10 characters)

After assigning a variable type, you can modify its value on the fly, tag by tag, in the “EDIT” interface. Variables with a type added will have a blue symbol in front of their name:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/INT\_VAR\_LINK.png)

<figure><img src="../../../../../../../.gitbook/assets/image (254).png" alt=""><figcaption></figcaption></figure>

Once you have mapped your variable, click the link symbol:

<figure><img src="../../../../../../../.gitbook/assets/image (255).png" alt=""><figcaption></figcaption></figure>

A window will appear with a list of different operations corresponding to the type chosen. Check the operation you want (for example, encode an email in sha256) and click “**SAVE**”)[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/INT\_PROSS\_FUNC.png)

<figure><img src="../../../../../../../.gitbook/assets/image (256).png" alt=""><figcaption></figcaption></figure>

## Categorizing internal variables



Since you can create a variable using other variables, it is important for you to be able to manage the order in which they are executed so as to avoid any problems.

Therefore, you must declare an internal variable A, on which an internal variable B is based, before variable B. Variable B needs variable A declared first in order to be executed without creating errors.

The variables’ order can be modified using the double-arrow icon:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/VINT\_CATEGO.png)

<figure><img src="../../../../../../../.gitbook/assets/image (257).png" alt=""><figcaption></figcaption></figure>

To categorize an internal  variable you must :

*   Click the edit button (pencil icon to the right in the same row where the internal variable is located) and select the type from the drop down menu as depicted below. This applies **only** when you add a predefined variable.

    <figure><img src="../../../../../../../.gitbook/assets/image (258).png" alt=""><figcaption></figcaption></figure>
* Select the type when you add a custom variable, whether with the “**Builder**” or ‘**Full Custom**” mode. (Similar window as the one above).

## Declare an internal variable in a container

You can link an internal variable to a container if you have multiple containers on your site.

By doing this action, you declare just once the internal variable code in the linked container(s).

Consequences:

* You reduce the weight of the other containers by avoiding to declare many times the code of one single internal variable.
* If you call 2 containers on the same page, you avoid to overwrite the variable value defined in the first container by the value defined in the second container (if the value can change during the page load)

Example: two containers are on the same page, one in the header and one in the body. If you link an internal variable to the header container you will reduce the code of the page as the variable won’t be declared twice, and keep the value of the variable defined in the header.

To link an internal variable to a container, select the container of your choice when you create or modify your variable in the “Declared in container” field:

<figure><img src="../../../../../../../.gitbook/assets/image (259).png" alt=""><figcaption></figcaption></figure>

To realize a bulk action on multiple variables, check the variables of your choice, then choose the container(s) in the list:

<figure><img src="../../../../../../../.gitbook/assets/image (260).png" alt=""><figcaption></figcaption></figure>

