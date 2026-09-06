# Gates

Gates are boolean checkpoints. The designer agent enforces them.

## Design-time gates (EMAAD session)

| Gate ID | Blocks | Pass condition |
|---------|--------|----------------|
| G-PATTERN | Agent cards freeze | Primary pattern + tradeoff recorded |
| G-SRP | Synthesis | SRP checklist zero unresolved overlaps |
| G-TOKENS | Synthesis | Token budget worksheet filled; bundles defined if skill count high |
| G-MCP | Approved | Allowlist complete OR explicit no-MCP; MCP01–10 addressed |
| G-SKILLS | Approved | Each skill risk-tiered; review/eval plan present |
| G-HITL | Approved | All high-blast side effects classified |
| G-AUDIT | Approved | Logging expectation stated |
| G-HUMAN | Approved | Named human accepted the package |

## Runtime gates (to specify in blueprint)

Document how the target platform will enforce:

- Confirm-then-act approvals  
- Allowlist enforcement for MCP  
- Version pins for skills  
- Sandbox for code execution  

## Waiver format

```markdown
### Waiver
- Gate:
- Reason:
- Owner:
- Expiry:
- Compensating control:
```

Waivers are allowed for `Review` status. **Approved** with waivers requires owner + expiry + compensating control.
