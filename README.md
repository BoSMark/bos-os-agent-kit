# Agent OS Starter Kit

A toolkit for running AI agents on real work, without the chaos of ad hoc adoption, in the BoS OS.

**Three interview-driven agents, one pipeline: _shape_ the mission → _staff_ it → _deliver_ it.**

---

## The Problem

Most teams adopting AI agents hit the same wall: agents that act when they shouldn't, ask when they should act, and produce work state that lives in someone's head rather than in files. Sessions start with archaeology. Decisions get made by whoever's paying attention.

This kit gives you the coordination layer that prevents that.

---

## The three agents

### 1. Mission Shaper — *shape the mission*
`/agent-specs/mission-shaper.md` · template: `/mission-templates/mission-brief.md`

An interview agent that coaches a rough idea into a sharp, measurable **Mission Brief** — by making the person do the thinking, not by writing it for them (coach, not consultant).

**The process it runs:** orients you on what to expect → interrogates the idea (outcome vs. activity · commit vs. explore · time-bound vs. ongoing · what needs *guarding*, both risk and voice/messaging · the capabilities the work requires) → synthesises the brief in your own words for you to correct.

**Input:** a rough goal, in your own words → **Output:** `MISSION-BRIEF.md`

### 2. Agent Planner — *staff the mission*
`/agent-specs/agent-planner.md`

Takes the Mission Brief and **staffs the mission** — casts the agent team the way you'd hire one, then specs each role to a runnable standard. Competency roles, not task-bots, so the agents compound across missions.

**The process it runs:** casts the team (*"if you were hiring people to run this, who would you hire?"*) → specs each role one at a time (role · type · decision boundary · escalation triggers · evaluation · model tier) → plans the prioritised backlog.

**Input:** `MISSION-BRIEF.md` → **Output:** agent specs in `03_AGENTS/` + a prioritised `todo.md`

It is the **canonical successor to the Agent Spec Builder** (below): it both *casts* and *specs*.

### 3. Delivery Manager — *deliver the mission*
`/agent-specs/delivery-manager.md`

Drives each deliverable from high-level goal to a running, validated system — and runs the day-to-day backlog. It is a **challenger**: it keeps you at decision altitude and out of the weeds, redirecting premature detail and lifting a one-off symptom to the systemic cause that should be fixed once.

**The process it runs — two modes:**
- **Build mode** (per system): `decompose → discover → ▸RECOMMEND gate → specify (+ acceptance tests) → build → ▸QA gate → operate`. Only the two gates reach you; the agents do the legwork.
- **Operate mode** (per session): `stand-up → pull → block → complete → wrap-up`, with `blocked.md` as the human decision queue and decision-boundary audit.

**Input:** the agent team + `todo.md` → **Output:** built & validated systems · `blocked.md` (your decisions) · `done.md`

---

### Superseded — kept for reference
- **Mission Planner** (`/agent-specs/mission-planner.md`) — the original all-in-one. Its *shaping* role is now the Mission Shaper; its *casting/planning* role is now the Agent Planner.
- **Agent Spec Builder** (`/skills/agent-spec-builder/SKILL.md`) — the earlier per-agent spec builder, now absorbed into the Agent Planner.

### State file templates
`/mission-templates/`

| File | Purpose |
|------|---------|
| `mission-brief.md` | The Mission Shaper's deliverable — the shaped mission |
| `todo.md` | Prioritised backlog |
| `in-progress.md` | What's being worked now |
| `blocked.md` | Human decision queue |
| `done.md` | Completed work |

---

## How they fit together

```
Mission Shaper        →  MISSION-BRIEF.md
  shape the mission        (outcome · measure · shape · guarding · capabilities · gaps)
        ↓
Agent Planner         →  agent specs (03_AGENTS/) + todo.md
  staff the mission        (the team, each role specced)
        ↓
Delivery Manager      →  built & validated systems · blocked.md · done.md
  deliver the mission
     ├─ build mode:    decompose → discover → ▸RECOMMEND → specify(+tests) → build → ▸QA → operate
     └─ operate mode:  stand-up → pull → block → complete → wrap-up
        ↓
Retro Agent (at close)   →  reads done.md      [forthcoming]
```

Each agent is **bounded**: the Shaper shapes (it doesn't cast), the Planner casts and specs (it doesn't run), the Delivery Manager delivers and runs (it doesn't re-shape). Outputs flow into inputs; one artefact hands to the next.

---

## How to use

1. **Shape** — load `agent-specs/mission-shaper.md`, describe your idea in your own words → `MISSION-BRIEF.md`.
2. **Staff** — load `agent-specs/agent-planner.md`, point it at the brief → agent specs + `todo.md`.
3. **Deliver** — copy the state-file templates into your mission folder, load `agent-specs/delivery-manager.md` each session → it decomposes, runs the gates, and runs the backlog.

Each spec is plain markdown — load it in any Claude session, or install as a Cowork skill.

---

## Grounded in established practice

These agents aren't invented from scratch — each design choice reflects a long-standing discipline in requirements engineering, product discovery, and project management. The mapping:

| Design choice | Established practice | Source |
|---|---|---|
| Make the outcome explicit; "write the success announcement first" | Amazon **Working Backwards / PR-FAQ**; **outcome-vs-output** (OKRs) | widely documented |
| Commit-vs-explore as a deliberate, crossable point | **dual-track agile** — the *commitment point* | [Dual-track / continuous discovery](https://blog.logrocket.com/product-management/dual-track-agile-continuous-discovery/) |
| Coach, don't consult — build the person's judgment | **coaching vs. consulting** | widely documented |
| Cast agents by refining goals until each is one agent's responsibility | **Goal-Oriented RE / KAOS** (goals → sub-goals → assign to a single agent) | [KAOS](https://www.utdallas.edu/~chung/SYSM6309/KAOS-AORE.pdf) · [GORE overview](https://www.cs.utoronto.ca/~alexei/pub/Lapouchnian-Depth.pdf) |
| Decompose a deliverable into systems, by function | **functional decomposition** (structured analysis) | [Functional decomposition](https://www.datacamp.com/tutorial/functional-decomposition) · [Requirements decomposition](https://argondigital.com/blog/product-management/requirements-decomposition/) |
| 100% coverage, deliverable-oriented, nothing extra | **Work Breakdown Structure** — the *100% rule* | [WBS](https://en.wikipedia.org/wiki/Work_breakdown_structure) |
| Discover and validate the cheapest way before building | **continuous discovery** (Cagan, Torres) | [Dual-track / continuous discovery](https://blog.logrocket.com/product-management/dual-track-agile-continuous-discovery/) |
| Review gates as go/no-go investment decisions | **Stage-Gate** (Cooper) | [Stage-Gate](https://www.toolshero.com/innovation/stage-gate-process/) |
| Acceptance tests defined at spec time; *verify* vs *validate* | **V-model** | [V-model V&V](https://www.coleyconsulting.co.uk/v-model-verification-and-validation.htm) |
| Detail the current wave only; keep the rest at altitude | **progressive elaboration / rolling-wave** | [WBS](https://en.wikipedia.org/wiki/Work_breakdown_structure) |

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

Designed for use with Claude (Anthropic) in Cowork mode or via Claude Code. The agent specs are plain markdown — they work in any Claude session, and can be installed as Cowork skills or used as prompts.

---

## Origin

Built and tested at [Business of Software](https://businessofsoftware.org) — a small team running two annual conferences and a growing online community. These tools emerged from real use, not theory.

---

## Licence

MIT. Use it, adapt it, share it.
