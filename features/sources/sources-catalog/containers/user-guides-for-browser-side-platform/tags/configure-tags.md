# Configure tags

Once a tag is added, you can configure it in the “**EDIT**” step.

A list of your tags is displayed in the left menu of the “**EDIT**” interface. Tags that need to be configured or validated have a warning (/!\\) sign before their name.

Note: You can find a tag on the list by using the search box :[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/TAG\_CONFIG\_1.png)

<figure><img src="../../../../../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

For each tag selected, a configuration window will appear in the center of the interface containing the following elements:

<figure><img src="../../../../../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

**Expiration**: An expiration date can be applied to the tag

**Tag variable(s)**: Tag variables that need data layer data or static information linked to them

**Tag code**: The selected tag’s code

**Use** **Tag** **Cleaner**: JavaScript correction tool and preview button to see the tag’s code once its variables have been mapped with variables from the datalayer

**Previous** **version(s)**: The tag’s version history;&#x20;

“**delete**” and “**save**” buttons

**Rules**: Shortcut to the tag’s rules configuration

## Expiration date

### Setting expiration on a tag

You can apply a custom **expiration** date to each tag. Check the box to activate this function and then select a date on the calendar or type it in the blank field.

<figure><img src="../../../../../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

When you activate the expiration function, it automatically deactivates the tag into the container on the expiration date selected.

This function is useful if you have added a tag for a specific campaign and you want it to be deactivated once it ends, so that your container is not needlessly overloaded with tags.



## Mapping tags' variables

Important reminder: You must create a link between the information requested by the different tags in the container and the data available in the data layer. Adding data layer variables to tag variables is called “**mapping**“.

The tag variables to map are called “**dynamic variables**“, and they are designated in the following manner: **#variable#**.

They appear in the tag’s code, in blue boldface, as well as above the tag’s code .

You must map these dynamic variables with the data layer variables available in the drop down menus (example: user email, user ID) or a static value (example: method) :[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/MAPPING\_TAGS\_VARS.png)

<figure><img src="../../../../../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

Additional information

If the tag’s code does not meet your needs, you can customize it directly in the “**JAVASCRIPT CODE**” section as well as the “**NOSCRIPT CODE**” section for browsers without JavaScript activated (this function will only work if you call the NOSCRIPT version of the container in your site’s source code):

\


<figure><img src="../../../../../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

You can modify your tag directly by transforming the dynamic variables within the code into data of your choice.

Example:

If you wish to hard code the USER ID, just replace #user\_id# with the value of the ID:\
\
<img src="../../../../../../.gitbook/assets/image (28).png" alt="" data-size="original">          ![](<../../../../../../.gitbook/assets/image (8) (3).png>)



You can also customize your tag’s code by changing the static elements into dynamic variables.

Example:\


If you want to make all the values to be collected in a tag dynamically, simply leave them in between hashtags signs. Then save the tag after making this change and you will be able to map your variable with your data layer data:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/MATCHING.png)

<figure><img src="../../../../../../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

Note: you can modify your tag anytime you want. However, please pay attention to its JavaScript structure: Dynamic elements must be placed between the ## and followed or preceded by a “+” if they are joined with static elements. The colored syntax in the tag code allows you to verify that there are no errors:

<figure><img src="../../../../../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

## Configuring custom tags

A “**Free input (custom)**” tag can be used to add a tag to your container even if it is not listed in the tag library.

To configure your custom tag, just replace the default code in the “**JAVASCRIPT** **CODE**” with the code supplied by your partner solution and click “**SAVE**”.

<figure><img src="../../../../../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

In the vast majority of cases, you will see that your tag is rewritten so that its structure is compatible with that of the container and is called asynchronously. This is also done to prevent errors linked to certain JavaScript data structures such as “document.write”.

Tags are corrected by using the “**Use Tag Cleaner**” feature:

<figure><img src="../../../../../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

Uncheck the “**Use Tag Cleaner**” box if you do not want your tag to be rewritten.

## Returning to a previous tag version

Each time a container is generated, Commanders Act saves the tags present in the container, thus allowing you to return to an old tag configuration if necessary.

You can display previous versions of a particular tag by clicking “**PREVIOUS VERSION(S)**”:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/PREVIOUS\_VERSIONS.png)

<figure><img src="../../../../../../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

The “**PREVIOUS VERSION(S)**” window contains all the saved versions of your tag. The version displayed by default is the previous version of the tag.[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/PREVIOUS\_V\_DETAILS.png)

