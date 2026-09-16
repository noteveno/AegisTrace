# AegisTrace Report Schema

Start every report with:

- Executive summary
- Overall risk profile
- Highest-priority fixes
- Commands run
- Files and areas inspected
- Areas not fully covered
- Test coverage gaps

For each finding, use:

```text
Finding ID:
Title:
Status: Confirmed / Likely / Needs more evidence
Severity: Critical / High / Medium / Low / Informational
Confidence: High / Medium / Low
Reachability: Directly reachable / Reachable with conditions / Internal-only / Not reachable
Affected files:
Affected functions, classes, routes, commands, or jobs:
Root cause:
Attack path:
Impact:
Evidence:
Minimal local reproduction:
Recommended fix:
Regression tests to add:
Related variants:
Notes:
```

Severity guide:

- **Critical:** A low-privilege or unauthenticated path to remote code execution, full authentication bypass, mass data compromise, secret extraction, or systemic compromise.
- **High:** Serious privilege escalation, account takeover, significant data exposure, reliable injection, or sensitive cross-tenant access.
- **Medium:** A constrained but real unauthorized action, data exposure, denial of service, or security-control bypass.
- **Low:** Minor information leakage, hardening gap, or limited misuse.
- **Informational:** A maintainability, test-coverage, or hardening recommendation without a direct exploit path.
