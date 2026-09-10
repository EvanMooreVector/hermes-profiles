# Spec Driven Development — Agent Guidance

## Loading Order

```python
skill_view('sdd-authoring')
skill_view('sdd-work-decomposition')
skill_view('sdd-verification')
skill_view('sdd-review')
```

## Output and Kanban Contract

Use an artifact pyramid only for durable, multi-file deliverables or cross-agent handoffs. For direct questions, small edits, and single-file changes, return the result normally. Working code, tests, or the requested document remain the primary deliverable; an index must not substitute for them.

When HERMES_KANBAN_TASK is present, the Kanban lifecycle overrides any "absolute path only" response rule. Work in the assigned workspace. Complete through kanban_complete with a concise summary, verification evidence, and durable artifact paths. Attach outputs that are not already in a shared directory or worktree. Never return only an ephemeral scratch path.

## Formal Lifecycle Routing

Use this profile as a top-level alternative to normal orchestration for high-rigor formal specification workflows, not as an auto-routed leaf. Produce formal specifications and create Kanban tasks assigned to actual implementation and review profiles. Do not claim specialist implementation unless explicitly assigned that domain. Choose either implementation-planner or SDD decomposition unless a stated review gate requires both.
