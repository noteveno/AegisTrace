# AegisTrace

![AegisTrace vulnerability discovery harness](assets/hero.png)

**An evidence-driven prompt workflow for AI-assisted vulnerability discovery.**

AegisTrace helps coding agents audit a repository methodically: map the system, run focused vulnerability hunts, challenge every suspected finding, trace actual reachability, and report only what survives scrutiny. It creates a durable `aegistrace-audit/` folder of Markdown notes so the audit stays reviewable from Recon through the final report.

It is a prompt kit, not a scanner. Its value is the disciplined investigation process it gives to an AI agent.

## Start here

1. Open [the full harness](prompts/full.md) in your preferred AI coding agent.
2. Give the agent access only to a project you are authorized to assess.
3. Ask it to begin at Recon and retain the staged workflow through the final report.

For a shorter starting point, use [the compact prompt](prompts/compact.md). See [the sample report](examples/sample-report.md) for the intended standard of evidence and clarity.

## Install as an agent skill

Paste this into your AI coding agent:

```text
Install AegisTrace from https://github.com/noteveno/AegisTrace: detect my compatible AI coding CLIs, ask whether to install it for one or all, safely install `skills/aegistrace`, verify it, and tell me how to use it—never use sudo or overwrite an existing installation without asking.
```

### Install manually

Clone the repository, then copy the `skills/aegistrace` folder to the personal skill directory for your coding agent. Choose one path—or install it in every tool you use.

| Tool | Personal skill directory |
| --- | --- |
| Codex | `~/.codex/skills/aegistrace` |
| Claude Code | `~/.claude/skills/aegistrace` |
| OpenCode | `~/.config/opencode/skills/aegistrace` |

For example, this installs AegisTrace for Claude Code:

```bash
git clone https://github.com/noteveno/AegisTrace.git
mkdir -p ~/.claude/skills
cp -R AegisTrace/skills/aegistrace ~/.claude/skills/aegistrace
```

For Codex or OpenCode, replace the final destination with the matching path in the table. Restart the agent if it does not notice the new skill automatically, then ask it to run an **AegisTrace audit** (or invoke `aegistrace` directly when your agent supports named skills).

Already have an `aegistrace` folder at that destination? Back it up or remove it only after checking what version it contains; do not overwrite it blindly.

## The workflow

| Stage | Outcome |
| --- | --- |
| Recon | Architecture, entry points, trust boundaries, and a prioritized hunt queue |
| Hunt | Narrow, evidence-led investigations by vulnerability class and subsystem |
| Validate | Skeptical review that removes weak or non-reachable claims |
| Gapfill | Focused second passes over high-risk, lightly covered areas |
| Dedupe | One finding per root cause, with meaningful variants preserved |
| Trace | An end-to-end path from untrusted input to impact |
| Feedback | Variant analysis based on confirmed patterns |
| Report | Actionable findings with evidence, fixes, and regression tests |

## Repository layout

```text
assets/             Visual assets for the project
examples/           Reference outputs
prompts/            Full and compact AegisTrace prompts
skills/             Portable Agent Skills package
```

## Safety and scope

Use AegisTrace only on systems and repositories you are explicitly authorized to assess. The included prompts prioritize local, safe, and non-destructive validation. They do not authorize testing external targets, extracting data, or making production changes.

If you discover a potential vulnerability in this project itself, follow [our security policy](SECURITY.md) rather than opening a public issue.

## Contributing

Contributions that make findings more precise, validation more rigorous, or reports more actionable are especially welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing a change.

## License

Released under the [MIT License](LICENSE).
