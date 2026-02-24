# Web container generator

## 2026

### 100.6

Release date:  **24/02/2026**

* [beta] enhance activation of Real Time Cookie Scanner
* [beta] Realtime cookie scanner: support Didomi & OneTrust CMPs

### 100.5

Release date:  **11/02/2026**

* [beta] Upgrade minifier for tags
* [beta] New implementation: Scanning cookies with Trust

### 100.4

Release date:  **03/02/2026**

* [public release] update CAID management

### 100.3

Release date:  **12/01/2026**

* [beta] Support Amazon Consent Signal in Trust
* [beta] update CAID management

## 2025

### 100.2

Release date:  **01/12/2025**

* Update bot exclusion list

### 100.1

Release date:  **19/11/2025**

* Refinement of the tc_do_not_track flag handling in CMP and server-side hits

### 100.0

Release date:  **17/11/2025**

* Update Trust view hits after opt-out action
* Added tc_do_not_track parameter to specific CMP and server-side hits for improved alignment with consent settings
  * Helps optimize cookie behavior in specific first-party and delegated domain setups
  * No impact for non-CMP use cases or standard tag configurations

### 99.7

Release date:  **03/11/2025**

* Optimizations in container generation script
* [beta] Refined CAID cookie handling for specific beta accounts, adds logic from in event hit parameters to set or overwrite the CAID when the CAID cookie is missing
* [public release] Load Trust banner in DOM ready event

### 99.6

Release date:  **23/10/2025**

* [beta] Update Trust DOM ready event handling for containers without banner embedded

### 99.5

Release date:  **20/10/2025**

* [beta] Load Trust banner in DOM ready event

### 99.4

Release date:  **13/10/2025**

* [public release] Remove tC.fn.css & tC.fn.resetCss support

### 99.3

Release date:  **06/10/2025**

* Optimizations in custom JS inclusion in Trust

### 99.2

Release date:  **30/09/2025**

* [public release] Optimizations in container generation process

### 99.1

Release date:  **08/09/2025**

* Support processing functions for event variables
* [beta] Remove tC.fn.css & tC.fn.resetCss support

### 99.0

Release date:  **02/09/2025**

* [beta] Optimizations in container generation process

### 98.5

Release date:  **12/08/2025**

* [public release] Finer support of Portuguese language in IAB module

### 98.4

Release date:  **04/07/2025**

* Update processing functions handling

### 98.3

Release date:  **02/07/2025**

* Optimizations in container generation process

### 98.2

Release date:  **16/06/2025**

* Update TCF support in GCM

### 98.1

Release date:  **10/06/2025**

* [beta] Remove cookie MIX_CLICK after first OneTag send

### 98.0

Release date:  **26/05/2025**

* [beta] Refined CAID cookie handling for clients using the Commanders Act CMP in first-party domain configurations
  * Improved handling during opt-out events to better align with specific consent configurations
  * No change for other types of events or for non-CMP setups

### 97.0

Release date:  **26/05/2025**

* [beta] Refined container core generation pipeline for extended system-level flexibility
* [beta] Finer support of Portuguese language in IAB module

### 96.1

Release date:  **05/05/2025**

* [public release] Support js function for TCPID behaviour customization

### 96.0

Release date:  **18/03/2025**

* Move `tC.privacy.includedVendorIds` initialization

### 95.9

Release date:  **10/03/2025**

* [public release] Update Billing hit First Party
* [beta] Support js function for TCPID behaviour customization

### 95.8

Release date:  **17/02/2025**

* Added an option to customize the CAID creation process
  * This new option allows to configure custom CAID cookie expiration. This option is only relevant for clients with specific technical constraints
  * This option is inactive by default, ensuring that the web container's behavior remains unchanged unless our support team has contacted you about this topic
  * By defaultCAID expiration remains at 12 months, still handled on the server side

### 95.7

Release date:  **06/01/2025**

* [beta] Update Billing hit First Party

## 2024

### 95.6

Release date:  **13/01/2025**

* Fully support sampling rules for privacy rules

### 95.5

Release date:  **11/12/2024**

* The creation of the CAID cookie in the web container has been adjusted, its expiration (13 months) is now managed outside the container, backend-side
* Update the safari browser detection

