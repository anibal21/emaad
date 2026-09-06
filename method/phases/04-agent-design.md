# Phase 04 — Agent Design

## Purpose

Name agents with unique responsibilities, scopes, and interaction rules.

## Do

1. Start from the draft agent list in phase 03 / [`../primitive-selection.md`](../primitive-selection.md)—do not invent agents outside that rationale without updating session state.  
2. For single-agent + skills: define **one** lead agent card; specialists are skills unless isolation demands agents.  
3. For subagents / GCP coordinator or hierarchical: define supervisor (+ mid levels if needed) + specialists.  
4. For handoffs / sequential: define stage agents and transition conditions.  
5. For router / parallel: define router/synthesizer + vertical specialists.  
6. For review & critique: ensure Generator and Critic are separate SRP mandates (or critic partially replaced by scripts).  
7. Apply [`../srp-and-boundaries.md`](../srp-and-boundaries.md).  
8. Draft Agent Cards from `templates/agent-card.md`.  

## Ask per agent

- Mandate (one sentence)?  
- Speaks to user? Y/N  
- Tools / MCP needed?  
- May call which other agents?  
- Max autonomy / budgets?  

## Exit criteria

- All agents named with SRP mandates  
- Handoff/call graph has no unauthorized edges  
- Preliminary SRP overlap scan clean (formal checklist in synthesis)  

## Next

Phase 05 Skills & workflows
