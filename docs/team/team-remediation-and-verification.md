# Team: Remediation and Verification

Use the Remediation Center to assign work, prepare a bounded fix, and verify the submitted change.

## Create and claim a task

1. Open a reviewed finding.
2. Choose **New remediation task**.
3. Write acceptance criteria.
4. Assign the Owner.
5. Let the Developer claim the task.
6. Generate a remediation context pack.

## Prepare and verify a fix

1. Generate a local fix package.
2. Preview the patch, test command, rollback path, and assumptions.
3. Apply the patch locally or submit a PR/MR.
4. Run the project tests and CI.
5. Bind the CI evidence to the task and commit.
6. Run fix verification.
7. Review Verified fixed, Accepted risk, or Pending verification.
8. Check the release readiness state.

![Team remediation task](../assets/team/team-remediation-and-verification.png)

### Result

The finding has an Owner, acceptance criteria, a linked change, test evidence, and a verification state.

### Common issue

If CI evidence does not match the submitted commit, bind the evidence to the exact source revision and run verification again.
