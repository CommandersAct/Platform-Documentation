# Javascript block

## Adding static JavaScript code

Commanders Act allows you to include “free” JavaScript in the tag container, with no character limit, in two places named “Static JavaScript Code”.

The “Static JS codes” allow you to perform different types of actions, notably:

–  Fixing data layer issues.

E.g. If your external variable “page\_name” contains values with special characters, you can delete or replace them in the Static JavaScript code (e.g. change “&” into “and” as follows:

<figure><img src="../../../../../../.gitbook/assets/image (39) (1).png" alt=""><figcaption></figcaption></figure>

Thus, you can continue to use your external variable “page\_name” in tags by removing its special characters via the Static JS code.

– Recovering data absent in the data layer from the site pages’ source code.

E.g. You can recover JQuery form fields in your Static JS block in the following manner:

<figure><img src="../../../../../../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>

The “Static JS codes” appear in two places in the left menu of the “EDIT” step interface:

–  The first Static JS code is placed before the declaration of internal variables in the order that elements in your site’s container are executed.

–  The second Static JS code is placed after the declaration of the internal variables (you can thus reuse previously declared internal variables in this position):

<figure><img src="../../../../../../.gitbook/assets/image (2) (4).png" alt=""><figcaption></figcaption></figure>

The same user interface is used for the Static JavaScript code regardless of whether it executes before or after the internal variables. Just enter the JavaScript code you desire and click “SAVE”.

## Adding dynamic JavaScript files

Commanders Act allows **dynamic** **JavaScript** file(s) to be included in a tag container, in two places named “**Dynamic** **JavaScript** **File(s)**“.

Unlike “**Static** **JavaScript** **codes**“, “**Dynamic** **JavaScript Files**” are JavaScript files **outside** Commanders Act that are **downloaded** and then **added** or updated in the  container each time it is generated.

The “**Dynamic JavaScript File(s)**” allow you to perform different types of actions.

For example, you can use them to import a JavaScript file containing a **JQuery** library (if it is not already called on your site) or a JavaScript currency converter file into your container. By importing these files into Commanders Act, you can add them to your solutions or use them to create new variables (for example, you can automatically update currencies in your solutions’ tags).

“Dynamic JavaScript File(s)” appear in two places in the left menu of the “**EDIT**” step:

* The **first** Dynamic JavaScript File(s) is placed before the declaration of the internal variables, in the order that the elements of the container on your site are executed.
*   The **second** Dynamic JavaScript File(s) is placed after the declaration of the internal variables (you can thus reuse previously declared internal variables in this position):

    <figure><img src="../../../../../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

The same user interface is used for the Dynamic JavaScript File(s) regardless of whether they execute before or after the internal variables. Just enter the URL of your JavaScript file and click “**SAVE**”.

You can perform this operation again for all the JavaScript files to be included in your tag container.

Caution: adding JavaScript files to the container will **increase** its size and thus increase the time for the pages to load.

You can update your dynamic file **manually** (by clicking “Refresh”), display its contents (“View”) or delete it (“Remove”):\


<figure><img src="../../../../../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>
