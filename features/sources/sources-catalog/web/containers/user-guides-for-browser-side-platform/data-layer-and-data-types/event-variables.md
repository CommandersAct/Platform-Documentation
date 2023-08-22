# Event variables

**Event variables** are the variables present in **Commanders Act browser-side events**. They are used primarily for tracking **user actions** (button clicks, links, etc.).

Event variables are useful if you want to send data specific to an event without having these data on your site pages as external variables.

Example: you wish to assign an event for the “**Send**” button on your form. The **event variables** could be the user’s last name, first name, email address and telephone number. These are data that are not available when the page is loaded; it only becomes available after the user has completed the fields on the form and clicked “Send”.

Event variables must be added in the Commanders Act interface before they can be used, and only for events, not tags.

**Event variables** must be created in the Commanders Act interface before they can be used in an event. See the “Adding event variables” article to find out how to create an event variable in the interface.

All event variables created can be used:

* To add information to the solutions embedded in Commanders Act (linking event variables and solutions is called mapping). See the “Mapping Tags’ Variables” article to find out how to **map** your variables in an event.
* To create activation rules for your events. See the “Adding Rules” section to find out how to create rules based on your event variables.

Additional information

**Event variables** must be implemented in the Commanders Act event function (**tC.events**).

Note: External variables that are already available on the page do not need to be implemented in your event. For example, you **do not** need to assign a “country” variable to an event if this information is **already** **present** in an **external variable**.

Here is an example of an event variable:

```
<a onclick="addtocart(0);{tC.event.addtocart(this, {'productID':123, 'user_email':'john@mail.com'})}">Add to cart</a>
```

## When to add an event variable

There are two situations in which you may need to declare your variables in the event variable management interface:

* &#x20;You want to implement Commanders Act events on a new site. The variables that your technical staff or technical provider implement in the site’s source code (in the tC.events function) must be declared in the interface first in order to be available to be added to your tags and rules.
* Variables are for your current event functions are missing or you want to add a new event to your site. Again, this variable must be declared in the interface first before it can be used in your tags and rules.

## Adding event variables

To add an event variable, you must go to the  "**Data Management**” > "**Web Datalayer**" > “**Event Variables**” and click “**ADD VARIABLE**”:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/ADD\_EVENT\_VAR.png)

<figure><img src="../../../../../../../.gitbook/assets/image (261).png" alt=""><figcaption></figcaption></figure>

The “**add**” window consists of the following elements:

<figure><img src="../../../../../../../.gitbook/assets/image (262).png" alt=""><figcaption></figcaption></figure>

“**Name**“: the variable’s name (mandatory field)

“**Type**“: the variable’s type

“**Description**“: A description of the variable, to clarify its name (e.g. “Page template” can be the description of the variable named “env\_template”)

“**Detailed description**“: A detailed description of the variable, to further clarify tits name (e.g. “possible values: homepage/category/product/funnel\_confirmation” can be the detailed description of the “env\_template” variable)

## Editing or deleting variables

You can edit an internal variable by clicking the “**Edit**” icon and delete it by clicking the “**X**”:

<figure><img src="../../../../../../../.gitbook/assets/image (263).png" alt=""><figcaption></figcaption></figure>
