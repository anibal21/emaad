# Research: EMAAD Designer

**Date**: 2026-09-06  
**Feature**: 001-architecture-designer

## 1. Multi-agent pattern selection

**Decision**: Adopt LangChain's four-pattern frame (Subagents, Skills, Handoffs, Router) plus an explicit **Single-agent + tools** baseline.

**Rationale**: Matches industry teaching; includes performance tradeoffs (extra hop for subagents; context accumulation for skills; sequential limits for handoffs; stateless cost for routers). Source: [Choosing the Right Multi-Agent Architecture](https://www.langchain.com/blog/choosing-the-right-multi-agent-architecture).

**Alternatives considered**: Only supervisor/worker (too narrow); only graph frameworks (premature stack lock-in).

## 2. Skills vs Workflows vs Agents

**Decision**: Use Miessler's hierarchy as the organizational taxonomy inside Skills-based systems: Skill = domain container, Workflow = task procedure, Agent = parallel/isolated worker.

**Rationale**: Resolves the "everything is markdown" confusion; maps cleanly to Cursor/Claude skills layouts. Source: [When to Use Skills vs Workflows vs Agents](https://danielmiessler.com/blog/when-to-use-skills-vs-commands-vs-agents).

**Alternatives considered**: Flat prompt libraries (poor discoverability); agents-only (expensive and overlapping).

## 3. Enterprise Skills governance

**Decision**: Embed Anthropic enterprise lifecycle: risk tiering, review checklist, evals (trigger/isolation/coexistence/instruction/output), version pin in prod, role-based bundles, recall limits.

**Rationale**: Treats skills as production software. Source: [Skills for enterprise](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/enterprise).

## 4. Security harness

**Decision**: Require OWASP MCP Top 10 coverage for any MCP-connected design; combine with Skills vetting and agentic excessive-agency controls.

**Rationale**: MCP introduces discovery-time trust boundaries distinct from classic LLM app risks. Source: [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/).

**Note**: Project is in beta (v0.1); EMAAD cites categories MCP01–MCP10 as stable enough to design against, with Accepted-risk allowed when residual risk is owned.

## 5. Spec-Driven Development shape

**Decision**: Follow Spec Kit philosophy (constitution → specify → plan → tasks → implement/converge) but **implement** as method artifacts, not application code.

**Rationale**: User requirement: product is specification + conversation. Sources: [GitHub Spec Kit](https://github.com/github/spec-kit), [Microsoft SDD overview](https://developer.microsoft.com/blog/spec-driven-development-ai-native-engineering/).

## 6. HITL optimality

**Decision**: Classify side effects into confirm-then-act vs act-then-audit; batch design approvals; never hide actions.

**Rationale**: Reduces fatigue while preserving control on irreversible operations; aligns with constitution Article VI.

## 7. Token strategy

**Decision**: Progressive disclosure + context isolation for large domains; role-based skill bundles; scripts to shrink reasoning load.

**Rationale**: LangChain performance notes show skills accumulate tokens; subagents/router isolate large packs at cost of extra calls.

## 8. Primitive selection (GCP + scripts/skills/agents)

**Decision**: Integrate [Google Cloud agentic design patterns](https://docs.cloud.google.com/architecture/choose-design-pattern-agentic-ai-system) as first-class interview questions and pattern catalog, mapped to EMAAD labels; add `primitive-selection.md` so Ema systematically chooses scripts, skills, and agents (Script → Skill → Agent).

**Rationale**: User request to complement EMA with use-case questions from GCP architecture guidance; closes the gap between pattern choice and concrete primitives.

**Alternatives considered**: Replacing LangChain vocabulary entirely (rejected—keep dual labels); linking GCP doc only in README without method integration (rejected—agents would not ask the questions).

## Open questions for future iterations

- Optional machine-checkable validators for blueprint completeness  
- Adapters exporting to LangGraph / Deep Agents / ADK scaffolds  
- Multilingual interview packs (method authored in Spanish/English dual where helpful)
