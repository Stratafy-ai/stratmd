# StratMD

**A Markdown-native format for strategy documentation.**
Human-readable. AI-parseable. Git-native. Open. Portable.

StratMD turns strategy into structured, versioned data without sacrificing readability. Write in plain Markdown, collaborate via Git, and feed reliably to AI agents.

## Why StratMD?

- **Simple & Portable**: Just `.md` files – works in Obsidian, VS Code, Notion export, or any editor.
- **Human-First**: Clean narrative with optional structure.
- **AI-Ready**: Standardized frontmatter, sections, and tables for easy parsing.
- **Git-Native**: Full history, diffs, merges, and branching.
- **Open Spec**: v0.1 – evolvable with community input.

Perfect for founders, teams, and agent builders who want strategy as living data, not static slides.

Visit the full documentation at [stratmd.org](https://stratmd.org).

## Quick Example

```markdown
# Strategy: Project X

---
type: strategy
version: 0.1
schema: stratmd
status: draft
owner: Team Lead
created: 2026-02-04
---

## Strategic Intent
How do we win the market?

## Objective
Achieve 10k users by EOY.

## Goals

| ID | Goal              | Measure       | Current | Target | Deadline   |
|----|-------------------|---------------|---------|--------|------------|
| G1 | User growth       | MAU           | 1k      | 10k    | 2026-12-31 |
| G2 | Revenue           | ARR (ZAR)     | 0       | 5m     | 2026-12-31 |
```

## Get Started

1. Copy a template from `/templates`
2. Fill in your strategy
3. Commit to Git and share

For advanced features like multi-file linking, versioning, and agent integration, check out [Stratafy](https://stratafy.ai).

## Repository Contents

- [`SPEC.md`](SPEC.md) – Full v0.1 specification
- [`/examples`](examples/) – Real-world examples (Viridis renewables, StratClaw agent, etc.)
- [`/templates`](templates/) – Ready-to-use starters for each document type
- [`/agents`](agents/) – Agent integrations (OpenClaw skill, etc.)

## License

MIT License – free to use, modify, and share.

Created by the Stratafy team. Contributions welcome!