**Tag version**: number of the last tag version saved, name of the user who generated the version, and the date and time it was generated

“**Rollback**“: button allowing you to return to the tag version displayed

**Tag** **code**: selected tag code (JavaScript or NoScript code depending on the option selected in (3))

**Tag** **versions**: previous versions of the tag

To return to a previous tag version, select the version you want and click “**ROLLBACK**“.

## Applying a rule on the fly

You can add a tag activation rule directly in the “**EDIT**” step.

You have two options:

* You can select a previously created perimeter or constraint by clicking the drop-down menu:\
  \
  &#x20;   <img src="../../../../../../.gitbook/assets/image (48).png" alt="" data-size="original">
* You can create a new perimeter or constraint by clicking “+” ![](<../../../../../../.gitbook/assets/image (13) (2).png>)

The rule creation window will appear so that you can create your rules in the same way as in the “**RULES**” step.

For more information on creating rules, please refer to the [Rules](rules/) section.

### Displaying the summary of tags and associated rules

To display a summary of all the tags present on your site along with their rules, go to the “**REPORTS**” tab > “**Tags’ Summary**“ \*this page is currently accessible only from Platform v7.

<figure><img src="../../../../../../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

You can display the code, rules and expiration date for each tag.

You can also filter the containers or tags that you want to analyze.

This report can be useful for displaying which tags are present on your site at a given time and for sharing this information with others internally. It can also help you find a tag from the list of tags present on your site.

## Saving and removing a tag

Once you have finished configuring your tag, click “**SAVE**” to save your modifications.

You can also delete a tag you do not need any more by clicking “**DELETE**”.

Caution: a deleted tag cannot be recovered.

<figure><img src="../../../../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

## Tags' activation and execution order

To activate or deactivate tags in the “**GENERATE**” step, just check or uncheck each tag in the “**ACTIVATION**” column and generate a new container version (blue button in the upper right-hand side of the screen):[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/MANAGING\_ACTIVATION.png)

<figure><img src="../../../../../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

All checked tags are active and all unchecked tags are inactive. The advantage of deactivating a tag rather than permanently deleting it is that you can keep all the tag parameters (mapping, rules) and reactivate them at a later date without having to reconfigure everything.

Note: Since a deactivated tag will be visible in the interface but not in the container called for your site, your container will not become needlessly cluttered.

To modify the order in which tags are executed in a container in the “**GENERATE**” step, just drag and drop each tag in the “**RANK**” column and place them in the order in which you want them to execute on your site’s pages, and then generate a new container version (blue button in the upper-right hand side of the screen):\


<figure><img src="../../../../../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

We recommend that you place the **most important tags** at the **top** of the container so that they have the best chance of executing if your visitors change pages quickly without waiting for them to fully load.

## Setting a timeout on a tag

To improve your site’s performance, Commanders Act suggests that you deactivate a tag if it takes too long to load. You can enter a maximum duration, in milliseconds, for a tag to execute. If the tag takes longer than this time to execute, it will be deactivated.

To add a timeout to tags in the “**GENERATE**” step, just enter a duration in milliseconds in the “**TIMEOUT MS”** column and generate a new container version:[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/01/TIMEOUT.png)

<figure><img src="../../../../../../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

## Customizing the tag library (whitelisting)

You can customize the tag library by restricting the number of tag templates available in the tag addition popin from the “Select” and “Edit” steps.&#x20;

This “tags whitelist” feature is useful if you wish to limit access to the solutions in the library and only make some of them available to your staff. This aims at preventing users from placing tags you did not authorize into your containers.

The “Library management” interface is accessible to administrators and to custom users this interface was granted access to. The tags whitelist is managed from the “Admin” > “Library management” interface. This page is currently only available on platform v7.

All tags will be selected by default.

You can click the “Unselect all” option and then choose the tags you wish to make available in your library.

<figure><img src="../../../../../../.gitbook/assets/image (14) (4).png" alt=""><figcaption></figcaption></figure>

Select the site you wish to set up the tags white list for from the drop down menu.

You can Check/Uncheck relevant tags.

The “Select all” and “Unselect all” buttons allow you to check or uncheck many tags simultaneously.

You have the possibility to filter tags by name or alphabetical order.

Click the “SAVE” button to save your settings.

**Must know:**

* When a new tag is added to the tag library by Commanders Act’s staff, it is automatically unchecked if you have already created at least one tag whitelist for your site.
* You can copy a tags whitelist from one site to another from the “Administration” > “Copy management” menu.

