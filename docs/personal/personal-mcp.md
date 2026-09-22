# Personal: MCP

Personal MCP lets an external editor or assistant read explicitly authorized Personal project context through the local STDIO bridge.

## Create a connection

1. Keep the Personal desktop app running.
2. Open **Settings → External Apps / MCP**.
3. Enable external application connections.
4. Enter a connection name.
5. Choose **Read only** or **Developer collaboration**.
6. Select the projects the connection may access.
7. Choose whether reports, evidence, and repair material may be returned.
8. Create the connection.
9. Copy the Codex or general MCP configuration into the client.

![Personal MCP configuration](../assets/personal/personal-mcp.png)

## Use and revoke the connection

1. Use the client to list authorized projects.
2. Read project snapshots, findings, reports, or fix material allowed by the connection.
3. Review pending work requests in the desktop app before starting them.
4. Open MCP activity to check request history.
5. Revoke the connection when it is no longer needed.

### Result

The client can read only the selected Personal projects and content. The matching Personal desktop instance must remain available.

### Boundary

A Personal MCP connection cannot connect to a Team desktop instance. MCP does not run arbitrary commands or bypass desktop confirmation.
