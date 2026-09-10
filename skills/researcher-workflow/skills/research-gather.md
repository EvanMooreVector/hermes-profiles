---
name: research-gather
description: >-
  Systematic multi-pass research gathering with Hermes web tools. Uses
  web_search for discovery and web_extract for selected pages and documents.
  Browser automation is a conditional fallback when extraction fails or
  interaction is required. When dispatched as a subagent, run this skill to
  execute the research phase of the researcher-workflow.
compatibility: Hermes Agent
metadata:
  tags: [research, gathering, web-search, web-extraction, citations]
  spec-version: "1.1"
---

# Research Gather

## When to Use

Load this skill after completing Phase 1 (Receive Mission) — `<work-root>/SCOPE.md` exists and the artifact directory is ready. This is the execution phase: turning the research questions into gathered material.

## Retrieval Defaults

| Need | Default route |
|------|---------------|
| Source discovery | `web_search` with focused queries |
| Page or document retrieval | `web_extract` on selected canonical URLs |
| Independent source retrieval | Batch independent `web_extract` calls |
| JS-heavy, blocked, or interactive source | Browser automation only after extraction fails or interaction is required |

Do not treat search snippets as page evidence. Extract the selected source before relying on body-level claims.

## What to Do

### 1. Read the Scope

Read `<work-root>/SCOPE.md`. Understand the research questions, scope boundaries, and known unknowns.

### 2. Load Research and Citation Methods

If not already loaded, load the shared methodology references:

```
skill_view(name="research-methodology", file_path="references/source-evaluation.md")
skill_view(name="research-methodology", file_path="references/synthesis-patterns.md")
```

For a source-backed deliverable, load:

```
skill_view(name="grounded-citations")
```

Register every source URL at retrieval time as that skill directs. Do not reconstruct URLs or citation identifiers from memory after drafting.

### 3. Execute First Research Pass

1. Run bounded `web_search` queries for each research question.
2. Select authoritative primary sources and independent corroborating sources.
3. Retrieve selected URLs with `web_extract`; batch independent extractions.
4. If normal extraction is empty or incomplete, retry a canonical URL or narrower page. Use browser automation only when extraction still fails or the source requires interaction.
5. Record unresolved access or coverage gaps instead of filling them with unsupported claims.

Save a timestamped research log to `<work-root>/layer-3-detailed/01-gather-pass-1.md` with `write_file`:

```markdown
# Gather Pass 1: <date>

## Sources Consulted
- <URL — what the retrieved source provided>

## Concise Evidence
- <claim — citation id and exact or faithfully paraphrased support>

## Key Findings
- <findings organized by research question>

## Conflicting Claims
- <where sources disagree>

## Potential Gaps
- <what seems missing or thin>
```

### 4. Fill Specific Gaps (Targeted Follow-ups)

For each identified gap, use the smallest sufficient retrieval path:

- **Light gap:** one focused `web_search`, then extract the best source.
- **Targeted gap:** `web_extract` a known canonical URL.
- **Deep gap:** several focused searches and independent extractions, then synthesize.
- **Extraction or interaction gap:** conditional browser automation.

### 5. Evaluate Source Quality

For each source, apply the CRAAP test (from source-evaluation.md):
- **Currency:** Is this timely for the research question?
- **Relevance:** Does it actually address the question?
- **Authority:** Who wrote it and what are their credentials?
- **Accuracy:** Is the evidence sound and verifiable?
- **Purpose:** Why does this source exist? Any bias?

Flag low-quality sources in the research log. Do not discard them — note their limitations so the synthesis can account for them.

## Transition Signals

Move to Phase 3 (Evaluate Gaps) when:
- Initial pass is complete and saved to the artifact directory.
- At least one round of targeted follow-ups has been done when needed.
- Gaps are documented in the research log.
- Source quality has been assessed.
- Retrieved URLs and concise evidence are recorded.

You may also transition if the initial pass clearly saturated the topic (no significant gaps remain).

## What to Save

Each research pass should produce a dated file in `<work-root>/layer-3-detailed/`. This builds the bottom layer of the pyramid: organized dossiers of source URLs, concise evidence, quality assessments, and findings rather than raw retrieval dumps.
