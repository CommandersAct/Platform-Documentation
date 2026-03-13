---
description: Realtime Cookie Scanner
---

# Legal and Technical Position Paper

#### For DPOs, Legal Teams and Compliance Officers

***

### 1. Purpose of this Document

This document presents the technical operation of the Commanders Act Realtime Cookie Scanner module, and provides legal and compliance teams with the information required to assess its regulatory qualification.

It describes the technical functioning of the module and the technical metadata it observes, followed by a legal analysis of its operation under Article 5(3) of the ePrivacy Directive and an explanation of why the module does not involve the processing of personal data within the meaning of the GDPR.

The document also outlines the technical safeguards implemented to ensure that the module operates exclusively as a compliance monitoring tool.

***

### 2. Technical Operation of the Module

#### 2.1 Nature and Purpose of the Module

Realtime Cookie Scanner is a JavaScript module executed in the visitor's browser. Its sole purpose is to enable website operators to verify that their websites comply with applicable rules governing the deployment of cookies and similar technologies, in particular the requirements arising from the ePrivacy framework.

Concretely, the module enables operators to:

* maintain an up-to-date inventory of cookies present on their website;
* identify the technical sources responsible for the creation of cookies;
* detect cookies that appear before user consent or after a refusal;
* monitor changes in cookie usage over time;
* support internal privacy and compliance audits.

#### 2.2 Technical Operations Performed

The module performs the following operations in the browser:

* reading the **names of cookies** present in the browser via `document.cookie`;
* reading the **keys present in `localStorage`**;
* reading the **keys present in `sessionStorage`**;
* attempting, on a best-effort basis, to identify the **technical sources** potentially associated with cookies, where technically possible;
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

* cookie values or any identifier associated with an individual user
* browser fingerprints
* behavioural or analytical data

**Note on IP address and user-agent:** when the module transmits metadata to Commanders Act servers, an HTTP request is initiated by the browser. As part of the normal functioning of the HTTP protocol, such requests inherently contain technical information including the sender’s IP address and user-agent string. These elements are not collected or used by the module for the purposes of the service and are not processed as part of the cookie scanning functionality.

#### 2.4 Data Hosting and Transfer

All technical metadata transmitted by the module is sent exclusively to Commanders Act servers hosted within the European Union. No data is transferred to servers located outside the EU.

#### 2.5 Execution Prior to Consent

The module executes at page load, independently of the user's consent status.

This is not an arbitrary design choice. In order to detect cookies that may appear before user consent or after a refusal, the module must be able to observe the browser environment at the moment the page is loaded. If the module were triggered only after consent had been collected, certain situations of non-compliant cookie deployment could not be detected.

The module subsequently monitors changes in consent status via the CMP API in order to compare cookie presence before and after the user's decision.

***

### 3. Legal Analysis

#### 3.1 Scope of Article 5(3) of the ePrivacy Directive

Article 5(3) of the ePrivacy Directive requires prior consent for any operation involving **access to information stored in the user's terminal equipment**, or the storing of information therein, regardless of whether that information constitutes personal data.

The Realtime Cookie Scanner, insofar as it accesses cookies and storage keys present in the browser, falls within the scope of this provision. This is acknowledged.

The relevant legal question is therefore whether this access can be considered strictly necessary for the provision of the service.

The module is not designed to track or identify users, and its operation can be assessed in light of the strict necessity exemption for the reasons set out below.

#### 3.2 Qualification Under the Strict Necessity Exemption

The ePrivacy Directive provides an exemption for operations that are **strictly necessary** either for the sole purpose of carrying out a transmission over an electronic communications network, or where access is strictly necessary in order to provide a service explicitly requested by the user. The relevant question is therefore whether the operation of the Realtime Cookie Scanner may fall within the second limb of this exemption, namely where access to the terminal equipment is strictly necessary for the provision of a service. This assessment can be examined on the following grounds:

**a) Exclusive compliance and technical audit purpose**

The module performs no user tracking, does not exploit data for marketing or analytical purposes, and produces no profiling. Its sole purpose is to enable the website operator to verify that its own website complies with applicable ePrivacy and GDPR obligations.

In this respect, the module operates as a technical monitoring tool intended to support internal compliance verification by the website operator.

**b) Technical necessity of pre-consent observation**

