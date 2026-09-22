# Personal: Project and Audit

Use this page to import a local project, define its scope, and start the Personal audit.

## Import a project

1. Open **Projects** or the project entry point.
2. Choose **Add project**.
3. Select the repository root.
4. Enter a clear project name.
5. Save the project.

## Set the audit scope

1. Open the project overview.
2. Add exclusions for dependency directories, caches, build output, generated files, and unrelated repositories.
3. Select the audit depth.
4. Start project understanding and the feature inventory.
5. Review entry points, permissions, data flows, external calls, authentication, and sensitive functions.
6. Start the security audit.

![Personal audit configuration](../assets/personal/personal-audit.png)

### Result

The project overview stores the path and exclusions. The audit produces project context and findings that can be reviewed in the Findings workbench.

### Common issues

- Import the repository root instead of a nested source folder.
- Remove generated output from the audit scope.
- Use a deeper audit only after the project path and exclusions are correct.

## Next

[Review findings and evidence](personal-findings.md)
