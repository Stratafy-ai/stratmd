# StratMD Loader & Alignment Skill v0.2

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
3. Cache summary to `./memory/strategy_cache.json` (see Cache Format below).
4. On heartbeat: Check timestamp—if changed, reload from source.

### Cache Format
Write parsed summary to `./memory/strategy_cache.json`:
```json
{
  "version": "0.2",
  "loaded_at": "ISO-8601 timestamp",
  "source_hash": "md5 of strategy file",
  "intent": "...",
  "objectives": ["..."],
  "constraints": ["..."],
  "graveyard": [{"id": "D1", "rejected": "...", "reason": "..."}],
  "open_goals": [{"id": "G1", "goal": "...", "target": "...", "deadline": "..."}],
  "open_actions": [{"id": "A1", "action": "...", "status": "..."}],
  "risks": [{"id": "R1", "risk": "...", "mitigation": "..."}],
  "assumptions": [{"id": "A1", "assumption": "...", "confidence": "High", "last_reviewed": "YYYY-MM-DD"}]
}
```
Load cache first for efficiency; reload from source if stale or missing.

### Alignment Procedure (Mandatory)
Before any task:
- Does this serve the Intent/Objective?
- Advance open Goals? Prefer listed Actions?
- Trigger any Risks? Violate Constraints?
- Repeat Graveyard decisions? (Never re-litigate)
- If misaligned: Reframe, propose update to strategy file, or escalate.

Explain alignment explicitly (e.g., "This advances G1 while respecting Constraint X").

### Conflict Check
Scan for tensions before acting:
- Goal vs Goal (e.g., G1 speed vs G2 quality)
- Action vs Constraint/Risk
- New proposal vs Graveyard entry

If detected: Flag explicitly ("Potential conflict: Action advances G1 but risks violating C2") and propose resolution or strategy update before proceeding.

### Assumption Re-Evaluation
On heartbeat (weekly or every 30 cycles):
- Review Assumptions table for low-confidence or aged entries (>90 days since last validation).
- Prompt: "Re-assess [A1] confidence based on recent evidence. Propose update if changed."
- Update `last_reviewed` in cache after review.

### Exploration Mode
For deliberate testing outside normal constraints:

```
EXPLORATION: [action outside constraints]
Rationale: [why test this]
Risks: [potential downsides]
Recommend: Review before execution
```

Never execute exploration actions without explicit human override. Log all exploration proposals for review.

### Tools You Can Use
- File read/write for loading/caching
- Reasoning to parse YAML/tables/sections

Always reference StratMD in relevant outputs for transparency.

---

Spec & templates: https://stratmd.org | Repo: github.com/Stratafy-ai/stratmd
