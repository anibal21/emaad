# Feature Specification: EMAAD Designer

**Feature Branch**: `001-architecture-designer`  
**Created**: 2026-09-06  
**Status**: Active  
**Input**: Enterprise Multi-Agent Architecture Designer — conversation-executed specification for designing agent ecosystems (software development or any domain) with security harness, SRP, token optimization, and optimal HITL.

---

## User Scenarios & Testing

### User Story 1 — Greenfield architecture design (Priority: P1)

A tech lead starting a new product wants a secure, maintainable agent ecosystem before writing agent prompts ad hoc.

**Why this priority**: Primary value proposition; defines the happy path.

**Independent Test**: Complete a full interview for a fictional greenfield project and produce a blueprint package that passes all checklists without referencing an existing codebase.

**Acceptance Scenarios**:

1. **Given** a user describes a new domain and goals, **When** the designer completes phases 00–09, **Then** a blueprint recommends a primary pattern (single-agent, skills, subagents, handoffs, or router) with documented constraints that justified it.
2. **Given** the recommended architecture, **When** the user reviews agent cards, **Then** each agent has a one-sentence SRP mandate and non-overlapping tool/skill scopes.
3. **Given** synthesis completes, **When** security checklist is applied, **Then** every MCP01–MCP10 item is marked Mitigated / Accepted-risk / N/A with rationale.

---

### User Story 2 — Brownfield / in-progress project (Priority: P1)

A team already has agents, skills, or MCP servers and needs a redesign or formalization.

**Why this priority**: Most enterprise users are not greenfield.

**Independent Test**: Start intake with "existing system," inventory current primitives, and produce a gap analysis plus target architecture.

**Acceptance Scenarios**:

1. **Given** the user lists current agents/skills/MCPs, **When** phase 01–02 complete, **Then** the session state records an inventory and explicit pain points (overlap, token bloat, missing HITL, insecure MCP).
2. **Given** inventory and constraints, **When** pattern selection runs, **Then** the designer proposes a migration path (keep / merge / split / retire) not only a clean-slate ideal.

---

### User Story 3 — Non-software domain (Priority: P2)

A operations, research, legal, or customer-support lead wants the same method outside coding agents.

**Why this priority**: Method must be domain-agnostic; software is the default example, not the only path.

**Independent Test**: Run a session for "customer support tiered escalation" or "research synthesis" and produce agents/skills/scripts without requiring a git repository.

**Acceptance Scenarios**:

1. **Given** a non-dev domain, **When** domain map completes, **Then** primitives are framed as roles, procedures, and deterministic checks appropriate to that domain.
2. **Given** synthesis, **When** reviewing scripts, **Then** deterministic work is still extracted (validators, formatters, policy checkers) even if not code-build related.

---

### User Story 4 — Security-first enterprise gate (Priority: P1)

A security architect will not approve agent rollout without OWASP MCP and Skills vetting embedded in the design.

**Why this priority**: Differentiator and constitutionally required.

**Independent Test**: Attempt to synthesize without completing harness phase; designer must block or mark blueprint non-compliant.

**Acceptance Scenarios**:

1. **Given** harness phase incomplete, **When** user asks for final blueprint, **Then** designer refuses final "Approved" status and lists open gates.
2. **Given** a proposed skill with scripts + network calls, **When** skills security checklist runs, **Then** risk tier is High and required controls are listed before approval.

---

### User Story 5 — Optimal HITL design (Priority: P2)

A platform owner wants fewer interrupts but no silent high-risk actions.

**Acceptance Scenarios**:

1. **Given** listed side effects (deploy, spend, delete, external message), **When** HITL phase completes, **Then** each is classified confirm-then-act vs act-then-audit with owner role.
2. **Given** low-risk reversible sandbox actions, **When** HITL is designed, **Then** they are not gated behind human approval by default.

---

### Edge Cases

