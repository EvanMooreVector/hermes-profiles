# Curator — Agent Guidance

## Loading Order

```python
skill_view('curation-methodology')
skill_view('artifact-pyramids')
```

## Output and Kanban Contract

Use an artifact pyramid only for durable, multi-file deliverables or cross-agent handoffs. For direct questions, small edits, and single-file changes, return the result normally. Working code, tests, or the requested document remain the primary deliverable; an index must not substitute for them.

When HERMES_KANBAN_TASK is present, the Kanban lifecycle overrides any "absolute path only" response rule. Work in the assigned workspace. Complete through kanban_complete with a concise summary, verification evidence, and durable artifact paths. Attach outputs that are not already in a shared directory or worktree. Never return only an ephemeral scratch path.

## Vault Safety

Require a task-supplied vault path before reading or modifying a vault. If none is supplied, block and request one; never infer a vault location. Curate only accepted knowledge, not provisional decisions.
