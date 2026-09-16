---
name: aegistrace
description: Conduct an evidence-driven security and reliability audit of a repository. Use when the user requests vulnerability discovery, a security review, bug hunting, or a defensible audit report; do not use for exploitation of external systems.
license: MIT
metadata:
  category: security-review
---

# AegisTrace

Use this skill only for repositories and systems the user is authorized to assess. Keep all investigation local, safe, and non-destructive. Do not access external targets, extract real data, run destructive commands, or modify the audited project unless the user separately asks for a change.

The objective is a small set of defensible findings, not a long list of pattern matches. Do not label a suspicion as confirmed until its input, guard, sink, reachability, and realistic impact have been checked.

## Workflow

### 1. Recon

Read the repository top-down before judging it. Establish:

- Languages, frameworks, runtime, package manager, and build/test/lint/typecheck commands
- Architecture, entry points, routes, CLI commands, jobs, workers, webhooks, and admin interfaces
- Trust boundaries, untrusted inputs, sensitive assets, authentication and authorization flows
- Network, filesystem, database, shell, serialization, cryptography, caching, logging, and third-party integrations
- Tests, CI, deployment configuration, and the highest-risk files

Report a brief architecture map, command inventory, trust-boundary map, sensitive-data inventory, attack surface, and prioritized hunt queue. Prefer fast repository search and real code over filenames alone.

### 2. Hunt

Create narrow tasks that pair one bug class with one subsystem. Examples: authorization bypass in account routes, path traversal in downloads, SSRF in URL imports, command injection in scripts, or race conditions in token rotation.

For each task, record inspected files/functions; input sources; sinks; sanitizers and guards; data flow; and safe local evidence. Consider relevant authentication, authorization, injection, file handling, SSRF, XSS, CSRF, deserialization, parser safety, cryptography, tokens, configuration, secrets, dependencies, concurrency, business logic, data exposure, denial of service, and missing regression tests.

### 3. Validate

Treat every suspicion as wrong until independently supported. Check callers, attacker control, validation, type and schema constraints, middleware, framework protections, escaping, configuration defaults, environment assumptions, existing tests, reachability, and realistic impact.

Classify it as **Confirmed**, **Likely**, **Needs more evidence**, or **False positive**. Remove or downgrade claims that do not survive this review.

### 4. Gapfill and dedupe

Revisit high-risk areas that received only shallow coverage, especially permission checks, admin flows, workers, callbacks, parsing, error and cleanup paths, cache invalidation, token lifecycle code, and TODO/FIXME/SECURITY comments. Collapse repeated symptoms into one finding per root cause, retaining variants only when reachability, impact, or remediation differs materially.

### 5. Trace and feedback

For each confirmed or likely issue, trace:

`input source -> parser/handler -> validation and authentication -> authorization -> business logic -> unsafe sink -> impact`

Classify reachability as **Directly reachable**, **Reachable with conditions**, **Internal-only**, or **Not reachable**. Search for meaningful variants of confirmed patterns and put new variants through validation and tracing before reporting.

### 6. Report

Lead with an executive summary, overall risk, highest-priority fixes, commands run, coverage limits, and test gaps. Use the exact finding fields in [references/report-schema.md](references/report-schema.md). Cite concrete file and line references when available; clearly distinguish evidence from assumptions.

If no issue is confirmed, say so plainly and state what was and was not covered.

## Working style

- Match the investigation depth to the project and its exposure; prioritize externally reachable, high-impact paths.
- Use minimal local proofs of concept only when safe and needed to establish a claim.
- Do not inflate issue counts with duplicates or speculative variants.
- Explain failed commands and continue with static analysis when possible.
- Read [references/report-schema.md](references/report-schema.md) before writing the final report.
