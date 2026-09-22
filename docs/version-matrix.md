# Code Hunter 3.1.94 version matrix

| Surface | Version in this guide | Build/source evidence | Scope |
| --- | --- | --- | --- |
| Personal desktop | `3.1.94` (`3.1.94-dev.0` capture build) | Source commit `e4b6868`, `desktop-ui/package.json` | Local project audit, finding review, report, scoped fix package |
| Team desktop | `3.1.94` (`3.1.94-dev.0` capture build) | Source commit `e4b6868`, Team dev profile | Workspace, SCM, baseline, iteration, SAST/SARIF, SCA, remediation, release readiness |
| Personal MCP | Local STDIO bridge shipped by the matching Personal desktop | `docs/external-apps-mcp.md` | Authorized project reads and user-confirmed work requests |
| Team MCP | Local STDIO bridge shipped by the matching Team desktop | `docs/external-apps-mcp.md` | Scoped Team project reads, task context, remediation material, formal verification requests |
| Team VS Code | `3.1.94` package metadata | Built from the same source checkout; see package manifest and SHA256SUMS | Remediation Inbox and bundled agent/LSP |
| Team JetBrains | `3.1.94` plugin metadata | Built from the same source checkout; see package manifest and SHA256SUMS | Remediation Inbox and bundled agent/LSP |

## Development build versus official release

The screenshots are development-channel UI evidence. The dev profile has license enforcement disabled so that navigation, forms, persistence, and local demo workflows can be exercised in an isolated test home. It does not prove that a production account is entitled, that an activation code is valid, or that an official download is signed and notarized.

For production use, download the official edition, sign in or enter the license details supplied for that edition, let the desktop application contact the official license service, and confirm the server-backed validation result in **Settings → License**. A local cache file or a manually assembled environment is not an entitlement proof.

## Interoperability rules

1. Keep Personal desktop, Personal MCP, and Personal screenshots on the Personal side of the matrix.
2. Keep Team desktop, Team MCP, VS Code, and JetBrains packages on the Team side.
3. Use the same major/minor/patch line for the desktop and developer tools. A newer plugin may require a newer Team desktop protocol.
4. Treat provider configuration as separate from license activation. A valid provider does not activate the product, and an activated product does not validate an unavailable provider.
5. Pin the source commit, package checksum, screenshot manifest, and public repository commit together for every update. This public tree contains only the current 3.1.94 package; historical installer and report archives are intentionally omitted.
