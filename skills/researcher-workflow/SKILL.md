---
name: researcher-workflow
description: >-
  Non-interactive deep research pipeline for specialist subagents.
  Use when the orchestrator, product-manager, or another profile assigns a
  research mission that requires systematic investigation with progressive
  disclosure. The researcher receives a brief, interpolates scope, executes
  multi-pass research with Hermes web tools, evaluates gaps for recursion, and
  produces a layered artifact pyramid in an assigned durable workspace.
compatibility: Hermes Agent — designed for non-interactive subagent operation
metadata:
  tags: [workflow, bundle, research, subagent, pipeline, progressive-disclosure]
  related-skills: [research-methodology, artifact-pyramids, grounded-citations]
  spec-version: "1.1"
---

# Researcher Workflow

A 5-phase workflow for systematic deep research with progressive disclosure artifact output. Designed for the researcher specialist subagent profile when dispatched by an orchestrator.

```
RECEIVE MISSION → GATHER → EVALUATE GAPS → [RECURSE] → BUILD PYRAMID → DELIVER
```

## Sub-Skills

| Phase | Skill | Trigger |
|-------|-------|---------|
| Receive Mission | `researcher-workflow/receive-mission` | Orchestrator assigns a research brief — reformulate into explicit scope |
| Gather | `researcher-workflow/research-gather` | Discover with `web_search`, retrieve with `web_extract`, and synthesize evidence |
| Evaluate Gaps | `researcher-workflow/evaluate-gaps` | Assess gathered material, decide on recursion depth |
| Build Pyramid | `researcher-workflow/build-pyramid` | Assemble progressive disclosure artifact files |
| Deliver | `researcher-workflow/deliver-findings` | Report back with absolute path references and layer descriptions |

## Navigation

When this umbrella is loaded (by the researcher profile), identify which phase you're in, load the corresponding sub-skill via `skill_view()`, and follow its instructions. Each sub-skill documents its transition signals.

For source-backed deliverables, also load the citation and grounding procedure:

```
skill_view(name="grounded-citations")
```

## Pipeline Heuristics

- **Entry:** Always starts at Phase 1 (Receive Mission). The other phases cannot be entered directly.
- **Recursion:** Phase 3 (Evaluate Gaps) can loop back to Phase 2 (Gather) for targeted follow-up. This is the only non-linear path.
- **Retrieval:** Use `web_search` for discovery and `web_extract` for page or document retrieval by default. Use browser automation only when normal extraction fails or interaction is required. See `references/tool-governance.md`.
- **Artifacts:** Resolve a durable `<work-root>` in Phase 1 from the assigned Kanban workspace or current project. Use a Windows-safe temporary directory only for explicitly ephemeral direct tasks. Each layer links downward with descriptions so consuming agents can choose their depth.
- **State:** No persistent state between phases. Each sub-skill reads the mission brief and artifact directory to determine context.

## Pitfalls

### Bounded delegation and retrieval recovery

The Gather phase may use `delegate_task` for bounded parallel research when the mission benefits from independent source or methodology coverage. If one broad sub-task times out, split it into focused sub-tasks (up to 3) with distinct, non-overlapping scopes rather than repeating the same request.

If search or extraction is empty, narrow the query, try the canonical source URL directly with `web_extract`, and record the coverage gap. Use browser automation only when extraction still fails or the source requires interaction. Never replace missing evidence with an unsupported claim.

Key recovery principle: preserve the research question while reducing retrieval scope. Prefer a few verified canonical sources over a broad but ungrounded synthesis.
