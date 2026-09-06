# Google Cloud Agentic Patterns (EMAAD mapping)

Source (cite in blueprints): [Choose a design pattern for your agentic AI system](https://docs.cloud.google.com/architecture/choose-design-pattern-agentic-ai-system) (Cloud Architecture Center).

EMAAD keeps **LangChain-style orchestration names** as the primary vocabulary in blueprints, and records the **GCP pattern** as `gcp_pattern` for precision. Use both.

## When NOT to use agents

If the workload is predictable, highly structured, or solvable with a **single model call** (summarize, translate, classify feedback), prefer **non-agentic** generative/assistive AI. Record `primary_pattern: non_agentic` and stop multi-agent design—optionally still recommend a script or a thin skill.

## Requirement questions (ask in phase 02 / start of 03)

These come from GCP “Define your requirements” and feed pattern choice:

### A. Task characteristics

1. Can the work follow **predefined steps**, or is it **open-ended**?
2. Must an **AI model orchestrate** the workflow, or can **fixed code/workflow logic** drive order?

### B. Latency and performance

3. Prioritize **fast/interactive** responses (even if quality drops), or tolerate delay for **higher quality**?

### C. Cost

4. Budget for **multiple model calls** per user request? (yes / limited / no)

### D. Human intervention

5. Are there **high-stakes, safety-critical, or subjective** decisions that need a person mid-flow?

### E. Complexity signal

6. Would a single agent with many tools already show **tool misuse, latency, or incomplete tasks**? (brownfield / expected)

## GCP pattern catalog → EMAAD

| GCP pattern | When (workload) | EMAAD primary (typical) | Primitives bias |
|-------------|-----------------|-------------------------|-----------------|
| **Single-agent** | Multi-step + tools; early product; one mandate | Single-agent + Skills (+ ReAct loop inside) | 1 agent · skills · scripts · MCP |
| **Sequential multi-agent** | Rigid pipeline; output→input; no model orchestration | Handoffs **or** code-driven sequential stages | Stage agents **or** workflows+scripts; fixed order |
| **Parallel multi-agent** | Independent subtasks / multi-view; code fan-out | Router / parallel subagents | Specialist agents or skills; synthesizer; scripts to merge if deterministic |
| **Loop** | Poll/monitor until exit condition | Loop as secondary; HITL/autonomy caps | Scripts for exit checks; agents for body |
| **Review & critique** | Generator + validator against criteria | Subagents or sequential pair | `Generator` + `Critic` agents; scripts for unit/policy checks |
| **Iterative refinement** | Harden artifact over cycles; quality > latency | Loop + skills | One refine skill/agent; max-iter script/gate |
| **Coordinator** | Dynamic route to specialists; structured business process | **Subagents** (supervisor) | Coordinator agent + specialist agents + skills |
| **Hierarchical task decomposition** | Ambiguous open goals; plan→delegate nested | Subagents / Deep-Agents-style | Root planner + mid + workers; heavy skills |
| **Swarm** | Peer debate; creative consensus; highest cost | Swarm (rare; justify) | Many agents; strict exit; usually discourage for enterprise v1 |
| **ReAct** | Dynamic plan: think→act→observe | Reasoning style **inside** an agent | Not a replacement for multi-agent; pairs with tools/scripts |
| **Human-in-the-loop** | Approval/correction at checkpoints | Overlay on any pattern | Gates (EMAAD HITL); external review channel |
| **Custom logic** | Branching mix of patterns; precise control | Custom (document graph) | Code orchestrator + agents/skills/scripts as nodes |

## Deterministic vs dynamic (GCP compare tables)

### Deterministic workflows

| Signals | Prefer GCP |
|---------|------------|
| Fixed multi-step, no model orchestration, A→B→C | Sequential |
| Independent concurrent subtasks, no model orchestration | Parallel |
| Multi-cycle improve without model orchestration of the loop | Iterative refinement |

### Dynamic orchestration

| Signals | Prefer GCP |
|---------|------------|
| Multi-step + tools, fast PoC | Single-agent |
| Dynamic route to specialists | Coordinator |
| Nested ambiguous planning | Hierarchical decomposition |
| Peer collaborative refinement | Swarm (last resort) |

### Iteration-heavy

| Signals | Prefer GCP |
|---------|------------|
| Think/act/observe adaptation | ReAct |
| Poll until condition | Loop |
| Distinct validation step | Review & critique |
| Progressive quality cycles | Iterative refinement |

### Special requirements

| Signals | Prefer GCP |
|---------|------------|
| Human judgment / compliance | Human-in-the-loop |
| Mixed branches beyond templates | Custom logic |

## Mapping GCP ↔ LangChain labels (record both)

| If GCP pick is… | Also set EMAAD `primary_pattern` |
|-----------------|----------------------------------|
| Single-agent | `single_agent_skills` |
| Sequential | `handoffs` or `sequential_pipeline` |
| Parallel | `router` or `parallel_subagents` |
| Coordinator / Hierarchical | `subagents` |
| Swarm | `swarm` (waiver-level justification) |
| ReAct | usually secondary: `react_reasoning` on the active agent |
| HITL | secondary overlay: already in phase 08 |
| Custom logic | `custom_logic` + mermaid of branches |

## Anti-patterns (GCP + EMAAD)

- Jumping to Swarm or Hierarchical without proving single-agent failure modes  
- Using Coordinator when a **sequential/parallel code workflow** would suffice (cheaper, lower latency)  
- Infinite loops without max-iter / exit scripts  
- Treating ReAct as a substitute for SRP (one agent, fifty tools)  
- Skipping non-agentic option for one-shot NLP tasks  

## Blueprint fields to fill

- `gcp_pattern`  
- `gcp_requirements` (A–E answers)  
- `primary_pattern` (EMAAD)  
- `secondary_patterns` (e.g. react_reasoning, hitl_overlay, review_critique)  
- `tradeoff_statement`
