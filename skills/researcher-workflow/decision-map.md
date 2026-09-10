# Researcher Workflow — Decision Map

```mermaid
graph TD
    START([Orchestrator dispatches mission]) --> Phase1[Phase 1: Receive Mission]
    Phase1 --> Phase1_Work[Reformulate brief, resolve work root, write SCOPE.md]
    Phase1_Work --> Phase2[Phase 2: Research Gather]

    Phase2 --> Phase2_Work["Discover with web_search<br/>retrieve with web_extract"]
    Phase2_Work --> ExtractCheck{Normal extraction succeeded?}
    ExtractCheck -->|Yes| Phase3[Phase 3: Evaluate Gaps]
    ExtractCheck -->|No or interaction required| BrowserFallback[Conditional browser automation]
    BrowserFallback --> Phase3

    Phase3 --> GapCheck{Apply three-question model}
    GapCheck -->|In scope, changes conclusions, adds depth| Recursed[Recurse: Full or targeted pass]
    GapCheck -->|In scope, doesn't change conclusions, adds depth| RecurseLight[Recurse: Lightweight pass]
    GapCheck -->|In scope, adds bulk only| StopGap[Log as out-of-scope]
    GapCheck -->|Out of scope| StopGap

    Recursed --> Phase2
    RecurseLight --> Phase2

    StopGap --> Phase4[Phase 4: Build Pyramid]

    Phase4 --> Layer3[Assemble Layer 3: Detailed dossiers]
    Layer3 --> Layer2[Assemble Layer 2: Analysis collection]
    Layer2 --> Layer1[Assemble Layer 1: Executive summary]
    Layer1 --> Verify[Verify cross-reference links]

    Verify --> Phase5[Phase 5: Deliver Findings]
    Phase5 --> Done([Return durable paths and concise evidence])

    style START fill:#4a90d9,color:#fff
    style Done fill:#4a90d9,color:#fff
    style GapCheck fill:#e6a817,color:#000
    style ExtractCheck fill:#e6a817,color:#000
    style Phase1 fill:#2d6a4f,color:#fff
    style Phase2 fill:#2d6a4f,color:#fff
    style Phase3 fill:#2d6a4f,color:#fff
    style Phase4 fill:#2d6a4f,color:#fff
    style Phase5 fill:#2d6a4f,color:#fff
```

## Flow Notes

- Phases 1, 2, 4, and 5 are mandatory and sequential.
- Phase 3 is the only research branching point: it can loop back to Phase 2 for recursion.
- Recursion intensity ranges from lightweight discovery to a full multi-source pass.
- Maximum 2 recursion cycles before escalation.
- Browser automation is conditional on failed extraction or required interaction.
- Artifacts accumulate under the `<work-root>` resolved in Phase 1.
- The pyramid is built from bottom up: dossiers → analysis → summary.
