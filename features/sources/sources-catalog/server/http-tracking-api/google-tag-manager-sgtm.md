# Google Tag Manager (sGTM)

{% hint style="info" %}
This template is currently under final review and will be released through the [Google Community Template Gallery](https://tagmanager.google.com/gallery) soon. Current version: **0.9.0-beta – 2026-11-20**.
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

| Field                                     | Default                              | Purpose                                                                                                                                                                                    |
| ----------------------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Site ID (`siteId`)                        |                                      | **Required.** Site ID of the source                                                                                                                                                        |
| Source key (`sourceKey`)                  |                                      | **Required.** Key of the HTTP tracking API source                                                                                                                                          |
| Collection domain / path                  | `collect.commander1.com` / `/events` | Collection endpoint (see below)                                                                                                                                                            |
| Event name override (`eventNameOverride`) |                                      | Replaces the incoming event name (see [section 7.5](google-tag-manager-sgtm.md#id-7.5-universal-analytics-format-event-names))                                                             |
| Event ID (`eventId`)                      |                                      | Otherwise the event's `event_id`, otherwise a generated ID                                                                                                                                 |
| Page type (`pageType`)                    |                                      | For `page_view`, when `page_type` isn't in the event                                                                                                                                       |
| Revenue (`revenue`)                       |                                      | See [section 7.2](google-tag-manager-sgtm.md#id-7.2-fields-with-no-ga4-equivalent-revenue-type-status)                                                                                     |
| Skip `gtm.*` events                       | on                                   | Ignores GTM internal events                                                                                                                                                                |
| CAID override (`caidOverride`)            |                                      | See [section 6](google-tag-manager-sgtm.md#id-6.-anonymous-id-caid)                                                                                                                        |
| Consent source                            | `variable`                           | `none` / `variable` / `cookie` ([section 5](google-tag-manager-sgtm.md#id-5.-consent))                                                                                                     |
| Forward unmapped fields                   | off                                  | [Section 8](google-tag-manager-sgtm.md#id-8.-extra-fields-personal-data-and-partner-cookies)                                                                                               |
| Excluded fields                           | personal data list                   | [Section 8](google-tag-manager-sgtm.md#id-8.-extra-fields-personal-data-and-partner-cookies)                                                                                               |
| Forward partner cookies                   | off                                  | [Section 8](google-tag-manager-sgtm.md#id-8.-extra-fields-personal-data-and-partner-cookies)                                                                                               |
| Custom fields                             |                                      | Added at the root of **every event the tag sends**; they override everything else (see [section 7.2](google-tag-manager-sgtm.md#id-7.2-fields-with-no-ga4-equivalent-revenue-type-status)) |

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

The value can be an array or a comma-separated list.

When the user refuses every category, send `none`: the tag sends an empty list (`[]`), which means "everything refused". An empty or missing value means consent unknown, and the field isn't sent.

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

**User data.** The `user_data` sent by GA4 (email, SHA-256 hashed email, phone, address) is converted into `user.*`. Only send what your legal basis and consent allow.

**Partner cookies.** Off by default. This option forwards `_fbp`, `_fbc` and `_ga` in `context.device.cookie`, provided sGTM is on a first-party subdomain.

## 9. GA4 → Commanders Act mapping

For each field, the first source found is used.

| Source                                                                                | Commanders Act                                                   |
| ------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| `event_name` (or `event`)                                                             | `event_name`                                                     |
| `transaction_id`                                                                      | `id`                                                             |
| `value`, `currency`, `coupon`, `affiliation`                                          | same names                                                       |
| `tax` / `shipping`                                                                    | `tax_amount` / `shipping_amount`                                 |
| `payment_type`                                                                        | `payment_method`                                                 |
| `shipping_tier`, `item_list_name`, `search_term`, `method`, `content_type`, `item_id` | same names                                                       |
| `items` (or `ecommerce.items`, or Universal Analytics format)                         | `items[]`                                                        |
| `item_id`, `item_variant`, `quantity`, `discount`, `index`                            | `items[].id`, `variant`, `quantity`, `discount`, `list_position` |
| `price × quantity`                                                                    | `items[].value`                                                  |
| `item_id`, `item_name`, `price`, `item_brand`                                         | `items[].product.{id, name, price, brand}`                       |
| `item_category` … `item_category5`                                                    | `items[].product.category_1` … `category_5`                      |
| `user_id`                                                                             | `user.id`                                                        |
| CAID cookie / CAID override                                                           | `user.consistent_anonymous_id`                                   |
| `user_data.*`                                                                         | `user.email`, `email_sha256`, `phone`, address fields            |
| `gcs` signal                                                                          | `user.google_consent_mode`                                       |
| `page_location`, `page_title`, `page_referrer`, `language`, `viewport_size`           | `context.page.*`                                                 |
| `user_agent`, `ip_override` (otherwise the request's own)                             | `context.device.*`                                               |
| `page_type` (`page_view` only)                                                        | `page_type`                                                      |

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
