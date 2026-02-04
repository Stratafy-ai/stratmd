# Changelog

All notable changes to StratMD will be documented in this file.

## [v0.1.0] - 2026-02-04

### Initial Public Release

**Specification**
- Full v0.1 spec with five document types: Foundation, Strategy, Initiative, Insight, Metrics
- Required YAML frontmatter schema
- Standardized table schemas for Goals, Risks, Actions, Assumptions, Decision Graveyard
- Wiki-style linking and hierarchy support
- Mermaid diagram support
- Agent parsing guidelines

**Templates**
- `foundation.strat.md` – Mission, vision, values, beliefs, principles
- `strategy.strat.md` – Full strategy with goals, risks, constraints, alignment
- `agent-strategy.strat.md` – Lightweight template for AI agents

**Examples**
- Stratafy foundation (real-world)
- Viridis community renewable energy strategy
- StratClaw agent strategy

**Agent Integrations**
- OpenClaw stratmd-loader skill v0.2
  - Cache schema for efficient loading
  - Conflict detection
  - Assumption re-evaluation with confidence decay
  - Exploration mode escape hatch

---

See full spec at [stratmd.org](https://stratmd.org) | Repo: [github.com/Stratafy-ai/stratmd](https://github.com/Stratafy-ai/stratmd)
