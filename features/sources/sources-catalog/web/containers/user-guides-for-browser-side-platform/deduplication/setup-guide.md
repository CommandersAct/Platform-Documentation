# Setup guide

## Prerequisites

Before you begin creating deduplication rules in the interface, you should define the following things and inform your Commanders Act consultant:

* The **digital marketing channels** you wish to include in the configuration of the deduplication interface. Commanders Act allows you to configure natural and paid channels to take into account for the deduplication rules.
* The **“**_**cookie window**_**” (**_**lookback window**_**)** settings you wish to configure for every channel: information on the channels that drove a user to your site are stored in a cookie whose lifetime usually is of 30 days. You can, for example, set it to 15 days for channel A and 30 days for channel B.

Setting deduplication rules is a **two-step** procedure:

1. Defining and configuring channel and sources recognition in the interface.
2. Applying deduplication and other rules to activate tags according to your needs.

/!\ If you wish to track impressions, you need to make sure a Commanders Act subdomain has been created for you and have your account manager confirm that the feature is enabled. Please note that setting up the subdomain and tracking impressions with our pixel is a paid service.

## Defining channels and sources



1.  Go in the menu "Data Management" > "Web Datalayer" > "Deduplication Channels"

    <figure><img src="../../../../../../../.gitbook/assets/image (274).png" alt="" width="256"><figcaption></figcaption></figure>

The Channel Identification menu will open, then

1. Click the ADD CHANNEL button.
2.  Your channel will be displayed afterwards in the channels list.

    <figure><img src="../../../../../../../.gitbook/assets/image (273).png" alt=""><figcaption></figcaption></figure>

When you click “ADD CHANNEL”, a new window will be displayed to allow you to configure a new paid channel (natural channels are set-up by default).

You can configure channels with one or more “channel” parameters and one or more “source” parameters (or no “source” parameters at all).

### Configuring a channel with a single "channel" parameter

1.  In the window that opens after you click “ADD CHANNEL”, enter your new channel’s name (Display, Affiliation, Retargeting, etc) – this is only a label to identify it in the Channel’s list in the interface – and click “ADD CONDITION”.

    <figure><img src="../../../../../../../.gitbook/assets/image (374).png" alt=""><figcaption></figcaption></figure>

In the menu that appears (see below)(2), select the parameter that will store the information defining the channel (there are default parameters such as those used by Google Analytics, AT Internet as well as the possibility to add custom parameters)(2).

Select the condition (whether the value of the parameter matches or doesn’t match the value you are about to enter)(3).

Enter the value that will identify the channel (4). /!\ If a parameter’s value is made of more elements than the one you require, you need to use a star (\*) to indicate what chunk is to be considered. For example, let’s say you only need “Retargeting” in this parameter: utm\_medium=Retargeting-A1B3C3-crt. You need to write “Retargeting\*” (values are case sensitive):

[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/03/C.png)Click ADD (5) on the line of the channel declaration to confirm the creation of the condition.

Click SAVE (6) at the bottom, right-hand corner of the window.

<figure><img src="../../../../../../../.gitbook/assets/image (375).png" alt=""><figcaption></figcaption></figure>

###

### Configuring a channel with a single "channel" parameter and a "source" parameter

1.  In the window that opens after you click “ADD CHANNEL”, enter your new channel’s name (Display, Affiliation, Retargeting, etc) – this is only a label to identify it in the Channel’s list in the interface – and click “ADD CONDITION”.

    <figure><img src="../../../../../../../.gitbook/assets/image (376).png" alt=""><figcaption></figcaption></figure>
2. In the menu that appears, select the parameter that will store the information defining the channel (there are default parameters such as those used by Google Analytics, AT Internet as well as the possibility to add custom parameters).
3. Select the condition (whether the value of the parameter matches or doesn’t match the value you are about to enter).
4. Enter the value that will identify the channel.

/!\ If a parameter’s value is made of more elements than the one you require, you need to use a star (\*) to indicate what chunk is to be considered. For example, let’s say you only need “Retargeting” in this parameter:

utm\_medium=Retargeting-A1B3C3-crt

You need to write “Retargeting\*” (values are case sensitive):

<figure><img src="../../../../../../../.gitbook/assets/image (377).png" alt=""><figcaption></figcaption></figure>

1. Click ADD on the line of the channel declaration to confirm the creation of the condition.
2.  Click the pencil icon next to “Source: Will not be captured” to modify settings for the source to be captured.

    <figure><img src="../../../../../../../.gitbook/assets/image (378).png" alt=""><figcaption></figcaption></figure>
3.  Select the capture method:

    <figure><img src="../../../../../../../.gitbook/assets/image (379).png" alt=""><figcaption></figcaption></figure>

