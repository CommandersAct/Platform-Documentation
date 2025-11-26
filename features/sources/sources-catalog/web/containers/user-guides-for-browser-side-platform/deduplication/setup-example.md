# Setup example

## Defining channels and sources

You work with Retargeting solutions and your tracking URLs look like:

* mysite.com?utm\_medium=**RETARGETING**\&utm\_source=**Criteo**
* mysite.com?utm\_medium=**RETARGETING**\&utm\_source=**MyThings**

Where the utm\_medium parameter stores the channel and utm\_source stores the source (namely your partners).

In order to fire only the tag of the partner to whom the sale is attributed, you would need to follow these steps:

**Defining Channels and Sources**

Adding a Channel: click “Add Channel”

<figure><img src="../../../../../../../.gitbook/assets/image (297).png" alt=""><figcaption></figcaption></figure>

Name the channel and add the parameter that will store the value defining Retargeting (Add Condition)

<figure><img src="../../../../../../../.gitbook/assets/image (298).png" alt=""><figcaption></figcaption></figure>

Define the condition (Parameter Match or Not and the comparison value) and specify whether or not the value of the parameter containing the source will be captured (pencil icon).

<figure><img src="../../../../../../../.gitbook/assets/image (299).png" alt=""><figcaption></figcaption></figure>

Select the capture mode of the parameter containing the source (the whole value, or parts of it), then confirm the channel identification condition by clicking ADD.

<figure><img src="../../../../../../../.gitbook/assets/image (300).png" alt=""><figcaption></figcaption></figure>

Save the source-capturing settings and save the Channel configuration (Click “SAVE”).

<figure><img src="../../../../../../../.gitbook/assets/image (301).png" alt=""><figcaption></figcaption></figure>

## Setting up deduplication rules

Now that you have defined the retargeting channel, you can define firing rules for your retargeting tags Criteo and MyThings.

Click the edition tab and go to the Rules step. Once there, click “Deduplication” on the menu to the left.

<figure><img src="../../../../../../../.gitbook/assets/image (302).png" alt=""><figcaption></figcaption></figure>

In the new window, click “ADD DEDUPLICATION RULE” to open the rule configuration window.

When the window opens, select the Criteo OneTag Conversion tag from the dropdown menu (3).

Select “Last” among the options relating to the touch point’s position in the customer journey. This will fire the tag if it is the last paid solution in the customer journey, now you need to define if it is the last paid click, impression or both (4).

Let’s say you want to launch the Criteo OneTag Conversion tag only if it is the last paid click. Select “click” from the options (5).

Select whether it corresponds or not to your channel (6).

Select “RETARGETING” from the dropdown menu. All channels that you have defined will become available in this menu (7).

Select “EQUALS” for the source. When you configured the channel you indicated that the source of traffic (partner) would be captured by “taking all” the value of the “utm\_source” URL parameter. Since your tracking URL for Criteo looks like this:

www.mysite.com?utm\_medium=**RETARGETING**\&utm\_source=**Criteo**

You will need to select “EQUALS”.

Enter the value of the parameter that will be compared to what was set in the interface (“Criteo”) (9)

Click “ADD” to add the rule (10).

<figure><img src="/broken/files/J7GSg0CNqHLgP14eiOqM" alt=""><figcaption></figcaption></figure>

**Repeat** these steps for your **MyThings** Conversion tag.

When both your rules are created, they will appear in the rule summary.

If your wish to edit any of them, click the pencil icon to the right on the line of each rule. If you wish to delete it, click the trash can.

<figure><img src="/broken/files/S54Vo3yN0Mf91gZ8jPnq" alt=""><figcaption></figcaption></figure>

The rules summary interface has a Deduplication column. A check mark will indicate that your two tags are deduplicated.

<figure><img src="../../../../../../../.gitbook/assets/image (306).png" alt=""><figcaption></figcaption></figure>
