# Realytics

Realytics helps you measuring the impact of TV/radio campaigns on digital conversions.\
Using this source, you can add TV touch points to customer journeys being able to to measure the contribution of TV to their conversions from within MixCommander.

## Setup

1. Access your [Commanders Act account](https://platform.commandersact.com/).
2. Add Realytics "Default tag".
3. Configure your tag.
4. Test and deploy your container.

## Add Realytics "Default tag"

From the "**INTEGRATIONS**" side menu, expand`(1)`"**Sources**" and select `(2)`"**Web containers**".

![Select "Sources" and "Web containers".](../../../.gitbook/assets/realytics\_1.png)

Select a "Web" container and, from the step `(3)`"**SELECT**" (or "EDIT"), click on `(4)`"**Add Tag(s)**".

![Click on "Add Tag(s)".](../../../.gitbook/assets/realytics\_2.png)

Search for the tag "**Realytics V2 - Default Tag**" and add it to your container. You can now proceed with its configuration.

![Tag template "Realytics V2 - Default Tag".](<../../../.gitbook/assets/realytics\_3 (1).png>)

## Configure your tag

Start by adding `(5)` "**Customer Key**" which is your unique identifier as provided by Realytics.\
Set the `(6)` "**Sync User**" with your desired value: this can be either "true" or "false" (without quotes) and input the `(7)` "**Metric Name**" (also know as "Conversion Action") that you want to track. Lastly, fill two specific fields related to your entered metric: `(8)` "**Transaction Amount**" and `(9)` "**Transaction Order Id**".

![Tag template "Realytics V2 - Default Tag": configuration.](../../../.gitbook/assets/realytics\_3.png)

Under "**RULES**", select `(10)` a "**Privacy Category**". This will link your tag with the explicit user consent for the selected category.

![Select a "Privacy Category" to link your tag.](../../../.gitbook/assets/realytics\_5.png)

{% hint style="info" %}
If your website adopts virtual pages, you need to add a trigger for when these pages are loaded. This can be done under the top section "TRIGGER(S)".
{% endhint %}

This completes your configuration. You can now start the testing phase, leading to the final deployment in production.

{% hint style="info" %}
**Documentation in progress**
{% endhint %}
