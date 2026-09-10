# Phase 2–3 source correction report

## Scope and branch

- Source repository: `C:/Users/EvanMoore/Documents/GitHub/hermes-profiles`
- Branch verified before edits: `hermes-agent-setup` at `867a555e13bae53a3945aa5328b1e09d347268cc`.
- Runtime profile files, runtime configuration, dependencies, gateway state, and secrets were not changed.
- No commit was created.
- Edited allowlist: exactly the 28 names in the approved plan.

## Source changes

For each allowlisted profile, the following behavioral source files changed:

- `profiles/<profile>/SOUL.md`
- `profiles/<profile>/AGENTS.md`
- `profiles/<profile>/profile.yaml`

The 84 exact changed source paths and SHA-256 values are in `reports/phase23-source-sha256.txt`. That manifest has 84 entries and SHA-256 `90ca50c2f50903ba9151a39a79aeb8506338e032fae0254cffb6e73e51456566` at generation time. Use it for source-to-runtime hash comparison during a later allowlisted deployment.

Implemented source behavior:

- Applied the plan’s common artifact/Kanban policy to both `SOUL.md` and `AGENTS.md` for all 28 profiles.
- Replaced retained AGENTS loading guidance with installed-skill loading sequences, including the required corrections for curator, data architect, data scientist, debugger, implementation planner, researcher, reviewer, UX designer, writer, technical architect, and SDD.
- Researcher now declares Hermes `web_search`/`web_extract` as its default retrieval path, browser fallback, workspace-safe paths, concise URL-backed evidence, and no raw-dump handoff.
- Orchestrator is framed as Kanban control plane only, with actual profile routing and a terminal verifier for consequential work; unsupported specialist-delegation, kanban-orchestrator, and council claims were removed from the retained source behavior.
- SDD is framed as a top-level formal-lifecycle alternative that creates Kanban tasks for actual implementation/review profiles and does not claim specialist implementation by default.
- Curator requires a task-supplied vault path and blocks rather than assuming one.
- Mermaid claims are conditional on a verified renderer; otherwise output is explicitly unrendered source. Platform/SRE guidance distinguishes design support from locally executable tooling.
- All 28 `profile.yaml` descriptions now state a positive scope plus an exclusion; collision guards in the plan are encoded for the named routing roles.

## Static validation output

Custom allowlist/policy/literal validator:

```text
allowlist_count=28
common_policy_files_checked=56
skill_view_literals_checked=68
source_SKILL_md_names=57
common_policy_and_literal_validation=PASS
forbidden[groktocrawl]=PASS
forbidden[/tmp/]=PASS
forbidden[specialist-delegation]=PASS
forbidden[kanban-orchestrator]=PASS
forbidden[council]=PASS
forbidden[role="orchestrator"]=PASS
platform_boundary[platform-engineer]=PASS
platform_boundary[site-reliability-engineer]=PASS
researcher_grounded_citations_source=ABSENT
```

`git diff --check` completed successfully (exit code 0).

The repository validator was executed with an ephemeral `uv run --with PyYAML` environment. It ran, but exited 1 because all profile skill links are reported as unreachable in this Windows checkout, including untouched excluded profiles. Example exact output:

```text
Profile validation failed:
- profiles\backend-engineer\profile.yaml: declares skills not reachable from profile skills/: artifact-pyramids, backend-engineering
...
- profiles\writer\profile.yaml: declares skills not reachable from profile skills/: artifact-pyramids, editorial-methodology
```

The direct `test -e` check nevertheless reported existing paths for representative retained links (`research-methodology`, `researcher-workflow`, `software-architecture-analysis`, `mermaid-diagrams`, and `architecture`). This is a source-checkout symlink/reachability limitation requiring resolution before accepting a deployment, not a runtime deployment action.

## Unresolved gaps and limitations

1. `skills/grounded-citations/SKILL.md` is absent from the source pool, so it was not invented or copied into researcher. Researcher guidance makes its use conditional on a future installed source skill. Add the source skill and a researcher-only relative link before deployment if grounded-citations is mandatory.
2. The repo validator’s unreachable-skill failure must be resolved on a symlink-capable checkout before the Phase 3 skills gate can be treated as fully passing.
3. This phase did not deploy behavioral files, install dependencies, configure tool/model routing, render Mermaid, or validate live profiles. Those are later phase responsibilities.

## Later deployment hash comparison

From the source repository, compare only allowlisted behavioral files listed in `reports/phase23-source-sha256.txt` against their intended runtime counterparts after copying. Do not copy `config.yaml`, `.env`, memory, sessions, state, cron, gateway, or profile-local environments.
