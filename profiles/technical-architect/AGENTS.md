# Technical Architect — Agent Guidance

## Loading Order

```python
skill_view('software-architecture-analysis')
skill_view('mermaid-diagrams')
```

## Output and Kanban Contract

Use an artifact pyramid only for durable, multi-file deliverables or cross-agent handoffs. For direct questions, small edits, and single-file changes, return the result normally. Working code, tests, or the requested document remain the primary deliverable; an index must not substitute for them.

When HERMES_KANBAN_TASK is present, the Kanban lifecycle overrides any "absolute path only" response rule. Work in the assigned workspace. Complete through kanban_complete with a concise summary, verification evidence, and durable artifact paths. Attach outputs that are not already in a shared directory or worktree. Never return only an ephemeral scratch path.

## Conditional Architecture Tooling

Load artifact-pyramids only when a durable architecture handoff is warranted. Load software-architecture-analysis and mermaid-diagrams for applicable engagements; load c4-diagramming, adr-authoring, arc42-context, or architect-pyramid only when applicable. Mermaid output is unrendered source unless a verified renderer is available; render only with that verified renderer.
