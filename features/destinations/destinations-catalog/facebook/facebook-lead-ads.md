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

<table><thead><tr><th width="300">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Pixel Id</code></td><td><em><strong><code>Required</code></strong></em><br>Your pixel identifier associated with your Conversions API event(s). You can retrieve your pixel identifier by accessing the <a href="https://www.facebook.com/events_manager2/">Events Manager</a>.</td></tr><tr><td><code>Access Token</code></td><td><em><strong><code>Required</code></strong></em><br>You can generate an access token by entering the <a href="https://www.facebook.com/events_manager2/">Events Manager</a>, selecting your pixel, and clicking the "Settings" tab. In the "Conversions API" section, you can click the button "Generate access token".</td></tr><tr><td><code>Lead Id</code></td><td><em><strong><code>Required</code></strong></em><br>The 15 or 16 digit Facebook generated lead identifier from your <a href="https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration/crm-integration/1-connecting-your-crm-with-lead-ads">downloaded leads</a>. More details are available by following this <a href="https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration/how-to-find-the-lead-id">LINK</a>.</td></tr><tr><td><code>Lead Event Source</code></td><td><em><strong><code>Required</code></strong></em><br>Set this to the name of the CRM/tool where the leads are coming from (E.g. "Hubspot", "SAP", "Oracle", "Dynamics", "In-house CRM", etc...).</td></tr><tr><td><code>Mapping</code></td><td><em><strong><code>Required</code></strong></em><br>Your mapping between Facebook's events and yours. In <code>Facebook event name</code> , you can set either a <a href="https://developers.facebook.com/docs/meta-pixel/implementation/conversion-tracking#standard-events">standard event</a> or a <a href="https://developers.facebook.com/docs/meta-pixel/implementation/conversion-tracking#custom-events">custom event name</a>. At least one entry is required. More details are available by following this <a href="https://developers.facebook.com/docs/marketing-api/conversions-api/conversion-leads-integration/crm-integration/3-implementing-the-crm-integration#step-1--build-a-payload">LINK</a>.</td></tr></tbody></table>

## Quick reference

| Commanders Act Events  | Facebook Events        |
| ---------------------- | ---------------------- |
| `[Any Event]` **\[1]** | `[Any Event]` **\[1]** |

{% hint style="info" %}
**\[1]** See [Mapping](facebook-lead-ads.md#configuration) for more details.
{% endhint %}

## Field Mappings

{% hint style="info" %}
Most properties can be remapped using our "Smart Mapping" feature.\
Facebook properties are set starting from the path <mark style="color:blue;">`data.0`</mark> .
{% endhint %}

<table><thead><tr><th width="404.6685580062746">Commanders Act Properties</th><th>Facebook Properties</th></tr></thead><tbody><tr><td><code>Facebook event name</code></td><td><code>event_name</code> <strong>[*][1]</strong></td></tr><tr><td><code>context.event_timestamp</code></td><td><code>event_time</code> <strong>[*][2]</strong></td></tr><tr><td><code>Lead Id</code></td><td><code>user_data.lead_id</code> <strong>[*]</strong></td></tr><tr><td><code>Lead Event Source</code></td><td><code>custom_data.lead_event_source</code> <strong>[*]</strong></td></tr></tbody></table>

{% hint style="info" %}
&#x20;**\[\*]** Mandatory property.\
&#x20;**\[1]** See [Mapping](facebook-lead-ads.md#configuration) for more details.\
&#x20;**\[2] I**f this field is not provided, the current timestamp is used.
{% endhint %}
