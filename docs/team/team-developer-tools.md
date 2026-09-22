# Team: Developer Tools

Team developer tools connect an enrolled developer agent to the Team Remediation Inbox. Plugin packages are distributed through the official Code Hunter download center and are not stored in this documentation repository.

## Install and enroll

1. Download the VS Code extension or JetBrains plugin from the [official download center](https://www.arvantacyber.com/code-hunter/download/).
2. Install the plugin in the IDE.
3. Open **Team → Agent Management** in the desktop app.
4. Create a one-time enrollment code.
5. Run the plugin enrollment command.
6. Confirm that `.codehunter/team-agent.toml` was created.
7. Return to Agent Management and check the agent state.

## Work from Remediation Inbox

1. Open **Remediation Inbox** in the IDE.
2. Refresh tasks.
3. Claim an assigned task.
4. Generate the fix context.
5. Preview the patch.
6. Apply the patch only after review.
7. Run the project tests.
8. Create the PR when the result is ready.

### Result

The IDE shows the enrolled agent, assigned task, patch preview, test result, and PR handoff state.

### Confirmation boundary

Enrollment, patch application, test execution, and PR creation can require desktop or IDE confirmation. The agent token, `.codehunter/team-agent.toml`, and desktop credentials are separate pieces of configuration.

### Common issue

If the inbox is empty, check the enrollment state, workspace membership, task assignment, and matching Team desktop instance.
