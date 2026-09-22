# Troubleshooting

## Provider is unavailable

Open **Settings → Providers**, test the saved provider, and check Base URL, model, credentials, and network access.

## Project path is wrong

Remove the project entry and import the repository root again. Do not select a build directory, dependency directory, or generated output folder.

## Audit results are too broad

Review the project scope and exclusions, then choose a deeper audit profile only after the project path is correct.

## A report is missing a finding

Confirm that the finding was reviewed and included in the report selection. Unreviewed or excluded findings are not added automatically.

## A fix package is too large

Return to Findings, select only the confirmed finding and its affected scope, and generate a new scoped package.

## MCP does not connect

Keep the matching desktop edition running, recreate the local STDIO configuration from **Settings → External Apps / MCP**, and check that the selected projects are still authorized.

## Team baseline cannot be materialized

Check the code source connection, selected branch or commit, and the project default branch before retrying baseline initialization.

## SCA blocks release

Open the Team SCA page, review the blocked component and its owner, then fix, verify, or approve an active exception according to the workspace policy.
