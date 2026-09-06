# Token Optimization

## Goals

Maximize **decision quality per token** and protect **skill recall accuracy** as catalogs grow.

## Strategies (apply in order)

### 1. Progressive disclosure

- At rest: agent sees skill **name + description** only.
- On trigger: load `SKILL.md` body.
- On demand: open nested reference files / workflows / schemas.

### 2. Extract determinism to scripts

Every time the model formats JSON, renames files by regex, or checks a checklist mechanically, prefer a script. Saves tokens and reduces drift.

### 3. Isolate large domains

If a domain pack is ~large (thousands of tokens of procedures/docs), prefer **subagents** or **router specialists** over loading multiple packs into one thread.

### 4. Role-based bundles

Do not load the enterprise-wide skill catalog into every session. Bundle by role: engineering, support, finance, etc.

### 5. Lean system prompts

Agent cards stay short. Details live in skills. Supervisor prompts describe **routing policy**, not every subdomain's how-to.

### 6. Session hygiene

- Summarize completed phase results into session state; avoid re-pasting full interviews into every later turn when exporting.
- For long-running agents: checkpoint state to files; don't rely on unbounded chat history.

### 7. Measure

Track roughly:

- Skills concurrently available  
- Estimated tokens of always-on instructions  
- Whether multi-domain queries blow the budget  

If recall drops, stop adding skills; consolidate or route.

## Budget worksheet (session state)

| Item | Budget guidance |
|------|-----------------|
| Agent system mandate | Aim < 1–2 screenfuls |
| Always-on skills metadata | Prefer < 15–20 active per request when platform-capped |
| Per-skill full body | Load only when selected |
| MCP tool descriptors | Pin needed tools; avoid mega-servers |

## Anti-patterns

- Monolithic "god prompt"  
- Loading all skills "just in case"  
- Duplicating the same policy text in every agent  
- Putting large datasets into prompts instead of retrieval/scripts
