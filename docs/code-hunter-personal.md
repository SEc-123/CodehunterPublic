# Code Hunter Personal — Complete User Guide

This guide follows the order in which a Personal user completes a real audit: install the desktop app, activate access, configure a model provider, import and understand a project, run the audit, review evidence, produce the result, and close remediation. Personal MCP is an optional connection after the desktop workflow is working.

Screenshots show the product workflow. Production activation and account entitlement are handled by the official service.

## Workflow at a glance

| Order | Stage | Required? | Completion signal |
| --- | --- | --- | --- |
| 1 | [Install and activate Personal](#get-started) | Required | The License page shows Personal access |
| 2 | [Configure and test a provider](#provider) | Required | The provider test succeeds and a default is selected |
| 3 | [Import the project and define scope](#project-and-audit) | Required | The repository root and exclusions are saved |
| 4 | [Build project understanding and run the audit](#project-and-audit) | Required | The project profile, feature inventory, and analysis results are available |
| 5 | [Review findings and evidence](#findings-and-evidence) | Required | Each promoted finding has a human decision |
| 6 | [Save the report](#reports-and-fixes) | Required for an audit deliverable | The reviewed findings appear in the exported report |
| 7 | [Generate, apply, and test a scoped fix](#reports-and-fixes) | Required for remediation closure | The patch is reviewed, tested, and either kept or rolled back |
| 8 | [Connect Personal MCP](#personal-mcp) | Optional | An explicitly scoped external client can read approved project material |

<a id="get-started"></a>
## Step 1 — Download, start, and activate Personal

**What this stage does:** installs the correct edition and establishes the access state used by the desktop app.

1. Download Personal from the [official Code Hunter download center](https://www.arvantacyber.com/code-hunter/download/).
2. Install and start the Personal desktop app.
3. Open **Settings → About** and confirm that the running edition is Personal.
4. Open **Settings → License**.
5. Choose the activation action shown by the app and complete the official service step.
6. Return to the desktop app and choose **Validate** or **Refresh**.
7. Use **Deactivate** only when access must move to another device.

![Personal license and edition](assets/personal/personal-get-started.png)

**Result:** the License page shows the current Personal access state. A development activation screen demonstrates the UI path but does not grant a production entitlement.

**If it fails:** refresh the License page after the service step, confirm that the installed app is Personal, and verify that the activation request was completed for the same device.

<a id="provider"></a>
## Step 2 — Configure the model provider

**What this stage does:** supplies the model used for project understanding, analysis, finding review, report preparation, and fix assistance.

1. Open **Settings → Providers**.
2. Choose the provider preset that matches the service you use.
3. Enter the **Base URL**.
4. Enter the exact **Model** name accepted by that provider.
5. Enter the API key in the protected credential field.
6. Save the provider.
7. Choose **Test provider**.
8. Set the provider as default after the test succeeds.
9. Reopen the provider once and confirm that the non-secret settings were saved.

![Personal provider configuration](assets/personal/personal-provider.png)

**Result:** the provider appears in the saved list, the test succeeds, and Personal can select it for analysis.

**If it fails:** check the Base URL for connection errors, the model name for model errors, and the credential for authentication errors. Save again after correcting the field.

<a id="project-and-audit"></a>
## Step 3 — Import the project and define the audit scope

**What this stage does:** tells Personal which source tree belongs to the audit and which files should stay outside the model context.

1. Open **Projects** and choose **Add project**.
2. Select the repository root, not a nested source, build, cache, or dependency directory.
3. Give the project a clear name.
4. Confirm the source path and workspace path shown by the app.
5. Add exclusions for dependencies, generated code, caches, build output, large vendored trees, test fixtures that are outside scope, and unrelated repositories.
6. Select the project language when it is not detected correctly.
7. Choose the audit depth.
8. Choose the model assurance strategy required for this audit.
9. Save the project and reopen it to confirm that the path, exclusions, depth, and provider selection persisted.

![Personal project and audit configuration](assets/personal/personal-audit.png)

**Result:** the project overview points to the intended repository root and stores a bounded audit scope.

**If it fails:** remove the project entry and import the repository root again. Correct the scope before increasing audit depth; a deeper run cannot repair a wrong source path.

## Step 4 — Build project understanding and run the security audit

**What this stage does:** creates the project context that later findings rely on, then runs the risk analysis stages.

1. Start **Project understanding** or the project profiling stage.
2. Review the generated feature inventory.
3. Check the detected entry points, trust boundaries, authentication flows, authorization controls, sensitive data, external calls, privileged operations, and business-critical functions.
4. Correct the project scope when important modules are missing or generated files dominate the inventory.
5. Start the general security risk analysis.
6. Start the business risk analysis when the project contains state, money, approval, tenant, identity, or other business-sensitive flows.
7. Run the finding review stage.
8. Open **Findings & Actions** when the run completes.

**Result:** the project has a reviewable profile and a set of candidate findings connected to project behavior.

**If it fails:** test the provider, review excluded paths, and rerun only the stage whose inputs changed. Broad or generic results usually mean the project scope or project understanding stage needs correction.

<a id="findings-and-evidence"></a>
## Step 5 — Review findings and evidence

**What this stage does:** turns analysis candidates into human-reviewed security decisions.

1. Open **Findings & Actions**.
2. Select a finding.
3. Check severity and confidence.
4. Read the affected behavior and source location.
5. Open **Proof / Evidence**.
6. Follow the source, transit, sensitive operation, and missing-control evidence when those elements are available.
7. Check whether the described behavior is reachable in the imported project and scope.
8. Choose the appropriate decision:
   - **Accept** when the risk and evidence are confirmed.
   - **Reject** when the candidate does not hold after review.
   - **Downgrade** when the issue exists but the current severity is too high.
   - **Defer** when the issue needs later evidence or scheduled work.
9. Record the reason and save the decision.

![Personal findings and evidence](assets/personal/personal-findings.png)

**Result:** every finding used in reporting or remediation has a visible decision, evidence, and current status.

**If it fails:** keep incomplete evidence unconfirmed, check the project scope and provider output, and rerun the relevant analysis before promoting the finding.

<a id="reports-and-fixes"></a>
## Step 6 — Produce the reviewed report

**What this stage does:** creates the audit deliverable from findings that have already been reviewed.

1. Select the reviewed findings to include.
2. Open the report preview.
3. Check the severity, decision state, evidence, affected files, impact, and remediation direction.
4. Remove items that have not completed human review.
5. Save or export the report.
6. Open the saved report and confirm that the selected findings are present.

![Personal report and fix workflow](assets/personal/personal-reports-and-fixes.png)

**Result:** the report contains the intended reviewed findings rather than every raw analysis candidate.

**If a finding is missing:** return to Findings, confirm that it has a saved decision, and include it in the report selection.

## Step 7 — Generate, apply, test, and close a scoped fix

**What this stage does:** takes one confirmed scope through a reversible repair loop.

1. Select the confirmed finding or bounded finding set.
2. Choose **Generate scoped fix package**.
3. Review the affected files, patch scope, assumptions, test command, and rollback instructions.
4. Check the source worktree. Save or commit unrelated work before applying the package.
5. Review the patch before applying it.
6. Apply the package.
7. Run the project’s real tests.
8. Inspect the resulting Git diff and confirm that unrelated files did not change.
9. Keep the fix when the tests and review pass.
10. Use the recorded rollback path when the result is not acceptable, then confirm that the source tree returned to its prior state.
11. Update the finding or report with the final remediation result.

**Result:** the finding has a bounded patch, test evidence, and a clear kept-or-rolled-back outcome.

**If the package is too large:** return to Findings, reduce the selected scope, and generate a new package. Do not apply a package that contains unrelated files.

<a id="personal-mcp"></a>
## Optional — Connect Personal MCP

Use Personal MCP after the desktop instance, provider, and project are working. It is an optional external access path, not a replacement for the desktop audit.

1. Keep the matching Personal desktop instance running.
2. Open **Settings → External Apps / MCP**.
3. Enable external application connections.
4. Create a connection name.
5. Choose **Read only** or **Developer collaboration**.
6. Select the Personal projects the connection may access.
7. Choose whether reports, evidence, and fix material may be returned.
8. Create the connection.
9. Copy the Codex or general MCP configuration into the client.
10. From the client, list authorized projects and read the allowed project snapshots, findings, reports, or fix material.
11. Review pending work requests in the desktop app before starting them.
12. Check request history and revoke the connection when it is no longer needed.

![Personal MCP configuration](assets/personal/personal-mcp.png)

**Result:** the external client can access only the selected Personal projects and material allowed by the connection.

**Boundary:** Personal MCP cannot connect to Team desktop, run arbitrary commands, or bypass a desktop confirmation.

<a id="troubleshooting"></a>
## Troubleshooting by stage

| Problem | Check |
| --- | --- |
| License remains pending | Finish the official service step, return to the same Personal instance, and refresh License |
| Provider is unavailable | Test Base URL, model, credential, and network access in Settings → Providers |
| Imported path is wrong | Remove the project entry and import the repository root |
| Results are too broad | Fix exclusions and project understanding before increasing depth |
| Report misses a finding | Save the human decision and include the finding in the report selection |
| Fix package is too large | Reduce the selected finding scope and regenerate |
| MCP cannot connect | Keep the matching Personal instance running and recreate the scoped STDIO configuration |

## Personal closure checklist

- Personal is activated and the edition is correct.
- The default provider passes its test.
- The repository root, exclusions, language, depth, and assurance mode are saved.
- Project understanding and required analysis stages completed.
- Every reported finding has a human decision and evidence review.
- The report opens and contains the intended findings.
- Every applied fix has a reviewed diff, test result, and rollback path.
- Any Personal MCP connection is scoped to named projects and can be revoked.
