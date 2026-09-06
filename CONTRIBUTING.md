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
- **Pushing Ema product changes straight to `main`** (use a PR unless explicitly overridden)

## Process (SDD + PR)

1. Read `constitution.md` — amendments need the Article X process  
2. Use **Option 3 (Hola Ema)** or an explicit PR for designer changes  
3. From latest `main`: create `specs/00N-short-slug/` and branch `00N-short-slug`  
4. Implement in `method/`, `templates/`, `checklists/`, `skills/emaad-designer`  
5. Push the branch and open **one Pull Request to `main`** (`gh pr create`; see `.github/PULL_REQUEST_TEMPLATE.md`). Spec status on the branch should already be **Converged** when the work is complete.  
6. Wait for maintainer **approve + merge**  
7. Pull `main`; delete the feature branch; only then start `00N+1` — **no second PR** for status stamps  

Details: [`method/ema-trunk.md`](./method/ema-trunk.md) · [`specs/README.md`](./specs/README.md)

Client design work belongs under `projects/` (boot Options 1–2; gitignored)—not as drive-by edits to the method.

## Style

- Short, imperative method docs  
- Tables over prose when classifying  
- Cite upstream sources with links (OWASP, LangChain, Anthropic, Spec Kit, Google Cloud)  
- Spanish or English prose is fine in discussions; prefer English for core method headings for portability  

## License

MIT — see `LICENSE`
