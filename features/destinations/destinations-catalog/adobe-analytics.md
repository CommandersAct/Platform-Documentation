# Adobe Analytics

Send events to Adobe Analytics.

Please note that we use the Adobe [Bulk Data Insertion API](https://developer.adobe.com/analytics-apis/docs/2.0/guides/endpoints/bulk-data-insertion/).

### Authentication

We use the Oauth2 authentication process.

Go to _Administration_ / _Connector Credentials_ and click on **Add connector credentials**. \
Select Adobe Analytics.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2022-12-13 à 11.26.33.png" alt=""><figcaption></figcaption></figure>

Enter the Client ID and Client Secret that you can find on your **Adobe Developer Console**.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2022-12-13 à 11.26.55.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/Capture d’écran 2022-12-14 à 10.48.17.png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
Please fill Redirect URL with: \
[https://api-internal.commander1.com/v2/connectors/adobe/callback](https://api-internal.commander1.com/v2/connectors/adobe/callback)

and Redirect URL Pattern with:\
[https://api-internal\\.commandersact\\.com/v2/connectors/adobe/callback](https://api-internal/.commandersact/.com/v2/connectors/adobe/callback)
{% endhint %}
