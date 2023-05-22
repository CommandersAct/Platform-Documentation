# Testing

The “**TEST**” step seeks to prevent problems in production by testing the version of a container and diagnosing its compatibility and reliability.

At first, it will block deployment of the faulty container, but you can ignore some of the errors found, such as those resulting from incompatible JavaScript elements with old versions of browsers (IE8 for example).

A total of 8 browsers/OS are tested:

* The latest version of Edge
* The latest version of Chrome
* The latest version of Firefox
* The latest version of Opera
* The latest version of Safari (for the Mac OS)
* &#x20;The latest version of Safari (for tablets)
* The latest version of Android (for tablets)

Tests are performed on five levels:

* Container: The container’s code (the JavaScript file) is tested globally
* Data layer: The data layer (internal and external variables, etc.) is tested in isolation
* Custom JS blocks: The static and dynamic JavaScript files are tested in isolation
* Tags: All tags are tested, and errors are displayed by tag
* Events: All events are tested, and errors are displayed by event

If no errors are detected, your version is “**DEPLOYABLE”**:

<figure><img src="../../../../../../.gitbook/assets/image (108) (1).png" alt=""><figcaption></figcaption></figure>

If an error is detected in your container, it will be indicated by a red “**X**” under the browser returning the error and on the line of the element  the error was found in (Data layer, Custom JS blocks, Tags, Events); it will also appear on the Container line .

In this case, your container version is “**NOT DEPLOYABLE**” until you correct or ignore the error.

We recommend that you correct the errors detected in the Data layer, Custom JS Blocks, Tags, and Event before correcting the Container errors since the latter will most often disappear after the other four levels are corrected.

To display and correct errors, click on a red “X”.

<figure><img src="../../../../../../.gitbook/assets/image (7) (2).png" alt=""><figcaption></figcaption></figure>

A window will appear displaying the test error details. Below is an example of a possible tag error:

<figure><img src="../../../../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

Error message details returned by the tested browser

Tag name and line number where the error is found. Clicking the button redirects you to the “Edit” step where you can correct your tag’s code directly.

Note: Do not hesitate to contact your personal consultant or the Commanders Act support team (support@commandersact.com) if you need help correcting an error.

Finally, the “**TEST**” step allows you to consult the error history for the different container versions generated. This history is displayed at the bottom of the “Test” page, where you can click the red “**X**“s again to display the error details:

<figure><img src="../../../../../../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

