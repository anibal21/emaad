# Architecture Decision Framework

Use this document in **phase 03**. Select **one primary pattern** (EMAAD label) and record the matching **GCP pattern**. Secondary patterns require explicit justification.

Complementary sources:
- LangChain multi-agent framing (subagents, skills, handoffs, router)
- [Google Cloud: choose agentic design pattern](https://docs.cloud.google.com/architecture/choose-design-pattern-agentic-ai-system) — full tables in [`gcp-agentic-patterns.md`](./gcp-agentic-patterns.md)
- After pattern choice → [`primitive-selection.md`](./primitive-selection.md) for scripts / skills / agents

## Step 0 — Non-agentic gate

Ask: *Is this solvable without an agent (single model call / batch job / plain automation)?*

| Signal | Action |
|--------|--------|
| Summarize, translate, classify, one-shot generation | Prefer **non_agentic**; optional script/skill only |
| Needs tools, multi-step autonomy, dynamic plans | Continue |

## Step 1 — Single-agent baseline

Ask: *If we had infinite discipline, could one agent + tools + progressive skills succeed?*

| Signal | Prefer |
|--------|--------|
| Few domains, shared context OK, one team owns prompts | **Single-agent + Skills** (+ ReAct inside if dynamic) |
| No need for parallel isolated reasoning | Stay single-agent |
| No staged unlock of capabilities mid-conversation | Stay single-agent |

Only leave the baseline when a **binding constraint** appears in Step 2 **or** GCP workload tables demand multi-agent.

## Step 2 — Binding constraints checklist (EMAAD)

Mark each true/false:

1. **Context pressure**: Specialized knowledge packs are large enough that loading several into one thread causes harmful token bloat or recall failure.
2. **Distributed ownership**: Different teams must maintain capabilities independently with clear boundaries.
3. **Parallel isolation**: Work must run concurrently in separate context windows and merge.
4. **Sequential unlock**: Capabilities/tools must unlock only after conversational preconditions (stateful stages).
5. **Multi-source synthesize**: One query must fan out to distinct verticals/sources and merge answers.
6. **Central workflow control**: A supervisor must decide routing and combine results; specialists should not talk to the user.
7. **Direct specialist UX**: The same agent must stay in continuous direct dialogue with the user while specializing.

## Step 3 — GCP requirements (mandatory)

Capture answers from [`gcp-agentic-patterns.md`](./gcp-agentic-patterns.md) sections A–E:

- Task: predefined vs open-ended; model orchestration needed?  
- Latency vs quality  
- Multi-call cost budget  
- Human intervention needs  
- Single-agent already failing / expected to fail with many tools?

Classify workload family:

| Family | Examples of GCP picks |
|--------|----------------------|
| Deterministic | Sequential, Parallel, Iterative refinement |
| Dynamic orchestration | Single-agent, Coordinator, Hierarchical, Swarm |
| Iteration | ReAct, Loop, Review & critique, Iterative refinement |
| Special | HITL overlay, Custom logic |

## Step 4 — Pattern mapping (unified)

| If these are true… | EMAAD primary | Typical GCP |
|--------------------|---------------|-------------|
| Non-agentic gate hit | `non_agentic` | (none) |
| Mostly false on constraints 1–5; early PoC | `single_agent_skills` | Single-agent (+ ReAct) |
| Fixed A→B→C; no model orchestration | `sequential_pipeline` / `handoffs` | Sequential |
| Independent concurrent subtasks; code fan-out | `router` / `parallel_subagents` | Parallel |
| Dynamic route to specialists; central control | `subagents` | Coordinator |
| Nested ambiguous planning | `subagents` (+ hierarchy note) | Hierarchical decomposition |
| Generator then validator | `subagents` or sequential pair | Review & critique |
| Quality via cycles + exit condition | secondary `iterative_refinement` / `loop` | Loop / Iterative refinement |
| Peer debate, no supervisor | `swarm` (discourage; waiver) | Swarm |
| Soft multi-domain, direct UX | `skills` | Single-agent + progressive skills |
| Stateful stage unlock + user chat | `handoffs` | Sequential + HITL as needed |
| Branches beyond templates | `custom_logic` | Custom logic |

### Capability matrix (qualitative)

| Pattern | Distributed dev | Parallel | Multi-hop series | Direct user UX |
|---------|-----------------|----------|------------------|----------------|
| Subagents | Excellent | Excellent | Excellent | Weak (via supervisor) |
| Skills | Excellent | Limited | Excellent | Excellent |
| Handoffs | Weak | Weak | Excellent | Excellent |
| Router | Good | Excellent | Weak | Medium |

### Cost intuition

| Workload | Better patterns |
|----------|-----------------|
| One-shot single task | Skills / Handoffs / Router (fewer hops than Subagents) |
| Repeat requests in-thread | Skills / Handoffs |
| Multi-domain large packs | Subagents / Router |
| Rigid pipeline | Sequential (often cheaper than Coordinator) |
| Swarm / Hierarchical | Highest cost—demand proof |

## Step 5 — Forced tradeoff

> We choose **{emaad_pattern}** (GCP: **{gcp_pattern}**) because **{constraints + GCP A–E}**, accepting **{cost: extra hops | token accumulation | sequential rigidity | routing overhead | loop risk}**.

## Step 6 — Primitive handoff

Immediately apply [`primitive-selection.md`](./primitive-selection.md): draft the candidate **agents / skills / scripts** lists before leaving phase 03 (refine in 04–06).

## Step 7 — Anti-patterns

- Multi-agent because "agents are cool"
- Coordinator when sequential/parallel **code** workflow would do
- Swarm without exit conditions and cost waiver
- Router + Handoffs + Subagents all primary with no ownership map
- One agent with 40 overlapping skills and no bundles
- Specialists with production write tools and no HITL
- Shared MCP with admin scopes across all agents
- Creating agents for deterministic merges/checks (use scripts)

## Step 8 — Record

Session state fields: `gcp_requirements`, `gcp_pattern`, `primary_pattern`, `secondary_patterns`, `constraints_true`, `tradeoff_statement`, `rejected_patterns`, draft `primitives`.
