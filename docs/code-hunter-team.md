# Code Hunter Team — Complete User Guide

This guide follows the Team delivery path from installation to a governed release decision: activate Team, enter a workspace, assign roles, connect source code, create a baseline and iteration, analyze change, review findings and dependencies, assign remediation, collect test evidence, verify the fix, decide release readiness, and promote a fresh baseline. Developer Agent, CLI, IDE, external reports, SCA, and Team MCP are placed at the stage where they are actually used.

Screenshots show the product workflow. Production activation and account entitlement are handled by the official service.

## Workflow at a glance

| Order | Stage | Required? | Completion signal |
| --- | --- | --- | --- |
| 1 | [Install, activate, and enter a workspace](#get-started) | Required | Team opens the intended workspace |
| 2 | [Add members and roles](#workspace-and-roles) | Required for collaboration | Reviewer, owner, developer, and remediation responsibilities are assigned |
| 3 | [Configure and test a provider](#provider) | Required for AI-assisted stages | The default provider test succeeds |
| 4 | [Create a project and connect code](#project-and-code-source) | Required | The SCM or local source test succeeds and the intended revision is selected |
| 5 | [Initialize the baseline](#baseline-and-iteration) | Required | The project has a materialized starting state |
| 6 | [Create an iteration and bind work](#baseline-and-iteration) | Required | Requirements and code changes point to the intended revision |
| 7 | [Run requirement, change, risk, and finding analysis](#analysis-and-findings) | Required | Reviewable iteration findings are available |
| 8 | [Import external SAST/SARIF](#analysis-and-findings) | Optional | External findings are normalized and reviewed |
| 9 | [Run SCA](#sca-and-release-gate) | Required when workspace policy enables dependency gates | Components, advisories, licenses, and exceptions are evaluated |
| 10 | [Assign findings and create remediation tasks](#remediation-and-verification) | Required for closure | Each accepted issue has an owner and acceptance criteria |
| 11 | [Use desktop, Developer Agent CLI, or IDE Inbox](#developer-tools) | Optional execution surface | A claimed task produces a reviewed patch or PR/MR |
| 12 | [Bind CI evidence and verify the fix](#remediation-and-verification) | Required for verified closure | Evidence matches the submitted commit and verification completes |
| 13 | [Decide release readiness and promote the baseline](#release-readiness) | Required for the governed release loop | The release has a recorded state and the accepted release becomes the next baseline |
| 14 | [Connect Team MCP](#team-mcp) | Optional | A scoped member/project connection can submit reviewable requests |

<a id="get-started"></a>
## Step 1 — Download, activate, and enter Team

**What this stage does:** starts the correct desktop edition and opens the workspace that owns later project and release records.

1. Download Team from the [official Code Hunter download center](https://www.arvantacyber.com/code-hunter/download/).
2. Install and start the Team desktop app.
3. Open **Settings → About** and confirm that the running edition is Team.
4. Open **Settings → License** and complete Team activation through the official service.
5. Return to Team and refresh the license state.
6. Open the workspace selector.
7. Select an existing workspace or create one when your role allows it.
8. Confirm that the workspace dashboard and its available projects load.

![Team license and workspace entry](assets/team/team-get-started.png)

**Result:** Team shows an active access state and the intended workspace.

**If it fails:** confirm that the account belongs to the workspace, refresh License and workspace state, and check that the Team installation was opened instead of Personal.

<a id="workspace-and-roles"></a>
## Step 2 — Add members and assign roles

**What this stage does:** establishes who can review risk, own a project, perform remediation, and supply approvals.

1. Open the Team workspace.
2. Open **Members**.
3. Add the member account.
4. Assign the role needed by the workflow:
   - **Security Reviewer** reviews findings and security decisions.
   - **Project Owner** owns the project and its delivery policy.
   - **Developer** works on assigned remediation.
   - **Remediation Owner** owns closure and acceptance criteria.
5. Save the membership.
6. Assign the Project Owner and other project-scoped responsibilities.
7. Confirm that each required person can see the workspace or project surface associated with the role.

**Result:** the workspace has an explicit responsibility chain before findings and tasks are created.

**If it fails:** verify that the member is active and that the selected role is allowed for the project and action.

<a id="provider"></a>
## Step 3 — Configure the Team provider

**What this stage does:** supplies the model used by requirement extraction, impact analysis, security analysis, finding review, report analysis, and remediation assistance.

1. Open **Settings → Providers**.
2. Choose the provider preset.
3. Enter the Base URL, model, and protected API credential.
4. Save and test the provider.
5. Set it as default after the test succeeds.
6. Reopen it and confirm that the non-secret settings persisted.

**Result:** Team analysis stages can select a tested provider.

**If it fails:** check the Base URL, exact model name, credential, and network access. Provider credentials do not grant workspace membership or Developer Agent enrollment.

<a id="project-and-code-source"></a>
## Step 4 — Create a Team project and connect source code

**What this stage does:** creates the governed project and binds analysis to a real repository and revision.

1. Open **Team Projects** and choose **New project**.
2. Enter the project name.
3. Assign the Project Owner.
4. Set the default branch and release policy.
5. Save the project.
6. Open project source settings.
7. Create an SCM profile for GitHub, GitLab, or Bitbucket, or choose the supported local Git path.
8. Configure the authorized authentication method: bearer token, basic authentication, or SSH key.
9. Create the Code Source.
10. Test the connection.
11. Load available branches, tags, commits, and PR/MR references.
12. Select the source form used by this work: local Git, remote Git, patch-only, branch, tag, commit, or PR/MR.
13. Confirm the selected revision before continuing.

![Team project and code source](assets/team/team-project-and-code-source.png)

**Result:** the project has a tested source and a specific revision that can be materialized.

**If it fails:** a repository URL belongs in the Code Source. The revision field must contain a branch, tag, or commit that the repository can resolve. When connection succeeds but no refs appear, check repository permissions and the default branch.

<a id="baseline-and-iteration"></a>
## Step 5 — Initialize the baseline

**What this stage does:** records the accepted starting state that later iterations compare against.

1. Open **Baseline** for the Team project.
2. Select the tested Code Source.
3. Select the intended branch, tag, or commit.
4. Start baseline initialization.
5. Wait for materialization and analysis to finish.
6. Review baseline status, source revision, reports, findings, contracts, diff, and timeline.
7. Correct the source reference before continuing if the baseline points to the wrong revision.

![Team baseline and iteration](assets/team/team-baseline-and-iteration.png)

**Result:** the project has a baseline tied to a resolvable source revision.

**If it fails:** retest the Code Source and verify the exact branch or commit. Do not enter a repository URL as the revision.

## Step 6 — Create an iteration and bind requirements and changes

**What this stage does:** defines the unit of delivery that will move through analysis, remediation, verification, and release readiness.

1. Open **Iterations** and choose **New iteration**.
2. Select the Team project and baseline.
3. Add requirement material when available.
4. Bind the code change using a branch, commit, patch, PR/MR, or local Git diff.
5. Confirm the before-and-after revisions.
6. Save the iteration.
7. Review the iteration timeline and diff.
8. Correct the change binding before analysis if unrelated files or the wrong revision appear.

**Result:** the iteration contains the requirement and source change that the team intends to release.

<a id="analysis-and-findings"></a>
## Step 7 — Run requirement, impact, risk, and finding analysis

**What this stage does:** turns the iteration inputs into security context and reviewable findings.

Run the stages in this order:

1. **Requirement extraction** — structure the requirement material.
2. **Requirement impact analysis** — identify affected modules, data, permissions, and controls.
3. **Security analysis / owner review** — confirm the security expectations.
4. **Change impact** — understand what the code change touches.
5. **Delta generic risk** — identify security risk introduced or changed by the iteration.
6. **Delta business risk** — identify risks in business state, money, approval, tenant, identity, or other sensitive flows.
7. **Delta finding review** — prepare the findings for human review.
8. Open the Findings workbench and inspect source, affected area, evidence, product impact, and current state.
9. Accept, reject, downgrade, defer, or request more evidence.
10. Assign an Owner to every accepted finding that requires work.

![Team analysis and findings](assets/team/team-analysis-and-findings.png)

**Result:** the iteration has findings tied to source, change context, evidence, product impact, and an accountable owner.

### Optional at this stage — Import external SAST or SARIF

1. Open external report intake.
2. Select the report file.
3. Preview the detected format and finding count.
4. Bind the report to the Team project, branch, commit, scanner, and report date.
5. Import the report.
6. Run external report analysis.
7. Review normalized findings.
8. Let the responsible owner decide which items enter the governed finding lifecycle.

**If the report is empty:** check its format, project binding, commit, scanner metadata, and report date before importing again.

<a id="sca-and-release-gate"></a>
## Step 8 — Run SCA and resolve dependency policy

SCA is a Team capability. Run it before release readiness whenever the workspace policy includes dependency or license gates.

1. Open the iteration SCA panel.
2. Select the dependency source or lockfile context.
3. Configure severity, exploitability, license, lifecycle, and blocking rules.
4. Run the dependency scan.
5. Review components, advisories, licenses, fixed versions, reachability or exploitability information, and lifecycle state.
6. Run SCA analysis.
7. Assign an Owner to blocking items.
8. Upgrade or replace the dependency when a fix is available.
9. When policy permits, create a scoped VEX record or time-limited exception with owner, reason, approval, and expiry.
10. Verify the dependency change or approved exception before evaluating the release gate.

![Team SCA and release gate](assets/team/team-sca-and-release-gate.png)

**Result:** every dependency gate condition has a fix, a verified state, or an active governed exception.

**If it remains blocked:** check for an expired exception, missing Owner, missing approval, unverified fixed version, prohibited license, or unresolved exploitability condition.

<a id="remediation-and-verification"></a>
## Step 9 — Create and assign remediation work

**What this stage does:** converts an accepted finding into work that a developer can claim and that a reviewer can verify.

1. Open the accepted finding.
2. Choose **New remediation task**.
3. Assign the Owner.
4. Write acceptance criteria that name the expected control and test result.
5. Link the iteration, finding, affected source revision, and due date.
6. Save the task.
7. Let the assigned developer claim it.
8. Generate the remediation context pack when the developer needs evidence, affected code, assumptions, and acceptance criteria together.
9. Choose the execution surface:
   - Team desktop local fix package.
   - Team Developer Agent CLI.
   - VS Code Remediation Inbox.
   - JetBrains Remediation Inbox.
   - An existing PR/MR supplied by the developer.

![Team remediation task](assets/team/team-remediation-and-verification.png)

**Result:** the task has an owner, acceptance criteria, source context, and a selected delivery path.

<a id="developer-tools"></a>
## Step 10 — Optional Developer Agent, CLI, IDE, and project sub-agents

Developer tools are optional execution surfaces inside the remediation stage. The Team desktop remains authoritative for workspace roles, risk acceptance, fix verification, release readiness, and baseline promotion.

### What the Developer Agent is

**Agent Management** can enroll multiple local Developer Agents for different developers and repositories. Each enrolled agent is a scoped worker for assigned Team remediation tasks. Some teams call these project child agents or sub-agents; the product UI calls them **Developer agents**.

A Developer Agent can receive tasks, claim work, obtain fix context, preview or apply a bounded patch, run approved tests, and synchronize a PR. It does not inherit workspace administrator rights and cannot accept risk, approve release, or promote a baseline.

### Components

| Component | Purpose |
| --- | --- |
| `code-hunter-team-agent` | Local CLI for enrollment, task sync, patch, tests, and PR handoff |
| `code-hunter-team-agent-lsp` | Language-service bridge used by IDE integrations |
| VS Code extension | CodeHunter activity view and Remediation Inbox |
| JetBrains plugin | CodeHunter Remediation Inbox tool window |
| `.codehunter/team-agent.toml` | Repository-scoped enrollment and endpoint configuration |

The IDE packages include the Team Agent and Team Agent LSP for supported platforms. The current verified packages are stored in this repository:

- [Download the VS Code extension (VSIX)](../developer-tools/code-hunter-team/3.1.94/plugins/vscode/codehunter-team-vscode-3.1.94.vsix)
- [Download the JetBrains plugin (ZIP)](../developer-tools/code-hunter-team/3.1.94/plugins/jetbrains/codehunter-team-jetbrains-3.1.94.zip)
- [Read package checksums, supported platforms, and installation notes](../developer-tools/code-hunter-team/3.1.94/README.md)

### Enroll a repository

1. In Team desktop open **Agent Management** for the intended project.
2. Create a one-time enrollment code for the developer.
3. Keep the code private; it is shown for enrollment, not for documentation or source control.
4. In the repository run the enrollment command supplied by Team. The CLI form is:

```bash
code-hunter-team-agent enroll \
  --code <one-time-code> \
  --developer-email <developer@example.com> \
  --repo .
```

5. Confirm that `.codehunter/team-agent.toml` was created.
6. Do not commit that file or its token.
7. Run the local health check:

```bash
code-hunter-team-agent doctor --repo .
```

8. Return to Agent Management and confirm that the agent is online and bound to the intended repository.

### CLI task flow

Run these commands from the bound repository. Replace placeholders with IDs and files shown by the Team task.

```bash
# Show assigned work
code-hunter-team-agent tasks

# Claim one remediation task
code-hunter-team-agent claim <task-id>

# Generate bounded repair material
code-hunter-team-agent generate-fix <task-id> \
  --mode patch \
  --output-dir .codehunter/fixes

# Inspect the patch against the enrolled repository boundary
code-hunter-team-agent preview \
  --patch-file <fix.patch> \
  --repo .

# Check application without changing the worktree
code-hunter-team-agent apply \
  --patch-file <fix.patch> \
  --repo . \
  --dry-run

# Apply only after reviewing the preview and current Git state
code-hunter-team-agent apply \
  --patch-file <fix.patch> \
  --repo .

# Run a command allowed by local and Team release policy
code-hunter-team-agent test \
  --task-id <task-id> \
  --program npm -- test

# Synchronize an existing PR URL, or let policy allow creation
code-hunter-team-agent create-pr \
  --task-id <task-id> \
  --branch <fix-branch> \
  --base main \
  --draft

# Refresh heartbeat, tasks, and server state
code-hunter-team-agent sync
```

Other operational commands include `heartbeat`, `bind-repo`, and JSON output through the global `--json` option. The advanced `run-e2e` command can orchestrate the policy-controlled claim, patch, test, PR, and verification sequence; use its installed `--help` output and the project policy rather than copying options from another build.

The CLI enforces the enrolled repository boundary, patch checks, local command allowlist, and Team release policy. Test or PR operations can be rejected when the configured command, remote, branch, or project policy does not allow them.

### VS Code flow

1. Download and install the [Team VS Code extension](../developer-tools/code-hunter-team/3.1.94/plugins/vscode/codehunter-team-vscode-3.1.94.vsix).
2. Open the CodeHunter activity bar.
3. Open **CodeHunter Remediation Inbox**.
4. Use **CodeHunter: Configure Agent** when the config or binary path is not detected automatically.
5. Choose **Refresh Tasks**.
6. Open and verify the task, project, and source commit.
7. Use **Claim Task → Generate Fix → Preview Patch → Apply Patch → Run Tests → Create PR**.
8. Confirm every action that changes the working tree, runs a command, or creates remote state.

### JetBrains flow

1. Download and install the [Team JetBrains plugin](../developer-tools/code-hunter-team/3.1.94/plugins/jetbrains/codehunter-team-jetbrains-3.1.94.zip).
2. Restart the IDE when requested.
3. Open **View → Tool Windows → CodeHunter Remediation Inbox**.
4. Configure the Agent config, Agent binary, LSP binary, API override, and default test command only when automatic discovery is not sufficient.
5. Refresh tasks, claim the intended task, generate and preview the patch, apply after review, run tests, and create or link the PR/MR.

No IDE screenshot is shown here because a native VS Code or JetBrains capture was not completed in the isolated documentation environment. Electron desktop screenshots are not presented as IDE evidence.

### Credential and confirmation boundaries

- The enrollment code is short-lived and must not be committed or placed in screenshots.
- `.codehunter/team-agent.toml` contains repository-scoped agent configuration and must stay out of source control.
- The Agent token is separate from the Team desktop license and provider API credential.
- Patch application, tests, commits, and PR creation require developer review and can require confirmation.
- The Team desktop and server remain authoritative for owner approval, accepted risk, fix verification, release readiness, and baseline promotion.

## Step 11 — Apply the fix, run tests, and bind CI evidence

1. Review the current source worktree and exact target commit.
2. Preview the patch, test command, rollback path, and assumptions.
3. Apply the patch locally or submit the PR/MR.
4. Run the project’s real tests.
5. Run CI on the submitted commit.
6. Bind the CI evidence to the remediation task and exact commit SHA.
7. Attach or synchronize the PR/MR.
8. Confirm that the task, patch, tests, CI, and source revision all refer to the same attempt.

**Result:** the remediation task has source-bound test and CI evidence rather than a detached success message.

**If evidence is rejected:** bind it to the exact submitted commit and rerun the current verification attempt. Evidence from an older patch or another revision is stale.

## Step 12 — Run formal fix verification

1. Open the remediation task.
2. Confirm the acceptance criteria.
3. Review the submitted diff and CI evidence.
4. Run **Fix verification**.
5. Review the final state:
   - **Verified fixed** — current evidence proves the control is restored.
   - **Accepted risk** — an authorized owner approved a scoped, recorded exception.
   - **Pending verification** — the fix or evidence is incomplete.
6. Reopen the task when the current code or evidence no longer supports the prior result.

**Result:** closure is tied to the current source attempt, reviewer decision, and evidence.

<a id="release-readiness"></a>
## Step 13 — Decide release readiness and promote a fresh baseline

1. Open **Release Readiness**.
2. Review the current state:
   - **Blocked** — a required finding, dependency, approval, or evidence item remains unresolved.
   - **Pending verification** — a submitted fix has not completed formal verification.
   - **Pass with risk** — remaining risk has a valid owner, scope, approval, and expiry.
   - **Ready** — required gates are satisfied.
3. Resolve missing finding decisions, SCA conditions, owner approvals, fix verification, and CI evidence.
4. Record the release decision.
5. After the accepted release is materialized, promote a fresh baseline from the released revision.
6. Confirm that the new baseline points to the released branch and commit.

**Result:** the release decision is reviewable, and the next iteration starts from the accepted source state.

<a id="team-mcp"></a>
## Optional — Connect Team MCP

Use Team MCP only after the workspace, members, project, and permission boundaries exist.

1. Keep the matching Team desktop instance running.
2. Open **Settings → External Apps / MCP**.
3. Enable external application connections.
4. Create a connection name.
5. Choose **Read only** or **Developer collaboration**.
6. Select the Team projects.
7. Select the acting Team member for each project.
8. Choose whether findings, reports, evidence, tasks, and repair material may be returned.
9. Create the connection and copy the Codex or general MCP configuration.
10. From the client, read only the authorized project and member context.
11. Submit analysis, report, repair, or verification requests when permitted.
12. Review the request preview in Team desktop.
13. Confirm or cancel the request.
14. Check the idempotency key and request history.
15. Revoke and recreate the connection when its scope changes.

![Team MCP configuration](assets/team/team-mcp.png)

**Boundary:** Team MCP does not automatically import arbitrary projects, execute arbitrary commands, accept risk, approve a release, or promote a baseline. A Team connection cannot be used with Personal desktop.

<a id="troubleshooting"></a>
## Troubleshooting by stage

| Problem | Check |
| --- | --- |
| Workspace is missing | Confirm account membership, role, Team license state, and workspace refresh |
| SCM connects but refs are empty | Check repository permissions and the configured default branch |
| Baseline cannot materialize | Use a resolvable branch, tag, or commit; do not use the repository URL as the revision |
| External report is empty | Check format, project, branch, commit, scanner, and report date |
| Finding has no Owner | Activate the member and assign an allowed project/remediation role |
| SCA blocks release | Resolve the component or supply an active owner-approved exception and verification |
| Agent inbox is empty | Check enrollment, repository binding, task assignment, agent heartbeat, and matching Team instance |
| CLI test is rejected | Use a command allowed by both the local allowlist and Team release policy |
| CI evidence does not match | Bind evidence to the exact submitted commit and current attempt |
| Release remains pending | Complete fix verification, owner approval, SCA, and required evidence |
| Baseline points to the wrong branch | Correct the source revision before promotion and verify the released commit |
| Team MCP cannot connect | Keep Team running and recreate the member/project-scoped STDIO configuration |

## Team closure checklist

- Team is activated and the intended workspace is open.
- Members and project roles are assigned.
- The provider test succeeds.
- The Team project has a tested Code Source and correct default branch.
- The baseline points to a resolvable accepted revision.
- The iteration contains the intended requirement and code change.
- Required analysis, external report, and SCA stages completed according to policy.
- Every accepted finding has an Owner and a remediation decision.
- Every submitted fix is tied to the current source revision, tests, CI evidence, and verification attempt.
- Developer Agent or IDE actions stayed inside the enrolled repository and approval policy.
- Release Readiness has a recorded result.
- The accepted release was promoted to a fresh baseline.
- Any Team MCP connection is scoped to named projects and members and can be revoked.
