# Batch Audience

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

Batch lets CRM Teams design, test and automate their customer engagement strategies to keep users engaged and grow revenue. Using this destination you can share audiences with Batch by leveraging the [Custom Audience API 1.1](https://doc.batch.com/api/custom-audience/1.1/create/).

{% hint style="warning" %}
Audiences are synchronized using their names as identifier. Avoid renaming to maintain consistency.
{% endhint %}

## Key features

The Batch Audience destination provides the following key features:

* **Audience sharing**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model drives audience sharing with Batch, meaning that you can synchronize your existing user segments, with your partner, in a seamless way.

## Destination setup

### Configuration

<table><thead><tr><th width="331">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Batch API Key</code></td><td><em><strong><code>Required</code></strong></em> <br>The <code>Batch API Key</code> value is either your Live or Dev Batch API key from the settings page of your app within the <a href="https://dashboard.batch.com">Batch dashboard</a> following <code>Settings</code> → <code>General</code>.</td></tr><tr><td><code>REST API Key</code></td><td><em><strong><code>Required</code></strong></em> <br>The <code>REST API Key</code> value is available in the settings page of your app within the <a href="https://dashboard.batch.com">Batch dashboard</a> following <code>Settings</code> → <code>General</code>.</td></tr><tr><td><code>Custom User Id</code></td><td><em><strong><code>Required</code></strong></em> <br>Set the property value you want to use as <code>Custom User Id</code>. More details are available by following this <a href="https://doc.batch.com/ios/custom-data/customid/">LINK</a>.</td></tr><tr><td><code>Custom Audience Properties</code><br><code>Mapping</code></td><td>Send custom properties related to audiences as Batch attributes. Set <code>Batch attribute name</code> with the attribute name to be set in Batch and <code>Your value</code> with the value you want to set. They can be used in <a href="https://doc.batch.com/guides/message-personalization/advanced/#custom-audience-data">message personalization</a>.</td></tr><tr><td><code>Custom Audience Properties</code><br><code>Tags</code></td><td>Send custom properties related to audiences as Batch tags. Set <code>Your value</code> with the tag value you want to use, one per line. See <a href="https://doc.batch.com/api/trigger-events-api/track-events/">Batch "Trigger Events API"</a> for more details.</td></tr></tbody></table>

## Field mappings

Created segments include the following properties:

<table><thead><tr><th width="193">Property Name</th><th width="586">Property Value</th></tr></thead><tbody><tr><td><code>name</code></td><td><code>context.segment_name</code></td></tr><tr><td><code>description</code></td><td><code>context.site_id</code>_<code>context.segment_id</code>_<code>context.segment_name</code></td></tr><tr><td><code>type</code></td><td>custom_ids</td></tr><tr><td><code>nb_ids</code></td><td>(Number of identifiers in segment)</td></tr><tr><td><code>indexing_state</code></td><td>APPLIED</td></tr><tr><td><code>created</code></td><td>(Creation time in the format YYYY-MM-DDTHH:MM:SS)</td></tr><tr><td><code>updated</code></td><td>(Update time in the format YYYY-MM-DDTHH:MM:SS)</td></tr></tbody></table>
