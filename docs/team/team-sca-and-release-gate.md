# Team: SCA and Release Gate

SCA is a Team feature. It inventories dependencies, evaluates advisories and licenses, and contributes to the release decision.

## Configure and run SCA

1. Open the Team iteration SCA panel.
2. Configure the dependency source and scan options.
3. Set severity and exploitability rules.
4. Start the SCA scan.
5. Review components, advisories, licenses, fixed versions, and lifecycle state.
6. Start SCA analysis.

![Team SCA and release gate](../assets/team/team-sca-and-release-gate.png)

## Handle exceptions

1. Open a blocked component.
2. Assign an Owner.
3. Fix the dependency, or create a time-limited exception or VEX entry when policy allows it.
4. Record the approval and expiry.
5. Verify the remediation.

## Check the release gate

1. Open **Release Readiness**.
2. Review Blocked, Pending verification, Pass with risk, and Ready items.
3. Resolve the required findings, evidence, SCA exceptions, and owner approvals.
4. Promote a fresh baseline after the release is accepted.

### Result

The Team release state shows which conditions block release and which risks have an approved owner or verification record.

### Common issue

An expired exception, missing Owner, or unverified dependency keeps the gate blocked. Fix or renew the item according to workspace policy.
