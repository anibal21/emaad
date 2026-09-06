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

## Process (SDD)

1. Read `constitution.md` — amendments need the Article X process  
2. For method changes: update `specs/001-architecture-designer/` if requirements shift  
3. Keep `method/`, `templates/`, `checklists/`, and `skills/emaad-designer` consistent  
4. Add or update an example when behavior changes  
5. Open a PR with: problem, change, how an agent session behaves differently  

## Style

- Short, imperative method docs  
- Tables over prose when classifying  
- Cite upstream sources with links (OWASP, LangChain, Anthropic, Spec Kit)  
- Spanish or English prose is fine in discussions; prefer English for core method headings for portability  

## License

MIT — see `LICENSE`
