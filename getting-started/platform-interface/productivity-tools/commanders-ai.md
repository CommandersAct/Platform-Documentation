---
description: Technical documentation on the use of artificial intelligence in the platform
---

# Commander's AI

## 1. Introduction

### 1.1. Overview of Commander's AI

**Commander's AI** is a set of artificial intelligence features integrated into the **Commanders Act** platform.\
These features leverage advanced language models (**LLM**) to optimize and automate various tasks.\
Its goal is to simplify and optimize tag management, data handling, insights, file import and destination configurations through natural language processing models.

The functionalities of Commander's AI are designed to:

* Improve user efficiency by automating repetitive tasks.
* Simplify data management and transformation.
* Ensure tag and destination compliance with privacy regulations.
* Assist users in optimizing configurations through intelligent suggestions.
* Accelerate and simplify complex tasks for users.
* Improve the quality and standardization of configurations/data.

{% hint style="info" %}
All Commanders AI suggestions are non-binding and subject to human validation. Users remain responsible for verifying any AI-generated content before applying it in production.
{% endhint %}

### 1.2. Key AI Features

Commanders AI includes several advanced functionalities (some are limited to beta testers) :

1. [**Automatic Change Summary**](commanders-ai.md#id-2.1-automatic-change-summary-in-web-containers): Generates a summary of modifications when generating a web container in the Tag Management System.
2. [**Cookie description translation/categorisation**](../../../features/realtime-cookie-scanner/): Find missing description/categorisation in Realtime Cookie Scanner, translate cookie descriptions in other languages
3. [**AI Copilot for Data Cleansing**](commanders-ai.md#id-2.2.-ai-copilot-for-data-cleansing-closed-beta) : Conversational assistant to generate or explain data transformation formulas.
4. [**Smart Suggestions**](commanders-ai.md#id-4.-smart-suggestions-for-names-and-descriptions-closed-alpha) (closed alpha): Optimized naming and description proposals for destinations and segments.
5. [**Automated Privacy Category Classification**](commanders-ai.md#id-5.-automatic-privacy-category-selection-closed-alpha) (closed alpha): Intelligent assignment of privacy categories when adding a tag or destination.
6. [**AI-assisted File Import Configuration**](commanders-ai.md#id-2.5.-ai-assisted-file-import-configuration): Automatic detection of file structure and suggested mapping between CSV columns and purchase event properties.

***

## 2. AI Features Description

### 2.1. Automatic Change Summary in Web containers

#### Feature Overview

When a user generates a web container in the **Tag Management System (TMS)**, Commander's AI analyzes the modifications and provides an automatic summary of the changes made since the last container generation.

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="305"><figcaption></figcaption></figure>

#### How It Works

1. The AI identifies changes made: additions, deletions, or modifications of tags, variables, triggers, etc.
2. An AI-based summarization algorithm generates a concise and readable description of the modifications.
3. The summary is displayed before the container is generated for user validation.

#### Customization and Validation

Users can manually edit the proposed summary before validation. This ensures the content meets expectations and facilitates team collaboration.

#### Personalization Options

Users have access to additional customization options via the gear icon ⚙️:

* **Summary Length**: Choose between short, medium, or detailed summaries.
* **Custom Prompting**: Define specific formatting rules or content guidelines for the AI to follow when generating summaries. Users can specify formatting or content preferences, such as writing in uppercase, adding emojis, structuring summaries with bullet points, (e.g., "Write in uppercase with emoticons with max 5 bullet points"). This allows for greater adaptability to specific workflows or reporting standards.

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="354"><figcaption></figcaption></figure>

***

### 2.2. AI Copilot for Data Cleansing

#### Feature Overview

Commanders AI includes a **conversational assistant (aka AI copilot)** that enables users to formulate queries for generating/explaining data transformation formulas tailored to specific data cleansing needs.

#### How It Works

1. The user interacts with the AI Copilot using natural language to describe a data transformation or asking an explanation.
2. The AI copilot interprets the request and suggests a transformation formula / explaination.
3. The user can test, modify, and apply the formula before final integration.

#### Use Cases

* Conditional values
* Converting date formats.
* Cleaning invalid values...

#### Verification and Adjustment

Users can edit and test the generated formulas to ensure they meet their requirements before applying them. Each generation includes a reminder that the result should be validated by the user.

***

### 2.3. Smart Suggestions for Names and Descriptions (closed alpha)

#### Feature Overview

When configuring destinations, segments in Commanders Act, Commanders AI suggests names and descriptions based on usage context.

#### How It Works

1. When a relevant field is detected (destination name, segment description, etc.), the AI analyzes existing data and suggests suitable content.
2. The user can accept, modify, or ignore the suggestion.
3. Suggestions adapt based on usage trends and best naming practices.

#### Use Cases

* Generating a destination name based on destination's settings and filters.
* Proposing a detailed description for a segment

***

### 2.4. Automatic Privacy Category Selection (closed alpha)

#### Feature Overview

When a user adds a **client-side tag in the TMS** or configures a **destination**, Commanders AI automatically suggests an appropriate privacy classification.

#### How It Works

1. The AI analyzes the tag or destination metadata.
2. A **privacy category** is suggested based on best practices and applicable regulations.
3. The user can validate, adjust, or modify the suggestion before final approval.

#### Customization and Validation

Users retain full control over the classification and can adjust the suggestion as needed.

***

### 2.5. AI-assisted File Import Configuration

#### Feature Overview

When configuring a file import source for conversion imports, Commanders AI can assist users by analyzing the sample file provided during setup.

The AI helps detect the file structure and proposes a pre-filled configuration to reduce manual setup effort and configuration errors.

#### How It Works

1. The user provides a sample file during the file import source configuration.
2. Commanders AI analyzes the structure of the file.
3. The AI suggests the appropriate column separator and item separator.
4. The AI proposes a pre-filled mapping between the CSV columns and the purchase event properties to be created.
5. The user reviews, adjusts, and validates the proposed configuration before activation.

#### Use Cases

* Accelerating setup of recurring conversion imports.
* Reducing configuration errors during import source creation.

#### Customization and Validation

The proposed configuration is only a suggestion. Users must review and validate the detected separators and proposed mappings before saving or activating the import source.

Users remain responsible for ensuring that the sample file is appropriate for AI processing and should avoid providing unnecessary personal data in sample files whenever possible.

## **3. Transparency and Accountability**

#### **3.1. Clear Identification of AI-Generated Content**

All **Commanders AI** features include explicit labels indicating AI usage:

* **Visible UI labels/icon** such as "AI-Generated", "AI Suggestion", "AI Copilot" or ✨icon
* **User Control**: Users can modify/verify AI-generated content to prevent unwanted automation.

#### **3.2. Human Oversight**

Users **always retain final control** over actions suggested or performed by **Commander's AI**. The AI does **not make irreversible autonomous decisions**.

#### **3.3. Data Privacy and Security**

Commanders AI complies with **GDPR** and the **AI Act**:

✔ **Transparency**: Explicit labeling of AI-powered functionalities.\
✔ **Human Oversight**: No AI action is irreversible.\
✔ **Data Privacy**: Generated suggestions and content are not stored/used for training purposes. User data remains within the scope of its intended use and is not shared externally.\
✔ **Technical Documentation**: Full traceability and governance of AI models are maintained.

Commanders AI processes inputs exclusively within EU-hosted infrastructure using vendors that guarantee strict data isolation, non-retention and full alignment with GDPR and the EU AI Act. No model provider receives any customer data for training or reuse.

#### 3.4. Scope of AI Usage and Data Boundaries

As of today, Commander's AI does **not process or analyze any personal data or event payloads** collected via the Tag Management System (TMS) or the Customer Data Platform (CDP).

Depending on the feature, Commanders AI may process configuration-level metadata, user-provided prompts, structural fields, or sample data explicitly provided by the user for configuration purposes.

Its usage is limited to assistance scenarios such as:

* Generating summaries of tag management changes.
* Assisting in writing regex, expressions, or formulas based on metadata or structural fields.
* Suggesting field names or descriptions based on metadata.
* Classifying tags or destinations based on structural criteria.
* Analyzing user-provided sample files to detect file structure, separators, and suggest mappings for file import configurations.

For the AI-assisted file import configuration feature, Commanders AI may analyze the sample file provided by the user in order to detect its structure and suggest a mapping between CSV columns and `purchase` event properties.

Commanders AI does not autonomously activate imports, create production configurations, or make irreversible decisions. All AI-generated configuration suggestions must be reviewed and validated by the user before use.

Users are responsible for ensuring that any sample file submitted for configuration assistance contains only the data necessary for setup purposes. Where possible, sample files should be anonymized, minimized, or limited to representative structural data.

**Applicability of German Works Council (Betriebsrat)**\
Commanders AI is designed to provide configuration assistance and does not aim to monitor employees, evaluate employee performance, or profile individual users. It does not make autonomous decisions about users or employees.\
If the scope of Commanders AI were to expand in the future to process behavioural data or data that could be used for employee monitoring, this would be documented and communicated accordingly.

#### 3.5. EU AI Act Compliance

Commanders AI falls under the **low-risk category** as defined by the European AI Act.\
It provides only configuration assistance and suggestions, with **no autonomous or irreversible decisions**.\
This means that the existing measures already described (transparency, human oversight, governance, EU hosting) ensure full compliance with the obligations applicable to low-risk AI systems.

#### 3.6. Summary for DPOs, Datenschutz and Works Councils

This section summarises the key compliance questions typically required by DPOs and German Works Councils (§87 BetrVG).

**Which AI models are used?**\
Commanders Act uses advanced Large Language Models (LLMs) selected for reliability and compliance.\
For security and contractual reasons, and because our underlying models may evolve over time or be combined to improve performance and reliability, we do not publicly disclose individual model names or vendors.\
All models we use operate under the strict EU hosting, GDPR and AI Act rules described on this page.

**What data do the models have access to?**\
Depending on the feature used, AI models may access configuration-level metadata, user-provided prompts, structural fields, or sample files explicitly provided by the user for configuration assistance, such as:\
– tag names, cookie descriptions, segment descriptions\
– transformation formulas\
– structural metadata\
– sample CSV content provided during file import source configuration\
– column names and representative values used to suggest mappings\
For AI-assisted file import configuration, the AI analyzes the sample file only to detect its structure and propose a mapping between CSV columns and purchase event properties.

AI models do not access customer databases directly and do not autonomously retrieve event payloads from the platform. Any sample file analyzed by the AI is provided by the user for the purpose of configuring the import source.

**Where is the AI hosted?**\
All processing related to Commanders AI is fully hosted within the European Union.\
No data leaves the EU at any stage.

**What data is used to train the models?**\
No customer data is ever used to train or fine-tune any model.\
All models are pre-trained by their providers on public or generic corpora only.

**Where is data stored, and for how long?**\
Commanders AI is designed around strict non-retention principles for AI processing.\
As described above, model providers do not retain customer data for training or reuse.\
This page describes the AI processing scope only. For any retention that may apply at the platform level (for example support handling, audit, or operational logs), please refer to your contractual and security documentation.

## 4. AI Model Governance and Updates

### 4.1. Models Used

Commanders AI is based on a combination of **advanced language models (LLMs)** carefully selected for their efficiency in **data management and tag management tasks**. These models may evolve over time and can be combined depending on the use case, in order to continuously improve performance, reliability, and relevance for our users. Any future models will be selected in accordance with the same security, compliance, and data protection commitments outlined in this documentation.

### 4.2. Updates and Monitoring

* Models are regularly updated to ensure **accuracy and relevance**.
* Validation tests are performed before each deployment to reduce biases and improve reliability.

### 4.3. Security and Privacy

Commanders AI ensures full compliance with European regulations (AI Act, GDPR) by enforcing strict rules on data processing, model selection, and infrastructure localization.

* AI-generated content is not stored for reuse or retraining.
* We do **not** fine-tune models on customer data and select only vendors that guarantee data isolation and full alignment with EU laws (GDPR, AI Act).
* Suggestions are based solely on technical and contextual criteria, including configuration metadata, structural fields, user-provided prompts, or user-provided sample files when required for a specific configuration assistance feature.

### 4.4. Model Origin and Hosting Transparency

Commanders AI uses Large Language Models chosen under strict criteria for performance, privacy, and legal compliance.

* **Model provider location:** **If** a model is provided by a non-European vendor, we ensure that it is **hosted entirely within the EU**.
* User data never leaves the EU (no transfer, no storage outside the EU).

\
To illustrate this approach, some of the models we evaluate or integrate may be provided by European players such as **Mistral**, when they meet the same high standards. However, the determining criterion remains EU hosting and compliance with our security and regulatory requirements, regardless of the provider’s origin.
