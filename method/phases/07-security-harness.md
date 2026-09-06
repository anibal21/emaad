# Phase 07 — Security Harness

## Purpose

Complete MVH and OWASP/Skills/Agent controls. Blocks Approved if incomplete.

## Do

1. Build MCP allowlist (or record none).  
2. Walk [`../harness/owasp-mcp.md`](../harness/owasp-mcp.md) per server.  
3. Risk-tier every skill; attach review/eval plan ([`../harness/skills-security.md`](../harness/skills-security.md)).  
4. Fill agent security sections ([`../harness/owasp-agents.md`](../harness/owasp-agents.md)).  
5. Define sandbox/egress/secret policies.  
6. Run through gate list in [`../harness/gates.md`](../harness/gates.md).  

## Ask

- Where do secrets live today?  
- Is there an MCP allowlist process already?  
- Who reviews skills for production?  
- What audit sink exists (SIEM, LangSmith, logs)?  

## Exit criteria

- Gates G-MCP, G-SKILLS, G-AUDIT pass or waivers filed  
- No hardcoded secrets in any draft artifact  

## Next

Phase 08 HITL
