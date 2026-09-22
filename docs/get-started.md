# Get Started

Code Hunter has two desktop editions. Choose the edition that matches how the project will be reviewed and remediated, then follow that guide from top to bottom.

## Choose an edition

| Edition | Use it when | Main workflow |
| --- | --- | --- |
| [Personal](code-hunter-personal.md) | One user imports a local project, audits it, reviews evidence, produces a report, and prepares a scoped fix | Activate → Provider → Project → Audit → Findings → Report → Fix → optional MCP |
| [Team](code-hunter-team.md) | A workspace coordinates owners, source revisions, baselines, iterations, dependency gates, remediation, verification, and release decisions | Activate → Workspace → Source → Baseline → Iteration → Analysis → Remediation → Verification → Release → optional MCP |

SCA, Release Gate, Developer Agents, IDE remediation, formal fix verification, and baseline promotion belong to Team.

## Before you begin

1. Download the required edition from the [official Code Hunter download center](https://www.arvantacyber.com/code-hunter/download/).
2. Prepare the account or license used by that edition.
3. Prepare a supported model provider, Base URL, model name, and API credential.
4. Make sure the source repository is available on the machine or through an authorized Team code source.
5. Keep credentials, enrollment codes, and agent configuration out of screenshots and source control.

## Personal path

Follow [Code Hunter Personal — Complete User Guide](code-hunter-personal.md).

The required path is installation and activation, provider setup, project import and scope, project understanding, audit, finding review, report, and remediation. Personal MCP is optional and should be connected after the desktop workflow works.

## Team path

Follow [Code Hunter Team — Complete User Guide](code-hunter-team.md).

The required path is installation and activation, workspace roles, provider setup, project and code source, baseline, iteration, analysis, finding ownership, remediation, evidence, fix verification, release readiness, and baseline promotion. External SAST/SARIF, Developer Agent or IDE execution, and Team MCP are optional surfaces used at their matching stage.

## Team Developer Tools

Team remediation can run through the desktop app, the Developer Agent CLI, VS Code, or JetBrains. The current packages are stored in this repository and include the Team Agent and Team Agent LSP for supported platforms.

- [Open Team Developer Tools downloads](../developer-tools/code-hunter-team/README.md)
- [Continue with the Team developer workflow](code-hunter-team.md#developer-tools)

Verify the published SHA-256 before installation. Enrollment codes and `.codehunter/team-agent.toml` are repository-scoped credentials and must not be committed.
