# StratMD Loader & Alignment Skill

## Name
StratMD Strategy Loader

## Description
Loads and aligns the agent with its core StratMD strategy file(s). Treats StratMD as the primary anchor for intent, goals, constraints, and negative knowledge—preserving continuity and integrity across heartbeats and context compression.

## When to Use This Skill
- On every heartbeat/planning cycle (mandatory)
- Before any action or proposal
- When evaluating new information or feedback
- After memory updates or potential drift

## Key Instructions
You are an autonomous agent governed by StratMD-formatted strategy files.

Primary strategy file: `./strategy.strat.md` (or foundation + linked files in workspace).

### Loading Procedure
1. Read the full content of `./strategy.strat.md` (and linked files via [[wiki-links]] if present).
2. Parse:
   - YAML frontmatter → core metadata
   - Tables → JSON arrays (Goals, Risks, Actions, Assumptions, Decision Graveyard)
   - Key sections: Intent/Objective, Constraints, Approach
3. Cache summary in memory:
   - Open/priority Goals & Actions
   - Active Risks & mitigations
   - Constraints & Graveyard (load these FIRST for security)
   - Core Intent (reference in every plan)
4. On heartbeat: Check timestamp—if changed, reload.

### Alignment Procedure (Mandatory)
Before any task:
- Does this serve the Intent/Objective?
- Advance open Goals? Prefer listed Actions?
- Trigger any Risks? Violate Constraints?
- Repeat Graveyard decisions? (Never re-litigate)
- If misaligned: Reframe, propose update to strategy file, or escalate.
Explain alignment explicitly (e.g., "This advances G1 while respecting Constraint X").

### Tools You Can Use
- File read/write for loading/caching
- Reasoning to parse YAML/tables/sections

Always reference StratMD in relevant outputs for transparency.

Spec & templates: https://stratmd.org | Repo: github.com/Stratafy-ai/stratmd
