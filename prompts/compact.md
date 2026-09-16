# AegisTrace Compact Prompt

```text
Analyze this repository using the AegisTrace 8-stage vulnerability discovery harness: Recon, Hunt, Validate, Gapfill, Dedupe, Trace, Feedback, and Report.

First map the architecture, entry points, trust boundaries, data flows, build/test commands, sensitive assets, and likely attack surface. Then create focused hunt tasks by attack class and subsystem. For each suspected issue, validate it independently, trace real reachability from untrusted input to vulnerable sink, deduplicate shared root causes, search for variants, and produce a structured report with severity, confidence, impact, evidence, reproduction steps, affected files, recommended fixes, and regression tests.

Be evidence-driven. Do not report speculative issues as confirmed. Prioritize reachable vulnerabilities, authorization flaws, injection, unsafe file handling, secret leakage, business logic bugs, dependency risks, unsafe configuration, denial-of-service vectors, and missing tests. Keep all testing local, safe, and non-destructive.
```
