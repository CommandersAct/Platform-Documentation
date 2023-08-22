# Data layer and data types

The data layer represents all your available data. It consists of **information about your site** (e.g. page name, product ID) **and your visitors** (e.g. user ID, customer status) in the form of **JavaScript variables**.

<figure><img src="../../../../../../../.gitbook/assets/image (223).png" alt="" width="271"><figcaption></figcaption></figure>

These variables have two uses:

– To populate the tags present in your container;

– To create activation rules for your tags.

Additional information:

The data layer can consist of two types of data:

– Data implemented by your IT department or your technical provider for all your web pages, based on the CSS, Backoffice and CRM. These data are called “**external variables**” and are displayed in your site’s source code as a **JavaScript object** containing all the variables used by your tags.

This is what the external variables look like in the source code:



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

– Data created in the interface by **Commanders Act staff** or **Commanders Act** users based on information available on the site’s pages (URL, cookies, HTML tags, external variables in the data layer, etc). They are called “**internal variables**” and are displayed in the **Commanders Act** **web container’s code**.
