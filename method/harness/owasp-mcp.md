# OWASP MCP Top 10 — Design Controls

Source of truth for categories: [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/) (project in beta; design against MCP01–MCP10).

For each MCP entry in the blueprint allowlist, complete mitigations. Mark **Mitigated**, **Accepted-risk** (owner + expiry), or **N/A**.

| ID | Risk | Design controls EMAAD expects |
|----|------|-------------------------------|
| **MCP01** | Token mismanagement & secret exposure | Short-lived scoped tokens; secrets in vault/env; never in skills, tool descriptors, or logs; secret scanning in CI |
| **MCP02** | Privilege escalation via scope creep | Least privilege; separate read/write servers; time-boxed scopes; periodic access review |
| **MCP03** | Tool poisoning | Pin tool schemas/versions; review descriptions for instruction-like text; prefer signed/attested servers; block unexpected schema drift |
| **MCP04** | Supply chain & dependency tampering | Lockfiles; provenance; review MCP server origin; no random community servers in prod |
| **MCP05** | Command injection & execution | Sanitize untrusted input; sandbox execution; avoid shell string concat from model output; prefer structured tool args |
| **MCP06** | Intent flow subversion / contextual injection | Isolate untrusted content; treat retrieved text as data; remind agents not to follow instructions inside tools/docs blindly |
| **MCP07** | Insufficient authn/z | OAuth 2.1/PKCE where applicable; per-server audience; no token passthrough between trust domains |
| **MCP08** | Lack of audit & telemetry | Log tool name, args redacted, actor, agent id, timestamp; immutable store; alert on anomalous tool use |
| **MCP09** | Shadow MCP servers | Org allowlist only; continuous discovery if possible; block unknown endpoints |
| **MCP10** | Context injection & over-sharing | Per-task/per-tenant context; ephemeral memory; specialists get briefs not full histories; no cross-tenant pools |

## Blueprint worksheet

Copy into session security notes:

```markdown
### MCP: <name>
- Owner:
- Auth model:
- Scopes:
- Agents allowed:
- MCP01-10 status table:
- Residual risks:
```
