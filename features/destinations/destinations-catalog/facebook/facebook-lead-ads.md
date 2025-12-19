# Facebook Lead Ads



[Facebook ](https://www.facebook.com/)is an online social media and social networking service owned by [Meta](https://www.meta.com/).\
This destination leverages [Conversions API](https://developers.facebook.com/docs/marketing-api/guides/lead-ads/v2.3/#conversions-api-integration) to help you get improved performance in [lead ads](https://developers.facebook.com/docs/marketing-api/guides/lead-ads/v2.3/) by sharing your CRM data about your leads back to Meta to unlock quality lead optimization.

## Key features

The Facebook Lead Ads destination provides the following key features:

* **Events structure**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) leverages [Facebook events](https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration/crm-integration/3-implementing-the-crm-integration#step-1--build-a-payload), meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.

## Destination setup

{% hint style="warning" %}
Integrating your CRM is required and documented following the [Plan Your Project Timeline](https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration#plan-your-project-timeline) section via Meta documentation: see [**1: Connecting Your CRM With Lead Ads**](https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration/crm-integration/1-connecting-your-crm-with-lead-ads) and [**2: Getting Started With the CRM Integration**](https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration/crm-integration/2-getting-started-with-integration) for detailed information. This destination covers [**3: Implementing the CRM Integration**](https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration/crm-integration/3-implementing-the-crm-integration) section in the [project](https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration#plan-your-project-timeline).\
Before continuing, you may want to inspect [Check If Your Business Is a Good Fit](https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration#check-if-your-business-is-a-good-fit) section to see if the optimization model can be beneficial to you. Moreover, you need to review [Before you begin](https://developers.facebook.com/docs/marketing-api/guides/lead-ads/v2.3/#before-you-begin) and [Limitations](https://developers.facebook.com/docs/marketing-api/guides/lead-ads/v2.3/#limitations) sections for a checklist of what is needed and current constraints.
{% endhint %}

### Configuration

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Pixel Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your pixel identifier associated with your Conversions API event(s). You can retrieve your pixel identifier by accessing the <a href="https://www.facebook.com/events_manager2/">Events Manager</a>.</td></tr><tr><td><code>Access Token</code></td><td><em><strong><code>Required</code></strong></em><br>You can generate an access token by entering the <a href="https://www.facebook.com/events_manager2/">Events Manager</a>, selecting your pixel, and clicking the "Settings" tab. In the "Conversions API" section, you can click the button "Generate access token".</td></tr><tr><td><code>Lead Event Source</code></td><td><em><strong><code>Required</code></strong></em><br>Set this to the name of the CRM/tool where the leads are coming from (E.g. "Hubspot", "SAP", "Oracle", "Dynamics", "In-house CRM", etc...).</td></tr><tr><td><code>Mapping</code></td><td><em><strong><code>Required</code></strong></em><br>Your mapping between Facebook's events and yours. In <code>Facebook event name</code> , you can set either a <a href="https://developers.facebook.com/docs/meta-pixel/implementation/conversion-tracking#standard-events">standard event</a> or a <a href="https://developers.facebook.com/docs/meta-pixel/implementation/conversion-tracking#custom-events">custom event name</a>. At least one entry is required. More details are available by following this <a href="https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration/crm-integration/3-implementing-the-crm-integration#step-1--build-a-payload">LINK</a>.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | Facebook Events        |
| ---------------------- | ---------------------- |
| `[Any Event]` **\[1]** | `[Any Event]` **\[1]** |

{% hint style="info" %}
**\[1]** See [Mapping](facebook-lead-ads.md#configuration) for more details.
{% endhint %}

## Field mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
Facebook properties are set starting from the path <mark style="color:blue;">`data.0`</mark> .
{% endhint %}

{% hint style="warning" %}
Meta requires at least one property for two of the following four groups:\
1\. <mark style="color:blue;">`ct`</mark> , <mark style="color:blue;">`country`</mark> , <mark style="color:blue;">`st`</mark> , <mark style="color:blue;">`zp`</mark> , <mark style="color:blue;">`ge`</mark> or <mark style="color:blue;">`client_user_agent`</mark> .\
2\. <mark style="color:blue;">`db`</mark> .\
3\. <mark style="color:blue;">`fn`</mark> .\
4\. <mark style="color:blue;">`ln`</mark> .\
Sending additional user information may improve Event Match Quality. More details are available following this [LINK](https://developers.facebook.com/docs/marketing-api/conversions-api/best-practices/).
{% endhint %}

<table><thead><tr><th width="404.6685580062746">Commanders Act Properties</th><th>Facebook Properties</th></tr></thead><tbody><tr><td><code>Facebook event name</code></td><td><code>event_name</code> <strong>[*][1]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>event_time</code> <strong>[*][2]</strong></td></tr><tr><td><code>Lead Event Source</code></td><td><code>custom_data.lead_event_source</code> <strong>[*][3]</strong></td></tr><tr><td><code>Lead Id</code></td><td><code>user_data.lead_id</code> <strong>[4]</strong></td></tr><tr><td><code>partners.facebook.fbc</code></td><td><code>user_data.fbc</code> <strong>[5]</strong></td></tr><tr><td><code>user.email</code></td><td><code>user_data.em</code> <strong>[6]</strong></td></tr><tr><td><code>user.phone</code></td><td><code>user_data.ph</code> <strong>[7]</strong></td></tr><tr><td><code>user.id</code></td><td><code>user_data.external_id</code> <strong>[8]</strong></td></tr><tr><td><code>user.firstname</code></td><td><code>user_data.fn</code> <strong>[9]</strong></td></tr><tr><td><code>user.lastname</code></td><td><code>user_data.ln</code> <strong>[9]</strong></td></tr><tr><td><code>user.birthdate</code></td><td><code>user_data.db</code> <strong>[10]</strong></td></tr><tr><td><code>user.gender</code></td><td><code>user_data.ge</code> <strong>[11]</strong></td></tr><tr><td><code>user.city</code></td><td><code>user_data.ct</code> <strong>[12]</strong></td></tr><tr><td><code>user.state_short</code></td><td><code>user_data.st</code> <strong>[13]</strong></td></tr><tr><td><code>user.country</code></td><td><code>user_data.country</code> <strong>[14]</strong></td></tr><tr><td><code>user.zipcode</code></td><td><code>user_data.zp</code> <strong>[15]</strong></td></tr><tr><td><code>context.device.ip</code></td><td><code>user_data.client_ip_address</code></td></tr><tr><td><code>context.device.user_agent</code></td><td><code>user_data.client_user_agent</code></td></tr></tbody></table>

{% hint style="info" %}
> **\[\*]** Mandatory property.\
> &#xNAN;**\[1]** See [Mapping](facebook-lead-ads.md#configuration) for more details.\
> &#xNAN;**\[2]** If this field is not provided, the current timestamp is used.\
> &#xNAN;**\[3]** Set this to the name of the CRM/tool where the leads are coming from (E.g. <mark style="color:blue;">`Hubspot`</mark> , <mark style="color:blue;">`SAP`</mark> , <mark style="color:blue;">`Oracle`</mark> , <mark style="color:blue;">`Dynamics`</mark> , <mark style="color:blue;">`In-house CRM`</mark> , etc...).\
> &#xNAN;**\[4]** The 15 or 16 digit Facebook generated lead identifier. More details are available following this [LINK](https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration/how-to-find-the-lead-id).\
> &#xNAN;**\[5]** The Meta click identifier. More details are available following this [LINK](https://developers.facebook.com/docs/marketing-api/conversions-api/parameters/fbp-and-fbc).\
> &#xNAN;**\[6]** User email in lowercase, without spaces and hashed via SHA256. If this is passed in clear text, it's automatically hashed.\
> &#xNAN;**\[7]** User phone number: remove symbols, letters, and any leading zeros. Phone numbers must include a country code to be used for matching (E.g., the number <mark style="color:blue;">`1`</mark>  must precede a phone number in the United States). Always include the country code as part of your customers' phone numbers, even if all of your data is from the same country. If this is passed in clear text, it's automatically hashed via SHA256.\
> &#xNAN;**\[8]** User unique identifier for a user in their space and hashed via SHA256, e.g. user\_id, loyalty\_id, etc. If this is passed in clear text, it's automatically hashed.\
> &#xNAN;**\[9]** In lowercase, hashed via SHA256. If this is passed in clear text, it's automatically hashed.\
> &#xNAN;**\[10]** User birthdate given as <mark style="color:blue;">`YYYY-MM-DD`</mark>  or <mark style="color:blue;">`YYYYMMDD`</mark>  and hashed via SHA256. If this is passed in clear text, it's automatically hashed.\
> &#xNAN;**\[11]** User gender, in lowercase, hashed via SHA256. If this is passed in clear text, it's automatically hashed. Accepted values: <mark style="color:blue;">`f`</mark>  (also <mark style="color:blue;">`female`</mark> ) or <mark style="color:blue;">`m`</mark>  (also <mark style="color:blue;">`male`</mark> ).\
> &#xNAN;**\[12]** User city, in lowercase with no punctuation, no special characters, no spaces, and hashed via SHA256. If this is passed in clear text, it's automatically hashed.\
> &#xNAN;**\[13]** User state, in lowercase with no punctuation, no special characters, no spaces, as [2-character ANSI abbreviation code](https://en.wikipedia.org/wiki/Federal_Information_Processing_Standard_state_code), and hashed via SHA256. If this is passed in clear text, it's automatically hashed.\
> &#xNAN;**\[14]** User country as two-character [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2), and hashed via SHA256. If this is passed in clear text, it's automatically hashed.\
> &#xNAN;**\[15]** User zipcode in lowercase, no spaces, no dash (5 digits for US zip codes and use the area, district, and sector format for the UK), and hashed via SHA256. If this is passed in clear text, it's automatically hashed.
{% endhint %}
