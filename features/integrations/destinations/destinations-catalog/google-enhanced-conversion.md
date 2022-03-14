# Google Enhanced Conversion

Send your conversions to Google Ads in order to improve the accuracy of conversion measurement on your Google Ads account.

By sending first party data from your website to Google, you can supplement your existing conversion tags by allowing to match these conversion data to attribute your campaign conversions to ad events, such as clicks or views.

More details here: [About enhanced conversions](https://support.google.com/google-ads/answer/9888656)

## How to configure Google Enhanced conversion?

On destination overview, click on Add Destination.

Select Google Enhanced Conversion

You will need to fill this information:

### Conversion ID (conversion tracking ID) and Conversion Label

These values can be found on your Google Ads account, **Tools and Settings** menu, select **Measurement / Conversions**.

{% hint style="info" %}
If you don't find this menu, be sure [Expert Mode](https://support.google.com/google-ads/answer/9520605?hl=en) is enabled for your profile to have access to all options.
{% endhint %}

Select the conversion created (or create one) and copy and paste Conversion ID and Conversion Label.

{% hint style="warning" %}
Enhanced Conversion could be only turned on for **website** conversion. \
Select **API** method for the set-up.
{% endhint %}

![](<../../../../.gitbook/assets/Capture d’écran 2022-03-07 à 09.36.45.png>)

![](<../../../../.gitbook/assets/Capture d’écran 2022-03-07 à 09.56.31 (1).png>)

### GCLID and property ID

Google Click ID (GCLID) is a parameter passed in the URL with ad clicks, to identify the campaign and other attributes of the click associated with the ad for ad tracking and campaign attribution. More details [here](https://support.google.com/google-ads/answer/9744275?hl=en#:\~:text=L'ID%20de%20clic%20Google,de%20l'attribution%20des%20campagnes.).

**Retrieve GCLID from**: \
Retrieve GCLID using all available cookies, a selected cookie, or via datalayer field/custom variable.

**Google Analytics Property ID**: \
The GA Tracking ID is a string like "UA-XXXXXX-Y".

