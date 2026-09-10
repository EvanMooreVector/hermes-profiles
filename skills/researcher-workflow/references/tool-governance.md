# Tool Governance for Researcher Subagents

Use Hermes built-in web tools as the normal retrieval path.

| Need | Default route |
|------|---------------|
| Discover relevant sources | `web_search` with focused queries and bounded result counts |
| Retrieve a selected page or document | `web_extract` on the canonical URL |
| Retrieve several independent sources | Batch independent `web_extract` calls, then synthesize |
| JS-heavy, blocked, or interactive source | Browser automation, but only after normal extraction fails or interaction is required |
| Local source or attachment | `read_file` or the appropriate document tool |

## Retrieval Sequence

1. Frame the question and identify preferred primary-source domains.
2. Use `web_search` to discover candidate URLs.
3. Select authoritative and independent sources; use `web_extract` to read them.
4. Register retrieved URLs with `grounded-citations` before drafting a source-backed deliverable.
5. If extraction is empty or incomplete, retry the canonical URL or a more specific page.
6. Use browser automation only when normal extraction still fails or the source requires interaction.
7. Record unresolved coverage gaps rather than presenting unsupported claims.

## Evidence Rules

- A search-result snippet supports only the text it contains. Extract the page before using body-level claims.
- Prefer primary sources, and triangulate consequential claims with an independent source.
- Include source URLs and concise supporting evidence in handoffs.
- Do not forward raw search or extraction dumps downstream.
