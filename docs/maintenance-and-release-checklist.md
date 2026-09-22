# Documentation maintenance and release checklist

Use this checklist for every Code Hunter documentation update.

## Source and product baseline

1. Record the desktop package version, source commit, active build profile, and Team agent protocol version.
2. Create clean isolated worktrees for the private source and public docs repositories. Preserve unrelated dirty work.
3. Build Personal and Team dev profiles from the recorded commit.
4. Run desktop tests, Go tests, Rust agent tests, and the desktop smoke harness.

## Evidence and screenshots

1. Use isolated Personal and Team homes with neutral fixture data.
2. Capture every user-visible gate: edition/version, license path, provider save/test, import/scope, audit depth, findings/evidence, report, fix package, MCP, Team governance, remediation, release readiness, and IDE tools.
3. Prefer a real Electron renderer or plugin capture. Label native file-picker or system-window actions as unexecuted when no native Computer Use surface is available.
4. Review every image for secrets, internal paths, private URLs, and stale version labels.
5. Update `docs/assets/manifest-3.1.94.json` and verify SHA-256 values.

## Developer tools

1. Update VS Code and JetBrains metadata to the desktop version.
2. Build agent and LSP binaries for `darwin-arm64`, `darwin-x64`, `linux-x64`, and `win32-x64` in CI or equivalent trusted builders.
3. Run package layout tests, protocol tests, VSIX install smoke, and JetBrains structure verification.
4. Publish a versioned package directory only when all four platform binaries and checksums are present.

## Public closeout

1. Run `git diff --check`, Markdown link checks, image existence/MIME/dimension checks, secret scans, version consistency checks, and package checksum verification.
2. Review the diff for old-version links. Historical links may remain inside historical directories only.
3. Commit the coherent documentation iteration locally.
4. Push `main` only when explicitly authorized, then verify `git ls-remote`, GitHub HTML, raw Markdown, image GETs, package GETs, and content lengths from outside the worktree.
5. Record the public commit and any CI status in the release note.
