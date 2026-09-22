# External Apps / MCP in Code Hunter 3.1.94

Code Hunter exposes a local **STDIO MCP bridge** from the running desktop application. Personal and Team connectors are separate products: use the Personal configuration with a running Personal instance and the Team configuration with a running Team instance. The bridge is intentionally scoped and desktop-governed.

## Configure a connection

1. Open **Settings → External Apps / MCP**.
2. Select **Add connection** and give it a recognizable name.
3. Select the projects that the connector may read.
4. Choose **Read-only** or **Development collaboration**.
5. Choose whether to expose reports, evidence, and fix material.
6. Copy the Codex configuration or the generic MCP configuration.
7. Put the configuration in the client’s MCP settings and keep the matching Code Hunter desktop instance running.

![MCP configuration](assets/3.1.94/personal/08-mcp/01-mcp-config.png)

The copied configuration refers to the local bridge. It must not contain a license key, provider API key, enrollment code, or a hard-coded private project path.

## What the connector can do

The exact tool names are exposed by the desktop bridge. The supported product contract is: list authorized projects; read a project snapshot; read findings and their evidence; read saved reports; read fix-package material when the connection allows it; submit a desktop-confirmed work request; and read request history. Team connections additionally expose scoped Team task context, remediation material, and formal verification requests when those options are enabled.

Begin with read-only calls:

1. List authorized projects.
2. Read one project snapshot.
3. Read one finding and its evidence.
4. Read the report or fix material allowed by the connection.
5. For development collaboration, submit a request that names the target project and intended action.
6. Inspect the idempotent request record and desktop confirmation result.

![MCP history and authorized projects](assets/3.1.94/personal/08-mcp/02-mcp-history.png)

## Permission and safety boundaries

- A connector cannot activate a license or create an entitlement.
- A connector cannot import an arbitrary new project outside its allowed list.
- A connector cannot execute an arbitrary shell command.
- A connector cannot silently apply a patch, accept a finding, accept risk, approve a release, or promote a baseline.
- Team requests remain subject to workspace membership, project roles, policy, owner approval, and desktop confirmation.
- Every mutating request should carry an idempotency key so a retry cannot create duplicate work.
- Personal and Team connector configurations are not interchangeable.

## Revoke and re-authorize

In **Settings → External Apps / MCP**, open the connection, review its project and material scope, and choose **Revoke**. Confirm that the client can no longer read the project. Create a new connection when the scope or edition changes. Keep old configuration files out of shared repositories and shell history.

## Troubleshooting

| Symptom | Check | Recovery |
| --- | --- | --- |
| Client cannot start bridge | Matching desktop is running; local STDIO command exists | Restart the matching edition and copy fresh configuration |
| Project list is empty | Project authorization and connector edition | Add the project to the connection or use the correct Personal/Team bridge |
| Read works but development request is denied | Permission mode, project role, desktop confirmation | Switch only with explicit authorization and confirm in the desktop |
| Team task context is missing | Team project membership and material toggle | Reauthorize with task context enabled |
| Request repeats after retry | Idempotency key and request history | Reuse the same key and inspect the original result |
| Configuration contains a local path or secret | Copied config was edited manually | Revoke it, remove the secret, and copy a fresh config |

The MCP screenshots in this repository are renderer captures from isolated demo data. They document the product path, not an external client’s native settings UI or a production entitlement.
