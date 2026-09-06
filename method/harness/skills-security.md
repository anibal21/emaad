# Skills Security

Aligned with [Anthropic Skills for enterprise](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/enterprise).

## Risk tier indicators

| Indicator | Concern |
|-----------|---------|
| Scripts in skill (`*.py`, `*.sh`, `*.js`, …) | High — full environment potential |
| Instruction manipulation ("ignore safety", "hide from user") | High — reject |
| MCP tool references | High — extends trust boundary |
| Network access patterns | High — exfil vector |
| Hardcoded credentials | High — reject |
| Broad filesystem / path traversal | Medium |
| Bash/file tool directives | Medium — review combined with network |

## Review checklist (mandatory before prod skill)

1. Read all skill directory content  
2. Verify scripts match stated purpose (sandbox run)  
3. Check for adversarial instructions  
4. Search for network/exfil patterns  
5. Verify no hardcoded credentials  
6. List tools/commands the skill tells the model to use  
7. Confirm external URL destinations  
8. Verify no data exfiltration patterns (including via model responses)

## Evaluation gates

Require 3–5 eval queries per skill covering: should-trigger, should-not-trigger, ambiguous edge.

Evaluate: triggering accuracy, isolation, coexistence, instruction following, output quality.

## Lifecycle

`Plan → Create+Review → Test (solo + coexistence) → Deploy (version pin) → Monitor → Iterate/Deprecate`

- Production: **pin versions**  
- Authors ≠ sole reviewers  
- Git as source of truth; sync deliberately across surfaces (API vs IDE skills often do not auto-sync)

## EMAAD blueprint fields

Each Skill Card must include: risk tier, review status, eval status, version policy, MCP dependencies.
