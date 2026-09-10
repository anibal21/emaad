# Phase 07 — Security Harness

## Purpose

Complete MVH and OWASP/Skills/Agent controls. Blocks Approved if incomplete.

## Do

1. Build MCP / live-systems list from session `primitives.mcp` + domain-map systems (or record **none**).  
2. Walk [`../harness/owasp-mcp.md`](../harness/owasp-mcp.md) **per server** (item-wise).  
3. Risk-tier every skill (usually already set in phase 05); attach review/eval plan for High (and Medium if user wants) via [`../harness/skills-security.md`](../harness/skills-security.md)—**item-wise per skill**.  
4. Fill agent security sections ([`../harness/owasp-agents.md`](../harness/owasp-agents.md)) when needed—prefer per-agent only for gaps.  
5. Define sandbox/egress/secret policies **per system**.  
6. Run gate list in [`../harness/gates.md`](../harness/gates.md).  

## Ask — item-wise (mandatory)

**Do not** ask a single general question for “all secrets”, “all MCPs”, or “all skills”. Follow [`../questioning.md`](../questioning.md) (self-explanatory + one question per turn).

### Set A — Secrets per system

`M` = count of external systems/MCP names from the session list.

```text
Fase 07 · Secretos · ítem 1/M — Trello
Phase 07 · Secrets · item 1/M — Trello
```

For each system, ask where **that** system’s credentials live (vault / env / not defined yet / other). Gloss **secreto** briefly on first item.

### Set B — MCP allowlist per server

For each MCP server, one field per turn (propose defaults):

| Step | Field | Gloss |
|------|-------|-------|
| 1 | `owner` | Quién es dueño operativo de este MCP |
| 2 | `auth_model` | Cómo se autentica (OAuth, API key, etc.) |
| 3 | `scopes` | Qué puede leer/escribir (mínimo privilegio) |
| 4 | `agents_allowed` | Qué agentes pueden usarlo |
| 5 | `residual_risk` | Riesgo residual aceptado o N/A |

Progress: `Fase 07 · MCP · <server> · campo k/5`.

If there are **zero** MCP servers, ask once: confirm none, then skip Set B.

### Set C — Skill review per High-tier skill

`M` = skills with `risk_tier: High` (include Medium only if human asks).

```text
Fase 07 · Revisión de skill · ítem 1/M — intake-evaluation-request
```

Ask who reviews/evals that skill before production use.

### Set D — Audit sink

If the org has **one** audit sink, one question is enough (gloss: dónde quedan logs de lo que hicieron los agentes/herramientas).  
If multiple sinks are in play, ask **per sink**.

## Anti-patterns (phase 07)

- “¿Dónde viven los secretos?” covering every system at once  
- “¿Hay proceso de allowlist MCP?” without walking each server  
- “¿Quién revisa skills?” without naming which High-tier skills  
- Bundling Sets A–D in one message  

## Exit criteria

- Gates G-MCP, G-SKILLS, G-AUDIT pass or waivers filed  
- Every listed system has a secrets answer  
- Every MCP has owner/auth/scopes/agents (or none confirmed)  
- Every High-tier skill has a reviewer (or explicit deferral)  
- No hardcoded secrets in any draft artifact  

## Next

Phase 08 HITL
