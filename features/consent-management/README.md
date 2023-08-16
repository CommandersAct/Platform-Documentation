# Consent management

### Overview

Increase brand loyalty by allowing users to control the data collected about them & establish trust through transparency.As a result of the increasing number of data breaches and the misuse of personal information, privacy management is a growing part of the modern marketing landscape.The General Data Protection Regulation (GDPR) has largely been perceived as a legal issue, due to the fines that can be imposed because of non-compliance, but it’s also created opportunities for brands to build greater trust with their users. In fact, according to research conducted by iProspect, 88% of global marketers say trust is a priority in 2019, and they are looking to build this trust through credibility, relevancy, and reliability.Fueled by consumer privacy laws like the GDPR, most marketers are turning to solutions like Commanders Act CMP that alert website and mobile app users of the personal data that’s being captured, stored, and shared with third parties.This documentation will provide you with an overview of Commanders Act CMP, setup guides per platform, user guides per feature and a knowledge base for frequently asked questions.ComponentsCommanders Act CMP consists of following components:

<figure><img src="https://files.gitbook.com/v0/b/gitbook-legacy-files/o/assets%2F-Lh69-tfWlhrtYE5Vhvq%2F-MUINzGDnAaMAT-OFye3%2F-MUIOcCJa02VKDgokKH0%2FTRUST%20architecture.png?alt=media&#x26;token=f4963dbc-1715-4927-86fd-e68612852865" alt=""><figcaption></figcaption></figure>

| Component       | Description                                                                                                                                                                                                                                                                           |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Privacy banner  | Banner that is shown to visitors to inform them about privacy settings and to ask for permission to collect their personal data.                                                                                                                                                      |
| Privacy center  | Banner that provides fine-grained privacy controls for website visitors for different privacy categories, vendors or tools. The privacy center is usually linked in the privacy banner and privacy policy.                                                                            |
| Privacy manager | A technical layer below the privacy banner and privacy center that manages and stores the privacy settings of the visitor. It connects with other tools like tag managers to control which features, services or tags are loaded for a visitor based on his privacy settings.         |
| Privacy cookies | First party cookies that are used to store the privacy settings of a user.                                                                                                                                                                                                            |
| Privacy log     | A database that logs visitor consent settings so that they can be proofed in case of an information request by the visitor.                                                                                                                                                           |
| Categories      | Groups of services and features that require personal data. These categories are used by the privacy center to present consent controls and are used by the privacy manager to communicate privacy settings to other tools. Typical categories are "Analytics" and "Personalisation". |
| Vendors         | Individual services and vendors that require personal data. These vendors are used by the privacy center to present consent controls and are used by the privacy manager to communicate privacy settings to other tools. Typical vendors are e.g. "Google" and "Facebook".            |
| Dashboard       | Dashboard that provides performance KPIs of each privacy banner.                                                                                                                                                                                                                      |
| OnSite API      | Allows to interact with Consent module with code.                                                                                                                                                                                                                                     |

### Frameworks <a href="#frameworks" id="frameworks"></a>

Commanders Act CMP supports following frameworks:

* IAB TCF 2.0 (v2.2 will be supported before September 30)
* Google ACM

### Extensions <a href="#extensions" id="extensions"></a>

It is possible to extend Commanders Act CMP with following modules:

[Cookie Scanner](extensions/cookie-scanner.md)

[TagFirewall](extensions/tag-firewall.md)

[Tag Hierarchy](extensions/tag-hierarchy.md)

{% hint style="info" %}
These modules are set up and configured by a Commanders Act consultant.
{% endhint %}



### Setup <a href="#setup" id="setup"></a>

Please refer to the Setup Guides section for detailed installation instructions of Commanders Act CMP per platform. In case your platform is not listed you can reach out to a Commanders Act consultant for a custom implementation.

[Setup Guides](setup-guides/)
