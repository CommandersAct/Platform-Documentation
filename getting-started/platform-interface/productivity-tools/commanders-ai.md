---
description: Commander's AI - Technical Documentation
---

# Commander's AI

## 1. Introduction

#### 1.1 Overview of Commander's AI

**Commander's AI** is a set of artificial intelligence features integrated into the **Commanders Act** platform. Its goal is to simplify and optimize tag management, data handling, and destination configurations through natural language processing models.

The functionalities of Commanders AI are designed to:

* Accelerate and simplify complex tasks for users.
* Improve the quality and standardization of configurations.
* Ensure better consistency and reliability of processed data.
* Assist users in implementing best practices.

#### 1.2 Key Features

Commanders AI includes several advanced functionalities:

1. **Automatic Change Summary**: Generates a summary of modifications when generating a web container in the Tag Management System.
2. **AI Copilot for Data Cleansing**: Conversational assistant to generate data transformation formulas.
3. **Smart Suggestions**: Optimized naming and description proposals for destinations and segments.
4. **Automated Privacy Category Classification**: Intelligent assignment of privacy categories when adding a tag or destination.

***

### 2. Automatic Change Summary in Web containers

#### 2.1 Feature Overview

When a user generates a web container in the **Tag Management System (TMS)**, Commander's AI analyzes the modifications and provides an automatic summary of the changes made.

<figure><img src="../../../.gitbook/assets/image.png" alt="" width="305"><figcaption></figcaption></figure>

#### 2.2 How It Works

1. The AI identifies changes made: additions, deletions, or modifications of tags, variables, triggers, etc.
2. An AI-based summarization algorithm generates a concise and readable description of the modifications.
3. The summary is displayed before the container is generated for user validation.

#### 2.3 Customization and Validation

Users can manually edit the proposed summary before validation. This ensures the content meets expectations and facilitates team collaboration.

#### 2.4 Personalization Options

Users have access to additional customization options via the gear icon ⚙️:

* **Summary Length**: Choose between short, medium, or detailed summaries.
* **Custom Prompting**: Define specific formatting rules or content guidelines for the AI to follow when generating summaries. Users can specify formatting or content preferences, such as writing in uppercase, adding emojis, structuring summaries with bullet points,  (e.g., "Write in uppercase with emoticons with max 5 bullet points"). This allows for greater adaptability to specific workflows or reporting standards.

<figure><img src="../../../.gitbook/assets/image (2).png" alt="" width="354"><figcaption></figcaption></figure>

***

### 3. AI Copilot for Data Cleansing (closed beta)

#### 3.1 Feature Overview

Commanders AI includes a **conversational assistant (aka AI copilot)** that enables users to formulate queries for generating data transformation formulas tailored to specific data cleansing needs.

#### 3.2 How It Works

1. The user interacts with the AI Copilot using natural language to describe a data transformation.
2. The AI copilot interprets the request and suggests a transformation formula.
3. The user can test, modify, and apply the formula before final integration.

#### 3.3 Use Cases

* Conditional values
* Converting date formats.
* Cleaning invalid values...

#### 3.4 Verification and Adjustment

Users can edit and test the generated formulas to ensure they meet their requirements before applying them. Each generation includes a reminder that the result should be validated by the user.

***

### 4. Smart Suggestions for Names and Descriptions  (closed alpha)

#### 4.1 Feature Overview

When configuring destinations, segments in Commanders Act, Commanders AI suggests names and descriptions based on usage context.

#### 4.2 How It Works

1. When a relevant field is detected (destination name, segment description, etc.), the AI analyzes existing data and suggests suitable content.
2. The user can accept, modify, or ignore the suggestion.
3. Suggestions adapt based on usage trends and best naming practices.

#### 4.3 Use Cases

* Generating a destination name based on destination's settings and filters.
* Proposing a detailed description for a segment

***

### 5. Automated Privacy Category Classification  (closed alpha)

#### 5.1 Feature Overview

When a user adds a **client-side tag in the TMS** or configures a **destination**, Commanders AI automatically suggests an appropriate privacy classification.

#### 5.2 How It Works

1. The AI analyzes the tag or destination metadata.
2. A **privacy category** is suggested based on best practices and applicable regulations.
3. The user can validate, adjust, or modify the suggestion before final approval.

#### 5.3 Customization and Validation

Users retain full control over the classification and can adjust the suggestion as needed.

***

### 6. AI Model Governance and Updates

#### 6.1 Models Used

Commanders AI is based on a combination of **advanced language models (LLMs)** and specialized algorithms for classification and metadata analysis.

#### 6.2 Updates and Monitoring

* Models are regularly updated to ensure **accuracy and relevance**.
* Validation tests are performed before each deployment to reduce biases and improve reliability.

#### 6.3 Security and Privacy

* AI-generated content is not stored for reuse or retraining.
* Suggestions are based solely on technical and contextual criteria without exploiting personal data.

***

### 7. Support and Assistance

For any technical questions or issues related to **Commanders AI**, contact our support team at support@commandersact.com&#x20;
