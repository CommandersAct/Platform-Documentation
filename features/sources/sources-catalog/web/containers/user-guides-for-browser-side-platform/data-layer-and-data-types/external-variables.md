# External variables

These variables are called **external variables** because they are outside the Commanders Act web container: They are embedded directly in the source code of your site’s pages, in contrast with internal variables, which are created inside the **container** and therefore not visible in the page’s source code. **External variables** are added by your **technical teams** or the technical provider in charge of implementing Commanders Act web containers on your site.

**External variables** are **indispensable** since they contain most of the data sent to the solutions present in the container. Their function and number vary depending on the **site’s economic model** (for example, media sites will not have the same external variables as e-commerce sites).

The list of external variables must be considered and established **before** Commanders Act web container is implemented in order to meet the embedded solutions’ medium- to long-term needs. A summary of the external variables to implement on your site will be provided by your **Commanders Act consultant** during the **setup** phase of the TMS, in an Excel file named “**deliverables**” or “**tagging plan**“.

**External variables** must be declared in the **Commanders Act interface** before you begin configuring tags in your containers. See the “Adding external variables” article in this section to find out how to declare an external variable in the interface.

All declared external variables can be used:

– To pass information to the solutions embedded in the container (linking external variables and solutions is called mapping). See the “Mapping Tags’ Variables” article to find out how to map your external variables in a tag.

– To create activation rules for your tags. See the “Adding Rules” section to find out how to create rules based on your external variables.

Additional information

As with your container, external variables must be present on **all of your site’s pages** and assigned values suited to the context. For example:

– The value of the “**page template**” variable will be different for the most important page templates on your site: homepage, product page, confirmation page, etc.

– The value of the “**user id**” variable will change for each visitor that connects to your site.

External variables must be declared in your site’s source code **before the call to your containers** (=JavaScript files). If you have a header container, the external variables will thus be present in the \<head>; if you have a container in the body, they must be declared in the \<body> html tag.

Here is a sample list of external variables:

```
<script type="text/javascript">
var tc_vars = new Array();
tc_vars["env_work"] = 'Prod';
tc_vars["env_channel"] = 'Web';
tc_vars["env_language"] = 'fr';
tc_vars["env_country"] = 'FR';
tc_vars['page_type'] = 'Homepage';
tc_vars["page_name"] = 'Tag Commander Market';
tc_vars["page_category_1"] = '';
tc_vars["page_category_2"] = '';
tc_vars["page_category_3"] = '';
</script>

/* Data layer is setup - call the Web Container Script underneath */

<script type="text/javascript" src="//cdn.tagcommander.com/674/my_web_container.js"></script>

```

### Adding external variables

There are **two** situations in which you may need to declare your variables in the external variable management interface:

1\) You wish to install **Commanders Act** on a **new site**: prior to having your technical teams or technical provider implement the data layer/variables in your site’s source code, you need to **declare the variables** in the Commanders Act interface so they are **available for mapping**.

2\) **Information is missing** from your current tagging plan (e.g. customer status): Again, this **variable** must be **declared** in the interface **first**, before it can be used in your tags and rules.

Note: If necessary, you can click “**Download**“, to retrieve your external variables in JavaScript format and send them to your technical team or the technical provider in charge of implementing the variables in you site’s source code:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/DOWNLOAD_VEXT_BUTTON.png)

<figure><img src="../../../../../../../.gitbook/assets/image (224).png" alt=""><figcaption></figcaption></figure>

Clicking “**Download**” will open a window containing the JavaScript code to insert in the site’s source code:

<figure><img src="../../../../../../../.gitbook/assets/image (225).png" alt=""><figcaption></figcaption></figure>

To add an external variable, you must go to the “**Data Management**” > "**Web Data layer**" > “**External Variables**” and click “**ADD VARIABLE**”

The “**add variable**” window contains various fields:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/VEXT_DETAILS.png)

<figure><img src="../../../../../../../.gitbook/assets/image (226).png" alt=""><figcaption></figcaption></figure>

“**Name**“: the variable’s name (mandatory field).

“**Category**“: used to categorize the variable according to its application (e.g. variable relative to users, product pages, confirmation pages, etc.) See the “Categorizing External Variables” article in this section.

“**Type**“: The type of variable. See the “Managing Variable Types” article in this section.

“**Use in noscript**“: Check the box so that the variable is present in the tag’s noscript code.

“**Description**“: A description of the variable, to clarify the variable’s name (e.g. “Page template” can be the description of the variable named “env\_template”).

“**Detailed description**“: A detailed description of the variable, to further clarify the variable’s name (e.g. “possible values: homepage/category/product/funnel\_confirmation” can be the detailed description of the “env\_template” variable).

Once the variable is added, it will appear on the variables list:

[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/VARIABLE_ADDED.png)

<figure><img src="../../../../../../../.gitbook/assets/image (227).png" alt=""><figcaption></figcaption></figure>

### Categorizing external variables

Variables can be **categorized** for easier management.

**Categories** allow you to **classify** variables according to their application (e.g. variables relative to site users in the “Users” category, variables for product pages in the “Product page” category, generic cross-functional variables for the site in the “Environment” category, etc.)

Categories are managed by clicking the “**manage categories**” button to the left of the “ADD VARIABLE” button:

