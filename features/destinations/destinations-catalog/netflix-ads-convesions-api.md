---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Netflix Ads Convesions API

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Netflix](https://www.netflix.com/) is a subscription video on-demand over-the-top streaming television service.\
Using this destination you can can leverage Netflix Ads Conversions API (alpha) to send conversion events directly to Netflix for downstream attribution and reporting.

## Key features

The Netflix Ads Conversions API destination provides the following key features:

* **Events structure**: our [Events reference](https://doc.commandersact.com/developers/tracking/events-reference) model meets Netflix's events structure, meaning that your data is properly bridged to the expected fields in an optimized way.
* **Prebuilt mappings**: data mapping for event-based destinations happens automatically, which simplifies user inputs.
* **Automatic hashing**: information is automatically hashed matching partner specifications.
* **Smart mapping**: data mapping can be readjusted using your datalayer defined fields.
* **Event mapping**: change standard mapping between Netflix events and yours.
* **Support batch mode**: send multiple events in one single request.

## Destination setup

Ensure you have access to [Netflix Ads](https://advertising.netflix.com/).

### Configuration

| Settings        | Description                                                                                                                                                                                                                                                                                                                                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Netkey`        | <p><em><strong><code>Required</code></strong></em><br>Your secure token-based authentication mechanism named <code>Netkey</code> as provided by Netflix. Normally they last one year and can be extended by contacting Netflix.</p>                                                                                                                                                                          |
| `Account Id`    | <p><em><strong><code>Required</code></strong></em><br>Your account identifier in <a href="https://advertising.netflix.com/">Netflix Ads</a>.</p>                                                                                                                                                                                                                                                             |
| `Endpoint`      | <p><em><strong><code>Required</code></strong></em><br>Select your endpoint:<br>• <code>Production</code><br>• <code>Staging</code><br>Default: <code>Production</code>.</p>                                                                                                                                                                                                                                  |
| `Event Mapping` | Change the standard mapping between Netflix events and yours or add new mappings. Accepted values for `Netflix event name` : `add_payment_info` , `add_to_cart` , `add_to_wishlist` , `app_install` , `app_open, initiate_checkout, contact, donate, lead, login, page_view, purchase, search, sign_up, start_trial, submit_application, subscribe, view_category, view_content, watch_video, watch_video` . |

## Quick reference

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Commanders Act Events</th><th>Netflix Events</th></tr></thead><tbody><tr><td><code>add_payment_info</code></td><td><code>add_payment_info</code></td></tr><tr><td><code>add_to_cart</code></td><td><code>add_to_cart</code></td></tr><tr><td><code>add_to_wishlist</code></td><td><code>add_to_wishlist</code></td></tr><tr><td><code>app_install</code></td><td><code>app_install</code></td></tr><tr><td><code>app_open</code></td><td><code>app_open</code></td></tr><tr><td><code>begin_checkout</code></td><td><code>initiate_checkout</code></td></tr><tr><td><code>contact</code></td><td><code>contact</code></td></tr><tr><td><code>donate</code></td><td><code>donate</code></td></tr><tr><td><p><code>generate_lead</code></p><p><code>lead</code></p></td><td><code>lead</code></td></tr><tr><td><code>login</code></td><td><code>login</code></td></tr><tr><td><code>page_view</code></td><td><code>page_view</code></td></tr><tr><td><code>purchase</code></td><td><code>purchase</code></td></tr><tr><td><code>search</code></td><td><code>search</code></td></tr><tr><td><code>sign_up</code></td><td><code>sign_up</code></td></tr><tr><td><code>start_trial</code></td><td><code>start_trial</code></td></tr><tr><td><code>submit_application</code></td><td><code>submit_application</code></td></tr><tr><td><code>subscribe</code></td><td><code>subscribe</code></td></tr><tr><td><p><code>view_item_list</code></p><p><code>view_category</code></p></td><td><code>view_category</code></td></tr><tr><td><p><code>view_item</code></p><p><code>view_content</code></p></td><td><code>view_content</code></td></tr><tr><td><p><code>video_start</code></p><p><code>watch_video</code></p></td><td><code>watch_video</code></td></tr><tr><td><code>[Any Event]</code></td><td><code>[Any Netflix Event]</code> <strong>[1]</strong></td></tr></tbody></table>

{% hint style="info" %}
**1.** See <mark style="color:blue;">`Event Mapping`</mark> in [Configuration](netflix-ads-convesions-api.md#configuration).
{% endhint %}

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.
{% endhint %}

<table data-header-hidden="false" data-header-sticky><thead><tr><th>Smart Mapping Fields</th><th width="371">Commanders Act Default Properties</th><th>Netflix Properties</th></tr></thead><tbody><tr><td><code>-</code></td><td><code>event_name</code></td><td><code>event_name</code> <strong>[*][1]</strong></td></tr><tr><td><code>Event Timestamp</code></td><td><code>context.event_timestamp</code></td><td><code>event_time</code> <strong>[*][2]</strong></td></tr><tr><td><code>Action Source</code></td><td><code>partners.netflix.action_source</code></td><td><code>action_source</code> <strong>[*][3]</strong></td></tr><tr><td><code>Page URL</code></td><td><code>context.page.url</code></td><td><code>event_source_url</code></td></tr><tr><td><code>Event Id</code></td><td><code>context.event_id</code></td><td><code>event_id</code></td></tr><tr><td><code>Data Processing Options</code></td><td><code>partners.netflix.data_processing</code></td><td><code>data_processing_options</code></td></tr><tr><td><code>Value</code></td><td><code>value</code></td><td><code>value</code> <strong>[4]</strong></td></tr><tr><td><code>Currency</code></td><td><code>currency</code></td><td><code>currency</code> <strong>[4]</strong></td></tr><tr><td><code>Integration</code></td><td><code>partners.netflix.integration</code></td><td><code>integration</code></td></tr><tr><td><code>User Email</code></td><td><code>user.email</code></td><td><code>email</code> <strong>[5]</strong></td></tr><tr><td><code>User Phone</code></td><td><code>user.phone</code></td><td><code>phone</code> <strong>[5]</strong></td></tr><tr><td><code>First Name</code></td><td><code>user.firstname</code></td><td><code>fn</code> <strong>[5]</strong></td></tr><tr><td><code>Last Name</code></td><td><code>user.lastname</code></td><td><code>ln</code> <strong>[5]</strong></td></tr><tr><td><code>User Address</code></td><td><code>user.street</code></td><td><code>address</code> <strong>[5]</strong></td></tr><tr><td><code>User Gender</code></td><td><code>user.gender</code></td><td><code>ge</code> <strong>[5][6]</strong></td></tr><tr><td><code>User City</code></td><td><code>user.city</code></td><td><code>ct</code> <strong>[5]</strong></td></tr><tr><td><code>User State</code></td><td><code>user.state</code></td><td><code>st</code> <strong>[5][7]</strong></td></tr><tr><td><code>User Postal Code</code></td><td><code>user.zipcode</code></td><td><code>zp</code> <strong>[8]</strong></td></tr><tr><td><code>User Country</code></td><td><code>user.country</code></td><td><code>country</code> <strong>[9]</strong></td></tr><tr><td><code>Device IP</code></td><td><code>context.device.ip</code></td><td><code>client_ip_address</code> </td></tr><tr><td><code>Device Mobile Identifier</code></td><td><code>context.device.advertising_id</code></td><td><code>madid</code></td></tr><tr><td><code>Partner Identifier</code></td><td><code>partners.netflix.partner_id</code></td><td><code>partner_id</code></td></tr><tr><td><code>Application Identifier</code></td><td><code>partners.netflix.app_id</code></td><td><code>app_id</code></td></tr><tr><td><code>Application Name</code></td><td><code>context.app.name</code></td><td><code>app_name</code></td></tr><tr><td><code>Application Package Name</code></td><td><code>context.app.namespace</code></td><td><code>app_package_name</code></td></tr><tr><td><code>Application Store</code></td><td><code>partners.netflix.app_store</code></td><td><code>app_store</code></td></tr><tr><td><code>Application Version</code></td><td><code>context.app.version</code></td><td><code>app_version</code></td></tr><tr><td><code>Install Time</code></td><td><code>partners.netflix.install_time</code></td><td><code>install_time</code></td></tr><tr><td><code>Device User Agent</code></td><td><code>context.device.user_agent</code></td><td><code>user_agent</code></td></tr><tr><td><code>Device Brand</code></td><td><code>context.device.manufacturer</code></td><td><code>brand</code></td></tr><tr><td><code>Device Type</code></td><td><code>context.device.type</code></td><td><code>type</code></td></tr><tr><td><code>Device Model</code></td><td><code>context.device.model</code></td><td><code>model</code></td></tr><tr><td><code>Form Factor</code></td><td><code>partners.netflix.form_factor</code></td><td><code>form_factor</code> <strong>[10]</strong></td></tr><tr><td><code>Device OS Family</code></td><td><code>context.device.os.name</code></td><td><code>os_family</code> <strong>[11]</strong></td></tr><tr><td><code>Device OS Name</code></td><td><code>partners.netflix.os_name</code></td><td><code>os_name</code></td></tr><tr><td><code>Device OS Version</code></td><td><code>context.device.os.version</code></td><td><code>os_version</code></td></tr><tr><td><code>Device Mobile Carrier</code></td><td><code>context.device.network.carrier</code></td><td><code>carrier</code></td></tr><tr><td><code>Device Screen Width</code></td><td><code>context.device.screen.width</code></td><td><code>screen_width</code></td></tr><tr><td><code>Device Screen Height</code></td><td><code>context.device.screen.height</code></td><td><code>screen_width</code></td></tr><tr><td><code>Device Screen Density</code></td><td><code>context.device.screen.density</code></td><td><code>screen_density</code></td></tr><tr><td><code>CPU Cores</code></td><td><code>partners.netflix.cpu_cores</code></td><td><code>cpu_cores</code></td></tr><tr><td><code>Storage Size</code></td><td><code>partners.netflix.storage_size</code></td><td><code>storage_size</code></td></tr><tr><td><code>Language</code></td><td><code>context.device.lang</code></td><td><code>languages</code></td></tr><tr><td><code>Network Type</code></td><td><code>partners.netflix.network_type</code></td><td><code>network_type</code> <strong>[12]</strong></td></tr><tr><td><code>Device Locale</code></td><td><code>partners.netflix.device_locale</code></td><td><code>locale</code></td></tr><tr><td><code>Device Timezone</code></td><td><code>context.device.timezone</code></td><td><code>timezone</code></td></tr><tr><td><code>Device Timezone Abbreviation</code></td><td><code>partners.netflix.device_timezone_abbr</code></td><td><code>timezone_abbr</code></td></tr><tr><td><code>Battery Level</code></td><td><code>partners.netflix.battery_level</code></td><td><code>battery_level</code></td></tr><tr><td><code>Custom City</code></td><td><code>partners.netflix.custom_city</code></td><td><code>custom_city</code></td></tr><tr><td><code>Custom Postal Code</code></td><td><code>partners.netflix.custom_postal_code</code></td><td><code>custom_postal_code</code></td></tr><tr><td><code>Custom Country</code></td><td><code>partners.netflix.custom_country</code></td><td><code>custom_country</code></td></tr><tr><td><code>Custom Predicted Lifetime Value</code></td><td><code>partners.netflix.custom_predicted_ltv</code></td><td><code>custom_predicted_ltv</code></td></tr><tr><td><code>Custom DMA Code</code></td><td><code>partners.netflix.custom_dma_code</code></td><td><code>custom_dma_code</code></td></tr><tr><td><code>Custom Check-in Dates</code></td><td><code>partners.netflix.custom_check_in_dates</code></td><td><code>custom_check_in_dates</code> <strong>[13]</strong></td></tr><tr><td><code>Custom Destination Id</code></td><td><code>partners.netflix.custom_destination_ids</code></td><td><code>custom_destination_ids</code> <strong>[14]</strong></td></tr><tr><td><code>Custom Hotel Score</code></td><td><code>partners.netflix.custom_hotel_score</code></td><td><code>custom_hotel_score</code> <strong>[14]</strong></td></tr><tr><td><code>Custom Num Items</code></td><td><code>partners.netflix.custom_num_items</code></td><td><code>custom_num_items</code> <strong>[15]</strong></td></tr><tr><td><code>Transaction Id</code></td><td><code>id</code></td><td><code>custom_order_id</code> <strong>[15]</strong></td></tr><tr><td><code>Search Term</code></td><td><code>search_term</code></td><td><code>custom_search_string</code> <strong>[16]</strong></td></tr></tbody></table>

{% hint style="info" %}
**\*** Mandatory property.\
**1.** See [Quick reference](netflix-ads-convesions-api.md#quick-reference) for more details.\
**2.** If it's not passed, the current timestamp is used.\
**3.** When it's not passed, this is set as follows (in the presented order):\
&#x20;   • If at least one property is set in <mark style="color:blue;">`context.app`</mark> then <mark style="color:blue;">`app`</mark> , \
&#x20;   • If <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`call`</mark> or <mark style="color:blue;">`phone`</mark> then <mark style="color:blue;">`phone`</mark> , \
&#x20;   • If <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`chat`</mark> then <mark style="color:blue;">`chat`</mark> ,\
&#x20;   • If <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`email`</mark> then <mark style="color:blue;">`email`</mark> ,\
&#x20;   • If <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`offline`</mark> then <mark style="color:blue;">`in_person`</mark> ,\
&#x20;   • If <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`system`</mark> then <mark style="color:blue;">`system`</mark> ,\
&#x20;   • If <mark style="color:blue;">`type`</mark> is <mark style="color:blue;">`other`</mark> then <mark style="color:blue;">`other`</mark> ,\
&#x20;   • If none of the above applies, default value <mark style="color:blue;">`web`</mark> .\
**4.** Recommended for <mark style="color:blue;">`add_payment_info`</mark> , <mark style="color:blue;">`add_to_wishlist`</mark> , <mark style="color:blue;">`initiate_checkout`</mark> , and <mark style="color:blue;">`search`</mark> events.\
**5.** Automatically normalized (except for <mark style="color:blue;">`st`</mark> and partially for <mark style="color:blue;">`phone`</mark> ) and hashed (expect for <mark style="color:blue;">`address`</mark> ) if passed in clear text.\
**6.** Pre-hashed accepted value: <mark style="color:blue;">`f`</mark> /<mark style="color:blue;">`female`</mark> , <mark style="color:blue;">`m`</mark> /<mark style="color:blue;">`male`</mark> , <mark style="color:blue;">`n`</mark> /<mark style="color:blue;">`non binary`</mark> /<mark style="color:blue;">`non-binary`</mark> (Case insensitive).\
**7.** As the 2-character ANSI abbreviation code in lowercase. Normalize states outside the US in uppercase with no punctuation, no special characters, and no spaces.\
**8.** Postal code in lower case, remove any space and <mark style="color:blue;">`-`</mark> characters. For US addresses, use only the first 5 digits of the zipcode. For UK addresses, use the area, district and sector format.\
**9.** ISO 3166 alpha-2 country code.\
**10.** Supported values: <mark style="color:blue;">`desktop`</mark> , <mark style="color:blue;">`laptop`</mark> , <mark style="color:blue;">`cellphone`</mark> , <mark style="color:blue;">`tablet`</mark> , <mark style="color:blue;">`smartwatch`</mark> , <mark style="color:blue;">`tv`</mark> , <mark style="color:blue;">`vr`</mark> , <mark style="color:blue;">`console`</mark> , <mark style="color:blue;">`other`</mark> .\
**11.** Supported values: <mark style="color:blue;">`ios`</mark> , <mark style="color:blue;">`android`</mark> , <mark style="color:blue;">`macos`</mark> , <mark style="color:blue;">`windows`</mark> , <mark style="color:blue;">`linux`</mark> , <mark style="color:blue;">`bsd`</mark> , <mark style="color:blue;">`other`</mark> .\
**12.** Supported values: <mark style="color:blue;">`wifi`</mark> , <mark style="color:blue;">`cellular_2g`</mark> , <mark style="color:blue;">`cellular_3g`</mark> , <mark style="color:blue;">`cellular_4g`</mark> , <mark style="color:blue;">`cellular_5g`</mark> , <mark style="color:blue;">`cellular_6g`</mark> , <mark style="color:blue;">`ethernet`</mark> , <mark style="color:blue;background-color:blue;">`unknown`</mark> .\
**13.** Supported formats: <mark style="color:blue;">`YYYYMMDD`</mark> , <mark style="color:blue;">`YYYY-MM-DD`</mark> , <mark style="color:blue;">`YYYY-MM-DDThh:mmTZD`</mark> , <mark style="color:blue;">`YYYY-MM-DDThh:mm:ssTZD`</mark> . Recommended for <mark style="color:blue;">`search`</mark> event.\
**14**. Recommended for <mark style="color:blue;">`booking`</mark> and <mark style="color:blue;">`purchase`</mark> events.\
**15**. Recommended for <mark style="color:blue;">`add_to_cart`</mark> and <mark style="color:blue;">`purchase`</mark> events.\
**16**. Recommended for <mark style="color:blue;">`search`</mark> event.
{% endhint %}
