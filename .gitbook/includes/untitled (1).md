---
title: Untitled
---

| Commanders Act Properties                  | AppsFlyer Properties                                     |
| ------------------------------------------ | -------------------------------------------------------- |
| `AppsFlyer Id`                             | `appsflyer_id` **\[\*]**                                 |
| `context.event_timestamp`                  | `eventTime`                                              |
| `user.id`                                  | `customer_user_id`                                       |
| `context.device.ip`                        | `ip`                                                     |
| `(event_name)`                             | `eventName` **\[1]**                                     |
| `value`                                    | `af_revenue` **\[2]**                                    |
| `partners.appsflyer.content_type`          | `af_content_type` **\[2]**                               |
| `partners.appsflyer.content_id`            | `af_content_id` **\[2]**                                 |
| `partners.appsflyer.your_custom_attribute` | `your_custom_attribute` **\[2]**                         |
| `context.app.version`                      | `app_version_name`                                       |
| `partners.appsflyer.app_store`             | `app_store`                                              |
| `currency`                                 | `eventCurrency`                                          |
| `context.app.namespace`                    | `bundleIdentifier`                                       |
| `partners.appsflyer.sharing_filters`       | `sharing_filter`                                         |
| `(partners.appsflyer.is_app_clip)`         | `app_type` **\[3]**                                      |
| `Custom Data Mapping`                      | `custom_data`                                            |
| `context.device.os.name`                   | `os`                                                     |
| `context.device.user_agent`                | `ua`                                                     |
| `(context.device.ad_tracking_enabled)`     | `aie` **\[4]**                                           |
| `context.device.advertising_id`            | <p><code>advertising_id</code> <br><code>idfa</code></p> |
| `partners.appsflyer.oaid`                  | `oaid`                                                   |
| `partners.appsflyer.aid`                   | `amazon_aid`                                             |
| `partners.appsflyer.imei`                  | `imei`                                                   |
| `partners.appsflyer.app_set_id_scope`      | `app_set_id.scope`                                       |
| `partners.appsflyer.app_set_id`            | `app_set_id.id`                                          |
| `context.device.idfv`                      | `idfv`                                                   |
| `partners.appsflyer.att`                   | `att`                                                    |
| `partners.appsflyer.tcf_string`            | `tcf.tcstring` **\[5]**                                  |
| `partners.appsflyer.tcf_policy_version`    | `tcf.policy_version` **\[5]**                            |
| `partners.appsflyer.cmp_sdk_id`            | `tcf.cmp_sdk_id`                                         |
