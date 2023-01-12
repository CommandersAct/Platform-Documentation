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

### Configuration

Click on _Destinations_ / _Add destination_ and select **Adobe Analytics** on the catalog.

Select sources, give a name to the destination and select the environment.

Select the authentication you've just created previously.

Fill the **Adobe Group ID** and **Customer ID Type** coming from your Adobe Analytics account.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2022-12-13 à 14.44.51.png" alt=""><figcaption></figcaption></figure>

#### **Mandatory parameters mapping**

This parameter is mandatory:

* userAgent

You can map corresponding properties or directly enter values.

#### **User id mapping**

At least one of these fields should be filled to identify users.

* visitorID
* marketingCloudVisitorId
* IP address
* CustomerID (CustomerIDType)

<figure><img src="../../../.gitbook/assets/Capture d’écran 2022-12-13 à 14.45.42.png" alt=""><figcaption></figcaption></figure>

#### Page identifier mapping

Adobe web page identifier. You can set several, but at least one is needed for the export. If you set either linkName, linkURL or linkType the other two must be set as well.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2022-12-13 à 14.46.02.png" alt=""><figcaption></figcaption></figure>

#### Mapping

You can map here all your event properties to Adobe Analytics properties, especially eVars.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2022-12-13 à 14.46.32.png" alt=""><figcaption></figcaption></figure>

#### Properties transformation

This step is optional, you can transform your properties before to send it.
