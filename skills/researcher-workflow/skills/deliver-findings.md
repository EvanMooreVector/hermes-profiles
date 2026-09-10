---
name: deliver-findings
description: >-
  Delivery phase of the researcher-workflow. Reports findings back to the
  orchestrator with absolute path references and a description of what's
  at each layer of the pyramid. This is the final phase.
compatibility: Hermes Agent
metadata:
  tags: [research, delivery, handoff]
  spec-version: "1.1"
---

# Deliver Findings

## When to Use

Load this skill after Phase 4 (Build Pyramid) is complete. All three layers of the artifact pyramid exist and cross-reference links have been verified.

## What to Do

### 1. Verify the Pyramid is Complete

Use `search_files(target='files')` on `<work-root>` to enumerate expected files. Confirm the summary, per-dimension analysis files, dossiers, and every referenced path exist.

For source-backed deliverables, run the verification procedure from `grounded-citations` and confirm the Sources mapping agrees with the citation ledger.

### 2. Report Back to the Orchestrator

Return a concise structured delivery report with absolute paths. The output should enable the orchestrator to read the layer appropriate to its needs and let downstream consumers drill down without receiving a raw research dump.

```
## Research Complete: <Mission Title>

### Artifact Pyramid

**Layer 1 — Executive Summary**
Path: <absolute-work-root>/layer-1-summary/README.md
Best for: Product managers, executives — the bottom line and key findings
Contains: Single-page summary with confidence assessments and links to deeper analysis

**Layer 2 — Analysis Collection**
Path: <absolute-work-root>/layer-2-analysis/
Best for: Architects, domain experts — thematic analysis organized by finding
Contains: N individual analysis files, each covering a major theme with evidence and links to detailed dossiers
Available files: <list each analysis file with one-line description>

**Layer 3 — Detailed Dossiers**
Path: <absolute-work-root>/layer-3-detailed/
Best for: Validators and deep investigators — organized source URLs, concise evidence, source evaluations, and gap decisions
Contains: N research logs, source quality assessments, and gap briefs
Available files: <list each dossier with one-line description>

### Evidence Handoff
- Source URLs: <canonical URLs actually retrieved>
- Concise evidence: <claim-to-source summary; do not paste raw retrieval dumps>
- Coverage gaps: <unresolved or inaccessible sources>

### Methodology Notes
- Sources evaluated using CRAAP framework (see layer-3-detailed/source-quality-assessment.md)
- Gaps evaluated as in-scope:
  - <gap that was filled> → resolved in gather pass 2
- Gaps evaluated as out-of-scope:
  - <gap set aside> → logged in layer-3-detailed/gap-brief-N.md

### Confidence Summary
- High: <list>
- Medium: <list>
- Low: <list>
```

### 3. Preserve Durable Artifacts

Keep Kanban and cross-agent deliverables in the assigned workspace or current project. If an explicitly ephemeral direct task used a Windows-safe temporary directory, attach or copy any user-requested deliverable to durable storage before completion.

## Transition Signals

This is the terminal phase. No further transition.

## Tool Use

- `search_files` and `read_file` for final verification.
- Standard output plus the Kanban lifecycle tool when assigned for the delivery handoff.
