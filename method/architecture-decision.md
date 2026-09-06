# Architecture Decision Framework

Use this document in **phase 03**. Select **one primary pattern**. Secondary patterns require explicit justification (e.g., "Skills inside each router specialist").

## Step 0 — Single-agent baseline

Ask: *If we had infinite discipline, could one agent + tools + progressive skills succeed?*

| Signal | Prefer |
|--------|--------|
| Few domains, shared context OK, one team owns prompts | **Single-agent + Skills** |
| No need for parallel isolated reasoning | Stay single-agent |
| No staged unlock of capabilities mid-conversation | Stay single-agent |

Only leave the baseline when a **binding constraint** appears in Step 1.

## Step 1 — Binding constraints checklist

Mark each true/false:

1. **Context pressure**: Specialized knowledge packs are large enough that loading several into one thread causes harmful token bloat or recall failure.
2. **Distributed ownership**: Different teams must maintain capabilities independently with clear boundaries.
3. **Parallel isolation**: Work must run concurrently in separate context windows and merge.
4. **Sequential unlock**: Capabilities/tools must unlock only after conversational preconditions (stateful stages).
5. **Multi-source synthesize**: One query must fan out to distinct verticals/sources and merge answers.
6. **Central workflow control**: A supervisor must decide routing and combine results; specialists should not talk to the user.
7. **Direct specialist UX**: The same agent must stay in continuous direct dialogue with the user while specializing.

## Step 2 — Pattern mapping

| If these are true… | Primary pattern |
|--------------------|-----------------|
| Mostly false on 1–5 | **Single-agent + Skills** |
| 1 or 2 or 6; specialists don't need user chat | **Subagents** |
| 2 and 7; soft boundaries; progressive disclosure enough | **Skills** (quasi-multi-agent) |
| 4 and 7 | **Handoffs** |
| 3 or 5; per-request fan-out | **Router** |
| 1 + 3 + 6 | **Subagents** (often with Deep Agents–style planning) |
| 5 + conversation memory needed | **Router wrapped as a tool** of a stateful conversational agent |

### Capability matrix (qualitative)

| Pattern | Distributed dev | Parallel | Multi-hop series | Direct user UX |
|---------|-----------------|----------|------------------|----------------|
| Subagents | Excellent | Excellent | Excellent | Weak (via supervisor) |
| Skills | Excellent | Limited | Excellent | Excellent |
| Handoffs | Weak | Weak | Excellent | Excellent |
| Router | Good | Excellent | Weak | Medium |

### Cost intuition (from public pattern analysis)

| Workload | Better patterns |
|----------|-----------------|
| One-shot single task | Skills / Handoffs / Router (fewer hops than Subagents) |
| Repeat requests in-thread | Skills / Handoffs (state saves calls) |
| Multi-domain large packs | Subagents / Router (isolation beats skills token accumulation) |

## Step 3 — Forced tradeoff

Write one sentence the human must accept:

> We choose **{pattern}** because **{binding constraints}**, accepting **{cost: extra hops | token accumulation | sequential limits | routing overhead}**.

## Step 4 — Anti-patterns

- Multi-agent because "agents are cool"
- Router + Handoffs + Subagents all primary with no ownership map
- One agent with 40 overlapping skills and no bundles
- Specialists with production write tools and no HITL
- Shared MCP with admin scopes across all agents

## Step 5 — Record

Fill session state fields: `primary_pattern`, `secondary_patterns`, `constraints_true`, `tradeoff_statement`, `rejected_patterns`.
