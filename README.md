# EMAAD — Enterprise Multi-Agent Architecture Designer

**Spec-driven method** for designing production-grade multi-agent systems through a structured technical conversation.

EMAAD is not an app. It is an **executable specification**: constitution, interview protocol, decision frames, security harness, and delivery templates. You open this repo with your coding agent, say **Hola Ema**, and run a long-form design dialogue. The output is a complete architecture package—agents, skills, workflows, scripts, MCP boundaries, HITL gates, and ecosystem flow.

**Ema** is the name of the designer. EMAAD is the project/method behind her.

MIT licensed. Built for individuals and enterprises who need agent ecosystems that are secure, token-efficient, and maintainable.

---

## Why EMAAD exists

Teams jump to multi-agent setups too early, invent overlapping roles, bolt on MCPs without allowlists, and discover token bloat or security gaps in production. EMAAD encodes software-engineering discipline for agentic systems:

- Choose architecture with evidence, not fashion ([LangChain pattern guide](https://www.langchain.com/blog/choosing-the-right-multi-agent-architecture))
- Separate **Skills / Workflows / Agents / Scripts / MCP** cleanly ([Miessler hierarchy](https://danielmiessler.com/blog/when-to-use-skills-vs-commands-vs-agents))
- Govern Skills like production software ([Anthropic enterprise Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/enterprise))
- Harness MCP and agent risk with [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/) and related agentic controls
- Optimize for **SRP**, **token budgets**, and **human-in-the-loop** that only interrupts when it matters

---

## Quick start

1. Clone this repository into your workspace (or add it as a submodule / reference folder).
2. Open your AI coding agent (Cursor, Claude Code, Copilot, etc.) in this project.
3. Start with the canonical greeting:

```text
Hola Ema
```

Ema responds with the boot menu:

```text
1. Trabajar en un nuevo proyecto
2. Trabajar en un proyecto en curso
3. Trabajar en mejoras de Ema
```

| Option | What happens |
|--------|----------------|
| **1** | Creates `projects/<slug>/` and registers it in `projects/index.json`, then starts the design interview |
| **2** | Lists projects from `projects/index.json` and resumes the one you pick |
| **3** | Improves Ema herself on `main` (trunk-based SDD + Git versioning) |

English greetings (`Hi Ema` / `Hello Ema`) get the same menu in English.

4. For project modes: answer the interview; push back when a recommendation feels wrong.
5. Deliverables land under `projects/<your-slug>/`. The index stays the catalog for Option 2.

Optional: copy `skills/emaad-designer` into your personal or project skills folder so the agent auto-discovers Ema.

---

## What you get at the end of a session

| Artifact | Purpose |
|----------|---------|
| **Architecture Blueprint** | Pattern choice, rationale, tradeoffs, ecosystem diagram |
| **Agent Cards** | Name, single responsibility, tools, skills, HITL, isolation |
| **Skill Cards** | Domain packs, triggers, progressive disclosure layout |
| **Workflow Cards** | Task procedures inside skills |
| **Script Cards** | Deterministic workers (validate, format, check, transform) |
| **MCP Allowlist** | Trust boundaries, scopes, OWASP mitigations |
| **Harness & Gates** | Security checklist results + approval points |
| **Implementation Backlog** | Ordered next steps to materialize the design |

---

## Repository map (SDD layout)

```text
constitution.md          # Binding principles (read first)
specs/001-.../           # Product spec, plan, research, tasks (SDD)
method/                  # Executable conversation method
  boot-menu.md           # Hola Ema → options 1/2/3
  ema-trunk.md           # Option 3: trunk-based Ema improvements
  phases/                # Interview phases 00–09 (project modes)
  harness/               # Security harness (MCP, skills, agents)
projects/                # Client design packages + index.json
templates/               # Deliverable templates
checklists/              # SRP, security, tokens, HITL
skills/emaad-designer/   # Skill that drives Ema
agents/                  # Optional specialist roles
examples/                # Worked blueprints
```

---

## Method at a glance

```text
Hola Ema → Boot menu
  ├─ 1 Nuevo proyecto     → projects/<slug>/ + index → phases 00–09
  ├─ 2 Proyecto en curso  → index → load → resume phases
  └─ 3 Mejoras de Ema     → trunk-based SDD on main → commit
```

Each project phase asks only the questions that unlock the next decision. Security and HITL are gates before synthesis.

---

## Design principles (summary)

See [`constitution.md`](./constitution.md) for the full binding text.

1. Specs are the product; conversation executes the method  
2. Single agent first; multi-agent only under binding constraints  
3. One responsibility per agent / skill / workflow / script / MCP  
4. Scripts for determinism; LLMs for judgment  
5. Progressive disclosure and context isolation for tokens  
6. HITL for irreversible / high-blast-radius decisions only  
7. OWASP MCP + Skills enterprise vetting + least privilege + audit  

---

## Contributing

See [`CONTRIBUTING.md`](./CONTRIBUTING.md). Improvements to decision quality, security coverage, and examples are especially welcome.

## License

[MIT](./LICENSE) © 2026 Aníbal Rodríguez Carrasco