* Taking all: the entire value of the URL parameter containing the source will be captured. For example, if the parameter in the URL is: “?utm\_source=criteo” and you use “Taking all”, all the parameter’s value will be taken. In this case, “criteo”.
*   Splitting: splits the parameter’s value and takes the block you want. For example, if the parameter in the URL is: “?utm\_source=retargeting|criteo|123456&(…)” and you use the setting depicted in the image below, you will obtain “criteo”.

    <figure><img src="../../../../../../../.gitbook/assets/image (380).png" alt=""><figcaption></figcaption></figure>
*   Cutting: cuts a part of the parameter’s value and returns it. For example, if the parameter in the URL is: “?utm\_source=criteo&”, you will obtain “cri” with the setting below.

    <figure><img src="../../../../../../../.gitbook/assets/image (381).png" alt=""><figcaption></figcaption></figure>

1. Select the parameter containing the source that will be captured.
2. Save
3.  Add the channel

    <figure><img src="../../../../../../../.gitbook/assets/image (382).png" alt=""><figcaption></figcaption></figure>

This will allow you to have the tag fire depending on the value of the channel AND the value of the source.

### Configuring a channel with two or more "channel" parameters and a single "source" parameter



1.  In the window that opens after you click “ADD CHANNEL”, enter your new channel’s name (Display, Affiliation, Retargeting, etc) – this is only a label to identify it in the Channel’s list in the interface – and click “ADD CONDITION”.

    <figure><img src="../../../../../../../.gitbook/assets/image (383).png" alt=""><figcaption></figcaption></figure>
2. In the menu that appears, select the parameter that will store the information defining the channel (there are default parameters such as those used by Google Analytics, AT Internet as well as the possibility to add custom parameters).
3. Select the condition (whether the value of the parameter matches or doesn’t match the value you are about to enter).
4. Enter the value that will identify the channel. Repeat these steps for as many possible combinations of parameters/values that could identify a channel. In the example below, if the utm\_medium parameter in the URL takes the values “Retargeting”, “rtg”, “RTG”, **or** “retargeting”, the channel called/labeled “Retargeting” (1) will be recognized.

**/!\\** If a parameter’s value is made of more elements than the one you require, you need to use a star (\*) to indicate what chunk is to be considered. For example, let’s say you only need “Retargeting” in this parameter:

utm\_medium=Retargeting-A1B3C3-crt

You need to write “Retargeting\*” (values are case sensitive):

<figure><img src="../../../../../../../.gitbook/assets/image (384).png" alt=""><figcaption></figcaption></figure>

1.  You can also create conditions based on the “AND” operator. For example: if the UTM\_MEDIUM parameter’s values are “Retargeting” or “rtg” AND the UTM\_CONTENT’s parameter’s value is “email”, then, the Retargeting channel will be recognized (see second screenshot below).

    <figure><img src="../../../../../../../.gitbook/assets/image (385).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../.gitbook/assets/image (387).png" alt=""><figcaption></figcaption></figure>

If you wish to base your conditions on sources too (B), for every condition defining a channel, you will need to select a source.

When everything is setup, click ADD in the bottom, right-hand corner of the window.

### Configuring condition groups with multiple "channel\[s]/source\[s]" combinations

In order to create groups of conditions combining “blocks” made of multiple channel+source parameters, follow the steps in C) (above), according to your needs. When you have created your first “block”, click the “ADD CONDITION GROUP” button to create a new set of parameters to be configured (1).

In the example below, the _Retargeting_ channel will be recognized by the interface when either of the two conditions\* is met.

