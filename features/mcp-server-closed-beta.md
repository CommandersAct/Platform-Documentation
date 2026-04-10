# MCP server (closed beta)

### Commanders Act MCP Server Setup Guide

This guide explains how to connect Claude (or chatGPT, etc.) to the Commanders Act MCP server so your team can experiment with AI access to Commanders Act through the standard Model Context Protocol.

### 1. Overview

The Commanders Act MCP server exposes Commanders Act platform capabilities as AI-callable tools through the standard Model Context Protocol.

It is designed to be consumed by MCP compatible AI clients, without requiring any proprietary integration.

The server uses OAuth 2.1 with PKCE for authentication and exposes a wide range of tools covering Sources, Destinations, Enrichments, Cleansing, Tag Management, Health, Reports and Admin.

The MCP server is currently in **closed beta**. At this stage, only a limited number of users are testing it.

Typical use cases include:

* discovering the sites available to the authenticated user
* exploring Sources, Destinations, Enrichments, Cleansing, Health, Reports, Tag Management, and Admin data
* using Commanders Act data through AI workflows without building a proprietary integration

### 2. Access conditions

Because the MCP server is currently in closed beta, access is not yet generally available. At this time, we are not accepting new users, but you can contact support team to be added to the waiting list.

### 3. Requirements

To use the Commanders Act MCP server, you need:

* a Commanders Act account
* access to the MCP server as part of the closed beta
* an MCP compatible AI client
* a browser available for the authentication flow

***

### 4. Authentication

The Commanders Act MCP server uses OAuth 2.1 with PKCE.

The authentication flow is fully automatic and secure. No token is manually handled or exposed to the user.

Typical flow:

1. The client attempts to call the MCP server
2. The server indicates that authentication is required
3. The client automatically discovers the authentication flow
4. A browser window opens with the Commanders Act login page
5. The user logs in with their Commanders Act credentials
6. The client securely completes the authentication process
7. The client includes the token in all subsequent tool calls

Once authenticated, the connection is established and all interactions with the MCP server are seamless.

***

### 5. Connecting an MCP client

The Commanders Act MCP server is exposed through a standard MCP interface.

To connect a compatible AI client, you need to register the MCP server using the connection details provided by the Commanders Act support team.

Depending on the client, this may involve:

* adding the MCP server in a UI
* or declaring it in a configuration file

Once configured, the authentication flow will start automatically on first use.

***

### 6.a. Example client environment: Claude Code

Claude Code is one example of an MCP compatible client.

To connect the Commanders Act MCP server:

1. Open Claude
2. Go to Settings → Integrations
3. Enable the connector named “Commanders Act MCP”
4. When prompted, enter the MCP server URL provided by Commanders Act
5. Complete the authentication flow in the browser

Once connected, you can start using the MCP server directly in conversations.

To verify the connection, you can ask:

“Can you list the available tools from the Commanders Act MCP?”

You should see all available tools exposed by the server.



### 6.b. Example client environment: ChatGPT

ChatGPT is another MCP compatible client.

To connect the Commanders Act MCP server:

1. Open ChatGPT
2. Go to Settings → Apps & Connectors → Advanced
3. Enable Developer Mode
4. Go to Connectors and create a new connector
5. Use the MCP server connection details provided by Commanders Act
6. Select OAuth as the authentication method
7. Save the connector

To use the MCP server in a conversation:

1. Start a new chat
2. Enable Developer Mode in the chat
3. Add the Commanders Act connector as a source

Once connected, ChatGPT will be able to call MCP tools directly.

To validate the connection, you can ask:

Can you list the available tools from the Commanders Act MCP?

ChatGPT will display tool calls in the interface. Some actions may require confirmation.

***

### 7. Available tool families

The MCP server exposes more than 35 tools across the following areas:

**Profile**

* list accessible sites for the authenticated user

**Sources**

* list source categories
* list configured sources
* retrieve source details

**Destinations**

* list destination categories
* list configured destinations
* retrieve destination details

**Enrichments and Cleansing**

* list enrichments
* retrieve enrichment details
* list cleansing transformations
* retrieve transformation details

**Health and Monitoring**

* retrieve source data quality
* retrieve cookie scanners
* retrieve scanner cookies
* retrieve scanner install code
* retrieve collection monitoring data
* retrieve privacy statistics
* retrieve health alerts
* retrieve health notifications

**Tag Management**

* list web containers
* retrieve container details
* list web datalayer variables
* list web triggers
* list web constraints
* list web perimeters
* list server-side containers
* list server-side datalayer variables
* list server-side tags

**Explore and Reports**

* list reports
* retrieve report data

**Data Management**

* retrieve normalized datalayer

**Admin**

* retrieve activity logs
* list users
* list redirect rules

***

### 8. First validation

After connecting and authenticating, you can validate the integration with a simple natural language request.

Recommended prompt:

Can you list the sites available to my Commanders Act account?

You can also verify that the MCP server is correctly connected by asking:

Can you list the available tools from the Commanders Act MCP?

This confirms:

* authentication is working
* the MCP connection is active
* the tools are correctly exposed
* your permissions are correctly applied

You can then continue with prompts such as:

Can you list the configured sources for my account?\
Can you show me the configured destinations?\
Can you show me current health alerts?\
Can you list the available web containers?\
Can you list the available reports?

***

### 9. Token lifetime

Access tokens are time limited.

The default lifetime is 8 hours.

When the token expires, a new authentication is required.

***

### 10. Troubleshooting

Login page does not open\
Make sure your client supports MCP with authentication and that a browser can be launched

Authentication does not complete\
Verify that the MCP server connection details provided by support are correct and reachable

Tools do not appear in Claude\
Make sure the “Commanders Act MCP” connector is enabled and authentication completed

You can validate by asking:

Can you list the available tools from the Commanders Act MCP?

If no tools appear, try reconnecting the MCP server or restarting the session

Connection works but no data is returned\
Start with a simple request such as listing available sites to verify permissions

***

### 11. Security and governance

The Commanders Act MCP server relies on:

* a standard MCP interface
* OAuth based authentication
* browser based login
* secure token usage handled by the client

This allows experimentation through approved MCP compatible AI clients without requiring a custom integration.

As the server is currently in closed beta, access remains restricted.

***

### 12. Support

For access or setup information, contact the Commanders Act support team.

They can provide:

* connection details
* setup guidance
* recommended first steps
