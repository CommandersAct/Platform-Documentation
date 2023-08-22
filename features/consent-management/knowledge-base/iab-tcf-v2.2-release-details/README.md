# IAB TCF V2.2 Release details

## Introduction

In February last year, the Belgian Data Protection Authority (APD, “Autorité de Protection des Données”) issued a decision against IAB Europe related to the Transparency and Consent Framework (TCF), fining the organization 250k€ and instructing it to come up with a plan to solve the issues that were identified.

Since then, IAB Europe has come up with a plan to update its TCF, which will come into action over the following months. In this article, we review the context surrounding the APD decision, catching you up on the events from last before presenting IAB Europe’s action plan, and finally going over what these changes will mean in practice for Commanders Act users.

March 2023 update: On March 15th, 2023, IAB Europe confirmed that the Belgian APD has voluntarily suspended the six-month implementation period of IAB Europe’s action plan. As a result, the July 2023 deadline no longer applies. It’s now reported for Q4 2023

For more details and pending additional information, read the official IAB [communication here](https://iabeurope.eu/all-news/iab-europe-obtains-suspension-of-tcf-action-plan-implementation-due-to-ongoing-proceedings/).\


## Context about the Belgian APD and the Transparency and Consent Framework

More than a year ago, on February 2nd, 2022, the Belgian APD issued a decision against IAB Europe citing 4 issues with its Transparency and Consent Framework (what’s the TCF? Learn more [here](https://iabeurope.eu/transparency-consent-framework/)). According to the Belgian APD:

The Transparency & Consent (TC) string, the consent signal stored by players in the advertising industry, is personal information. As such, participants should establish a legal basis.

IAB Europe is a data controller of that information, whether or not it processes the consent information

IAB Europe is a joint controller with TCF participants (vendors, CMPs, publishers)

Security measures in place to protect the integrity of the consent signal were not sufficient

IAB Europe was subsequently fined and instructed to come up with an action plan to solve these issues. The IAB Europe, along with some TCF participants, has worked on the action plan and submitted it to the APD in April 2022. Despite additional procedural events in September, the action plan was reviewed on January 11th by the Belgian APD.

Of course, we will communicate with Commanders Act customers with specific action points before then.

## What is going to change in 2023 for the TCF?

Here are the main changes and obligations that will impact your Consent Management Platform if you’re using the TCF after April 2023:

**New TC string special purpose**

Users of the TCF will be required to add a new (special) purpose to the classification of purposes in the TCF, informing their users that they are capturing and sharing data subject choices via the TC String.

**No more legitimate interest for targeted advertising**

Going forward, users won’t be able to rely on legitimate interest for personalized advertising.

Specifically, the purposes impacted will be purpose 3 (create a personalized ads profile), purpose 4 (select personalized ads), purpose 5 (create a personalized content profile), and purpose 6 (select a personalized content profile).

**Mandatory disclosures in the second layer of the CMP**

After April, users of the TCF will be required to disclose new information in their CMP second layer:

* The legitimate interests at stake
* The categories of data collected and/or already held by Vendors
* The retention periods (in the Vendors’ description)

**Vendor-related changes**

Publishers will be presented with a warning about the impact that a large number of vendors can have on the ability of users to make informed choices.

Additionally, the **number of vendors will need to be disclosed in the first layer** of the CMP. Finally, we will recommend using event listeners to ensure proactive communication of changed TC String to vendors.&#x20;

## As a Commanders Act customer, what am I supposed to do?

As a Commanders Act customer, what do these changes in the TCF mean and what are you supposed to do? Don’t worry, we’ve got it all planned out.

Not a lot will be expected from Commanders Act customers. However, if you decide to continue using the Transparency and Consent Framework, you must know that consent notices/consent banners will be changing slightly (based on the changes listed in the previous section), and you should therefore be ready for it.

The migration from the **TFC v2.2 will take place in September 30, 2023** serving as the hard deadline for the change. You will be must to **regenerate your consent banners TCF before this deadline.**

Once the migration will be complete, **we will recommend that you recollect consent from your customers**, as previously collected consent was deemed invalid following the Belgian APD decision.  Additionally, you’ll most likely have to reduce your vendor list, and updating mobile SDK versions to get the new TCF various updates will be compulsory.

But don’t worry, we will remind you about this before the deadline.

## Conclusion

To conclude, and while it’s important to be aware of the upcoming changes following this important industry decision, the impact on Commanders Act customers should be minimal, and we’re hoping to provide thorough assistance to everyone along the way\
\
If you wish to go further, you will be able to verify your TCF compliancy, since IAB Europe has released a new CMP Validator Chrome Extension available [here](https://chrome.google.com/webstore/detail/cmp-validator/ffhhjklgcfabkpholngojpkijlafjooc) that includes all requirements of TCF v2.2.\
