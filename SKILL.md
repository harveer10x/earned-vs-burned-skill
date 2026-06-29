---
name: earned-vs-burned
description: Evaluate any project, sprint, or backlog using the Earned vs Burned Framework — an outcome-based measurement system that replaces token counts, story points, and velocity with one honest metric: value earned vs effort burned. Use this skill whenever someone wants to score tasks, evaluate a sprint, measure AI delivery ROI, audit a project for outcome verification, assess FTE or outsourcing team performance, or answer "are we actually delivering value or just burning effort?" Triggers on phrases like "score my sprint", "evaluate these tasks", "measure our AI ROI", "how much value did we earn", "replace velocity with something real", "outsourcing transparency", "what did we actually deliver", or any request to apply outcome-based measurement to work in progress or completed work. Works with Jira, Linear, Asana, GitHub Issues, Azure DevOps, or plain pasted/CSV task lists.
---

# Earned vs Burned Framework Skill

## What this skill does

This skill evaluates any set of tasks, stories, or deliverables against the **Earned vs Burned Outcome Hierarchy** — a 5-level gate system developed by Harveer Singh based on his developing a Factory Model for offshoring work in 2010 — and now the most honest way to measure AI-native delivery.

The core principle: **value is only EARNED when a verifiable business outcome is achieved.** Everything before that is BURNED effort — not waste necessarily, but not earned value either.

Read `references/framework.md` for the full hierarchy and origin story before scoring anything.

---

## Workflow

### Step 1 — Identify the input source

Determine where the tasks are coming from. Ask the user if unclear.

**Connected tools** (check what MCP connectors are available):
- **Linear** → use Linear MCP to fetch issues for a project/cycle
- **Asana** → use Asana MCP to fetch tasks from a project
- **GitHub** → use GitHub MCP to fetch issues/PRs
- **Jira / Azure DevOps** → ask user to paste or export a task list (or use available MCP if connected)

**No tool connected** → ask the user to paste their task list, upload a CSV, or describe the work. Accept any format — table, bullet list, rough notes.

Don't gate on format. If the user says "here are my tasks" in any form, work with it.

### Step 2 — Gather scoring data

For each task, you need four things to score it. Collect what you can from the tool/input; ask the user only for what's genuinely missing.

| Field | What to look for | If missing |
|-------|-----------------|------------|
| **Current status** | Done, In Review, In QA, Deployed, Merged, In Progress | Ask |
| **Outcome verified?** | Is there a KPI, user acceptance, or production confirmation? | Ask (yes/no) |
| **Hours burned** | Time logged, estimate, or hours field | Ask or skip (metric becomes N/A) |
| **AI tokens burned** | If tracked per task | Ask or skip (metric becomes N/A) |

Don't ask for all four upfront in one wall of questions. If status alone tells you the level, map it and move on. Only surface gaps that actually change the score.

### Step 3 — Map each task to the Outcome Hierarchy

Map each task to a level. When status is ambiguous, apply the *lower* of the two possible levels — conservative scoring is more credible.

| Level | Gate | Earned | Status signals |
|-------|------|--------|----------------|
| 0 | Not Started | 0.00 | Backlog, To Do, Open |
| 1 | In Progress | 0.00 | In Progress, Active, WIP |
| 2 | Dev Complete | 0.25 | Dev Done, Code Review, PR Open, Merged to Dev |
| 3 | QA Passed | 0.60 | QA Passed, Testing Done, Accepted, UAT Complete |
| 4 | Deployed to Prod | 0.85 | Released, Deployed, Live, Closed (without verification) |
| 5 | Outcome Verified | 1.00 | KPI confirmed, user accepted, revenue impact noted, bug resolved in prod with evidence |

**Critical rule:** A task can only reach Level 5 if there is a named, verifiable outcome. "Deployed" without outcome confirmation = Level 4. Ask the user: "Is there a business result you can point to — a metric moved, a user confirmed it works, a defect closed in production?" If yes → Level 5. If unsure → Level 4.

### Step 4 — Calculate the metrics

Once all tasks are scored, compute the portfolio metrics. Read `references/metrics.md` for interpretation guidance on each one.

```
Earn Rate %           = (Count of Level 5 tasks) ÷ (Total tasks) × 100
Earned / Hours        = (Sum of all Earned values) ÷ (Total hours burned)
Earned per AI Token   = (Sum of all Earned values) ÷ (Total tokens burned)
Outcome Verification% = (Count Level 5) ÷ (Count Level 4 + Level 5) × 100
Team Effectiveness    = Per-person: their Earned sum ÷ their hours burned
```

If hours or tokens are unavailable for some tasks, calculate the metrics only for the tasks where data exists and flag what's missing.

### Step 5 — Generate the Earned Value Report

Output a clean, scannable report. Always use this structure:

---

```
EARNED VALUE REPORT
[Project / Sprint / Team Name]
[Date]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PORTFOLIO SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Total Tasks:              [N]
Outcomes Fully Earned:    [N] (Level 5)
Earn Rate:                [X]%   [vs 70% target: ▲ above / ▼ below]
Total Earned Value:       [X.XX] of [N.00] possible

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
EFFICIENCY METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Earned / Hours:           [X.XX]   [vs >0.10 target]
Earned per AI Token:      [X.XXXX] [vs >0 benchmark]
Outcome Verification %:   [X]%     (L5 confirmed / L4+L5 deployed)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TASK BREAKDOWN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Table: Task ID | Description | Level | Earned | Hours | Status note]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
WHAT THIS MEANS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[2–4 sentences interpreting the pattern. What's healthy? What's the gap?
Which metric is the leading signal? What's the single most important next action?]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TOP 3 ACTIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. [Specific, actionable — not generic advice]
2. [Tied to a specific gap in the data]
3. [Forward-looking: what to define before the next sprint starts]
```

---

### Step 6 — The coaching close

End every report with the framework's core coaching question, applied specifically to what you found:

> "Before the next sprint starts: for every story you pick up, answer — **what is the verifiable outcome that will confirm this work is done?** Name the KPI, user, or production signal. That answer is your Level 5 definition. Write it in the ticket before the first token fires."

Adapt the wording to the team's context (AI-heavy, outsourced, internal FTE, etc.) but always land on this principle.

---

## Edge cases

**"We don't track hours or tokens"** — Score the hierarchy anyway. Earn Rate % and Outcome Verification % are the two metrics that need no additional data. Flag which efficiency metrics are unavailable and recommend adding tracking going forward.

**Mixed-level data** — Some tasks fully described, some vague. Score what you can confidently. Flag vague tasks as "Level uncertain — assumed Level 1" and note what information would resolve them.

**Outsourcing/offshoring context** — The framework applies identically. Hours burned by an external team still earn nothing until Level 5. The only adjustment: note that for vendor transparency, L4 (Deployed) should never be the final contractual gate — L5 (Outcome Verified) must be the acceptance criterion.

**AI-only tasks** (no human hours) — Earned per AI Token becomes the primary metric. Earn Rate still applies. Note that agentic workflows with no outcome gate are the highest-risk scenario — flag any task where AI was activated without a Level 5 definition written first.

---

## Reference files

- `references/framework.md` — Full Earned vs Burned framework, origin story, and hierarchy detail
- `references/metrics.md` — "So what" interpretation guide for each metric
- `references/integrations.md` — How to pull task data from Linear, Asana, GitHub, Jira, and ADO
- `assets/tracker_template.csv` — Blank tracker the user can fill in and re-upload
