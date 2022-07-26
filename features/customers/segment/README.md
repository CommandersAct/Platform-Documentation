# Segment

## Segment management

This is where you create, edit and/or delete segments.

1. The first column displays the segments’ names.
2. The second column displays the segments’ technical IDs (present in the “TC AUDIENCE” cookie we use to store information about a segment).
3. The third column shows the percentage of visitors that are included in a segment.
4. The fourth column specifies the associated streams, using this segment.
5. The fifth column shows when was the last time a segment was modified.
6. The sixth column is where you edit or delete a segment, by clicking the pencil or the trash can.

![](<../../../.gitbook/assets/Capture d’écran 2022-04-08 à 09.53.27.png>)

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

![](<../../../.gitbook/assets/image (6) (1) (1) (1).png>)

Then the button 'ADD CONDITION' will appear, and you can define more conditions, including conditions for conversion items, select '**product**':

![](<../../../.gitbook/assets/image (2) (1) (1) (1).png>)

Then, you can easily segment on conversion items:

![](<../../../.gitbook/assets/image (10) (1) (1).png>)
