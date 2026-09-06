# Agent Security Controls

Complements MCP and Skills controls. Focus: **autonomy, goals, and blast radius**.

## Core risks to design against

| Risk | Design response |
|------|-----------------|
| Excessive agency | Narrow tool allowlists; split read/write; HITL on irreversible acts |
| Goal hijack / intent subversion | Fixed mandate text; treat tool/browser content as untrusted; supervisor re-checks goals on long runs |
| Unbounded loops / spend | Max iterations, timeouts, budget caps |
| Confused deputy | Per-agent identities; no credential sharing across agents |
| Latent multi-agent collusion paths | Explicit allowed handoff graph; deny arbitrary agent-to-agent tool invent |
| Insecure output handling | Never pipe raw model output to shell without validation/scripts |
| Over-broad memory | Scoped memory stores; retention limits |

## Agent card security section (required)

- Tool allowlist  
- Data scopes (repos, tenants, folders)  
- Network egress policy  
- Max autonomy (iterations/budget)  
- Handoff allowlist (which agents it may call)  
- HITL references  

## Supervisor-specific rules

- Supervisors should not silently inherit all specialist write tools  
- Prefer specialists returning **results**, not raw credentials  
- Parallel fan-out must still respect per-specialist scopes  

## Denial defaults

If unspecified:

- No production writes  
- No secret exfiltration paths  
- No installing new MCP/skills  
- No cross-tenant data access