### 95.4

Release date:  **10/12/2024**

* Enhance container generation performances

### 95.3

Release date:  **06/11/2024**

* Update on specific rule on CAID cookie, added parameters `expiration` on `13 months` (396 days) and `SameSite` when necessary (`Lax` value)

### 95.2

Release date:  **14/10/2024**

* Closed-Beta: include CDN 1st party loaded from another site in file generators

### 95.1

Release date:  **07/10/2024**

* Closed-Beta: implement CDN 1st party loaded from another site

### 95.0

Release date:  **30/09/2024**

* Closed-Beta: implement CDN 1st party in Trust files

### 94.3

Release date:  **03/09/2024**

* Support multiple containers for a data storage

### 94.2

Release date:  **08/08/2024**

* New method for Google Consent Mode sequencing validation

### 94.1

Release date:  **26/06/2024**

* Add default event to tag triggers
* Add events for standard tag triggers (`tag_trigger_dom_ready`, `tag_trigger_clicks`, `tag_trigger_form_submission`, `tag_trigger_scroll`)

### 94.0

Release date:  **24/06/2024**

* Add context variables to tags
* Enable CAID sync for Mix

### 93.3

Release date:  **20/06/2024**

* Add `setProperty` API to allow to set global event properties

### 93.2

Release date:  **19/06/2024**

* Beta: New improvement for CAID sync

### 93.1

Release date:  **18/06/2024**

* Privacy: set developer id on the page
* Beta: Improve CAID sync for Mix tracking

### 93.0

Release date:  **04/06/2024**

* Better handling of privacy events (consent.onReady, consent.onUpdate)
* Add `addEventListener`, `once`, `removeEventListener`, `dispatchEvent` methods to `cact` API
* Integrate `trigger` api with Web Container Triggers

### 92.1

Release date:  **29/05/2024**

* Fix bug where TCF would conflict with GCM initialization
* Support new hashes to check container integrity

### 92.0

Release date:  **27/05/2024**

* New generation method for CAID (Platform X events only). Previously introduced as beta for version 90.0

### 91.0

Release date:  **14/05/2024**

* Closed-Beta: implement CDN 1st party in Tag containers

### 90.5

Release date:  **13/05/2024**

* Infer value of page_type from env_template in page_view events

### 90.4

Release date:  **10/04/2024**

* Handle TCF purposes within Google Consent Mode. This upgrade requires regenerating the containers and the privacy banners.
* Include vendors in signal to other TMS

### 90.3

Release date:  **25/03/2024**

* Closed-Beta: Follow up of the feature introduced in 90.0, now for privacy events

### 90.2

Release date:  **13/03/2024**

* Optimization of the generation engine

### 90.1

Release date:  **11/03/2024**

* Optimization of the generation engine

### 90.0

Release date:  **07/03/2024**

* Closed-Beta: New generation method for CAID (Platform X events only)

### 89.2

Release date:  **21/02/2024**

* Add default signal on GCM banners load

### 89.1

Release date:  **01/02/2024**

* Update `tC.onDomReady` method

### 89.0

Release date:  **29/01/2024**

* Make source key available for each container
* Initialize container config earlier
* Support Google Consent Mode (closed beta)
* Security update for `tc_privacy_wait_body` function

## 2023

### 88.0

Release date:  **06/12/2023**

* Make generator version available on container / banner versions listing

### 87.2

Release date:  **20/11/2023**

* Fix IAB TCFv2 VendorList cache to better support TCF < 2.2

### 87.1

Release date:  **14/11/2023**

* Fix IAB TCFv2 text translation (bug introduced in v87.0)

### 87.0

Release date:  **13/11/2023**

* Allow tracking domains to be defined as fourth level (and more) domains. As in the past, if multiple subdomains were setup, only the first one matching the visited url will be used.
* Upgrade official IAB TCF SDK
* Fix first layer text for IAB TCF 2.2 banners

### 86.5

Release date:  **23/10/2023**

* Update sampling cookie settings

### 86.4

Release date:  **12/10/2023**

* Update Privacy options in TagCommander

### 86.3

Release date:  **09/10/2023**

