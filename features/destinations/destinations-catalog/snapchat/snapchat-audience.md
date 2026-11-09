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
  anchors:
    visible: true
---

# Snapchat Audience

{% hint style="info" %}
This destination is currently under final review and will be available soon.
{% endhint %}

[Snapchat](https://forbusiness.snapchat.com/) is a social media and messaging app with a self-serve advertising platform.\
This destination keeps Snapchat audiences in sync with your segments. When a user enters a segment, their identifiers are added to a matching Snapchat audience, and when they leave it, they are removed. Provided identifiers (email, phone, mobile advertising ID) are hashed with SHA-256 before they are sent through the [Snapchat Customer Lists API](https://developers.snap.com/marketing-api/Ads-API/audience-creation/customer-lists).

## Key features

The Snapchat Audience destination provides the following key features:

* **Audience sharing**: your segments are synchronized with Snapchat as users enter and leave them. No file export or manual upload is needed.
* **Automatic audience creation**: each segment gets its own Snapchat audience, created automatically in your ad account. You don't need to prepare anything on the Snapchat side.
* **Multiple identifiers**: email, phone and mobile advertising ID can be sent for the same user, each as a separate match key, which gives Snapchat more ways to match the user.
* **Automatic hashing**: clear-text identifiers are normalized and hashed before they leave the platform. Values that are already hashed are sent as they are.

## Destination setup

{% hint style="info" %}
Select the segments to share in the **Audience** tab. Each selected segment becomes its own audience in Snapchat. To send only users who granted a given consent category, use the **Filters** tab (see [Destination filters](https://doc.commandersact.com/features/destinations/destination-filters)).
{% endhint %}

Each segment is linked to a Snapchat audience **by name**. The audience name is `ca_` followed by the segment name, in lowercase, with spaces replaced by underscores. For example, the segment `VIP Customers` feeds the Snapchat audience `ca_vip_customers`.

* The audience is created the first time a user enters the segment. Until then, it does not appear in Snapchat Ads Manager.
* If an audience with that name already exists in the ad account, it is reused instead of being created again.
* A user leaving a segment that has no Snapchat audience yet is rejected (`missing_audience_id`), because there is nothing to remove them from.

{% hint style="warning" %}
The link between a segment and its Snapchat audience relies only on the name:

* **Renaming a segment** creates a new, empty Snapchat audience at the next segment entry. The previous audience stops being updated but is not deleted.
* **Renaming or deleting the audience in Snapchat** has the same effect: a new audience is created at the next segment entry.
* **Two segments whose names differ only by case or by spaces vs underscores** (for example `VIP Customers` and `vip_customers`) feed the same Snapchat audience.
{% endhint %}

### Configuration

| Setting         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Credentials`   | <p><em><strong><code>Required</code></strong></em><br>Your Snapchat Ads connection, created in <code>Administration</code> ➜ <code>Connector Credentials</code> ➜ <code>Add connector credentials</code> ➜ <code>Snapchat</code>, or directly with the <strong>add a new account</strong> link. The Snapchat user behind these credentials must have access to the ad account below, with permission to manage audiences. The access token is renewed automatically when it expires.</p> |
| `Ad Account Id` | <p><em><strong><code>Required</code></strong></em><br>Identifier of the Snapchat ad account where audiences are created and updated, as shown in Snapchat Ads Manager (UUID format, for example <code>1a2b3c4d-5e6f-7a8b-9c0d-1e2f3a4b5c6d</code>). All segments of this destination go to this ad account.</p>                                                                                                                                                                          |

## Field mappings

{% hint style="info" %}
Properties can be remapped using our [Smart Mapping](https://doc.commandersact.com/features/destinations/advanced-mapping#smart-mapping) feature.\
At least one of `User Email`, `User Phone` or `Device Mobile Identifier` must have a value for each user. Otherwise, the user is rejected with `missing_identifiers`. To stop sending an identifier, clear its mapping.
{% endhint %}

Users are sent to Snapchat with the following identifiers. Each identifier is sent as its own match key.

<table><thead><tr><th width="245">Smart Mapping Fields</th><th width="290">Commanders Act Default Properties</th><th>Sent to Snapchat as</th><th>Processing before sending</th></tr></thead><tbody><tr><td><code>User Email</code></td><td><code>user.email</code></td><td><code>EMAIL_SHA256</code></td><td>Trimmed, lowercased, then hashed with SHA-256</td></tr><tr><td><code>User Phone</code></td><td><code>user.phone</code></td><td><code>PHONE_SHA256</code></td><td>Trimmed, non-digit characters removed, then hashed with SHA-256</td></tr><tr><td><code>Device Mobile Identifier</code></td><td><code>context.device.advertising_id</code></td><td><code>MOBILE_AD_ID_SHA256</code></td><td>Trimmed, lowercased, then hashed with SHA-256</td></tr></tbody></table>

{% hint style="info" %}
**Already-hashed values**: a value that is already a SHA-256 hash (64 hexadecimal characters) is sent as it is, without any normalization. If you hash identifiers yourself, normalize them first: email trimmed and lowercased, phone in international format with digits only, mobile ID lowercased. A hash of a non-normalized value will not match any Snapchat user.
{% endhint %}

{% hint style="warning" %}
**Phone numbers must include the country code.** Automatic normalization only removes spaces, `+`, `-`, parentheses and other non-digit characters. It does not add a country code or remove a leading `00` or national `0`.

| Value in your data   | Sent (before hashing) | Expected format        |
| -------------------- | --------------------- | ---------------------- |
| `+33 6 12 34 56 78`  | `33612345678`         | ✅                      |
| `0033 6 12 34 56 78` | `0033612345678`       | ❌ remove the `00`      |
| `06 12 34 56 78`     | `0612345678`          | ❌ missing country code |
{% endhint %}

Audiences created with the [Snapchat Customer Lists API](https://developers.snap.com/marketing-api/Ads-API/audience-creation/customer-lists#create-an-audience-segment) have the following properties:

| Property Name   | Property Value                                                            |
| --------------- | ------------------------------------------------------------------------- |
| `name`          | `ca_` + `context.segment_name`, lowercase, spaces replaced by underscores |
| `source_type`   | `FIRST_PARTY`                                                             |
| `ad_account_id` | Value of the `Ad Account Id` setting                                      |

{% hint style="info" %}
**Reading delivery statuses in Event Delivery**: users are sent to Snapchat in batches, and the status is calculated per batch. If Snapchat accepts some requests in a batch but rejects others, every user in that batch shows `success` with the detail `partial_identifiers_rejection`.\
A `success` status means Snapchat accepted the identifiers. It does not mean the user was matched to a Snapchat account; matching happens afterwards on Snapchat's side and shows in the audience size in Ads Manager.
{% endhint %}
