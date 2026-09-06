# Contributing to EMAAD

Thank you for improving a method that others will run as law in design conversations.

## What to contribute

- Clearer interview questions (higher decision yield per turn)
- Better pattern decision edges / anti-patterns
- Stronger security harness coverage (MCP, Skills, agents)
- New realistic examples (support, research, ops, compliance)
- Translations of conversational guidance (keep template keys stable)
- Optional validators that check blueprint completeness

## What to avoid

- Locking the core method to one vendor runtime
- Examples with hardcoded secrets or "disable audit" advice
- Expanding scope into a full application without an accepted spec change
- Vague multi-agent recommendations without constraints
- Appending new requirements into a **frozen/converged** spec folder

## Process (SDD)

1. Read `constitution.md` — amendments need the Article X process  
2. Prefer **Option 3 (Hola Ema)** or explicit PRs for designer changes; trunk = `main` (`method/ema-trunk.md`)  
3. **Create `specs/00N-short-slug/`** for the change (see [`specs/README.md`](./specs/README.md)). Never extend frozen `001`.  
4. Implement in `method/`, `templates/`, `checklists/`, `skills/emaad-designer`  
5. Mark the spec Converged; update the specs index  
6. Add or update an example when behavior changes  
7. Commit to `main` (or short-lived PR) with a clear message; push when asked  

Client design work belongs under `projects/` (boot Options 1–2; gitignored)—not as drive-by edits to the method.

## Style

- Short, imperative method docs  
- Tables over prose when classifying  
- Cite upstream sources with links (OWASP, LangChain, Anthropic, Spec Kit, Google Cloud)  
- Spanish or English prose is fine in discussions; prefer English for core method headings for portability  

## License

MIT — see `LICENSE`
