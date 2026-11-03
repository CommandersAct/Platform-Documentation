# Capabilities, Security & FAQ

The Commanders Act MCP server is a **read-only connection** between your Commanders Act account and an MCP-compatible AI assistant such as ChatGPT or Claude. It lets the assistant retrieve relevant platform information and help you interpret it. Availability depends on your Commanders Act permissions and which tools or datasets the current integration exposes.

## What can I explore?

| Area                           | Examples of information available                                                                                      |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| **Tag Management (web)**       | Web containers, tags, triggers, datalayer variables, constraints and perimeters                                        |
| **Server-side**                | Server-side containers, tags and datalayer variables                                                                   |
| **Collection & activation**    | Sources, destinations, connector configurations, data cleansing and event enrichments                                  |
| **Data & audiences**           | Normalized datalayer configuration, available CDP segments                                                             |
| **Privacy & monitoring**       | Cookie scanners and detected cookies, consent statistics, collection monitoring, source data quality and health alerts |
| **Reporting & administration** | Available reports and report data, activity logs, accessible sites, users and redirect rules                           |

Some information is subject to additional filters, date ranges, supported site features, and access rights. The assistant cannot infer a live system behavior reliably from configuration alone.

## What the integration cannot do

* **No editing or publishing:** it cannot create, modify, delete or deploy tags, containers, destinations, segments or other Commanders Act objects.
* **No execution guarantee:** finding a configured tag or destination does not prove it actually fired or delivered an event.
* **No automatic view into third-party platforms:** unless you separately connect an external service, it cannot verify what Meta Ads, Google Ads or another external platform recorded.
* **No automatic compliance verdict:** cookie and consent findings help investigate possible issues; they are not legal determinations.
* **AI-generated visuals are client-side capabilities:** charts, flow diagrams and interactive dashboards depend on the assistant you use, not on a separate Commanders Act rendering feature.

## Authentication and permissions

* The MCP uses **OAuth 2.1 with PKCE**. You authenticate through a browser-based Commanders Act sign-in flow; you do not need to paste an API token into your AI conversation.
* **SSO and two-factor authentication (2FA)** are supported where configured for your Commanders Act account.
* Accessible sites and retrieved information are governed by your **Commanders Act user permissions**.
* OAuth sessions are time-limited. If access expires, the AI client may prompt you to sign in again.
* Access to the MCP is currently limited to participating organizations during its controlled rollout.

## What happens to the data?

The MCP retrieves authorized information from Commanders Act and makes the requested results available to your connected AI client. Your AI provider may process the prompts and tool responses according to your organization's contract, provider settings and applicable data policies.

Before connecting an AI assistant, follow your organization's security requirements and review the data-handling terms of the chosen AI provider. **Read-only protects your Commanders Act configuration from modification; it does not mean that retrieved data stays solely within Commanders Act.**

## Frequently asked questions

### Does it change anything in my account?

No. The current MCP offers read-only operations, not configuration changes.

### Does it work with SSO and 2FA?

Yes. Authenticate through the normal Commanders Act login flow, including any configured SSO or 2FA steps.

### Why can my colleague see different sites?

Each user is limited by their Commanders Act permissions. Check that the correct identity is connected.

### Can it explain how a purchase event reaches my marketing destinations?

It can reconstruct the relationships visible in the configuration and produce a diagram, while identifying inferred steps and missing runtime evidence. See the [purchase-event prompt](use-cases-and-prompt-library.md#visualize-the-journey-of-a-purchase-event).

### Can it investigate missing conversions?

It can inspect available health alerts, event monitoring, data quality and activity history to form hypotheses. It cannot diagnose an external advertising-platform discrepancy from Commanders Act data alone.

### Can I use ChatGPT, Claude or another compatible client?

ChatGPT and Claude are supported examples. Other remote-MCP-compatible clients may work, depending on their authentication and workspace capabilities.

### How do I get access or report an issue?

Contact your Commanders Act account or support team. When reporting a problem, include the AI client, the affected site and the operation or question you tried (without sharing credentials).

***

Ready to try it? [Connect your assistant](getting-started-closed-beta.md) or browse the [prompt library](use-cases-and-prompt-library.md).