* Fix TagCommander retro-compatibility issue introduced in 86.1 where the TCPID might not be retrieved properly in some cases:
  * If you have a container with generator version >= 86.1 and < 86.3, make sure to regenerate it to include this patch

### 86.2

Release date:  **09/10/2023**

* Refactoring on container core javascript code

### 86.1

Release date:  **04/10/2023**

* Privacy - Standalone: allow to force the value of the secure attribute of cookies via customJS

### 86.0

Release date:  **02/10/2023**

* Upgrade of the container and privacy banner generation engine.
  * Although this upgrade should be transparent for your containers and banners, please make sure to test your newly generated containers and banners before deploying them in production.
  * As usual, please report to <support@commanderact.com> issues that you would encounter with this generator version.

### 85.1

Release date:  **21/08/2023**

* Use IAB TCF GVLv3 in Trust banner generation

### 85.0

Release date:  **16/08/2023**

* Internal update of `tC.trigger()` to update the event format
* Support legitimate interest policy urls for IAB TCF GVLv3 vendors

### 84.6

Release date:  **04/07/2023**

* Support GPC activation by privacy banner

### 84.5

Release date:  **29/06/2023**

* Support various URLs for IAB vendor list
* Support new "illustrations" attribute for IAB TCF GVLv3 purposes, specialPurposes, features and specialFeatures

### 84.4

Release date:  **28/06/2023**

* Update handling of hidden subcategories
* Support dataRetention & dataCategories attributes published in IAB TCF GVLv3

### 84.3

Release date:  **19/06/2023**

* Support localization of vendor policy URLs included in IAB TCF GVLv3

### 84.2

Release date:  **14/06/2023**

* Fix Privacy GPC handling when statistics are included in privacy scope

### 84.1

Release date:  **14/06/2023**

* Fix `tC.isCookieEnabled()` in iframe context

### 84.0

Release date:  **06/06/2023**

* Privacy - Add an option to handle Global Privacy Control
* Privacy - TCFv2 - Add `tC.privacy.getNbIabVendors()`
* Optimize OnSite consent API to make IAB TCFv2 consent available sooner

### 83.1

Release date:  **23/05/2023**

* Update IAB TCFv2 module to protect from wrong vendor configuration in IAB TCFv2 official vendor list
* Fix collision on TCSESSION 1st party cookie between TagDedup and Campaign tracking

### 83.0

Release date:  **04/04/2023**

* Fixes a generator bug introduced on the **30/03/2023** (side-effect from a generation engine upgrade)
  * The bug was causing an ordering issue where Tags may be loaded in a different order from before
  * **It is highly recommended you generate a new version for containers generated between the 30/03/2023 and the 04/04/2023 to prevent any unexpected behavior on your website**

### 82.1

Release date:  **28/03/2023**

* Update IAB TCFv2 module to automatically add vendor number to banner text (new TCF requirement)

### 82.0

Release date:  **08/03/2023**

* Trigger module update to add `tC.generateEventId()` and allow to pass a specific event id to the trigger API

### 81.1

Release date:  **28/02/2023**

* Trigger module update for Rakuten and Microsoft UET integration

### 81.0

Release date:  **14/02/2023**

* Internal upgrade of the generator engine. Greatly improves generator performance. This upgrade should not impact the generation result, though we recommend that you test your first generated container before your next deployment.

### 80.3

Release date:  **08/02/2023**

* Refactoring on various TagCommander modules

### 80.2

Release date:  **08/02/2023**

* Add tc_privacy_do_not_track flag
* Refactoring on the TagDeduplication

### 80.1

Release date:  **24/01/2023**

* Refactoring on the tC.privacy module

### 80.0

Release date:  **17/01/2023**

* Add new Consent OnSite API commands:
  * `consent.onReady`
  * `consentBanner.show`
  * `consentBanner.hide`
  * `consentCenter.show`
  * `consentCenter.hide`

### 79.1

Release date:  **16/01/2023**

* Refactoring on the Privacy Banners

### 79.0

Release date:  **12/01/2023**

* Refactoring on the tC object initialization

## 2022

### 78.0

Release date:  **13/12/2022**

* Update `tC.setCookie` to encode `!'()~` characters in the cookie value. This is a requirement for WAF restrictions of some TagCommander users.

