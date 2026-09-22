# Personal: Reports and Fixes

Use this page to export reviewed findings and prepare a limited repair package.

## Create a report

1. Open **Findings & Actions**.
2. Select findings that have been reviewed.
3. Open the report preview.
4. Check severity, evidence, affected files, and remediation direction.
5. Save or export the report.

## Generate and apply a fix package

1. Select a confirmed finding.
2. Choose **Generate scoped fix package**.
3. Review the patch scope, assumptions, test command, and rollback instructions.
4. Check that the source worktree is clean or that your current changes are saved.
5. Apply the package only after reviewing the diff.
6. Run the project tests.
7. Inspect the resulting diff.
8. Revert the package using the recorded rollback path when the result is not acceptable.

![Personal report preview](../assets/personal/personal-reports-and-fixes.png)

### Result

The report contains only the selected reviewed findings. The fix package contains a bounded patch and the information needed to test or roll it back.

### Common issue

If the package includes unrelated files, return to Findings, reduce the selection, and generate a new scoped package.
