# Decision Matrix (quick reference)

## Requirements → Pattern

| Your requirements | Pattern |
|-------------------|---------|
| Multiple distinct domains, parallel, centralized control, specialists not user-facing | **Subagents** |
| Single agent, many specializations, lightweight composition, direct UX | **Skills** |
| Sequential workflow, state transitions, agent talks to user throughout | **Handoffs** |
| Distinct verticals, parallel query + synthesize | **Router** |
| No binding multi-agent constraint | **Single-agent + Skills** |

## Primitive → When

| Primitive | When |
|-----------|------|
| Skill | Domain container / progressive disclosure |
| Workflow | Specific task procedure inside a skill |
| Agent | Isolation, ownership boundary, parallel worker, staged persona |
| Script | Deterministic I/O |
| MCP | Live external system with auth boundary |

## Performance intuition

| Scenario | Leaner patterns |
|----------|-----------------|
| One-shot task | Skills / Handoffs / Router |
| Repeat in-thread | Skills / Handoffs |
| Multi-domain large context | Subagents / Router |
