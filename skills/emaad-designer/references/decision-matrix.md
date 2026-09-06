# Decision Matrix (quick reference)

## Boot → then design

After Hola Ema: (1) new project (2) continue (3) improve Ema.

## Requirements → Pattern (EMAAD + GCP)

| Your requirements | EMAAD | GCP (typical) |
|-------------------|-------|---------------|
| One-shot NLP / no tools / no multi-step autonomy | non_agentic | — |
| Multi-step + tools, PoC, one mandate | single_agent_skills | Single-agent (+ ReAct) |
| Fixed pipeline A→B→C, no model orchestration | handoffs / sequential_pipeline | Sequential |
| Independent concurrent subtasks | router / parallel_subagents | Parallel |
| Dynamic route to specialists, central control | subagents | Coordinator |
| Nested ambiguous planning | subagents (hierarchy) | Hierarchical decomposition |
| Generator + validator | subagents pair | Review & critique |
| Soft multi-domain, direct UX | skills | Single-agent + skills |
| Stateful stage unlock + user chat | handoffs | Sequential + HITL |
| Peer debate (rare) | swarm | Swarm |
| Precise mixed branches | custom_logic | Custom logic |

Full tables: `method/gcp-agentic-patterns.md` · `method/architecture-decision.md`  
Source: [Google Cloud agentic patterns](https://docs.cloud.google.com/architecture/choose-design-pattern-agentic-ai-system)

## Primitive → When (ask these)

| Primitive | When |
|-----------|------|
| Script | Same bytes in → same bytes out; exit checks; merges; linters |
| Skill (+ Workflow) | Domain container / progressive disclosure / procedures |
| Agent | Isolation, ownership boundary, parallel worker, supervisor/critic/stage |
| MCP | Live external system with auth boundary |

Prefer **Script → Skill → Agent**. Details: `method/primitive-selection.md`

## Performance intuition

| Scenario | Leaner patterns |
|----------|-----------------|
| One-shot task | Skills / Handoffs / Router |
| Repeat in-thread | Skills / Handoffs |
| Multi-domain large context | Subagents / Router |
| Rigid pipeline | Sequential (often cheaper than Coordinator) |
