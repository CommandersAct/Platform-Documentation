# RTB House Audience

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[RTB House](https://rtbhouse.com/) is an advertising-technology company specialized in target advertising including retargeting and real-time bidding. Using this destination you can share audiences with RTB House by leveraging the [RTB House Audience API](https://rtbhouse-traffic-audiences.ew.r.appspot.com/v1/docs/).

{% hint style="warning" %}
Audiences are synchronized using their names as identifier. Avoid renaming to maintain consistency.
{% endhint %}

## Key features

The RTB House Audience destination provides the following key features:

* **Audience sharing**: our [Events reference](https://community.commandersact.com/platform-x/developers/tracking/events-reference) model drives audience sharing with Batch, meaning that you can synchronize your existing user segments, with your partner, in a seamless way.

## Destination setup

{% hint style="warning" %}
One of the following properties is required:

* `user.email`
* `user.email_sha256`
* `user.email_md5`
{% endhint %}

### Configuration

<table><thead><tr><th width="331">Settings</th><th>Description</th></tr></thead><tbody><tr><td><code>Account Id</code></td><td><em><strong><code>Required</code></strong></em> <br>Your account identifier as provided by RTB House.</td></tr><tr><td><code>API Key</code></td><td><em><strong><code>Required</code></strong></em> <br>Your API key as provided by RTB House.</td></tr></tbody></table>

## Field mappings

Created segments include the following properties:

<table><thead><tr><th width="275">Property Name</th><th width="586">Property Value</th></tr></thead><tbody><tr><td><code>audience_id</code></td><td>[rtb_identifer] _<code>context.segment_name</code> <strong>[1]</strong></td></tr><tr><td><code>audience_name</code></td><td><code>context.segment_name</code></td></tr><tr><td><code>audience_compact_id</code></td><td><code>context.segment_name</code> <strong>[1]</strong></td></tr><tr><td><code>size</code></td><td>(number of overall users)</td></tr><tr><td><code>user_types.X.user_type</code></td><td>EMAIL</td></tr><tr><td><code>user_types.X.size</code></td><td>(number of user of the specific type)</td></tr></tbody></table>

{% hint style="info" %}
**\[1]** <mark style="color:blue;">`context.segment_name`</mark> is converted in lower case with spaces replaced by the underline character ( `_` ).
{% endhint %}
