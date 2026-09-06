# EMAAD Method

This folder is the **runtime** of EMAAD. An agent loads `skills/emaad-designer`, then executes these documents in order during a design conversation.

## How to run

1. Read [`../constitution.md`](../constitution.md)
2. Follow [`interview-protocol.md`](./interview-protocol.md)
3. Walk [`phases/`](./phases/) 00 → 09
4. Apply decision aids and harness docs when a phase references them
5. Fill [`../templates/`](../templates/) and verify with [`../checklists/`](../checklists/)

## Document index

| Doc | Purpose |
|-----|---------|
| [interview-protocol.md](./interview-protocol.md) | Global conversation rules |
| [architecture-decision.md](./architecture-decision.md) | Pattern selection tree |
| [primitive-taxonomy.md](./primitive-taxonomy.md) | Skills / Workflows / Agents / Scripts / MCP |
| [srp-and-boundaries.md](./srp-and-boundaries.md) | Single responsibility rules |
| [token-optimization.md](./token-optimization.md) | Context & cost strategy |
| [human-in-the-loop.md](./human-in-the-loop.md) | Approval design |
| [harness/](./harness/) | Security harness |
| [phases/](./phases/) | Phase-by-phase interview |

## Status meanings for blueprints

| Status | Meaning |
|--------|---------|
| `Draft` | Interview in progress |
| `Draft / Security Incomplete` | Synthesis attempted without harness |
| `Review` | Package complete; awaiting human acceptance |
| `Approved` | Human accepted; all gates passed or residual risks owned |