Execution prior to consent is closely linked to module's core functionality. A tool designed to detect cookies deployed before consent must be able to operate by observing the browser environment at that precise moment. Restricting the module to post-consent observation would prevent it from detecting precisely the situations of non-compliant cookie deployment that the module is designed to identify. This operational requirement therefore stems directly from the service’s purpose rather than from a discretionary implementation choice.

In practice, approaches based solely on automated crawler scans present structural limitations when attempting to detect certain categories of cookie deployments.

Crawler-based scans generally rely on predefined navigation scenarios and cannot reproduce the full diversity of real user navigation paths.

Certain cookies only appear under specific conditions, rare cookies, cookies triggered by particular user paths, or cookies deployed conditionally depending on technical parameters, which may not always be captured through automated scanning scenarios.

Because the purpose of the module is precisely to identify situations of non-compliant cookie deployment, the observation of real navigation conditions becomes necessary to achieve this objective.

Crawler-based approaches cannot reliably replicate the full range of real navigation conditions, making real-time observation the most reliable method for ensuring comprehensive detection of non-compliant cookie deployments.

**c) Absence of personal data processing**

The module does not collect cookie values, user identifiers, or browser fingerprints. The metadata observed (cookie names, storage keys, URLs) is processed solely for the purpose of establishing a technical inventory of cookies deployed on the website and is not used to identify individual users. Accordingly, the module is not designed to process personal data as part of its functional purpose.

**d) No transfer to advertising or analytical third parties**

Data observed by the module is transmitted exclusively to Commanders Act servers, for the purpose of providing the compliance monitoring service. It is not shared with advertising or analytical third parties and is not used for marketing, tracking or profiling purposes.

#### 3.3 Absence of Personal Data Processing Under the GDPR

To the extent that the metadata observed by the module does not allow a user to be directly or indirectly identified, the module is not designed to process personal data as part of its functional purpose.

Accordingly, the legal analysis of the module primarily concerns the application of Article 5(3) of the ePrivacy Directive.

As a subsidiary point, should a supervisory authority consider that certain technical metadata could qualify as personal data in a specific context, the legitimate interest of the data controller in ensuring its own regulatory compliance (Article 6(1)(f) GDPR) would constitute a legal basis, subject to the balancing test.

#### 3.4 Position of National Authorities and Documentation Recommendations

Certain supervisory authorities, notably the AEPD (Spain) and German authorities, have historically adopted a particularly strict interpretation of the "strictly necessary" concept for technologies executed in the browser prior to consent.

The technical architecture of the Realtime Cookie Scanner has been designed with these stricter regulatory interpretations in mind. The combination of a compliance-exclusive purpose, minimal data collection, absence of personal data processing as part of the module’s functional design, and EU-based data hosting is intended to provide a robust basis for assessment by organizations operating across different European jurisdictions, including those applying particularly demanding regulatory standards.

#### 3.5 Overall Assessment

The deployment of a real-time compliance monitoring tool may contribute to an organization’s ability to identify and manage potential regulatory risks related to cookie deployment.

Approaches based solely on automated crawler scans, or the absence of continuous monitoring mechanisms, may in certain circumstances provide only a partial view of the cookies effectively deployed on a website.

Certain categories of cookies, such as conditional cookies, cookies triggered by specific navigation paths, or cookies deployed only in particular technical contexts, may therefore remain more difficult to detect without observation in real navigation conditions.

In this regard, the Realtime Cookie Scanner can contribute to reducing an organization’s regulatory exposure by helping identify potential situations of non-compliant cookie deployment.

On this basis, the module may reasonably be characterized as a compliance monitoring tool, rather than as a tracking technology designed to analyze or profile user behavior.

The technical safeguards described in this document contribute to supporting this qualification.

***

### 4. Summary of Technical Safeguards

| Criterion | Realtime Cookie Scanner |
| --- | --- |
| Personal data collection | No (the module is not designed to collect personal data as part of its functional purpose) |
| Cookie value collection | No |
| User identifiers | No |
| Browser fingerprinting | No |
| Tracking or profiling purpose | No |
| Transfer to advertising third parties | No transfer to advertising or analytics third parties |
| IP address / user-agent stored or exploited | No (technical transmission via HTTP may occur but these elements are not stored or used by the module) |
| Technical necessity of pre-consent execution | Yes — linked to the module’s function of detecting cookies appearing before consent |
| Exclusive compliance and audit purpose | Yes |