<figure><img src="../../../../../../../.gitbook/assets/image (228).png" alt=""><figcaption></figcaption></figure>

Once your category is created, it can be used in the window to **add** and **edit external variables;** you can edit them by clicking the pencil icon, delete them by clicking the cross and adding them by entering a name and clicking the blue "+" button :[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/CAT_WINDOW.png)

<figure><img src="../../../../../../../.gitbook/assets/image (229).png" alt=""><figcaption></figcaption></figure>

### Managing variable types

The variable “**type**” (also called “**processing function**“) allows you to modify the variable format on the fly when mapping your tags.

They are useful when one of your solutions requires a variable format that is different from the format used in the **external variables** by the technical teams in charge of implementing the data layer.

For example, if your “page\_name” variable contains **special characters** in the source code, the processing functions allow you to **correct** them so that your solutions can receive the value without special characters.

The most commonly used types are:

* **Order amount**: this allows you to modify the number format (amount) on the fly.

You can change separating commas into periods (e.g. “12,50” becomes “12.50”), choose the number of decimal places to retain (e.g. “12.50 becomes “12.5”), or convert the amount into pennies (“12.50 becomes “1250”).

* **Alphanumeric & Special chars**: this allows you to modify the character string format on the fly.

You can replace special characters with “\_” (e.g. “the company\&its values” changes to “the company\_its values”) or truncate a character string (e.g. limiting the variable’s value to 10 characters).

After assigning a variable type, you can modify its value on the fly, tag by tag, in the “**EDIT**” interface. Variables with a type added will have a blue symbol in front of their name (1):[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/PROCESSING_FUNCTpng.png)

<figure><img src="../../../../../../../.gitbook/assets/image (230).png" alt="" width="320"><figcaption></figcaption></figure>

Once you have mapped your variable, click the link **symbol**:

<figure><img src="../../../../../../../.gitbook/assets/image (231).png" alt=""><figcaption></figcaption></figure>

A window will appear with a list of different operations corresponding to the type chosen. Check the box corresponding to the operation you want (for example, remove special characters and replace them by “\_”) and click “**SAVE**” :[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/STRING_OPS_PROSFUNC.png)

<figure><img src="../../../../../../../.gitbook/assets/image (234).png" alt="" width="399"><figcaption></figcaption></figure>

#### Advanced : 2-dimensional array

This type can be assigned to variables having a **two-dimensional array** as a value. On an ecommerce site, this will deal very often with “list\_product” and “order\_product” variables that return, respectively, **information** on **products** displayed on a **category page** or added to the cart.

We speak of “two-dimensional arrays” since these variables return an **array of values** for each **product** (e.g. for all the products on the site’s page, their ID, name, price, quantity, etc.).

Certain partner solutions may request that you send product data in their tag that are separated by a character called a “**separator**” (e.g. all product IDs separated by “**|**“, or all product prices separated by a **comma** in their confirmation tag).

The operation will be much easier if you select the “Two-dimensional array” processing function for your “order\_product” variable.

You will then be able to send your partners the information they expect without requiring any knowledge of JavaScript.

The first step in the configuration process is to select the “**Two-dimensional array**” type (1) for your variable:

<figure><img src="../../../../../../../.gitbook/assets/image (235).png" alt=""><figcaption></figcaption></figure>

Once this type is added, click on the “**Lis**t” icon that appears next to your variable to see a summary of the external variables:

<figure><img src="../../../../../../../.gitbook/assets/image (236).png" alt=""><figcaption></figcaption></figure>

Enter all your array keys in the window that appears (e.g. if your main variable is “list\_products”, the keys will be characteristics of your products, i.e. the ID, name, price, etc.):

<figure><img src="../../../../../../../.gitbook/assets/image (237).png" alt=""><figcaption></figcaption></figure>

After selecting the “**Two-dimensional array**” type for your variable go to the “**EDIT**” step. Click the symbol appearing to the left of the variable that you just mapped:

<figure><img src="../../../../../../../.gitbook/assets/image (231) (1).png" alt=""><figcaption></figcaption></figure>

Enter the array key in the configuration window (e.g. the product ID) and the separator:

<figure><img src="../../../../../../../.gitbook/assets/image (239).png" alt="" width="448"><figcaption></figcaption></figure>

You can also use the “**Two-dimensional array**” type to create internal variables that return product keys separated by the symbol of your choice. For more information, go to the “Adding Custom Internal Variables – Builder Mode” article.[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/TWO_DIM_ARRAY_WITH_INTERNAL.png)

<figure><img src="../../../../../../../.gitbook/assets/image (240).png" alt=""><figcaption></figcaption></figure>

### Editing and deleting external variables

You can edit an **external variable** by clicking the “**Edit**” icon and delete it by clicking the trash can. The flag next to the variable’s name will tell you if it is mapped and the tag(s) it is mapped with:

Note: The variables used in a container (to be added to a tag, for example) cannot be deleted, and their names cannot be modified.

<figure><img src="../../../../../../../.gitbook/assets/image (243).png" alt=""><figcaption></figcaption></figure>

By clicking on the flag, you will see which container(s), tag(s) or rule(s) use this variable:

<figure><img src="../../../../../../../.gitbook/assets/image (241) (1).png" alt=""><figcaption></figcaption></figure>
