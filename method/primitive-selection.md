# Primitive Selection — Scripts, Skills, Agents

Use **after** pattern choice (phase 03) and throughout phases 04–06. Goal: Ema does not invent primitives ad hoc—each script, skill, and agent is justified by the use case and the chosen pattern.

Upstream: [`architecture-decision.md`](./architecture-decision.md), [`gcp-agentic-patterns.md`](./gcp-agentic-patterns.md), [`primitive-taxonomy.md`](./primitive-taxonomy.md).

## Golden rule

```text
Deterministic same-bytes-in → same-bytes-out?     → SCRIPT
Reusable domain know-how / procedures in-thread? → SKILL (+ Workflows)
Autonomy + context / ownership / parallel boundary? → AGENT
Live external system with auth?                  → MCP (not a substitute for the three above)
```

Prefer **Script → Skill → Agent** (cheapest capable primitive first). Never create an agent where a skill or script suffices.

## Step 1 — Decompose the use case into capability units

From the domain map, list units as rows:

| unit_id | description | judgment? | repeatable procedure? | deterministic check/transform? | needs isolation/parallel/ownership? | external system? |
|---------|-------------|-----------|----------------------|--------------------------------|-------------------------------------|------------------|

Ask the human (batch, 2–5 at a time) only for rows that are ambiguous.

## Step 2 — Classify each unit

| If… | Then create | Notes |
|-----|-------------|-------|
| Deterministic transform, validate, lint, score, merge JSON, regex rename, checklist compute | **Script** | Exit codes; sandbox if exec |
| Open procedure with domain rules, voice, playbooks, progressive docs | **Skill** + **Workflow(s)** | One domain per skill |
| Separate context window, different owner team, parallel worker, stage persona, supervisor/critic role required by pattern | **Agent** | One-sentence SRP |
| API/repo/ticket access | **MCP** allowlist entry | Attach to the agent/skill that needs it |

### Pattern-driven defaults

| Pattern (EMAAD / GCP) | Typical agents | Typical skills | Typical scripts |
|------------------------|----------------|----------------|-----------------|
| Single-agent + Skills / GCP single | 1 solo agent | One skill per domain | Validators, formatters |
| Subagents / Coordinator / Hierarchical | Supervisor + specialists (+ mid-level planners if hierarchical) | Skills **inside** specialists | Risk class, schema checks, exit conditions |
| Handoffs / Sequential | One agent per stage **or** one agent with stage profiles | Stage skills | Handoff payload validators |
| Router / Parallel | Router/synthesizer + vertical specialists | Per-vertical skills | Merge/normalize results if deterministic |
| Review & critique | Generator + Critic | Generation skill; critique criteria skill | Unit tests, policy scanners as scripts |
| Iterative refinement / Loop | Refiner (and optional critic) | Refine workflow | **max_iter / quality threshold** scripts |
| ReAct (secondary) | (no extra agent) | Tool-use guidance in skill | Observation parsers if structured |
| HITL overlay | (no extra agent unless review UI agent) | — | Evidence packagers |
| Swarm | Only with explicit waiver | Narrow expert skills | Consensus/timeout scripts |
| Custom logic | As graph nodes demand | Per node domain | Branch predicates in code/scripts |
| Non-agentic | none | optional thin prompt pack | optional batch scripts |

## Step 3 — Questions Ema MUST ask before freezing the list

1. Which units are **100% deterministic** if we specify I/O contracts? → scripts  
2. Which domains need **progressive disclosure** (large docs/playbooks)? → skills  
3. Where do we need **isolated context** or **parallelism** the pattern requires? → agents  
4. Who **owns** each skill/agent in the org? (distributed development)  
5. What would **break** if we merged two agents into one skill? (if nothing → merge)  
6. For critics/validators: can a **script** replace the critic agent for part of the criteria?

## Step 4 — Naming & SRP pass

- Run [`srp-and-boundaries.md`](./srp-and-boundaries.md)  
- Ensure no skill description steals another’s triggers  
- Supervisor must not hold all write tools “for convenience”

## Step 5 — Record in session state

```yaml
primitives:
  agents: [ ... ]
  skills: [ ... ]
  workflows: [ ... ]
  scripts: [ ... ]
  mcp: [ ... ]
selection_rationale: |
  short paragraph linking gcp_pattern + primary_pattern → primitive list
```

## Worked micro-example

**Use case:** Customer feedback analysis (sentiment + keywords + category + urgency), then optional manager approval before CRM write.

| Unit | Primitive |
|------|-----------|
| Sentiment / keywords / category / urgency (parallel LLM views) | 4 specialist **agents** or 4 **skills** under parallel pattern |
| Fan-out + merge orchestration | **Router** or parallel workflow agent (GCP parallel) |
| Normalize four JSON blobs into one schema | **Script** `merge_feedback_analysis` |
| CRM write | **MCP** write + **HITL** confirm-then-act |
| Critique before CRM | **Critic** agent **or** script policy checks + human |

Do **not** invent a fifth “FeedbackGod” agent that does all of the above.
