---
description: Realtime Cookie Scanner
---

# Legal and Technical Position Paper

#### For DPOs, Legal Teams and Compliance Officers

***

### 1. Purpose of this Document

This document presents the technical operation of the Commanders Act Realtime Cookie Scanner module, clarifies its legal qualification under the ePrivacy Directive and the GDPR, and provides legal and compliance teams with the information required to assess its regulatory standing.

It covers the technical description of the module and the data it observes, followed by a legal analysis of its qualification under Article 5(3) of the ePrivacy Directive, the absence of personal data processing, and the technical safeguards in place.

***

### 2. Technical Operation of the Module

#### 2.1 Nature and Purpose of the Module

Realtime Cookie Scanner is a JavaScript module executed in the visitor's browser. Its sole purpose is to help website operators verify that their website complies with ePrivacy and GDPR obligations regarding cookie deployment.

Concretely, the module allows operators to:

* maintain an up-to-date inventory of cookies present on their website;
* identify which scripts or tools create cookies;
* detect cookies that appear before user consent or after a refusal;
* monitor changes in cookie usage over time;
* support internal privacy and compliance audits.

#### 2.2 Technical Operations Performed

The module performs the following operations in the browser:

* reading the **names of cookies** present in the browser via `document.cookie`;
* reading the **keys present in `localStorage`**;
* reading the **keys present in `sessionStorage`**;
* recording the **URLs of the pages being analysed**;
* detecting the **consent state** provided by the Consent Management Platform (CMP) (e.g. Didomi, OneTrust, Commanders Act CMP).

The scanner **does not modify** any cookies present in the browser. Its role is strictly limited to observation.

#### 2.3 Data Observed and Transmitted

The module collects only technical metadata necessary to build a cookie inventory.

**Data observed and transmitted to Commanders Act servers:**

* cookie names
* keys present in `localStorage` and `sessionStorage`
* URLs of the analysed pages
* consent categories activated by the CMP

**Data neither collected nor exploited:**

* cookie values
* user identifiers
* browser fingerprints
* behavioural or analytical data

**Note on IP address and user-agent:** when the module transmits metadata to Commanders Act servers, an HTTP request is initiated. By design of the HTTP protocol itself (and independently of any decision made at the application level) every HTTP request inherently carries the sender's IP address and user-agent string. This is a fundamental and unavoidable characteristic of how the protocol operates, not a data collection choice made by the module. These pieces of information are neither stored, processed, nor exploited for any purpose whatsoever, and are not recorded in any system associated with the module.

#### 2.4 Data Hosting and Transfer

All metadata transmitted by the module is sent exclusively to Commanders Act servers hosted within the European Union. No data is transferred to servers located outside the EU.

#### 2.5 Execution Prior to Consent

The module executes at page load, independently of the user's consent status.

This is not an arbitrary design choice: it is the technical prerequisite for the module's core function. A tool designed to detect cookies deployed **before consent** or **after a refusal** can only fulfil its purpose if it is able to observe the browser environment at that precise moment. If the module were triggered only after consent had been collected, it would be technically unable to detect the non-compliant situations it is designed to flag.

The module subsequently monitors changes in consent status via the CMP API in order to compare cookie presence before and after the user's decision.

***

### 3. Legal Analysis

#### 3.1 Scope of Article 5(3) of the ePrivacy Directive

Article 5(3) of the ePrivacy Directive requires prior consent for any operation involving **access to information stored in the user's terminal equipment**, or the storing of information therein, regardless of whether that information constitutes personal data.

The Realtime Cookie Scanner, insofar as it accesses cookies and storage keys present in the browser, falls within the scope of this provision. This is acknowledged. The legal question is therefore whether this access can be considered strictly necessary for the provision of the service. \
**The module is not designed to track or identify users, and the analysis below demonstrates that its operation is consistent with the strict necessity exemption.**

#### 3.2 Qualification Under the Strict Necessity Exemption

The ePrivacy Directive provides an exemption for operations that are **strictly necessary** either for the sole purpose of carrying out a transmission over an electronic communications network, or where access is strictly necessary in order to provide a service explicitly requested by the user. \
The Realtime Cookie Scanner falls within the second limb of this exemption, on the following grounds:

**a) Exclusive compliance and technical audit purpose**

