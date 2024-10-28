# Equativ Audience

[Equativ ](https://equativ.com/)is an advertising technology company.\
Using this destination you can share audiences with Equativ using the [Audience data - API integration](https://help.smartadserver.com/s/article/Audience-data-API-integration-v2).

## Key features

The Equativ Audience destination provides the following key features:

* **Audience sharing**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model drives audience sharing with Equativ, meaning that you can synchronize your existing user segments, with your partner, in a seamless way.

## Destination setup

{% hint style="info" %}
Select your audiences/user segments to be shared and synchronized with Equativ.
{% endhint %}

### Configuration

<table><thead><tr><th width="307">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Authentication</code></td><td><em><strong><code>Required</code></strong></em> <br>Your credentials with Equativ as set in the Commanders Act interface following: <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Equativ</code></td></tr></tbody></table>

## Field mappings

Created segments using [Equativ Segment API](https://datasync-eu.smartadserverapis.com/swagger/v2/index.html#/Segments/post\_segmentproviders\_\_segmentProviderId\_\_segments) hold the following properties:

<table><thead><tr><th width="188">Property Name</th><th width="466">Property Value</th></tr></thead><tbody><tr><td><code>active</code></td><td>true</td></tr><tr><td><code>description</code></td><td><code>context.segment_name</code></td></tr><tr><td><code>name</code></td><td><code>context.segment_name</code></td></tr><tr><td><code>price</code></td><td>0</td></tr><tr><td><code>segmentId</code></td><td>ca_<code>context.site_id</code>_<code>context.segment_id</code></td></tr><tr><td><code>selectable</code></td><td>true</td></tr><tr><td><code>ttl</code></td><td>2147483646</td></tr></tbody></table>