### 77.0

Release date:  **01/12/2022**

* Update `tC.privacy.hit` to not send hits when analytics category was refused using consent JS OnSite API

### 76.1

Release date:  **30/11/2022**

* Update `trigger` JS OnSite API to better use source-keys in multi-container contexts

### 76.0

Release date:  **15/11/2022**

* Update `tC.setCookie` to use `encodeURIComponent` instead of `escape` (deprecated)

### 75.3

Release date:  **19/09/2022**

* Update page data format in `cact('trigger')` API

### 75.2

Release date:  **15/09/2022**

* Refactoring on privacy hits generation

### 75.1

Release date:  **02/08/2022**

* Better handling of old .tagcommander.com domain redirections on Tag Deduplication

### 75.0

Release date:  **19/07/2022**

* Improve tC.privacy.getCategoryIdList

### 74.1

Release date:  **13/07/2022**

* Fix domain detection

### 74.0

Release date:  **06/07/2022**

* Do not mutate `cact()` arguments

### 73.0

Release date:  **05/07/2022**

* Automatically integrate domains set up in Domain Management

### 72.1

Release date:  **20/06/2022**

* Make consent data available in `consent.get` before privacy file is loaded

### 72.0

Release date:  **18/05/2022**

* Add refused_vendors in CAX events

### 71.1

Release date:  **26/04/2022**

* Fix blocked on categories not sent in CAX events

### 71.0

Release date:  **18/01/2022**

* Integrate TrustCommander settings with DataStorage cookies

### 70.0

Release date:  **13/04/2022**

* Commanders Act - Platform X Source keys enabled on all web containers

### 69.1

Release date:  **05/04/2022**

* Add page and device information in OneTag events

### 69.0

Release date:  **22/03/2022**

* Improve TrustCommander event format. `list_categories` is renamed `optin_categories`. `optout_categories` are now included in the event.

### 68.1

Release date:  **24/01/2022**

* Improve setCookie domain detection

### 68.0

Release date:  **18/01/2022**

* Tag Deduplication - Add a (programatic) option to not use tc_cj_v2 encryption. This is a requirement for WAF restrictions of some TagCommander users.

## 2021

### 67.1

Release date:  **07/12/2021**

* Store generated versions on remote server (no more NFS usage)

### 67.0

Release date:  **03/12/2021**

* Fix tC.log escaping

### 66.0

Release date:  **02/12/2021**

* Fix minor tags generation

### 65.0

Release date:  **24/11/2021**

* Integrate `tC.trigger` / `cact('trigger')` natively  inside web containers

### 64.0

Release date:  **18/10/2021**

* Tag Deduplication - Fix campaign/medium cookie initialization

### 63.0

Release date:  **07/10/2021**

* Include blocked on categories in Privacy hits

### 62.0

Release date:  **07/09/2021**

* Refactoring on Privacy Banner Templates

### 61.0

Release date:  **28/06/2021**

* Tag Deduplication - Fix launcher on "bypass" setups

### 60.0

Release date:  **31/05/2021**

* TrustCommander - Fix analytics for setups where it is set as blocked on category

### 59.0

Release date:  **15/04/2021**

* TrustCommander - Fix `tC.privacy.getBlockedOnCategories`

### 58.0

Release date:  **25/02/2021**

* Add new Consent OnSite APIs:
  * `consent.onUpdate`
  * `consent.update`
  * `consent.revoke`

### 57.0

Release date:  **23/02/2021**

* Add `consent.get` OnSite API

### 56.0

Release date:  **09/02/2021**

* Privacy - Rework parameters inclusion

### 55.0

Release date:  **26/01/2021**

* Privacy - Fix categories statistics sending

### 54.0

Release date:  **11/01/2021**

* Privacy - Fix missing TCID on some opin hits

## 2020

### 53.0

Release date:  **12/11/2020**

* Privacy - Optimize vendor statistics when visitor is optin to all vendors

### 52.0

Release date:  **19/10/2020**

* TrustCommander - Integrate Google ACM

### 51.0

Release date:  **16/10/2020**

* Improve generator performance

### 50.0

Release date:  **15/10/2020**

