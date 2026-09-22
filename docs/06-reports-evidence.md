# Reports And Evidence

Code Hunter reports are the delivery artifact. Evidence is the product memory that makes those reports defensible.

## Evidence Chain

A defensible finding should connect:

1. Source scope.
2. Project or baseline context.
3. Function or behavior context.
4. Risk path.
5. Human decision.
6. Remediation direction.
7. Verification or accepted risk.
8. Report or release-readiness output.

## Personal Reports

Personal reports are generated from reviewed findings.

Use the current screenshot-backed Personal and Team tutorials for the report path. Historical customer-style report archives are intentionally not included in this public repository.

Typical contents:

- Executive summary.
- Project context.
- Reviewed findings.
- Severity and confidence.
- Evidence and reasoning.
- Remediation direction.
- Appendix or supporting context.

Rules:

- Do not export unreviewed candidate findings.
- Do not include rejected findings unless the report explicitly documents triage decisions.
- Keep the report language aligned with the run language.

## Team Reports

Team reports include governance context.

Typical contents:

- Project and baseline summary.
- Iteration scope.
- Findings and remediation state.
- Task owner and verification state.
- CI or PR/MR evidence.
- Accepted-risk rationale.
- Release-readiness result.

## Release Readiness Evidence

Release readiness should be based on current project and iteration evidence:

- Blocking findings.
- Open remediation tasks.
- Verified fixes.
- CI evidence.
- Reviewer approval.
- Accepted risk.
- SCA policy and exceptions.
- Baseline promotion state.

Do not use a narrow check as proof of a broad release decision. For example, a passing unit test does not prove an SCA policy has passed unless the SCA gate and policy state are also current.

## Fix Packages

Fix packages should include:

- Finding reference.
- Scope.
- Proposed patch or instructions.
- Tests to run.
- Rollback notes.
- Assumptions.
- Checksums or package metadata when available.

Fix packages are not a replacement for review. They are a way to move selected, reviewed findings into scoped repair work.

## Audit Retention

Keep:

- Reports.
- Run metadata.
- Reviewed findings.
- Remediation tasks.
- CI evidence.
- Accepted-risk decisions.
- Release-readiness records.

Avoid storing:

- Provider API keys.
- Raw credentials.
- Customer secrets.
- Unnecessary copies of source code outside the approved workspace.
