# Get Started

Code Hunter has two desktop editions. Choose the edition that matches how the project will be reviewed and remediated, then follow that guide from top to bottom.

## Choose an edition

| Edition | Use it when | Main workflow |
| --- | --- | --- |
| [Personal](code-hunter-personal.md) | One user imports a local project, audits it, reviews evidence, produces a report, and prepares a scoped fix | Activate → Provider → Scope → Audit choices → Project understanding → Security audit → Finding review → Report → conditional fix → optional MCP |
| [Team](code-hunter-team.md) | A workspace coordinates owners, source revisions, baselines, iterations, dependency gates, remediation, verification, and release decisions | Activate → Workspace and roles → Provider → Team Project → Code Source → Baseline → Iteration → Requirement and change analysis → Finding → conditional SCA → Remediation → Verification → Release Readiness → Baseline promotion → optional MCP |

SCA, Release Gate, Developer Agents, IDE remediation, formal fix verification, and baseline promotion belong to Team.

## How to read the guides

| Step type | Meaning |
| --- | --- |
| **Required** | Complete this step for a normal audit or Team release workflow |
| **Conditional** | Complete this step when the project, policy, or selected capability requires it |
| **Optional** | Configure this capability when it is useful; it does not block the basic workflow |

## Before you begin

1. Download the required edition from the [official Code Hunter download center](https://www.arvantacyber.com/code-hunter/download/).
2. Prepare the account or license used by that edition.
3. Prepare a supported model provider, Base URL, model name, and API credential.
4. Make sure the source repository is available on the machine or through an authorized Team code source.
5. Keep credentials, enrollment codes, and agent configuration out of screenshots and source control.

## Personal path

Follow [Code Hunter Personal — Complete User Guide](code-hunter-personal.md).

The required path is activation, provider setup, project scope, audit choices, project understanding, security analysis, finding review, and report generation. Remediation is conditional on confirmed findings. Personal MCP is optional.

### Understand Personal choices

- [Provider, Default provider, Auditor, and Reviewer](code-hunter-personal.md#provider-and-model-roles)
- [Reasoning effort, Audit depth, and Model assurance](code-hunter-personal.md#audit-choices)
- [Rescan, Update Foundation Info, Resume, and Restart](code-hunter-personal.md#run-controls)
- [Theme, language, advanced provider, and report settings](code-hunter-personal.md#personal-settings)

## Team path

Follow [Code Hunter Team — Complete User Guide](code-hunter-team.md).

The required path is activation, workspace roles, provider setup, project and code source, baseline, iteration, governed analysis, finding ownership, remediation, evidence, fix verification, release readiness, and baseline promotion. Connectors, external SAST/SARIF, SCA policy, Developer Agent or IDE execution, and Team MCP apply at their matching stages.

### Understand Team concepts

- [Workspace, Project, SCM, Code Source, Connector, Agent, and MCP](code-hunter-team.md#team-object-map)
- [Baseline and Iteration](code-hunter-team.md#baseline-and-iteration)
- [Requirement Source, Extraction, and Review](code-hunter-team.md#requirements)
- [SAST, SCA, VEX, Exception, and Release Gate](code-hunter-team.md#sca-and-release-gate)
- [Remediation, evidence, and verification](code-hunter-team.md#remediation-and-verification)
- [Developer Agent, CLI, VS Code, and JetBrains](code-hunter-team.md#developer-tools)
- [Team MCP](code-hunter-team.md#team-mcp)

## Team Developer Tools

Team remediation can run through the desktop app, the Developer Agent CLI, VS Code, or JetBrains. The current packages are stored in this repository and include the Team Agent and Team Agent LSP for supported platforms.

- [Open Team Developer Tools downloads](../developer-tools/code-hunter-team/README.md)
- [Continue with the Team developer workflow](code-hunter-team.md#developer-tools)

Verify the published SHA-256 before installation. Enrollment codes and `.codehunter/team-agent.toml` are repository-scoped credentials and must not be committed.
