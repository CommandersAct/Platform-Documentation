# Cookie Inventory

Cookie Inventory is the operational view of the storage items **actually observed by Realtime Cookie Scanner**.

It is designed to answer a simple question:

> **What is really happening in users’ browsers?**

This is intentionally different from Cookie Notice Manager, which represents what is **declared and managed** in your Cookie Notice.

***

### What belongs in the inventory

Cookie Inventory only contains items observed during the selected period.

As a consequence:

* manually created entries that were never observed are not included;
* items marked as `Missing` are not included;
* Cookie Notice configuration does not determine whether an item appears in the inventory.

This distinction matters when comparing Cookie Inventory with Cookie Notice Manager.

A cookie can be:

* present in Cookie Inventory but absent from the Cookie Notice;
* present in the Cookie Notice but absent from Cookie Inventory because it was not observed during the selected period.

Neither situation is necessarily an error. They answer different questions.

***

## Reading the summary

The summary cards highlight the main situations worth investigating.

### Detected

All items observed in the current scope.

This is the best representation of your effective browser-storage footprint for the selected period.

### New

Highlights items that appeared recently compared with a reference period.

For periods of at least 48 hours, **New - last 48h** identifies items observed in the last 48 hours that were not observed earlier in the selected period.

For shorter periods, **New in selected period** compares the selected period with the preceding period of equivalent duration.

This makes the metric particularly useful for detecting changes introduced by releases, new vendors or configuration changes.

### Before consent

Items observed before the visitor made a consent choice.

This is an observation, not automatically a compliance issue.

An item explicitly configured as consent-exempt can legitimately appear here.

### Violations

Items whose observed consent behavior is considered problematic by the scanner.

This currently covers situations such as:

* storage before consent when the item is not exempt;
* storage observed after a refusal.

Use this population to prioritize investigation, rather than treating every pre-consent item as a violation.

### Uncategorized

Items for which no meaningful category is currently available.

A high number here generally indicates that the inventory needs metadata qualification before it can be reliably used for governance or Cookie Notice maintenance.

### Outside Cookie Notice

Observed items that are not currently included in the Cookie Notice.

This is the population to review when checking whether your declaration reflects what is actually happening on the site.

***

## Understanding the table

The most important columns are not purely descriptive: several contain interpretation derived from RCS observations.

### Frequency

Frequency represents how often the item was observed in the traffic analyzed by RCS.

It is useful for distinguishing:

* widespread storage behavior;
* behavior limited to specific pages, journeys or conditions;
* very rare observations that may require deeper investigation.

Frequency should not be interpreted as a percentage of users.

***

### Consent timing

Consent timing describes when the item was observed relative to the visitor’s consent state.

#### Before

The item was observed before a consent choice.

Whether this is acceptable depends on its exemption status.

#### After

The item was observed after consent.

#### After refuse

The item was observed after the visitor refused consent.

This normally deserves investigation unless the item is legitimately exempt.

#### Unknown

RCS does not have enough consent context to determine the timing reliably.

`Unknown` should therefore be interpreted as **insufficient evidence**, not as compliant or non-compliant behavior.

***

### Compliance

Compliance is the scanner’s interpretation of the available observations.

#### Violation

RCS detected behavior considered incompatible with the expected consent state.

#### Exempt

The item is explicitly marked as exempt from consent requirements.

An exempt item may therefore appear under **Before consent** without being considered a violation.

#### OK

No compliance issue was identified from the available observations.

`OK` does not constitute a legal certification. It means that the scanner did not detect one of the monitored problematic behaviors.

#### Unknown

The available observations are insufficient to determine a reliable status.

***

### Notice status

Notice status compares the observed item with the Cookie Notice configuration.

#### Included

The item is already included in the Cookie Notice.

#### To review

The item has been observed but is not currently included.

This is the same population represented by the **Outside Cookie Notice** summary.

***

## Cookie Inventory and Cookie Notice Manager

The distinction between these two views is fundamental.

| Cookie Inventory                              | Cookie Notice Manager                         |
| --------------------------------------------- | --------------------------------------------- |
| Observed reality                              | Declared configuration                        |
| What RCS has actually seen                    | What is managed in the Cookie Notice          |
| Period-dependent                              | Configuration-dependent                       |
| Excludes items not observed during the period | Can contain items that are no longer observed |
| Best suited to investigation and monitoring   | Best suited to declaration and maintenance    |

Cookie Notice Manager should therefore not be used as the source of truth for determining what is currently present on the website.

Cookie Inventory is the better starting point for that question.

***

## Typical investigations

### A new tracking behavior appeared after a release

Focus on **New**, then compare Vendor, Category, Frequency and Consent timing.

The combination helps distinguish a genuinely new technology from an existing item whose behavior has changed.

***

### You want to identify the most important consent issues

Start with **Violations** and use Frequency to prioritize.

A violation observed broadly across traffic usually deserves attention before an isolated occurrence.

Also check whether the item is exempt before drawing conclusions from a **Before consent** observation.

***

### You want to reconcile your Cookie Notice with production

Use **Outside Cookie Notice** as the starting population.

For each item, verify:

* whether it is expected;
* its vendor and purpose;
* its category;
* its consent behavior;
* whether it should be included in the Cookie Notice.

Items that should be declared can be added directly to the Cookie Notice from the inventory.

***

### You see an item in Cookie Notice Manager but not here

This does not mean the item has been deleted.

It only means that it was **not observed in the current Cookie Inventory scope**.

Cookie Notice Manager can retain entries that were manually created or that are currently `Missing`.

Cookie Inventory intentionally excludes them because it represents observed activity.

***

## Interpreting the data correctly

Cookie Inventory is based on browser observations collected by Realtime Cookie Scanner.

It should therefore be treated as **observational evidence**, not as a static registry.

A few principles are important:

* absence from the inventory means “not observed in this scope”, not necessarily “does not exist”;
* `Unknown` means that RCS lacks sufficient evidence;
* `Before consent` describes timing, not automatically a violation;
* `OK` means no monitored issue was detected, not that legal compliance is guaranteed;
* Frequency describes observed prevalence, not a user-level percentage.

Keeping these distinctions in mind is essential when using Cookie Inventory for compliance investigations or technical debugging.