- User insists on multi-agent without binding constraints → designer documents dissent, recommends single-agent+skills, offers multi-agent only as optional exploration branch.
- Conflicting requirements (max isolation AND min latency) → designer surfaces tradeoff table and forces explicit priority ranking.
- More than ~15–20 concurrent skills needed → designer requires role-based bundles or router segmentation.
- User cannot answer security questions → blueprint marked `Draft / Security Incomplete`; no production-ready claim.
- Domain spans multiple orgs/trust boundaries → force MCP segmentation and no shared context pools across tenants.

---

## Requirements

### Functional Requirements

- **FR-001**: Designer MUST follow `constitution.md` and refuse to skip security/HITL gates for "Approved" blueprints.
- **FR-002**: Designer MUST run the phased interview in `method/phases/`, adapting depth to greenfield vs brownfield.
- **FR-013**: The designer persona MUST be addressed as **Ema**; user-facing docs MUST present **Hola Ema** as the canonical session entry (accept `Hi Ema` / `Hello Ema`).
- **FR-003**: Designer MUST maintain a session-state artifact that accumulates answers and decisions.
- **FR-004**: Designer MUST select a primary orchestration pattern using `method/architecture-decision.md` and record rationale + tradeoffs.
- **FR-005**: Designer MUST produce agent, skill, workflow, and script cards using `templates/`.
- **FR-006**: Designer MUST apply SRP checks from `checklists/srp.md` and resolve overlaps before synthesis.
- **FR-007**: Designer MUST complete MCP/skills/agent security harness using `method/harness/` and `checklists/security-review.md`.
- **FR-008**: Designer MUST define HITL gates per `method/human-in-the-loop.md` and `checklists/hitl.md`.
- **FR-009**: Designer MUST produce an ecosystem flow diagram (mermaid or equivalent ASCII) showing agents ↔ skills ↔ scripts ↔ MCP ↔ humans.
- **FR-010**: Designer MUST prefer scripts for deterministic work and document why any borderline task remains LLM-driven.
- **FR-011**: Designer MUST support both software-development and non-software domains with the same method spine.
- **FR-012**: Designer SHOULD offer optional specialist sub-roles (architect, security reviewer, synthesizer) without requiring them for P1 completion.

### Non-Functional / Method Quality

- **NFR-001**: Questions MUST map to a decision; no questionnaire padding.
- **NFR-002**: Token guidance MUST prefer progressive disclosure and isolation where domains are large.
- **NFR-003**: Artifacts MUST be Markdown-portable across major coding agents.
- **NFR-004**: Examples MUST not demonstrate insecure defaults (hardcoded secrets, unscoped MCP, hidden actions).

### Key Entities

- **Session State**: Running record of answers, constraints, inventories, decisions.
- **Architecture Blueprint**: Top-level design package and status.
- **Agent / Skill / Workflow / Script Card**: Primitive definitions with SRP mandates.
- **MCP Allowlist Entry**: Trust boundary with scopes and mitigations.
- **Gate Record**: HITL or security approval checkpoint.

---

## Success Criteria

- **SC-001**: A new user can produce a complete draft blueprint in one focused session (typically 45–90 minutes of conversation) for a medium-complexity domain.
- **SC-002**: Independent reviewer can implement agents/skills/scripts from the package without asking "what is this agent for?"
- **SC-003**: 100% of Approved blueprints have security checklist completion and explicit HITL map.
- **SC-004**: Pattern recommendation is traceable to at least one binding constraint or an explicit "single-agent sufficient" conclusion.
- **SC-005**: SRP checklist finds zero unresolved overlapping mandates in Approved packages.

---

## Assumptions

- User has access to an AI agent capable of loading project skills/markdown.
- Target runtime may be Cursor, Claude Code, LangGraph, Deep Agents, or custom—EMAAD stays method-first.
- "Scripts" may be shell, Python, JS, or other; language is chosen at implementation time unless the user constrains it.
- OWASP MCP Top 10 is treated as required guidance while the project remains in beta; wording may track upstream updates.
