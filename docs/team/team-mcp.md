# Team: MCP

Team MCP connects an external client to explicitly authorized Team projects and member-scoped work context through the local STDIO bridge.

## Create a Team connection

1. Keep the Team desktop app running.
2. Open **Settings → External Apps / MCP**.
3. Enable external application connections.
4. Enter a connection name.
5. Choose **Read only** or **Developer collaboration**.
6. Select the Team projects.
7. Select the acting Team member for each project.
8. Choose whether reports, evidence, and repair material may be returned.
9. Create the connection.
10. Copy the Codex or general MCP configuration into the client.

![Team MCP configuration](../assets/team/team-mcp.png)

## Use and review requests

1. List authorized projects and read project context.
2. Read findings, tasks, reports, and release status allowed by the connection.
3. Submit an analysis, report, fix package, or verification request.
4. Review the request preview in the desktop app.
5. Confirm or cancel the request.
6. Check the idempotency key and request history.
7. Revoke and recreate the connection when its scope changes.

### Result

The client receives only the selected Team project context and actions permitted for the selected member and connection preset.

### Boundary

Team MCP does not automatically import arbitrary projects, execute arbitrary commands, accept risk, approve a release, or promote a baseline. A Team MCP connection cannot be used with Personal desktop.
