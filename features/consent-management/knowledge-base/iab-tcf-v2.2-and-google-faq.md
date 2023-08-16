# IAB TCF V2.2 and Google FAQ



{% hint style="info" %}
Google is a TCF 2.0 member, and Google Ad Manager (GAM), Adsense, and Admob can use the IAB TCF API to get the user consent status (the TC string) from Commanders Act CMP.
{% endhint %}

## How to enable Google ACM Vendors

{% hint style="success" %}
To enable Google ACM vendors go to `Data Governance > Consent Management > Settings` and follow [this instruction ](../user-guides/categories-and-tags/manage-vendors.md)
{% endhint %}

## Common issues encountered while using the TCF 2 to integrate with Google Advertising Products

### GAM's recorded errors

GAM's recorded errors GAM displays an error message in your GAM Console if it is unable to collect a TC string from the CMP:

The specific errors found are detailed in a report, which you can compare to the GAM documentation in the Troubleshooting TCF 2 implementation post.

We've mentioned some of the most common error codes we've seen while integrating with GAM below.

1.x (1.1 or 1.2 or 1.3) : Google is not approved as a vendor regarding consent or legitimate interest. \
**1.x errors are to be anticipated**, **it's normal to expect a certain amount of these errors** as they mean that the user has refused permission for Google, main Google purposes, or that you have publisher restrictions that prohibit Google from running.

{% hint style="info" %}
The rate of negative consent for a given website or mobile app should be approximately matched by the 1.x errors.
{% endhint %}

Checklist for determining why 1.x errors are so common:

1. Verify that your 1.x errors as a percentage of all ad requests are approximately equal to your negative consent rate (within a 5 points margin). For instance, if Commanders Act Consent Analysis reports a 90% consent rate per page view, a typical 1.x error rate is beetween 5% to15%.
2. Examine whether the IAB TCF 2 was implemented on your website or mobile app prior to September 2020.
3. Check to see if there are publisher restrictions. If so, make sure they don't affect Google or do so in a way that's compliant with Google's requirements : [https://support.google.com/admanager/answer/9805023?hl=en](https://support.google.com/admanager/answer/9805023?hl=en).

Errors are found in the following ways:

1.1 Errors: Google is not permitted as a vendor along with consent or legitimate interest.&#x20;

1.2 errors: For EEA countries and the UK, there is no consent for Purpose 1. Before determining whether or not the TC string causes an error, Google will always check whether Purpose 1 has permission before determining whether or not Google, as a vendor, is allowed.&#x20;
