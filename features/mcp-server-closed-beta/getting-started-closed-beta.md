# Getting Started (closed beta)

Connect your Commanders Act account to **ChatGPT or Claude** to explore your actual configuration in natural language.

**MCP server URL:** Contact Commanders Act Support or your account manager to obtain the correct URL and access instructions. The MCP is currently available only to selected customers as part of its closed beta.

**Before you begin:** You need an active Commanders Act account, access to the sites you want to explore, and an invitation to the current MCP early-access program. Your AI client or workspace must also allow remote MCP connections. If your organization manages connectors centrally, ask your AI workspace administrator to enable Commanders Act.

The current integration is **read-only**: it can inspect available configuration and monitoring information, but it cannot modify anything in Commanders Act.

## Option A — Connect with ChatGPT

### If your workspace already provides Commanders Act

1. Open ChatGPT and start a new conversation.
2. Select the **Commanders Act** plugin/app when composing your message (for example, by typing `@` and selecting it).
3. If prompted, sign in to Commanders Act in your browser and complete any SSO or two-factor authentication steps.
4. Try the first prompt below.

### If Commanders Act has not been added yet (workspace administrator or authorized user)

1. Open **Plugins** in ChatGPT.
2. Select **+ → Add custom MCP server**.
3. Give the connection a recognizable name, such as **Commanders Act**.
4. Enter the MCP server URL provided by Commanders Act Support or your account manager.
5. Follow the authentication setup and authorize with your Commanders Act account when prompted.
6. Review the connection and its discovered tools, then create it. If needed, publish or share it through your workspace's admin controls.
7. In a chat, select the new connection and try a prompt.

The exact menus and administrator permissions vary by ChatGPT plan and workspace. Some organizations still use the legacy **Settings / Apps → Create** flow. If you cannot add a custom server, contact your ChatGPT workspace administrator.

[Official ChatGPT guidance for custom MCP servers](https://help.openai.com/en/articles/12584461-connecting-custom-mcp-servers-in-chatgpt)

## Option B — Connect with Claude

### If your organization already provides Commanders Act

1. In Claude, go to **Customize → Connectors**.
2. Find **Commanders Act** and choose **Connect**.
3. Sign in with your Commanders Act account, completing SSO or 2FA if required.
4. Enable the connector for your conversation if it is not already enabled.
5. Try the first prompt below.

### If the connector has not been added yet

**Individual plans:** In **Customize → Connectors**, choose **Add → Custom → Web** (the wording may vary), name the connector **Commanders Act**, enter the MCP server URL provided by Commanders Act Support or your account manager, and follow the authentication prompts.

**Claude Team / Enterprise:** An organization owner or authorized administrator first adds the remote custom connector under **Organization settings → Connectors**. Team members can then connect individually under **Customize → Connectors**.

These instructions are for **Claude's chat interface**. Claude Code is a separate client with a different setup process.

[Official Claude remote MCP connector guide](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp)

## Your first successful result

Try:

> List the Commanders Act sites available to my account, with their site names and IDs.

**Expected result:** a list of the Commanders Act sites your account can access. This is a simple way to check the connection and your site permissions.

Next, choose one site and try:

> For \[site], summarize the configured sources and destinations, and explain what marketing use cases they appear to support. Separate observations from assumptions.

Then explore the full [Use Cases & Prompt Library](use-cases-and-prompt-library.md).

## Troubleshooting

| Problem                                          | What to check                                                                                                                                          |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| I cannot add the connector                       | Your ChatGPT/Claude plan or workspace settings may restrict custom MCP connections. Ask your AI workspace administrator.                               |
| The sign-in window does not open or login fails  | Check the endpoint URL and whether your AI client supports remote MCP with OAuth. Retry the browser authentication and complete any SSO or 2FA prompt. |
| I connected successfully but the MCP is not used | Select or enable the Commanders Act connector for your message. In ChatGPT, mentioning the plugin with `@` can help.                                   |
| No sites appear                                  | Confirm that you signed in with the expected Commanders Act account and that it has access to the sites.                                               |
| Tools are missing or stop working                | Reconnect; if your workspace centrally manages tool lists, ask the administrator to check whether the approved tools need refreshing.                  |
| Data for a particular site is missing            | Specify the site name or ID, check access rights, and ask the AI to explain which data or operations it could not retrieve.                            |

For access or setup assistance, contact your Commanders Act support or account team.
