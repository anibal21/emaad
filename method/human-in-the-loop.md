# Human-in-the-Loop (HITL)

## Principle

Humans should decide **policy, ambiguity, and irreversible blast radius**. Agents should execute **clear, logged, reversible** work without nagging.

## Classification

For each side effect, assign one class:

| Class | Meaning | Examples |
|-------|---------|----------|
| **Confirm-then-act** | Human approval required before execution | Prod deploy, delete data, spend money, message customers, widen IAM, install new MCP/skill to prod |
| **Act-then-audit** | Agent may act; human reviews samples/alerts | Lint autofix in branch, draft PR description, summarize logs in sandbox |
| **Autonomous** | No human gate; still logged | Read-only search, run unit tests, format markdown |
| **Human-only** | Agent must not perform | Legal commitments, physical safety actions, signing as a person without authority |

## Gate record fields

- `gate_id`
- `action`
- `class`
- `approver_role`
- `evidence_required` (diff, plan, risk summary)
- `timeout_behavior` (block / escalate / expire safe)
- `sla`

## Batching for optimality

During design sessions and during runtime:

1. Prefer **one design review** of the full blueprint over per-card pings.
2. Prefer **grouped runtime approvals** (e.g., "approve migration plan") over approving each file write.
3. Use **risk-tiered policies** so low-risk actions don't inherit high-risk gates.

## Transparency rule

Agents MUST surface what they will do before confirm-then-act gates. Skills MUST NOT instruct models to hide actions from users (enterprise Skills security).

## Designing HITL in phase 08

1. List all external side effects from agent/MCP cards.  
2. Classify each.  
3. Assign approver roles.  
4. Remove gates that only exist from fear—replace with better scopes/sandbox.  
5. Ensure audit logs cover autonomous and act-then-audit paths (MCP08).
