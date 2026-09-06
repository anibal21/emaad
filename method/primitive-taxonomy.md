# Primitive Taxonomy

Canonical definitions for EMAAD blueprints.

## Skill

**What**: Domain container. Progressive disclosure package (instructions, resources, optional scripts).

**Contains**: `SKILL.md` (triggers + routing), context files, `Workflows/`, optional `Tools/` or `scripts/`.

**Does**: Specializes one conversational agent (or one specialist) in a domain.

**Does not**: Replace orchestration pattern choice; does not own cross-domain routing policy for the whole system (unless it *is* the router skill).

## Workflow

**What**: Task procedure inside a skill ("how to do X").

**Does**: Step-by-step execution path for one operation (Create, Publish, Triage, …).

**Does not**: Cross-cut unrelated domains; does not become a second competing skill.

## Agent

**What**: Autonomy + context boundary with a single responsibility mandate.

**Does**: Plans, calls tools/skills/scripts, may hand off or supervise, may speak to users (if allowed).

**Does not**: Own every domain "just in case"; does not share unscoped credentials.

## Script

**What**: Deterministic program invoked by agents/skills.

**Does**: Validate, lint, format, transform, check policies, compute diffs—stable I/O, exit codes.

**Does not**: Open-ended reasoning; if it needs judgment, it's not a script (or wrap judgment outside).

## MCP server

**What**: External capability trust boundary exposing tools to agents.

**Does**: Authenticated, scoped access to one system or API family.

**Does not**: Become a dumping ground for unrelated tools; does not run unsanctioned (shadow MCP).

## Mapping to patterns

| Pattern | How primitives compose |
|---------|------------------------|
| Single-agent + Skills | 1 agent · N skills · workflows/scripts · few MCPs |
| Subagents | Supervisor agent · specialist agents as tools · each may load skills |
| Handoffs | Multiple agents (or prompt/tool profiles) · shared state · sequential |
| Router | Routing step · specialist agents/skills in parallel · synthesizer |

## Naming conventions

- Agents: `TitleCase` role noun — `ResearchLead`, `Migrator`, `SupportTriager`
- Skills: domain `TitleCase` or kebab per target platform — be consistent inside a blueprint
- Workflows: verb-led — `Create`, `Publish`, `AssessIncident`
- Scripts: verb-noun — `validate_blueprint.py`, `check_allowlist.sh`
- MCP: system-named — `mcp-github-readonly`, `mcp-pagerduty`

## Decision: Skill vs Agent vs Script

```text
Need parallel isolation or separate ownership boundary? → Agent
Need reusable domain knowledge/procedures in one conversation? → Skill (+ Workflows)
Need stable deterministic transform/check? → Script
Need live external system access? → MCP (minimal tools)
```
