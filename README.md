# AegisTrace

![AegisTrace vulnerability discovery harness](assets/hero.png)

**An evidence-driven prompt workflow for AI-assisted vulnerability discovery.**

AegisTrace helps coding agents audit a repository methodically: map the system, run focused vulnerability hunts, challenge every suspected finding, trace actual reachability, and report only what survives scrutiny.

It is a prompt kit, not a scanner. Its value is the disciplined investigation process it gives to an AI agent.

## Start here

1. Open [the full harness](prompts/full.md) in your preferred AI coding agent.
2. Give the agent access only to a project you are authorized to assess.
3. Ask it to begin at Recon and retain the staged workflow through the final report.

For a shorter starting point, use [the compact prompt](prompts/compact.md). See [the sample report](examples/sample-report.md) for the intended standard of evidence and clarity.

## Install as an agent skill

The portable source is [skills/aegistrace](skills/aegistrace). Copy that directory into the relevant location, then invoke the skill by name or ask the agent to perform an AegisTrace audit.

| Tool | Personal installation | Project installation |
| --- | --- | --- |
| Codex | `~/.codex/skills/aegistrace` | `.agents/skills/aegistrace` |
| Claude Code | `~/.claude/skills/aegistrace` | `.claude/skills/aegistrace` |
| OpenCode | `~/.config/opencode/skills/aegistrace` | `.opencode/skills/aegistrace` |
| Other compatible agents | See the tool's Agent Skills location | `.agents/skills/aegistrace` |

For example, after cloning this repository, install it for Claude Code with:

```bash
mkdir -p ~/.claude/skills
cp -R skills/aegistrace ~/.claude/skills/aegistrace
```

The same source folder works for all listed tools; only its destination changes. Claude Code and OpenCode both support the interoperable `SKILL.md` directory pattern. [Claude Code documentation](https://code.claude.com/docs/en/skills) and [OpenCode documentation](https://opencode.ai/v2/docs/skills) describe their respective locations.

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
```

## Safety and scope

Use AegisTrace only on systems and repositories you are explicitly authorized to assess. The included prompts prioritize local, safe, and non-destructive validation. They do not authorize testing external targets, extracting data, or making production changes.

If you discover a potential vulnerability in this project itself, follow [our security policy](SECURITY.md) rather than opening a public issue.

## Contributing

Contributions that make findings more precise, validation more rigorous, or reports more actionable are especially welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing a change.

## License

Released under the [MIT License](LICENSE).