* Update vendor statistics format

### 49.0

Release date:  **17/09/2020**

* Fix optional modules inclusion in unminified web containers

### 48.0

Release date:  **20/08/2020**

* Fix TC_PRIVACY cookie content caused by a retro-compatibility issue with old banners

### 47.0

Release date:  **18/08/2020**

* Fix privacy vendors initialization

### 46.0

Release date:  **17/08/2020**

* Fix privacy vendors usage in TMS

### 45.0

Release date:  **14/08/2020**

* Integrate __tcfapi stub

### 44.0

Release date:  **06/07/2020**

* Use privacy vendors in TMS

### 43.0

Release date:  **28/05/2020**

* Set consent duration by Privacy banner

### 42.0

Release date:  **29/04/2020**

* Fix vendor encoding in web containers

### 41.0

Release date:  **20/04/2020**

* Fix tC.events sorting

### 40.0

Release date:  **24/02/2020**

* Fix internal variable initialization on container reload

### 39.0

Release date:  **24/02/2020**

* Fix internal variable initialization on container reload

### 38.0

Release date:  **11/02/2020**

* Deactivate tC reach

### 37.0

Release date:  **03/02/2020**

* Fix privacy statistics on optin all

### 36.0

Release date:  **21/01/2020**

* Fix privacy statistics intialization from container

### 35.0

Release date:  **20/01/2020**

* Fix privacy statistics intialization from container

### 34.0

Release date:  **09/01/2020**

* Fix Tag Deduplication initialization on container reload

## 2019

### 33.0

Release date:  **07/11/2019**

* Do not run Privacy code when cookies are disabled

### 32.0

Release date:  **07/11/2019**

* Refactoring on generator code base

### 31.0

Release date:  **07/11/2019**

* Fix tC.event initialization on container reload

### 30.0

Release date:  **06/11/2019**

* Fix to avoid reloading tC.event when triggred on Dom Ready

### 29.0

Release date:  **01/10/2019**

* Fix conflict between containers when initializating internal variables

### 28.0

Release date:  **25/09/2019**

* Fix Tag Deduplication by merging config when multiple containers are on the same page

### 27.0

Release date:  **18/09/2019**

* Add `tC.isCookieEnabled`

### 26.0

Release date:  **25/07/2019**

* Add more details for privacy statistics on optin all

### 25.0

Release date:  **10/06/2019**

* Security fix

### 24.0

Release date:  **30/05/2019**

* Fix platform user rights

### 23.0

Release date:  **28/05/2019**

* Fix privacy analytics

### 22.0

Release date:  **28/05/2019**

* Fix TCPID in privacy analytics

### 21.0

Release date:  **28/05/2019**

* Add option to disable TCPID

### 20.0

Release date:  **29/04/2019**

* Privacy - add custom separator and domain

### 19.0

Release date:  **08/04/2019**

* Fix custom events to work without second argument

### 18.0

Release date:  **05/04/2019**

* Fix tc_array_events object initialization

### 17.0

Release date:  **20/03/2019**

* Refactoring for Privacy Standalone

### 16.0

Release date:  **02/03/2019**

* Fix privacy analytics

### 15.0

Release date:  **21/02/2019**

* Fix `tC.array_launched_tags` initialization

### 14.0

Release date:  **16/01/2019**

* Fix `tC.privacy.validRules` initialization

### 13.0

Release date:  **14/01/2019**

* Refactoring on Privacy Templates (Privacy v2)

### 12.0

Release date:  **07/01/2019**

* Add custom privacy default status (optin/optout) for tags

## 2018

### 11.0

Release date:  **15/08/2018**

* Add option to set default privacy default status (optin/optout) for banners

### 10.0

Release date:  **10/08/2018**

* Privacy - On Premise option

### 9.0

Release date:  **08/10/2018**

* Fix Browser Extension error

### 8.0

Release date:  **01/10/2018**

* Fix tC.event on mutli-container contexts

### 7.0

Release date:  **17/09/2018**

* Fix Dom Ready Trigger

### 6.0

Release date:  **12/06/2018**

* Handle dynamic change of version from Browser Extension

### 5.0

Release date:  **11/04/2018**

* Initial release of TagCommander v2
