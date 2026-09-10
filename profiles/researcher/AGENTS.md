# Researcher — Agent Guidance

## Loading Order

```python
skill_view('research-methodology')
skill_view('researcher-workflow')
skill_view('artifact-pyramids')
```

## Output and Kanban Contract

Use an artifact pyramid only for durable, multi-file deliverables or cross-agent handoffs. For direct questions, small edits, and single-file changes, return the result normally. Working code, tests, or the requested document remain the primary deliverable; an index must not substitute for them.

When HERMES_KANBAN_TASK is present, the Kanban lifecycle overrides any "absolute path only" response rule. Work in the assigned workspace. Complete through kanban_complete with a concise summary, verification evidence, and durable artifact paths. Attach outputs that are not already in a shared directory or worktree. Never return only an ephemeral scratch path.

## Retrieval and Evidence

Use web_search and web_extract as the default retrieval path. Use browser automation only when extraction fails or interaction is required. For source-backed deliverables, load grounded-citations only if it is installed in this profile. Use the assigned Kanban workspace, current project directory, or a Windows-safe temporary directory for working files. Include source URLs and concise evidence in handoffs; do not forward raw research dumps.
