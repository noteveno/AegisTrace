# AegisTrace audit artifacts

Create `aegistrace-audit/` at the audited repository root after scope is authorized. It contains audit evidence and should not be committed unless the user explicitly requests it.

| File | Required content |
| --- | --- |
| `scope.md` | Target, authorization, permitted actions, prohibited actions, network/dependency permission, coverage budget, assumptions |
| `recon.md` | Architecture, commands, entry points, trust boundaries, sensitive assets, attack surface, prioritized hunt queue |
| `hunt-log.md` | One entry per scoped hunt: bug class, scope, files/functions checked, sources, sinks, guards, evidence, outcome |
| `findings.md` | Confirmed, likely, downgraded, and rejected findings with the reason for each classification |
| `report.md` | Executive summary, risk profile, prioritized fixes, complete finding records, commands run, and coverage limits |

Keep notes concise and evidence-linked. Update the relevant artifact as work proceeds rather than reconstructing it at the end. If machine-readable output is requested, create `findings.json` alongside `report.md` and preserve the same finding IDs and statuses.
