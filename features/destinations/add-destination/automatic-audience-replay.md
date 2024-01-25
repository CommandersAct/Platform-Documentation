---
description: For realtime audience based destination
---

# Automatic Audience replay

### Introduction

The "Automatic Audience Replay" feature is designed to enhance dynamic segments usage within real-time audience-based destinations like Facebook Custom Audiences.

### Background

In our previous system, for real-time audience-based destinations, only users who joined a segment after the creation of the destination were automatically sent to that destination. This approach overlooked users who were already in the segment. The Audience Replay feature rectifies this by ensuring that all segment users, both existing and new, are sent to the relevant destination.

### The Audience Replay Feature

#### Simplified Process

* **When Creating a Destination**:
  * **Immediate Activation**: If the destination is activated immediately, an operation is launched to send all users from the segment to the destination without delay.
  * **Scheduled Activation**: For destinations set to activate later, an operation is scheduled to send all users in the segment to the destination at the specified start time.
* **When Updating a Destination**:
  * **Reactivation/Modification**: Some updates to the destination (changing start times or timezones) automatically initiates an operation to send all segment users to the updated destination.
  * **Adding New Segments**: Incorporating new segments into the destination triggers an operation to send only the users from these new segments.

#### Supported Destinations

This feature works seamlessly with various real-time, audience-based destinations, including:

* Facebook Custom Audiences
* Google Customer Match
* Criteo Audiences
* Google Ads Customer Match
* Rakuten
* Google DDP

#### Benefits

* **Comprehensive User Engagement**: Ensures every historical relevant user in the segment is sent to the destination, enhancing audience coverage.
* **Efficient Automation**: Reduces manual efforts and error potential, streamlining the process of managing audience data.
* **Current and Relevant Audience Data**: Keeps your audience segments up-to-date, maximizing the impact of your marketing efforts.
