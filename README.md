# Code Hunter 3.1.94 Documentation

![Code Hunter logo](docs/assets/logo/codehunter-logo.png)

This repository is the public evidence and release index for **Code Hunter 3.1.94**. The canonical, screenshot-led product tutorial is hosted on the official website:

**[Open the official Code Hunter 3.1.94 tutorial](https://www.arvantacyber.com/code-hunter/docs/)**

The English tutorial is written against the `3.1.94-dev.0` development build from source commit `e4b6868`; production activation, release downloads, and tenant entitlements still require the official distribution and account service. GitHub keeps the versioned source guides, screenshot manifest, and verified Team developer-tool packages that support the official page.

## Choose your edition

| Product | Complete tutorial | What it covers |
| --- | --- | --- |
| **Personal 3.1.94** | [Personal usage tutorial](docs/personal-usage-tutorial.md) | Activation, provider setup, project scope, audit, finding decisions, evidence, reports, scoped fixes, and Personal MCP |
| **Team 3.1.94** | [Team usage tutorial](docs/team-usage-tutorial.md) | Workspace governance, SCM, baselines, iterations, SAST/SARIF, SCA, remediation, CI evidence, release readiness, Team MCP, and developer tools |
| **Team developer tools 3.1.94** | [Developer tools package guide](developer-tools/code-hunter-team/3.1.94/README.md) | VS Code and JetBrains installation, enrollment, remediation inbox, patch review, tests, and PR handoff |

## Version and compatibility

- [3.1.94 version matrix](docs/version-matrix.md)
- [MCP and external apps guide](docs/external-apps-mcp.md)
- [Maintenance and release checklist](docs/maintenance-and-release-checklist.md)
- [Security and redaction rules](docs/security-and-redaction.md)
- [Screenshot and evidence manifest](docs/assets/manifest-3.1.94.json)
- [Official visual tutorial](https://www.arvantacyber.com/code-hunter/docs/)
- [Offline tutorial mirror](docs/tutorial.html)

The desktop MCP integration is a local STDIO bridge. A Personal connector can only be used with the matching Personal desktop instance, and a Team connector can only be used with the matching Team instance. A connector does not grant an entitlement, bypass a license, import arbitrary projects, execute arbitrary commands, accept risk, approve a release, or promote a baseline by itself.

## Reference

- [SCA and release governance](docs/04-sca-release-governance.md)
- [Integrations](docs/05-integrations.md)
- [Reports and evidence](docs/06-reports-evidence.md)
- [Administration and security](docs/07-admin-security.md)
- [Troubleshooting](docs/08-troubleshooting.md)
- [Security policy](SECURITY.md)

For product access, license, or enterprise pilot questions, contact `contact@arvantacyber.com`.
