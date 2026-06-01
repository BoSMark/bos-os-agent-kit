# Agent OS Starter Kit

A toolkit for running AI agents on real work, without the chaos of ad hoc adoption, in the BoS OS.

Three components. They work together.

---

## The Problem

Most teams adopting AI agents hit the same wall: agents that act when they shouldn't, ask when they should act, and produce work state that lives in someone's head rather than in files. Sessions start with archaeology. Decisions get made by whoever's paying attention.

This kit gives you the coordination layer that prevents that.

---

## What's In Here

### 1. Mission Planner (agent spec)
`/agent-specs/mission-planner.md`

An interview-driven agent that turns a vague goal into a scoped mission: named agents, phased rollout, state files, success criteria. Run it before starting any significant piece of agent work.

**Input:** A goal ("launch a founder community programme")  
**Output:** A `MISSION.md` with phases, agents, and entry/exit criteria

---

### 2. Delivery Manager (agent spec)
`/agent-specs/delivery-manager.md`

Runs the task backlog loop every working session. Moves work from `todo → in-progress → blocked/done`. Its most important output is `blocked.md` — a clean, specific decision queue that tells the human exactly what needs their judgment, with options and a recommendation.

**Runs:** Every session on any active mission  
**Feeds from:** Mission Planner (`todo.md`)  
**Feeds to:** Retro agent at close (`done.md`)

---

### 3. Agent Spec Builder (skill)
`/skills/agent-spec-builder/SKILL.md`

An interview-driven skill that takes one named agent and produces a finished, runnable spec — role, type, decision boundary, escalation triggers, evaluation criteria. Installable as a Cowork skill or usable as a prompt in any Claude session.

---

### State File Templates
`/mission-templates/`

The four files the Delivery Manager reads and writes. Copy into any mission folder to get started.

| File | Purpose |
|------|---------|
| `todo.md` | Prioritised backlog |
| `in-progress.md` | What's being worked now |
| `blocked.md` | Human decision queue |
| `done.md` | Completed work |

---

## How They Fit Together

```
Mission Planner
  → produces MISSION.md + todo.md
      ↓
Delivery Manager (runs every session)
  → pulls from todo.md
  → surfaces blocked.md (your decision queue)
  → writes done.md
      ↓
Retro Agent (at mission close)
  → reads done.md
```

Agent Spec Builder sits upstream of all of this — use it to spec any agent before adding it to a mission.

---

## How to Use

**To spec a new agent:**
Load `skills/agent-spec-builder/SKILL.md` into your Claude session. Name the agent. Answer the interview.

**To plan a mission:**
Load `agent-specs/mission-planner.md` into your Claude session. Describe your goal. It will interview you to produce a `MISSION.md` and initial `todo.md`.

**To run a mission:**
Copy the four state file templates into your mission folder. Load `agent-specs/delivery-manager.md` at the start of each session. It runs the stand-up, pulls work, surfaces blocks.

---

## Governance Assumptions

These specs assume:
- **Silence is not approval.** Agents block and wait; they don't guess past decision boundaries.
- **Draft before tracked.** Agent work goes to a local/draft folder first; humans approve before it moves to tracked files.
- **One decision at a time.** Agents present one decision for approval before moving to the next.
- **Block entries are specific.** A good block names the decision, the options, and a recommendation. A vague block is rejected.

Adapt the governing document references in each spec to point to your own system's authority documents.

---

## Compatibility

Designed for use with Claude (Anthropic) in Cowork mode or via Claude Code. The agent specs are plain markdown — they work in any Claude session. The Agent Spec Builder is packaged as a `.skill` file for Cowork users and as a plain `SKILL.md` for everyone else.

---

## Origin

Built and tested at [Business of Software](https://businessofsoftware.org) — a small team running two annual conferences and a growing online community. These tools emerged from real use, not theory.

---

## Licence

MIT. Use it, adapt it, share it.
