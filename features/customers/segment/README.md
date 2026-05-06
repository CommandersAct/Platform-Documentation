# Segment

## Segment management



The Segment Overview page lists all segments organized into folders. For each segment, the following information is displayed:

* **Name**
* **ID** — public identifier of the segment
* **Labels** — custom tags assigned to the segment
* **Nb users** — audience size (count and percentage of total users)
* **Associated destinations** — destinations fed by this segment
* **Last updated** — date of the last modification

Available actions for each segment: move to another folder, change labels, duplicate, edit conditions, delete.

{% hint style="info" %}
Every segment must belong to a folder. A segment cannot exist outside of a folder.
{% endhint %}

#### Managing folders

Folders are used to organize segments into logical groups. Up to 10 folders can be created per account.

To create a folder, click the folder management button on the Segment Overview page. A side panel opens, listing suggested folders to help structure the segment library (e.g. Value & RFM, Triggers, Technical, Tests). Select a suggested folder or create a custom one.

Each folder has a name and an icon, both of which can be edited at any time.

To delete a folder, it must be empty. Move or delete all segments within it before proceeding.

{% hint style="info" %}
When a segment is deleted, it is removed from its folder. If the segment is restored, a folder must be selected manually.
{% endhint %}

#### Managing labels

Labels are custom tags that can be assigned to segments to facilitate filtering and organization. Up to 20 labels can be created per account, and up to 4 labels can be assigned to a single segment.

Labels can be created from three entry points:

* The label management side panel, accessible from the Segment Overview page
* The actions menu of a specific segment
* The segment creation form

Labels are optional. When creating a new segment, a name and a folder are required; labels can be added at that stage or later.

A label name can be edited at any time. Deleting a label removes it from all segments it was assigned to.

#### Duplicating a segment

A segment can be duplicated directly from the Segment Overview page via the actions menu. Before confirming the duplication, the following fields are pre-filled and can all be modified:

* **Name** — the original segment's name followed by "(copy)"
* **Folder** — the original segment's folder
* **Labels** — the original segment's labels, if any

The duplicate is created with the same conditions as the original.

## How to add multiple values in a segment?

Let’s say, for example, you want to match all users with ZIP code equals ‘75009’ or ‘92120’ or ‘94230’… and you realized you have more than 30 different values!

You can type one zip code per one, but it is long.

Or you can also copy and paste directly your values. However, you should **use a separator** between these values **;** or **|**

{% hint style="warning" %}
Don’t forget to add the separator behind the last value also to paste all your values.
{% endhint %}

{% hint style="warning" %}
You can paste-up to 1024 values in the segment
{% endhint %}

## How to segment on conversion items?

You can segment on conversion items, meaning products bought by users.

First, you have to select '`conversion`' universe and define a condition for conversions, like '`conversion ID exists`' = users have at least 1 conversion.

![](<../../../.gitbook/assets/image (6) (1) (1) (2) (1) (1).png>)

Then the button 'ADD CONDITION' will appear, and you can define more conditions, including conditions for conversion items, select '**product**':

![](<../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)

Then, you can easily segment on conversion items:

![](<../../../.gitbook/assets/image (10) (1) (1).png>)

## How to segment on calculated variables

<figure><img src="../../../.gitbook/assets/image (1) (3) (2).png" alt=""><figcaption></figcaption></figure>

On our storage model, the main universe is **users**, and, attached to this main universe, there are sub universes: **page views, views, clicks, conversions**...

On the segmentation, you can find calculated variables like "count of page view" or "count of conversion", it represents the count of documents in the sub-universe for a specific user. As a result, you can create segments like "all users with count of page view > 10".
