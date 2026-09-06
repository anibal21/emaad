# Checklist — Security Review

| # | Check | Result | Notes |
|---|-------|--------|-------|
| 1 | No secrets in skills, prompts, cards, or examples | | |
| 2 | MCP allowlist exists or explicit no-MCP | | |
| 3 | MCP01–MCP10 addressed per server | | |
| 4 | Skill risk tiers assigned | | |
| 5 | High-risk skills have review + eval plan | | |
| 6 | Prod version pin policy stated | | |
| 7 | Per-agent tool allowlists defined | | |
| 8 | Code execution sandboxed when scripts/shell exist | | |
| 9 | Audit/telemetry expectation defined (MCP08) | | |
| 10 | Shadow MCP denied (MCP09) | | |
| 11 | Context isolation for sensitive/tenant data (MCP10) | | |
| 12 | Authors ≠ sole prod reviewers (SoD) noted | | |
| 13 | Waivers have owner + expiry + compensating control | | |
| 14 | Skills forbid hiding actions from users | | |

**Overall:** Pass / Fail / Pass with waivers
