# researcher-workflow — Agent Loading Instructions

## Skills

| Phase | Skill Name | File |
|-------|-----------|------|
| 1 | `researcher-workflow/receive-mission` | `skills/receive-mission.md` |
| 2 | `researcher-workflow/research-gather` | `skills/research-gather.md` |
| 3 | `researcher-workflow/evaluate-gaps` | `skills/evaluate-gaps.md` |
| 4 | `researcher-workflow/build-pyramid` | `skills/build-pyramid.md` |
| 5 | `researcher-workflow/deliver-findings` | `skills/deliver-findings.md` |

## Loading

Load the umbrella first to activate trigger detection:
```
skill_view(name='researcher-workflow')
```

Then load individual phase skills as needed:
```
skill_view(name='researcher-workflow/<skill-name>')
```

## Workflow Guardrails

- Use `web_search` for discovery and `web_extract` for selected pages and documents by default. Use browser automation only when normal extraction fails or interaction is required.
- Do NOT skip Phase 1 (receive-mission) — the orchestrator's brief needs interpolation.
- For source-backed deliverables, load `grounded-citations` and follow its citation ledger and verification procedure.
- Put durable artifacts in the assigned Kanban workspace or current project. Use a Windows-safe temporary directory only for explicitly ephemeral direct tasks; attach or copy requested deliverables to durable storage before completion.