**\*Condition 1:** if utm\_medium = “retargeting” **or** “rtg” and the source is captured and matches the configured value (said value is configured in the [rules](setup-guide.md#setting-up-deduplication-rules) step).

**OR**

**\*Condition 2:**  if utm\_medium = retargeting **and** utm\_medium = email and the source matches the configured (said value is configured in the [rules](setup-guide.md#setting-up-deduplication-rules) step).

<figure><img src="../../../../../../../.gitbook/assets/image (264).png" alt=""><figcaption></figcaption></figure>

Note:

You can select the default parameters (below) but also enter custom parameters or use the “Advanced” option to add custom JavaScript.

<figure><img src="../../../../../../../.gitbook/assets/image (265).png" alt=""><figcaption></figcaption></figure>

Example of custom parameter:  “gclid” (SEM)

When you connect Google Adwords and Google Analytics, Google allows you to automatically link your two accounts by adding the “gclid” tracking parameter in your URL. This parameter replaces “utm\_source = SEM” and indicates that traffic is SEM-originated. You can use a custom parameter to set this up.

<figure><img src="../../../../../../../.gitbook/assets/image (266).png" alt=""><figcaption></figcaption></figure>

When your channels and source-capturing methods are defined, you will return to the channel list and options.

### Configuring a channel based on MixCommander Tracking

You just need to write the iD values available on Mixcommander side. For each value you have to declare a channel. For example for the channel AFFILIATION, you have to create as many channels as IDs available on the mapping table ("Affiliation", "aff", "affiliate"). That's why it's very important when you create a campaign to use always the same id. Example : chn=affiliation.&#x20;

<figure><img src="../../../../../../../.gitbook/assets/image (267).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../.gitbook/assets/image (268).png" alt=""><figcaption></figcaption></figure>

### Channel prioritization and cookie window configuration

**Channel prioritization**

You can change the order of paid channels and move them up and down according to the priority you want to give to each one of them. Channels are detected in the exact same order they are listed in the interface and do not exclude each other. So, in the event in which two or more conditions are true, the last condition will be taken into account.

For example, if you have two channels (Email Retargeting and Retargeting) configured as below.

**Email Retargeting**

<figure><img src="../../../../../../../.gitbook/assets/image (269).png" alt=""><figcaption></figcaption></figure>

**Retargeting**

<figure><img src="../../../../../../../.gitbook/assets/image (270).png" alt=""><figcaption></figcaption></figure>

The interface will only pay attention to the last condition (if utm\_medium = retargeting) and will ignore the rest.

So if you have channels sharing one or more conditions, it is necessary that you place the channels with the least conditions first and those with the most conditions at the bottom of the queue so that all conditions are taken into consideration.

To reorder the channels, please use the handles to the left of the channel’s label.

<figure><img src="../../../../../../../.gitbook/assets/image (271).png" alt=""><figcaption></figcaption></figure>

**Cookie Window Configuration**

1. You can change the order of paid channels and move them up and down according to the priority you want to give to each one of them.
2. Check this box if the channel considers clicks.
3. Define the lifetime to the cookie storing click information (in number of days).
4. Check this box if the channel considers views.
5. Define the lifetime to the cookie storing views information (in number of days).
6. Define the number of touch points you want to store in the deduplication cookie. You can store no less than ten and no more than 50. The larger the amount of touchpoints, the heavier the cookie’s weight.
7. Enter the keywords for SEO brand identification, the full word or part of if (you can choose between “_contains_” or Regex). Declaring keywords is useful to differentiate branded and unbranded SEO in case one of both should be taken into consideration in the deduplication rules. Since some browsers, such as Google, have ceased to provide keywords – this is referred to as “not provided”-, the branded and unbranded SEO distinction is less complete than it used to be.
8. Add more keywords if necessary.
9. See the list of your keywords and how they are captured.
10. Configure your impression tracking pixel’s URL by replacing Channel with one of the channels you created and source with the desired parameter value.

    <figure><img src="../../../../../../../.gitbook/assets/image (272).png" alt=""><figcaption></figcaption></figure>

/!\ If you wish to track impressions, you need to make sure a Commanders Act subdomain has been created for you and have your account manager confirm that the feature is enabled. Please note that setting up the subdomain and tracking impressions with our pixel is a paid service.

For more information on these fees please contact your account manager. For more information about Commanders Act’s view pixel, please refer to the “Tracking impressions” and “Structure of Commanders Act's impression pixel” articles.

## Setting up deduplication rules

When your channels are defined in the interface and you have specified whether the parameter storing the source of traffic will be considered or not to launch a tag, you will need to go to the “RULES” step in the Commanders Act TMS interface.

Set-up your deduplication rules by following these steps:

1.When on the RULES step, click the “Deduplication” button on the menu to the left.

<figure><img src="../../../../../../../.gitbook/assets/image (275).png" alt=""><figcaption></figcaption></figure>

2.In the new window, click “ADD DEDUPLICATION RULE” to open the rule configuration window. If you click “MANAGE CHANNEL(S)” you will be taken to the Channel Identification interface again\
[\
](https://community.commandersact.com/wp-content/uploads/sites/2/2016/03/S.png)3.When the window opens, select the tag on which you wish to apply a rule from the dropdown menu.Please note: Deduplication is used on confirmation tags only.

4.Select the touchpoint’s position in the customer journey (beginning, end, anywhere).

* First refers to the first touchpoint at the **beginning** of the customer journey (SEM/Google in the illustration below). A rule based on this position would call Google’s tag on the confirmation page and allocate the conversion to it.
* Last refers to the last touchpoint before the conversion, at the **end** of the customer journey (if we consider paid traffic, it would be RETARGETING/Criteo in the image below, and Direct Access overall). A rule based on this position, would call Criteo’s tag on the confirmation page and allocate the conversion to it.
*   Any refers to any place throughout the customer journey (in the example below, all paid traffic solutions contributing to the conversion would be called on the confirmation page. That is Google, Tradedoubler and Criteo).\


    <figure><img src="../../../../../../../.gitbook/assets/image (276).png" alt=""><figcaption></figcaption></figure>

5\. Select the nature of the touch point (click, view or both) you wish to include in your conversion attribution rules. For example, if you wish to consider only clicks, check that box and leave the view box unchecked. If you wish to consider them both, you should check both boxes.

6\. Select your channel(s) (you must declare them first in the Channel Identification section; you can select more than one channel).

7\. Select whether it corresponds or not to your channel.

8.State whether the source is ignored or (if you configured it to be captured in the channel identification interface) not. If not, define if all or only a part of it will be captured and if it has to match or not a certain value.

9.Enter the value of the parameter that will be compared to what was set in the interface, during the channel identification step, when you chose to capture the source.

10\. Click “ADD” to add the rule.

<figure><img src="../../../../../../../.gitbook/assets/image (277).png" alt=""><figcaption></figcaption></figure>

After you create your rules, they will appear in the rules summary.

If your wish to edit a rule, click the pencil icon to the right on the line of each rule. If you wish to delete it, click the trash can.

<figure><img src="../../../../../../../.gitbook/assets/image (278).png" alt=""><figcaption></figcaption></figure>

The rules summary interface has a Deduplication column. A check mark will indicate what tags are deduplicated.

<figure><img src="../../../../../../../.gitbook/assets/image (279).png" alt=""><figcaption></figcaption></figure>

## Adding tags necessary to the proper operation of the deduplication module

In order to enable the deduplication module, you will need to place the “Commanders Act – Get dedup cookie” and “Commanders Act– Reporting Deduplication v1.2” tags inside your container.

**The “Commanders Act – Reporting Deduplication v1.2” tag**

The “Commanders Act – Reporting Deduplication v1.2” tag allows you to collect conversion-related data (order ID and amount) and display it in the “By Tag” and “By Conversion” deduplication reports explained [here](https://community.commandersact.com/en/category/manage/deduplication/deduplication-reports/).

You will then need to go to the tag library and add the tag to the container you placed in the confirmation page(s).

In the “Edit” section, map the “Commanders Act – Reporting Deduplication v1.2” tag with the corresponding variables from your data layer:

* \#TCIDORDER# (mandatory field) must be mapped with the data layer variable that collects the conversion ID (ex: tc\_vars\[“order\_id”]).
*   \#TCAMOUNTORDER# (optional field) must be mapped with the data layer variable that collects the conversion amount (ex: tc\_vars\[“order\_amount”]). Whether you collect the order amounts excluding taxes or all taxes included is your choice.

    <figure><img src="../../../../../../../.gitbook/assets/image (280).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../.gitbook/assets/image (282).png" alt=""><figcaption></figcaption></figure>

In the “Rules” section, add a condition to your “Commanders Act – Reporting Deduplication v1.2” tag to call it only on your website’s confirmation page(s) (“confirmation page” perimeter).

<figure><img src="../../../../../../../.gitbook/assets/image (283).png" alt=""><figcaption></figcaption></figure>

**The “Commanders Act – Get dedup cookie” tag**

_**Important note**: Before adding this tag, you need to make sure that a “commander1.com” subdomain has been added to your account from the “Admin”>”Domain management” interface (only administrators have access to this area). If the subdomain has not yet been created, please contact our support department (support@commandersact.com)._

The “Commanders Act – Get dedup cookie” tag lets you retrieve all the touch points from a user’s customer journey. These touch points are collected on the “commander1.com” subdomain that is associated to your account. This tag is indispensable if you track impressions for your deduplication rules.

Go to the tag library and add the tag to the container you placed in the confirmation page(s).

In the “Edit” section, make sure that the tag does indeed call your “commander1.com” subdomain (scriptElt1.src = “//domain.commander1.com/dg3/”). If it is not the case, please contact our support department ([support@commandersact.com](mailto:support@tagcommander.com)). No additional configuration is required for this tag.

<figure><img src="../../../../../../../.gitbook/assets/image (284).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../.gitbook/assets/image (285).png" alt=""><figcaption></figcaption></figure>

In the “Rules” section, add a condition to your “Commanders Act– Get dedup cookie” tag to call it on all but the conversion page among the conversion funnel pages. This will allow you to retrieve all information stored in the “commander1.com” subdomain (especially impressions) when a user engages in the purchase process. Your tags will thus be called depending on the user touch points that are identified.

<figure><img src="../../../../../../../.gitbook/assets/image (286).png" alt=""><figcaption></figcaption></figure>
