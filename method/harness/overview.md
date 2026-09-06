# Security Harness Overview

The harness is the set of **technical and methodological controls** that keep agent behavior inside organizational intent. EMAAD requires harness design before **Approved** status.

## Layers

```text
┌─────────────────────────────────────────────┐
│ Methodological harness (this repo / process)│
│  - constitution, reviews, evals, version pin│
│  - separation of duties, approval gates     │
└─────────────────┬───────────────────────────┘
                  │
┌─────────────────▼───────────────────────────┐
│ Technical harness (runtime)                 │
│  - MCP allowlists, scopes, sandboxes        │
│  - tool pinning, secret stores, audit logs  │
│  - HITL gates, network egress controls      │
└─────────────────────────────────────────────┘
```

## Required coverage

| Area | Doc |
|------|-----|
| MCP protocol risks | [owasp-mcp.md](./owasp-mcp.md) |
| Skills packages | [skills-security.md](./skills-security.md) |
| Agent autonomy | [owasp-agents.md](./owasp-agents.md) |
| Gate machinery | [gates.md](./gates.md) |

## Minimum viable harness (MVH)

Every Approved blueprint MUST specify:

1. MCP allowlist (or explicit "no MCP")  
2. Secret handling rule (no secrets in prompts)  
3. Per-agent tool scope  
4. Audit/logging expectation  
5. Skill review + version pin policy  
6. HITL map for high-blast-radius actions  
7. Sandbox policy for code execution  

## Status rule

If any MVH item is missing → blueprint status cannot be `Approved` (use `Draft / Security Incomplete` or `Review` with open gates listed).
