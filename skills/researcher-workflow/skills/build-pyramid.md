---
name: build-pyramid
description: >-
  Progressive disclosure artifact pyramid assembly. Loaded after gap evaluation
  determines saturation is reached. Reads gathered material from layer-3-detailed/
  and produces layered output: summary (layer 1), analysis collection (layer 2),
  detailed dossiers (layer 3). Each layer links downward with descriptions.
compatibility: Hermes Agent
metadata:
  tags: [research, pyramid, artifacts, writing, synthesis]
  spec-version: "1.1"
---

# Build Pyramid

## When to Use

Load this skill after Phase 3 (Evaluate Gaps) indicates saturation. All gathered material is in `<work-root>/layer-3-detailed/`. This phase transforms material into the progressive disclosure pyramid.

## Pyramid Structure

```
<work-root>/
├── layer-1-summary/
│   └── README.md
├── layer-2-analysis/
│   ├── 01-market-analysis.md
│   ├── 02-risk-assessment.md
│   └── 03-competitive-landscape.md
└── layer-3-detailed/
    ├── 01-gather-pass-1.md
    ├── 02-gather-pass-2.md
    ├── gap-brief-1.md
    └── source-quality-assessment.md
```

The pyramid shape is narrow at the top (summary, dense) and wide at the bottom (detailed, comprehensive).

## What to Do

### 1. Read All Gathered Material

Read all files in `<work-root>/layer-3-detailed/` to understand the full body of findings.

### 2. Build Layer 3 — Detailed Dossiers (already populated)

The research logs from Phase 2 already live here. Review and organize them into a logical order. Prefix filenames with numbers to indicate reading order. Add a `_index.md` that lists all dossiers with one-line descriptions:

```markdown
# Detailed Dossiers: <Mission Title>

## Available Files

- `01-gather-pass-1.md` — Initial research pass covering <breadth>
- `02-gather-pass-2.md` — Follow-up on <specific gap>
- `source-quality-assessment.md` — CRAAP evaluation of all sources
- `gap-brief-1.md` — Gap that was evaluated as out-of-scope
```

### 3. Build Layer 2 — Analysis Collection

For each major theme from the research, write a focused analysis file. Each analysis file should:

- State the claim or finding.
- Summarize the supporting evidence.
- Note conflicting evidence or uncertainty.
- Link to specific dossiers in layer 3 for detail.

Link format (absolute path plus description):

```
See [<absolute-work-root>/layer-3-detailed/01-gather-pass-1.md]
for the initial discovery that led to this finding.
```

### 4. Build Layer 1 — Executive Summary

Write a single README.md in `layer-1-summary/`. This is the most constrained file — densest, most distilled. Structure:

```markdown
# Research Summary: <Title>

## One-Paragraph Bottom Line
<The single most important thing the PM needs to know>

## Key Findings
- <Finding 1> → [See analysis](<absolute-work-root>/layer-2-analysis/01-market-analysis.md)
- <Finding 2> → [See analysis](<absolute-work-root>/layer-2-analysis/02-risk-assessment.md)

Each finding links to the relevant analysis file with a brief description of what's there.

## Confidence Assessment
- **High confidence:** <claims with strong, triangulated evidence>
- **Medium confidence:** <claims with reasonable but incomplete evidence>
- **Low confidence:** <claims with thin or conflicting evidence>

## Out of Scope
- <Items evaluated and set aside during gap evaluation>

## How to Dive Deeper
- For thematic context → load `<work-root>/layer-2-analysis/`.
- For source URLs, concise evidence, and gap evaluations → load `<work-root>/layer-3-detailed/`.
```

### 5. Ensure Links Work

After writing all layers, verify that each cross-reference actually resolves to a file on disk. A broken link defeats progressive disclosure.

For source-backed deliverables, run the verification procedure from `grounded-citations` before delivery. Include source URLs and concise evidence; do not embed raw retrieval dumps.

## Transition Signals

Proceed to Phase 5 (Deliver) when:
- All three layers are written.
- Cross-reference links are verified.
- Citation verification passes for source-backed files.
- Files are organized with numbered prefixes and `_index.md` guides.

## Tool Use

- `read_file` and `search_files` for inspecting gathered artifacts.
- `write_file` for creating artifact files.
- No web research tools — you're building, not gathering.
