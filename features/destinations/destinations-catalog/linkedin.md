# LinkedIn

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[LinkedIn](https://www.linkedin.com/) is a business and employment-focused social media platform.\
Using this destination you can stream conversion events to LinkedIn through their [Conversions API](https://learn.microsoft.com/en-us/linkedin/marketing/integrations/ads-reporting/conversions-api?view=li-lms-2023-11\&tabs=http#streaming-conversion-events).

## Key features

The LinkedIn destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model matches [Linkedin's conversion rules](https://learn.microsoft.com/en-us/linkedin/marketing/integrations/ads-reporting/conversions-api?view=li-lms-2023-07\&tabs=curl#create-a-conversion-rule), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.&#x20;

## Destination setup

{% hint style="info" %}
In order to set the optional "Smart Mapping" field<mark style="color:blue;">`Linkedin UUID`</mark>or the related cookie <mark style="color:blue;">`li_fat_id`</mark>, advertisers need to enable enhanced conversion tracking from [Campaign Manager](https://www.linkedin.com/help/lms/answer/a423304/enable-first-party-cookies-on-a-linkedin-insight-tag). This activates first party cookies that append a click identifier parameter ("li\_fat\_id") to the click URLs. Refer [Enabling Click Ids](https://learn.microsoft.com/en-us/linkedin/marketing/conversions/enabling-first-party-cookies?view=li-lms-2023-11) for implementation details.&#x20;
{% endhint %}

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Conversion Rule Id</code></td><td><p><em><strong><code>Required</code></strong></em></p><p>The conversion rule identifier is generated after creating a <a href="https://learn.microsoft.com/en-us/linkedin/marketing/integrations/ads-reporting/conversions-api?view=li-lms-2023-07&#x26;tabs=curl#create-a-conversion-rule">conversion rule</a>. You can retrieve the identifier by following this instruction <a href="https://learn.microsoft.com/en-us/linkedin/marketing/integrations/ads-reporting/conversions-api?view=li-lms-2023-07&#x26;tabs=curl#find-conversion-rules-by-ad-account">LINK</a> (See field "id"). Its value is set in the following string, by replacing the bold part: "urn:lla:llaPartnerConversion:<strong>ID</strong>".</p></td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | LinkedIn Tracking                |
| ---------------------- | -------------------------------- |
| `[Any Event]` **\[1]** | `[Any Conversion Rule]` **\[2]** |

{% hint style="info" %}
**\[1]** Use [**Destination filters**](https://doc.commandersact.com/features/destinations/destination-filters) to specify your matching events.\
**\[2]** See<mark style="color:blue;">`Conversion Rule Id`</mark>in [Configuration](linkedin.md#configuration) for more details.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.
{% endhint %}

{% hint style="warning" %}
At least one of the following statement must be fulfilled:\
• The "Smart Mapping" field<mark style="color:blue;">`User Email SHA256`</mark>is set with value.\
• The "Smart Mapping" field<mark style="color:blue;">`Linkedin UUID`</mark>is set with a value or the cookie <mark style="color:blue;">`li_fat_id`</mark>is available and set.\
• The "Smart Mapping" field<mark style="color:blue;">`LiveRamp ACXIOM Id`</mark>is set with a value.\
• The "Smart Mapping" field<mark style="color:blue;">`Oracle MOAT Id`</mark>is set with a value.\
• Both "Smart Mapping" fields<mark style="color:blue;">`User First Name`</mark>and<mark style="color:blue;">`User Last Name`</mark>are set with  values.\
More details are available following this [LINK](https://learn.microsoft.com/en-us/linkedin/marketing/integrations/ads-reporting/conversions-api?view=li-lms-2023-11\&tabs=http#input-data-validation).
{% endhint %}

<table><thead><tr><th width="341.6685580062746">Commanders Act Properties</th><th>LinkedIn Properties</th></tr></thead><tbody><tr><td>"urn:lla:llaPartnerConversion:" + <code>Conversion Rule Id</code></td><td><code>conversion</code> <strong>[*]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>conversionHappenedAt</code> <strong>[*]</strong></td></tr><tr><td><code>value</code></td><td><code>conversionValue.amount</code></td></tr><tr><td><code>currency</code></td><td><code>conversionValue.currencyCode</code></td></tr><tr><td><code>context.event_id</code></td><td><code>eventId</code> <strong>[1]</strong></td></tr><tr><td><p><code>user.email_sha256</code></p><p><code>partners.linkedin.uuid</code></p><p><code>partners.linkedin.acxiom_id</code></p><p><code>partners.linkedin.moat_id</code></p></td><td><code>user.userIds.X.idValue</code> <strong>[2]</strong></td></tr><tr><td><p><code>(user.email_sha256</code></p><p><code>partners.linkedin.uuid</code></p><p><code>partners.linkedin.acxiom_id</code></p><p><code>partners.linkedin.moat_id)</code></p></td><td><code>user.userIds.X.idType</code> <strong>[3]</strong></td></tr><tr><td><code>user.firstname</code></td><td><code>user.userInfo.firstName</code></td></tr><tr><td><code>user.lastname</code></td><td><code>user.userInfo.lastName</code></td></tr><tr><td><code>user.country</code></td><td><code>user.userInfo.countryCode</code></td></tr><tr><td><code>user.title</code></td><td><code>user.userInfo.title</code></td></tr><tr><td><code>user.company_name</code></td><td><code>user.userInfo.companyName</code></td></tr></tbody></table>

{% hint style="info" %}
**\[\*]** Mandatory property.\
**\[1]** The unique id generated by advertisers to indicate each event. This is used for deduplication. More details are available following this [LINK](https://learn.microsoft.com/en-us/linkedin/marketing/conversions/deduplication?view=li-lms-2023-11).\
**\[2]** If a clear text user email is provided, it's automatically hashed via SHA256.\
The "Smart Mapping" field<mark style="color:blue;">`Linkedin UUID`</mark>has priority over the cookie <mark style="color:blue;">`li_fat_id`</mark>.\
**\[3]** Depending on the value being set in<mark style="color:blue;">`user.userIds.X.idValue`</mark>, this is one of the following strings:<mark style="color:blue;">`SHA256_EMAIL`</mark>, <mark style="color:blue;">`LINKEDIN_FIRST_PARTY_ADS_TRACKING_UUID`</mark>, <mark style="color:blue;">`ACXIOM_ID`</mark>or<mark style="color:blue;">`ORACLE_MOAT_ID`</mark>. More details are available following this [LINK](https://learn.microsoft.com/en-us/linkedin/marketing/integrations/ads-reporting/conversions-api?view=li-lms-2023-11\&tabs=http#idtype).
{% endhint %}
