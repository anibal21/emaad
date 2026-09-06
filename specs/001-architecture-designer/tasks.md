# Tasks: 001-architecture-designer

**Goal**: Materialize the EMAAD method so an agent can run a full design session from the skill entry point.

## Phase A — Foundation

- [X] T001 Create `constitution.md` with binding articles
- [X] T002 Create root `README.md` and `.gitignore`
- [X] T003 Create `specs/001-architecture-designer/{spec,plan,research}.md`

## Phase B — Method spine

- [X] T004 Create `method/README.md` and `method/interview-protocol.md`
- [X] T005 Create `method/architecture-decision.md`
- [X] T006 Create `method/primitive-taxonomy.md`
- [X] T007 Create `method/srp-and-boundaries.md`
- [X] T008 Create `method/token-optimization.md`
- [X] T009 Create `method/human-in-the-loop.md`

## Phase C — Security harness

- [X] T010 Create `method/harness/overview.md`
- [X] T011 Create `method/harness/owasp-mcp.md`
- [X] T012 Create `method/harness/skills-security.md`
- [X] T013 Create `method/harness/owasp-agents.md`
- [X] T014 Create `method/harness/gates.md`

## Phase D — Interview phases

- [X] T015 Create `method/phases/00-intake.md` through `09-synthesis-deliverable.md`

## Phase E — Templates & checklists

- [X] T016 Create templates: blueprint, agent, skill, workflow, script, mcp-allowlist, session-state
- [X] T017 Create checklists: srp, security-review, token-budget, hitl

## Phase F — Executable designer

- [X] T018 Create `skills/emaad-designer/SKILL.md` + decision-matrix reference
- [X] T019 Create optional `agents/` definitions
- [X] T020 Create `examples/software-dev-team/` sample blueprint
- [X] T021 Create `CONTRIBUTING.md`
- [X] T022 Mark this tasks file complete and converge against spec acceptance criteria

## Converge notes

Spec FR-001–FR-021 covered by constitution, boot menu, projects index, GCP patterns, primitive selection, phases, harness, templates, skill, ema-trunk.  
SC-001–SC-005 validated by method completeness + example package inspectability.  
Status: **Converged** for P1 method scope including boot modes (2026-09-06).

### Follow-up (v1.1)

- [X] T023 Boot menu options 1/2/3
- [X] T024 `projects/` + `index.json`
- [X] T025 Trunk-based Option 3 (`ema-trunk.md`)
- [X] T026 Migrate paths from `sessions/` to `projects/`

### Follow-up (v1.2)

- [X] T027 GCP agentic patterns guide + mapping
- [X] T028 Primitive selection (scripts/skills/agents)
- [X] T029 Wire phases 02–06 + templates + FR-019–021

### Follow-up (v1.3)

- [X] T030 One-question-at-a-time + k/N (`questioning.md`)
- [X] T031 Gitignore user `projects/*/` and live `index.json`; ship `index.example.json`
