# Google Search Ads 360 Enhanced Conversions

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Google](https://about.google/) is a multinational technology company focusing on online advertising, search engine technology, cloud computing, and computer software. Taking advantage of the [Campaign Manager 360 offline conversion API](https://developers.google.com/doubleclick-advertisers/guides/conversions\_ec), you can leverage the "Enhanced Conversions" feature to send first-party data, while also giving the option to modify quantity and value, in the form of [conversion batch updates](https://developers.google.com/doubleclick-advertisers/rest/v4/conversions/batchupdate).

{% hint style="warning" %}
The "Enhanced Conversions" (EC) in Campaign Manager 360 (CM360) API is a hybrid solution with API, which is covered by this destination, and client-side tag: See our  template tag <mark style="color:blue;">gtag - Google SA360 - Floodlight for server-side Enhanced Conversions</mark> for more details. Google still requires Floodlight tags to get conversion info from advertisers' websites.&#x20;
{% endhint %}

{% hint style="warning" %}
Google recommends triggering [conversion batch updates](https://developers.google.com/doubleclick-advertisers/rest/v4/conversions/batchupdate) **between 90 minutes and 24 hours**, with the latter being the upper time limit, after the client-side Floodlight tag is fired to maximize EC matching. After **30 minutes** has passed since the client-side Floodlight is fired, you can already trigger [conversion batch updates](https://developers.google.com/doubleclick-advertisers/rest/v4/conversions/batchupdate), but it's suggested to follow Google reccomandation as reported above. More details are available following this [LINK](https://developers.google.com/doubleclick-advertisers/guides/conversions\_ec#recommended\_setup).
{% endhint %}

## Destination setup

Before configuring this destination, you need to fullfil the following requirements:&#x20;

{% hint style="info" %}
### Accept ToS

Log in to the CM360 account and choose the advertiser you want to implement EC with. On the left, open the menu <mark style="color:blue;">`Floodlight`</mark> ➜ <mark style="color:blue;">`Configuration`</mark>, and flag the checkbox under the <mark style="color:blue;">`Enhanced conversions`</mark> section:\
\
![](../../../../.gitbook/assets/sa360ec\_1.png)\
\
CM360 users of agency admin and DC account manager roles should be able to accept the ToS. Note that accepting the ToS can also be done in the previous version of Search Ads 360 (SA360), but only if the CM360 advertiser controlling the floodlight configuration is linked to a SA360 advertiser. In that case, the ToS can be accepted in the linked advertiser under <mark style="color:blue;">`Advertiser Settings`</mark> ➜ <mark style="color:blue;">`Advertiser Details`</mark> ➜ <mark style="color:blue;">`Enhanced conversions`</mark>:\
\
![](../../../../.gitbook/assets/sa360ec\_2.png)\


### Enrich you Floodlight client-side tag

Ensure that both [**match\_id**](https://support.google.com/campaignmanager/answer/7554821?hl=en#custom\&zippy=%2Ccustom-fields) and [**transaction\_id**](https://support.google.com/campaignmanager/answer/7554821?hl=en#zippy=%2Cfields-in-the-event-snippet---overview) fields are properly set. \
If you're setting up your client-side tag for the first time, you may want to use our template tag <mark style="color:blue;">gtag - Google SA360 - Floodlight for server-side Enhanced Conversions</mark>.
{% endhint %}

### Configuration

<table><thead><tr><th width="344">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Floodlight Configuration Id</code></td><td><em><strong><code>Required</code></strong></em><br>Floodlight configuration identifier of the related conversion. More details are available following this <a href="https://developers.google.com/doubleclick-advertisers/rest/v4/Conversion">LINK</a>. <strong>[1]</strong></td></tr><tr><td><code>Floodlight Activity Id</code></td><td><em><strong><code>Required</code></strong></em><br>Floodlight activity identifier of the related conversion. More details are available following this <a href="https://developers.google.com/doubleclick-advertisers/rest/v4/Conversion">LINK</a>. <strong>[1]</strong></td></tr><tr><td><code>Match Id</code></td><td><em><strong><code>Required</code></strong></em><br>A unique advertiser created identifier also to be passed in the client-side Floodlight. More details are available following this <a href="https://support.google.com/campaignmanager/answer/7554821?hl=en#custom&#x26;zippy=%2Ccustom-fields">LINK</a> (See field name "match_id").</td></tr><tr><td><code>Total Quantity</code></td><td>Flag this option to consider the total quantity instead of the number of unique products.</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** To find both values you can log into the CM360 account, and select the advertiser, then locate the <mark style="color:blue;">`Floodlight`</mark> tab in the left panel. Open <mark style="color:blue;">`Floodlight`</mark> ➜ <mark style="color:blue;">`Activities`</mark> and find/create the activity you are using to receive the EC data. Values being shown, highlighted in green below, are`(1)`<mark style="color:blue;">`Floodlight Configuration Id`</mark>`(2)`<mark style="color:blue;">`Floodlight Activity Id`</mark>:\


![](<../../../../.gitbook/assets/sa360ec\_3 (1).png>)
{% endhint %}

## Quick reference

| Commanders Act Events  | Google Tracking API       |
| ---------------------- | ------------------------- |
| `[Any Event]` **\[1]** | `conversions.batchupdate` |

{% hint style="info" %}
**\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
All Google properties on the right column are set in the object <mark style="color:blue;">`conversions.0`</mark>.
{% endhint %}

<table><thead><tr><th width="362.6685580062746">Commanders Act Properties</th><th>Google Properties</th></tr></thead><tbody><tr><td><code>Floodlight Configuration Id</code></td><td><code>floodlightConfigurationId</code> <strong>[*][1]</strong></td></tr><tr><td><code>Floodlight Activity Id</code></td><td><code>floodlightActivityId</code> <strong>[*][1]</strong></td></tr><tr><td><code>Match Id</code></td><td><code>matchId</code> <strong>[*][1]</strong></td></tr><tr><td><code>context.event_timestamp</code> * 1000</td><td><code>timestampMicros</code> <strong>[*]</strong></td></tr><tr><td><code>id</code></td><td><code>ordinal</code> <strong>[*]</strong></td></tr><tr><td><code>value</code></td><td><code>value</code> <strong>[*]</strong></td></tr><tr><td><p><code>items.length</code></p><p><code>items.X.quantity</code></p></td><td><code>quantity</code> <strong>[*][2]</strong></td></tr><tr><td><code>user.email_sha256</code></td><td><code>userIdentifiers.0.hashedEmail</code> <strong>[3]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>userIdentifiers.0.hashedPhoneNumber</code> <strong>[3]</strong></td></tr><tr><td><code>user.firstname</code></td><td><code>userIdentifiers.0.addressInfo.hashedFirstName</code> <strong>[3]</strong></td></tr><tr><td><code>user.lastname</code></td><td><code>userIdentifiers.0.addressInfo.hashedLastName</code> <strong>[3]</strong></td></tr><tr><td><code>user.street</code></td><td><code>userIdentifiers.0.addressInfo.hashedStreetAddress</code> <strong>[3]</strong></td></tr><tr><td><code>user.city</code></td><td><code>userIdentifiers.0.addressInfo.city</code></td></tr><tr><td><code>user.state</code></td><td><code>userIdentifiers.0.addressInfo.state</code></td></tr><tr><td><code>user.country</code></td><td><code>userIdentifiers.0.addressInfo.countryCode</code></td></tr><tr><td><code>user.zipcode</code></td><td><code>userIdentifiers.0.addressInfo.postalCode</code></td></tr><tr><td><code>partners.google.non_personalized_ad</code></td><td><code>nonPersonalizedAd</code></td></tr><tr><td><code>partners.google.child_directed_treatment</code></td><td><code>childDirectedTreatment</code></td></tr><tr><td><code>partners.google.limit_ad_tracking</code></td><td><code>limitAdTracking</code></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** See [Configuration](google-search-ads-360-enhanced-conversions.md#configuration) for more details on these mandatory properties.\
**\[2]** See [Configuration ](google-search-ads-360-enhanced-conversions.md#configuration)(<mark style="color:blue;">`Total Quantity`</mark>) for more details.\
**\[3]** Automatically normalized and hashed if passed in clear.&#x20;
{% endhint %}
