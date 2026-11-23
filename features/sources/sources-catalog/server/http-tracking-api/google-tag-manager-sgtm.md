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

# Google Tag Manager (sGTM)

{% hint style="info" %}
This template is in beta. Publication in the [Google Community Template Gallery](https://tagmanager.google.com/gallery) is planned after the beta. Current version: **0.9.1-beta – 2026-11-23**.
{% endhint %}

## 1. What the template does

The **Commanders Act | Server-side events (sGTM)** tag template is installed in a **Google Tag Manager server container**. It takes the events the container receives (usually through the GA4 client), converts them to the Commanders Act event format, and sends them to the PlatformX **HTTP tracking API**. Nothing runs in the browser.

It complements the web template **Commanders Act | Serverside events bridge**, which remains the solution for a web container.

## 2. Prerequisites

* **A GTM server container** deployed, with an **up-to-date** tagging server (Admin > Container Settings > Tagging Server Version).
* **An HTTP tracking API source** created in PlatformX. Note its:
  * **site ID** (`tc_s`);
  * **source key** (`token`).
* **The GA4 client** active in the server container. In the browser, the GA4 tag must send its hits to the server (`server_container_url`).
* **Recommended:** the sGTM server on a **first-party subdomain** of the site (for example `sgtm.yourdomain.com`). This is required to read the site's cookies (CAID, consent, partner cookies). See sections 5, 6 and 8.

## 3. Installation

**Import the template**

1. In the server container: **Templates > Tag Templates > New**.
2. Menu **⋮ > Import**, then choose the `.tpl` file provided by Commanders Act.
3. Save.

**Create the tag**

1. **Tags > New**, then choose the type _Commanders Act | Server-side events (sGTM)_.
2. Fill in the fields below.

<table><thead><tr><th>Field</th><th width="331">Default</th><th width="377">Purpose</th></tr></thead><tbody><tr><td>Site ID (<code>siteId</code>)</td><td></td><td><strong>Required.</strong> Site ID of the source</td></tr><tr><td>Source key (<code>sourceKey</code>)</td><td></td><td><strong>Required.</strong> Key of the HTTP tracking API source</td></tr><tr><td>Collection domain / path</td><td><code>collect.commander1.com</code> / <code>/events</code></td><td>Collection endpoint (see below)</td></tr><tr><td>Event name override (<code>eventNameOverride</code>)</td><td></td><td>Replaces the incoming event name (see <a href="google-tag-manager-sgtm.md#id-7.5-universal-analytics-format-event-names">section 7.5</a>)</td></tr><tr><td>Event ID (<code>eventId</code>)</td><td></td><td>Otherwise the event's <code>event_id</code>, otherwise a generated ID</td></tr><tr><td>Page type (<code>pageType</code>)</td><td></td><td>For <code>page_view</code>, when <code>page_type</code> isn't in the event</td></tr><tr><td>Revenue (<code>revenue</code>)</td><td></td><td>See <a href="google-tag-manager-sgtm.md#id-7.2-fields-with-no-ga4-equivalent-revenue-type-status">section 7.2</a></td></tr><tr><td>Skip <code>gtm.*</code> events</td><td>on</td><td>Ignores GTM internal events</td></tr><tr><td>CAID override (<code>caidOverride</code>)</td><td></td><td>See <a href="google-tag-manager-sgtm.md#id-6.-anonymous-id-caid">section 6</a></td></tr><tr><td>Consent source</td><td><code>variable</code></td><td><code>none</code> / <code>variable</code> / <code>cookie</code> (<a href="google-tag-manager-sgtm.md#id-5.-consent">section 5</a>)</td></tr><tr><td>Forward unmapped fields</td><td>off</td><td><a href="google-tag-manager-sgtm.md#id-8.-extra-fields-personal-data-and-partner-cookies">Section 8</a></td></tr><tr><td>Excluded fields</td><td>personal data list</td><td><a href="google-tag-manager-sgtm.md#id-8.-extra-fields-personal-data-and-partner-cookies">Section 8</a></td></tr><tr><td>Forward partner cookies</td><td>off</td><td><a href="google-tag-manager-sgtm.md#id-8.-extra-fields-personal-data-and-partner-cookies">Section 8</a></td></tr><tr><td>User data (<code>userDataMode</code>)</td><td>Email hashed (SHA-256) only</td><td>How GA4's <code>user_data</code> is sent (<a href="google-tag-manager-sgtm.md#id-8.-extra-fields-personal-data-and-partner-cookies">section 8</a>)</td></tr><tr><td>Custom fields</td><td></td><td>Added at the root of <strong>every event the tag sends</strong>; they override everything else (see <a href="google-tag-manager-sgtm.md#id-7.2-fields-with-no-ga4-equivalent-revenue-type-status">section 7.2</a>)</td></tr></tbody></table>

**Collection endpoint.** By default, the event is sent as a `POST` to:

```
https://collect.commander1.com/events?tc_s={site ID}&token={source key}
```

If you use a first-party collection domain, enter your domain and the path `/cdp/events`.

**Never point the collection at the sGTM container itself**: events would loop.

**Template permissions**

| Permission        | Value                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------- |
| `send_http`       | any URL, because the domain is configurable. You can restrict it to your collection domain. |
| `read_event_data` | any key                                                                                     |
| `get_cookies`     | `CAID`, `TC_PRIVACY` (or the custom name), `_fbp`, `_fbc`, `_ga`                            |
| `read_request`    | headers `user-agent`, `forwarded`, `x-forwarded-for`, and the remote IP address             |

## 4. Trigger

Create a trigger: **Custom > Some Events > Client Name equals GA4**.

Why not "All Events": if the container has other clients, especially one that already receives events in Commanders Act format, the tag would send them again.

* This creates duplicates.
* The conversion would break those events, which are already in the right format.

**One path per event.** If an event is already sent from the browser (web template or `cact()`), don't also send it through sGTM. The two sends are processed as two separate events: don't rely on deduplication.

## 5. Consent

The `user.consent_categories` field holds the categories the user accepted, for example `["1","3"]`.

**Variable mode (recommended)**

1. In the browser, add a `consent_categories` parameter to your GA4 events. Its value is the list of accepted categories, provided by the PlatformX CMP, for example `1,3`.
2. In the server container, create an **Event Data** variable on the key `consent_categories`.
3. Select that variable in the tag's "Consent categories" field.
4. In Variable mode, the Consent categories field is required. To send no consent, choose **None** as the consent source. If the variable is empty for an event, the tag logs a warning and doesn't send `consent_categories`.

The value can be an array or a comma-separated list.

When the user refuses every category, send `none`: the tag sends `consent_categories: []`, meaning no category was granted. An empty or missing value means consent unknown, and the field isn't sent. Consent-filtered destinations receive neither.\
`consent_categories` is required by the event specification: send the CMP consent on every event.

**Cookie mode (fallback)**

The tag reads the `TC_PRIVACY` consent cookie from the request received by sGTM.

Tag settings:

* **Cookie name and separator**: `TC_PRIVACY` and `@` by default. If they were changed in _Data Governance > Consent > Settings_, enter the same values.
* **List of all categories**: required when the cookie lists the refused categories instead of the accepted ones.
* **Include "blocked on" categories**: optional.

Conditions for the cookie to reach sGTM:

* sGTM is on a first-party subdomain of the site;
* the cookie is set on the parent domain (for example `.yourdomain.com`). Check it in the browser's developer tools, Domain column.

This mode has not yet been validated in real conditions. The documentation also recommends the Consent Object over reading the cookie directly. Prefer Variable mode.

**Google Consent Mode.** If the GA4 hit contains Google's consent signal (`gcs`), the tag fills `user.google_consent_mode` with `ad_storage` and `analytics_storage`. The `ad_user_data` and `ad_personalization` signals are not forwarded.

## 6. Anonymous ID (CAID)

To link sGTM events to the visitor's web journey, the tag fills `user.consistent_anonymous_id` with the **CAID** cookie.

**Reading the CAID cookie.** It only works when:

* sGTM is on a first-party subdomain of the site;
* the CAID cookie is set on the parent domain.

Who creates the CAID cookie:

* With first-party collection through CNAME or A-record, **your server** creates it: 20 random digits preceded by the year, 12-month lifetime, domain `.yourdomain.com`.
* With the proxy method, Commanders Act servers manage it.

**If the cookie can't be read**, provide the ID through the **CAID override** field, for example with an event parameter sent from the browser.

**Without a CAID**, the platform assigns an ID itself. How it is built isn't documented: don't use it to link these events to the site's events.

## 7. Events

### 7.1 Supported events

The template supports the GA4 recommended events below. Their names are the same in GA4 and in the Commanders Act Events reference, so no renaming is needed. Most work with the data GA4 already sends; a few need extra configuration.

| Event                                                                          | Data from GA4                                                                     | Extra configuration                                                                                                                                                                                                |
| ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `page_view`                                                                    | page URL, title, referrer, language                                               | `page_type` (Page type field or a `page_type` event parameter)                                                                                                                                                     |
| `view_item_list`, `select_item`                                                | `items`, `item_list_name`                                                         | none                                                                                                                                                                                                               |
| `view_item`, `add_to_wishlist`, `add_to_cart`, `remove_from_cart`, `view_cart` | `value`, `currency`, `items`                                                      | none                                                                                                                                                                                                               |
| `begin_checkout`                                                               | `value`, `currency`, `coupon`, `items`                                            | `revenue` ([7.2](google-tag-manager-sgtm.md#id-7.2-fields-with-no-ga4-equivalent-revenue-type-status))                                                                                                             |
| `add_shipping_info`                                                            | `value`, `currency`, `shipping_tier`, `coupon`, `items`                           | none                                                                                                                                                                                                               |
| `add_payment_info`                                                             | `payment_type`, `value`, `currency`, `items`                                      | `payment_method` values ([7.3](google-tag-manager-sgtm.md#id-7.3-payment_method-values))                                                                                                                           |
| `purchase`                                                                     | `transaction_id`, `value`, `currency`, `tax`, `shipping`, `payment_type`, `items` | `revenue`, `type`, `status` ([7.2](google-tag-manager-sgtm.md#id-7.2-fields-with-no-ga4-equivalent-revenue-type-status)), `payment_method` values ([7.3](google-tag-manager-sgtm.md#id-7.3-payment_method-values)) |
| `refund`                                                                       | `transaction_id`, `value`, `currency`, `items`                                    | `revenue`, `type` ([7.2](google-tag-manager-sgtm.md#id-7.2-fields-with-no-ga4-equivalent-revenue-type-status))                                                                                                     |
| `search`                                                                       | `search_term`                                                                     | none                                                                                                                                                                                                               |
| `select_content`                                                               | `content_type`, `item_id`                                                         | none                                                                                                                                                                                                               |
| `login`, `sign_up`                                                             | `method`                                                                          | none                                                                                                                                                                                                               |
| `generate_lead`                                                                | `value`, `currency`                                                               | none                                                                                                                                                                                                               |

Other event names are sent as they are, with the same mapping. Custom events are accepted as long as they have an `event_name`.

### 7.2 Fields with no GA4 equivalent: `revenue`, `type`, `status`

| Field     | Needed for                             | Definition                                                                                                                                                             |
| --------- | -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `revenue` | `begin_checkout`, `purchase`, `refund` | Amount **excluding tax and shipping**, after discount                                                                                                                  |
| `type`    | `purchase`, `refund`                   | Type of conversion, for example `online` or `offline`                                                                                                                  |
| `status`  | `purchase`                             | One of: `canceled`, `delivered`, `in_progress`, `partially_delivered`, `partially_returned`, `partially_shipped`, `pending_shipment`, `returned`, `shipped`, `pending` |

**Custom fields apply to every event the tag sends.** Don't enter fixed values such as `type = online`: that value would be added to every event (`page_view`, `add_to_cart`, …), and on `page_view` it would overwrite the page type.

**Recommended setup:** send these values as event parameters, only on the events that need them, and read them with Event Data variables.

1. In the browser, add these GA4 event parameters:
   * `revenue` on `begin_checkout`, `purchase` and `refund`;
   * `conversion_type` on `purchase` and `refund`;
   * `status` on `purchase`.
2.  In the server container, create three **Event Data** variables:

    | Variable               | Key path          |
    | ---------------------- | ----------------- |
    | `ED - revenue`         | `revenue`         |
    | `ED - conversion_type` | `conversion_type` |
    | `ED - status`          | `status`          |
3. In the tag:
   * **Revenue:** `{{ED - revenue}}`
   * **Custom fields:** `type` → `{{ED - conversion_type}}`, `status` → `{{ED - status}}`

When an event doesn't carry a parameter, the variable is empty and the field isn't sent. So `type` and `status` only appear on the events that need them.

### 7.3 `payment_method` values

`payment_method` (on `add_payment_info` and `purchase`) is taken from GA4's `payment_type` and passed through as is. The expected values are: `by_invoice`, `by_bank_transfer_in_advance`, `card`, `check_in_advance`, `cod`, `coupon`, `direct_debit`, `online_payment_system`, `other`.

If your values are different:

1. Create a **Lookup Table** variable on an Event Data variable reading `payment_type`, with the expected values as outputs.
2. Add it under **Custom fields** with the name `payment_method`. Custom fields override the automatic mapping.

### 7.4 Price and tax

Each item's GA4 `price` feeds two fields:

* `items[].product.price`, expected **excluding tax and discount**;
* `items[].value`, calculated as `price × quantity` and expected **including tax**.

Check what the `price` in your dataLayer contains. Depending on the case, one of the two fields won't exactly match its definition.

### 7.5 Universal Analytics–format event names

If your dataLayer still uses the Universal Analytics e-commerce format, the template converts its data (products, `actionField`), but **not the event names**. An event named `addToCart` arrives as `addToCart`, not `add_to_cart`.

To rename events:

1. Create a **Lookup Table** variable on the event name, mapping each name to its Commanders Act equivalent (for example `addToCart` → `add_to_cart`).
2. Use it in the **Event name override** field.

Events sent by a standard GA4 setup don't need this.

## 8. Extra fields, personal data and partner cookies

**Unmapped fields.** Off by default. When on, every event parameter that isn't converted is copied to the event root, except:

* `x-*` and `gtm.*` keys;
* keys already converted;
* the **excluded fields**.

The default exclusion list removes personal data: `email,email_address,phone,phone_number,first_name,last_name,street,address,postal_code`. Add your own sensitive parameters before turning the option on.

**Precedence:** unmapped fields < converted fields < custom fields.

**User data.** The tag's **User data** setting controls how GA4's `user_data` is sent:

<table><thead><tr><th width="384">Option</th><th>Sent</th></tr></thead><tbody><tr><td>Email hashed (SHA-256) only (default)</td><td><code>user.email_sha256</code>: the email trimmed, lowercased and hashed, or GA4's <code>sha256_email_address</code> as is. Phone and address aren't sent.</td></tr><tr><td>Don't send</td><td>nothing from <code>user_data</code></td></tr><tr><td>Send as received</td><td><code>user.email</code>, <code>user.email_sha256</code>, <code>user.phone</code> and address fields, in clear text</td></tr></tbody></table>

`user.id` (from `user_id`) is always sent. Destinations that read `user.email`, such as Facebook Conversions API, receive no email in the default mode. Map `user.email_sha256` with Smart Mapping, or choose Send as received if your legal basis allows it.

**Partner cookies.** Off by default. This option forwards `_fbp`, `_fbc` and `_ga` in `context.device.cookie`, provided sGTM is on a first-party subdomain.

## 9. GA4 → Commanders Act mapping

For each field, the first source found is used.

<table><thead><tr><th width="513">Source</th><th>Commanders Act</th></tr></thead><tbody><tr><td><code>event_name</code> (or <code>event</code>)</td><td><code>event_name</code></td></tr><tr><td><code>transaction_id</code></td><td><code>id</code></td></tr><tr><td><code>value</code>, <code>currency</code>, <code>coupon</code>, <code>affiliation</code></td><td>same names</td></tr><tr><td><code>tax</code> / <code>shipping</code></td><td><code>tax_amount</code> / <code>shipping_amount</code></td></tr><tr><td><code>payment_type</code></td><td><code>payment_method</code></td></tr><tr><td><code>shipping_tier</code>, <code>item_list_name</code>, <code>search_term</code>, <code>method</code>, <code>content_type</code>, <code>item_id</code></td><td>same names</td></tr><tr><td><code>items</code> (or <code>ecommerce.items</code>, or Universal Analytics format)</td><td><code>items[]</code></td></tr><tr><td><code>item_id</code>, <code>item_variant</code>, <code>quantity</code>, <code>discount</code>, <code>index</code></td><td><code>items[].id</code>, <code>variant</code>, <code>quantity</code>, <code>discount</code>, <code>list_position</code></td></tr><tr><td><code>price × quantity</code></td><td><code>items[].value</code></td></tr><tr><td><code>item_id</code>, <code>item_name</code>, <code>price</code>, <code>item_brand</code></td><td><code>items[].product.{id, name, price, brand}</code></td></tr><tr><td><code>item_category</code> … <code>item_category5</code></td><td><code>items[].product.category_1</code> … <code>category_5</code></td></tr><tr><td><code>user_id</code></td><td><code>user.id</code></td></tr><tr><td>CAID cookie / CAID override</td><td><code>user.consistent_anonymous_id</code></td></tr><tr><td><code>user_data.*</code> (depends on the User data setting, see section 8)</td><td><p></p><ul><li>Default: <code>user.email_sha256</code></li><li>Send as received: <code>user.email</code>, <code>email_sha256</code>, <code>phone</code>, address fields</li><li>Don't send: nothing</li></ul></td></tr><tr><td><code>gcs</code> signal</td><td><code>user.google_consent_mode</code></td></tr><tr><td><code>page_location</code>, <code>page_title</code>, <code>page_referrer</code>, <code>language</code>, <code>viewport_size</code></td><td><code>context.page.*</code></td></tr><tr><td><code>user_agent</code>, <code>ip_override</code> (otherwise the request's own)</td><td><code>context.device.*</code></td></tr><tr><td><code>page_type</code> (<code>page_view</code> only)</td><td><code>page_type</code></td></tr></tbody></table>

## 10. Verification

1. **In the server container's Preview:**
   * the tag fires on the GA4 client's events;
   * the outgoing request to the collection domain ends with a **200**. A 307 redirect may appear first; the tag follows it automatically.
2. **In PlatformX, open the source's event inspector:**
   * the event must appear;
   * fix the reported warnings (for example missing `type`, `status` or `consent_categories`) using sections 5 and 7.

The API returns 200 for any valid request: only the event inspector confirms the content is correct. An invalid request, or one over 32 KB, gets a 400 error.

Warnings are checked against the **event specifications** defined for your source in PlatformX. A `type_error` means a property doesn't have the type your specification expects: check the source's **Data Quality** tab for the property concerned.

## 11. Known limitations

* **Size:** 32 KB maximum per event. Very large baskets may be rejected.
* **No deduplication:** an event sent both by the browser and by sGTM is counted twice.
* **Custom fields** apply to every event the tag sends: use event-based variables ([section 7.2](google-tag-manager-sgtm.md#id-7.2-fields-with-no-ga4-equivalent-revenue-type-status)), not fixed values.
* **Event names** aren't renamed: Universal Analytics–format names need a lookup table (section 7.5).
* **Consent cookie mode** has not been validated in real conditions: prefer Variable mode.
* **Variable mode:** the browser must send `none` when every category is refused. An empty value is treated as "consent unknown".
* **Google Consent Mode:** only `ad_storage` and `analytics_storage` are forwarded.
* **`payment_method`** is passed through as is: a lookup table is needed if your values aren't in the list.
