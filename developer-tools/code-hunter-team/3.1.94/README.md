# Code Hunter Team Developer Tools 3.1.94

These packages are the Team developer surface for Code Hunter 3.1.94. They are built from the same source baseline as the desktop documentation and bundle both the Team Agent and Team Agent LSP for:

The four-platform packages have passed layout, protocol, and structure validation. Native IDE installation and a live Team tenant were not executed in the current environment; the public package therefore includes a capture-boundary record instead of historical screenshots.

- macOS Apple Silicon: `darwin-arm64`
- macOS Intel: `darwin-x64`
- Linux x64: `linux-x64`
- Windows x64: `win32-x64`

Use the package checksum before installing. The package metadata, binary layout, and SHA-256 values are recorded in [`manifest.json`](manifest.json) and [`SHA256SUMS`](SHA256SUMS).

## VS Code

1. Download `plugins/vscode/codehunter-team-vscode-3.1.94.vsix` and verify its SHA-256.
2. In VS Code open **Extensions → … → Install from VSIX** and select the file.
3. Open the CodeHunter activity bar and **Remediation Inbox**.
4. In Code Hunter Team desktop open **Agent Management**, create a one-time enrollment code for the intended Team project, and keep the code private.
5. Run the bundled agent enrollment command shown by the desktop. It creates `.codehunter/team-agent.toml` in the workspace.

6. In the inbox choose **Refresh tasks**, open a task, and confirm the project and source commit.
7. Use **Claim task → Generate fix → Preview patch → Apply patch → Run tests → Create PR**. Review and confirm each working-tree or remote-source change.

Native IDE screenshot capture was not executed in the current environment; see [`screenshots/CAPTURE_NOT_EXECUTED.md`](screenshots/CAPTURE_NOT_EXECUTED.md).

The extension settings allow an explicit Team API base URL, agent config path, agent binary path, LSP binary path, and default test command. Leave overrides empty when the enrolled workspace configuration should be used.


## JetBrains

1. Download `plugins/jetbrains/codehunter-team-jetbrains-3.1.94.zip` and verify its SHA-256.
2. In IntelliJ IDEA or another supported JetBrains IDE open **Settings → Plugins → gear → Install Plugin from Disk**.
3. Select the ZIP, restart the IDE, and open **View → Tool Windows → CodeHunter Remediation Inbox**.
4. Enroll the Team Agent from **Agent Management** using the one-time code and the workspace config path.
5. Refresh tasks, claim a task, preview the patch, apply only after review, run tests, and create a PR/MR when the project policy permits it.


## Confirmation and credential boundaries

- Enrollment codes are one-time credentials. Do not commit them or put them in screenshots.
- The agent configuration identifies the enrolled Team endpoint and project scope; it is not a Personal license or provider API key.
- The desktop and Team control plane remain authoritative for workspace roles, risk acceptance, release readiness, and formal fix verification.
- Applying a patch, running tests, and creating a PR/MR require the developer's review and confirmation.
- If the four-platform layout check, protocol tests, VSIX install smoke, or JetBrains structure verification fails, treat the package as unavailable and do not substitute a historical package.