The module performs no user tracking, does not exploit data for marketing or analytical purposes, and produces no profiling. Its sole purpose is to enable the website operator to verify that its own website complies with applicable ePrivacy and GDPR obligations. It is comparable to an internal control or technical audit mechanism — analogous to monitoring tools used by IT and legal teams to verify the compliance of their own systems.

**b) Technical necessity of pre-consent observation**

Execution prior to consent is the sine qua non of the module's core functionality. A tool designed to detect cookies deployed before consent can only operate by observing the browser environment at that precise moment. Restricting the module to post-consent observation would render it unable to detect the very situations of non-compliance it exists to identify. This technical necessity is therefore intrinsic to the service's purpose, not a discretionary implementation choice.

Furthermore, alternative approaches based solely on automated crawler scans present structural limitations that make them insufficient to guarantee exhaustive detection of non-compliant cookie deployments. Crawlers operate on predefined navigation scenarios and cannot reproduce the full range of real user journeys. Certain cookies only appear under specific conditions — rare cookies, cookies triggered by particular user paths, or cookies deployed conditionally depending on technical parameters — that automated scans systematically fail to capture. The real-time observation of actual visitor navigation is therefore not merely a product differentiator: it is the only technically reliable method to achieve comprehensive compliance coverage.

**c) Absence of personal data processing**

The module does not collect cookie values, user identifiers, or browser fingerprints. The metadata observed (cookie names, storage keys, URLs) does not, in itself, allow any individual to be identified. The module is therefore not designed to process personal data within the meaning of the GDPR.

**d) No transfer to advertising or analytical third parties**

Data is transmitted exclusively to Commanders Act servers, strictly within the scope of the compliance service. It is not shared with third parties nor exploited for any other purpose.

#### 3.3 Absence of Personal Data Processing Under the GDPR

To the extent that the data observed by the module does not allow a user to be directly or indirectly identified, the GDPR and the question of a legal basis under Article 6 of the Regulation do not apply.

The legal analysis should therefore be conducted primarily under Article 5(3) of the ePrivacy Directive.

As a subsidiary point, should a supervisory authority consider that certain metadata constitutes personal data in a given context, the legitimate interest of the data controller in ensuring its own regulatory compliance (Article 6(1)(f) GDPR) would constitute a defensible legal basis, subject to the balancing test.

#### 3.4 Position of National Authorities and Documentation Recommendations

Certain supervisory authorities — notably the AEPD (Spain) and German authorities — have historically adopted a particularly strict interpretation of the "strictly necessary" concept for technologies executed in the browser prior to consent.

The technical architecture of the Realtime Cookie Scanner has been designed with these stricter frameworks in mind. The combination of a compliance-exclusive purpose, minimal data collection, absence of any personal data processing, and EU-based data hosting is intended to provide a robust basis for assessment in all European jurisdictions, including those with the most demanding regulatory environments.

#### 3.5 Overall Assessment

It should also be noted that the deployment of a real-time compliance monitoring tool directly serves the organisation's own regulatory interests. Crawler-based approaches, or the absence of continuous monitoring, result in a structurally incomplete view of the website's cookie landscape. The cookies most likely to go undetected — conditional cookies, rare cookies, cookies dependent on specific user journeys — are precisely those most likely to constitute undiscovered ePrivacy violations, and therefore the greatest source of regulatory exposure under scrutinity from the AEPD or any other supervisory authority. In this regard, the Realtime Cookie Scanner is best understood as a risk reduction tool, not a risk factor.\
\
The qualification of the Realtime Cookie Scanner as a compliance monitoring tool — as distinct from a tracking tool subject to consent — is **legally well-founded**. The technical safeguards documented in this paper, taken together, provide a coherent and verifiable basis for that qualification.

***

### 4. Summary of Technical Safeguards

| Criterion                                    | Realtime Cookie Scanner                 |
| -------------------------------------------- | --------------------------------------- |
| Personal data collection                     | No                                      |
| Cookie value collection                      | No                                      |
| User identifiers                             | No                                      |
| Browser fingerprinting                       | No                                      |
| Tracking or profiling purpose                | No                                      |
| Transfer to advertising third parties        | No                                      |
| IP address / user-agent stored or exploited  | No (received via HTTP but not recorded) |
| Technical necessity of pre-consent execution | Yes — inherent to the module's function |
| Exclusive compliance and audit purpose       | Yes                                     |
