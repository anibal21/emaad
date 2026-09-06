# SRP and Boundaries

## Agent SRP test

An agent passes if:

1. Mandate is **one sentence** without stacking unrelated verbs.
2. Success metric is singular (e.g., "correct migration PR" not "migrate and also write blog and also page on-call").
3. Tool allowlist contains only tools required for that mandate.
4. No other agent shares the same mandate wording or trigger space.

**Split heuristic**: If onboarding docs need a bullet list of unrelated jobs, split agents.

## Skill SRP test

1. Description triggers on a coherent domain, not "general helper".
2. Workflows inside all belong to that domain.
3. Coexistence: does not steal triggers from sibling skills (narrow descriptions).

**Consolidate heuristic**: Merge only when evals show the bundle matches individual skill quality (enterprise Skills guidance).

## Script SRP test

1. One input contract, one output contract.
2. No hidden network I/O unless declared and approved.
3. Fail closed on invalid input.

## MCP boundary test

1. One system / one auth audience where possible.
2. Read vs write split into separate servers or distinct tool groups with different agent grants.
3. No admin scope "for convenience".

## Context boundary test

1. Secrets never in skill bodies or transcripts destined for logs.
2. Tenant/user data not shared across agents without need-to-know.
3. Specialist subagents receive **task briefs**, not entire org memory dumps (MCP10).

## Overlap resolution order

1. Rename / narrow descriptions  
2. Move workflow into the correct skill  
3. Split agent  
4. Introduce router or supervisor explicitly  
5. Retire duplicate
