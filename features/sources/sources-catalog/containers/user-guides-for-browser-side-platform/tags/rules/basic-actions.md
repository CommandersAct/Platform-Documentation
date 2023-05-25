# Basic actions

## Summary of rules for tags and events

You can use the “**Summary**” interface to assign previously created rules directly to the new tags you want to add to the container:

<figure><img src="../../../../../../../.gitbook/assets/image (15) (3).png" alt=""><figcaption></figcaption></figure>

By **default**, a newly added tag is called on the **container loaded** trigger, on **all pages**, with **no constraints**.

You can use this interface to add perimeters and constraints alerady created to tags or events added afterwards or modify them from the “**Summary**” interface:

* To add a **perimeter** to a tag, you must check the box where the tag line and the perimeter column intersect.\
  You can also delete a tag’s perimeter(s) by checking the green “**All** **pages**” column. The tag will now activate on all pages.
* To add a **constraint** to a tag, click edit button (pencil icon) close to the triggers and use the existing constraints list to select those you wish to add to your tag.

Additional information:

You can add multiple triggers, perimeters and constraints to the same tag:

* The “**OR**” logic operates when multiple triggers are added to a tag. For example, if you check the “Container loaded” and “add to cart button” triggers, your tag will activate in one case **OR** the other, i.e. on the container loaded and at the click on the button.
* The “**OR**” logic operates when multiple perimeters are added to a tag. For example, if you check the “homepage” and “account creation page” perimeters, your tag will activate in one case **OR** the other, i.e. for the homepage and the account creation page.
* The “**AND**” logic operates when multiple constraints are added to a tag. For example, if you check the “logged user” and “mobile exclusion” constraints, your tag will activate only if the two conditions are met, i.e. only for logged users **AND** everything except a mobile device.
* The “**AND**” logic operates when a trigger, a perimeter and a constraint are added to the same tag. For example, if you check the “container loaded” trigger, the “homepage” perimeter and the “logged user” constraint, your tag will activate only if the three rules are valid, i.e. only at the container loaded AND on the homepage AND logged visitors.

## Adding rules

You can add 3 types of rules: **constraint**, **perimeters** and **triggers.**

* **Perimeters** are the **page types** you want to activate your tags for (example: the homepage, “my account” page, product page, etc.).
* **Constraints** are rules based on criteria other than the page type (example: rules based on visitor status, the type of browser or device, etc.).
* **Triggers** are rules allowing to execute tags on different conditions: container loaded, DOM Ready, clicks, form submissions, scroll and custom events.

To create a new trigger, click “**Trigger**” > “**ADD TRIGGER**”:

<figure><img src="../../../../../../../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

To create a new perimeter, click “**Perimeters**” > “**ADD PERIMETER**”:

<figure><img src="../../../../../../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

To create a new constraint, click “**Constraints**”> “**ADD TAG CONSTRAINT**”:

<figure><img src="../../../../../../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

By clicking “**Add** **trigger**” a rule creation interface will appear. This interface allows you to create a trigger of your choice: container loaded, DOM ready, click, form submission, scroll and custom.

<figure><img src="../../../../../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

By clicking “**Add** **perimeter**” or “**Add** **tag** **constraint**“, a rule creation interface will appear. This interface can be seen as a “tool box” that allows you to create rules based on various elements: cookies, data layer variables, URLs, etc.

The “tools” available to you can be selected at the top of the rules creation interface, and various options allow you to create the most appropriate rule for your tag. For each new rule created, make sure to complete the “**Name**” field (rule name), check the boxes of the tags to which the rule applies and configure the rule.

<figure><img src="../../../../../../../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

Note: The perimeter and constraint creation interfaces offer the same options, but in the constraint creation interface you need to link the constraint to a specific trigger:

<figure><img src="../../../../../../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

## Modifying a rule

To modify a rule, click the “**edit**” icon (pencil icon).

<figure><img src="../../../../../../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

Note: you can modify the rule’s name and value. However, you must create a **new** rule if you wish to **change** its **type**: if you want to replace the “If Variable Equals” rule with “If Variable Is not Equal”.

## Deleting a rule

To delete a rule, click the “**trash**” icon (garbage bin icon):

<figure><img src="../../../../../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Note: your rule will be saved in the trash, where you can recover or permanently delete it at any time:\


<figure><img src="../../../../../../../.gitbook/assets/image (4) (6).png" alt=""><figcaption></figcaption></figure>
