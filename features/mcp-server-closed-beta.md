# MCP server (closed beta)

### Commanders Act MCP Server Setup Guide

### For Claude Code experimentation

This guide explains how to connect Claude to the Commanders Act MCP server so your team can experiment with AI access to Commanders Act through the standard Model Context Protocol.

### 1. Overview

The Commanders Act MCP server exposes Commanders Act platform capabilities as MCP tools through a standard remote MCP interface.

It is designed to be consumed by MCP compatible AI clients, with OAuth 2.1 and PKCE used for authentication.

The MCP server is currently in **closed beta**. At this stage, only a limited number of users are testing it.

Typical use cases include:

* discovering the sites available to the authenticated user
* exploring Sources, Destinations, Enrichments, Cleansing, Health, Reports, Tag Management, and Admin data
* using Commanders Act data through AI workflows without building a proprietary integration

### 2. Access conditions

Because the MCP server is currently in closed beta, access is not yet generally available.

If you are part of the beta program and want to experiment with the Commanders Act MCP server, please request the connection details from the Commanders Act support team.

The support team can provide:

* the MCP server connection details
* the relevant setup information
* guidance on the recommended first steps

### 3. What you need

Before starting, make sure you have:

* access to a Commanders Act account
* access to the Commanders Act MCP server as part of the closed beta
* an MCP compatible Claude environment, such as Claude Code
* a browser available on your machine for the OAuth login step

### 4. Authentication model

The Commanders Act MCP server uses OAuth 2.1 with PKCE.

The login flow is automatic:

1. The Claude client connects to the MCP server
2. The server indicates that authentication is required
3. The Claude client discovers the OAuth endpoints
4. A browser window opens for login
5. The user signs in with their Commanders Act credentials
6. The Claude client receives an authorization code
7. The Claude client exchanges it for a bearer token
8. Subsequent MCP tool calls are authenticated automatically

No manual session key copy and paste is required.

### 5. Connecting from Claude

If your Claude environment supports remote MCP servers with OAuth, the authentication flow should start automatically when the first authenticated call is made.

If your environment requires MCP servers to be declared in a configuration file, add an entry for the Commanders Act server using the connection details provided by the Commanders Act support team.

The exact configuration format may vary depending on the Claude client and version being used.

### 6. Available tool families

The Commanders Act MCP server exposes more than 35 tools, including the following categories:

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
* retrieve collection event monitoring data
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

* retrieve normalized datalayer configuration

**Admin**

* retrieve activity logs
* list users
* list redirect rules

### 7. First recommended validation

After authentication, a good first validation is to ask Claude a simple natural language question that confirms the connection is working and that your Commanders Act permissions are correctly available.

Recommended prompt:

“Can you list the sites available to my Commanders Act account?”

This is a good first step because it helps confirm:

* authentication succeeded
* the MCP connection is working
* the user’s Commanders Act permissions are available

Once this works, you can continue with prompts such as:

* “Can you list the configured sources for my account?”
* “Can you show me the configured destinations?”
* “Can you show me current health alerts?”
* “Can you list the available web containers?”
* “Can you list the available reports?”

### 8. Token lifetime

Access tokens are time limited.

The default token lifetime is 8 hours.

When the token expires, the user must authenticate again.

### 9. Troubleshooting

#### The login page does not open

Make sure your Claude environment supports OAuth capable remote MCP servers and that a browser can be opened from your machine.

#### Authentication starts but does not complete

Check that the MCP server connection details provided by the Commanders Act support team have been configured correctly and that the environment can reach the server over HTTPS.

#### The connection works but no business data is returned

Start with a simple request such as:

“Can you list the sites available to my Commanders Act account?”

This helps confirm that the authenticated user has valid Commanders Act access and that the expected permissions are available.

### 10. Notes for security and governance teams

The Commanders Act MCP server uses:

* a standard MCP interface
* OAuth 2.1 with PKCE
* browser based user authentication
* bearer tokens for subsequent authenticated tool calls

This means experimentation can be performed through an MCP compatible AI client without building a custom proprietary integration layer.

As the server is currently in closed beta, access is limited to selected users at this stage.

### 11. Support

If you are participating in the closed beta and need access or setup information, please contact the Commanders Act support team.

They can provide:

* the MCP server connection details
* setup guidance
* recommended first steps for experimentation
