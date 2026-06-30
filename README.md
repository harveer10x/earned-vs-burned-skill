# Earned vs Burned — Claude Skill

**An open source Claude skill for measuring what actually matters in AI-native delivery.**

By [Harveer Singh](https://www.linkedin.com/in/harveer/) | Author, *[When Data Moves](https://whendatamoves.com/)* | Founder, Rizz Wireless

---

## The Problem

Every team building with AI is measuring the wrong things.

Token usage. Lines of code. Story points. Velocity. Hours burned. These are **burned** metrics — they measure effort, not value. A model that hallucinates in 100 tokens is not better than one that solves the problem in 10,000. 500 lines of code that don't ship earn nothing. 40 story points closed on work that never reaches production delivers zero business value.

The only measure that matters: **did we earn it?**

---

## The Frameworkde

Value is only **EARNED** when a tangible, verifiable business outcome is achieved. Until that point, all effort is only **BURNED**.

This is the **Earned vs Burned Framework** — originally built at for a manufacturing and logistics data factory processing 1M+ SKUs (a human-AI hybrid workflow that predated the term). Now generalised for AI-native software delivery.

### The Outcome Hierarchy


| Level | Gate             | Earned   | What it means                                                        |
| ----- | ---------------- | -------- | -------------------------------------------------------------------- |
| 0     | Not Started      | 0.00     | Backlog. Zero burn, zero earn.                                       |
| 1     | In Progress      | 0.00     | Effort accumulating. Still zero earned.                              |
| 2     | Dev Complete     | 0.25     | Code written and unit-tested. Partial.                               |
| 3     | QA Passed        | 0.60     | Tested and accepted. Meaningful but not in prod.                     |
| 4     | Deployed to Prod | 0.85     | Running in production. Close — but not confirmed.                    |
| 5     | Outcome Verified | **1.00** | KPI moved. User confirmed. Revenue impacted. **The only full earn.** |


### The Key Metrics


| Metric                  | Formula                      | Target      |
| ----------------------- | ---------------------------- | ----------- |
| Earn Rate %             | L5 outcomes ÷ Total stories  | 70%+        |
| Earned / Hours          | Total Earned ÷ Total Hours   | >0.10       |
| **Earned per AI Token** | Total Earned ÷ Total Tokens  | Trending up |
| Outcome Verification %  | L5 verified ÷ L4+L5 deployed | Trending up |


**Earned per AI Token** is the metric the industry doesn't have yet. It replaces token volume entirely.

---

## What This Skill Does

Install this skill into Claude and it can:

- **Pull tasks from any project tool** — Linear, Asana, GitHub Issues, Jira, Azure DevOps, or a pasted/CSV list
- **Score each task** against the 5-level Outcome Hierarchy
- **Calculate all metrics** — Earn Rate, E/H Ratio, Earned per Token, Outcome Verification %, Team Effectiveness
- **Generate an Earned Value Report** — one page, three numbers, replaces your velocity report
- **Coach your team** — ends every report with the question that changes delivery culture: *what is the verifiable outcome that will confirm this work is done?*

Works for FTE teams, outsourced/offshored delivery, AI-agent workflows, or any mix.

---

## Installation

### Option 1 — Install the .skill file (Claude Desktop / Cowork)

1. Download `earned-vs-burned.skill` from the [Releases](../../releases) page
2. In Claude Desktop or Cowork: Settings → Capabilities → Install Skill
3. Drop the `.skill` file in

### Option 2 — Manual install (Claude Code)

```bash
# Clone the repo
git clone https://github.com/[your-org]/earned-vs-burned-skill

# Point Claude at the skill directory
# Add to your .claude/settings.json:
# "skillPaths": ["./earned-vs-burned"]
```

---

## Usage Examples

Once installed, just talk to Claude naturally:

> "Score my Linear sprint against the Earned vs Burned framework"

> "Here are my Jira tasks — how much value did we actually earn this sprint?"

> "We burned 400 hours and 2M tokens this month. What did we earn?"

> "I'm an outsourcing vendor — help me prove our value to the client using outcome metrics"

> "Pull our GitHub issues and give me an Earned Value Report"

---

## Repository Structure

```
earned-vs-burned/
├── SKILL.md                        # Core skill instructions for Claude
├── README.md                       # This file
├── references/
│   ├── framework.md                # Full framework, origin story, hierarchy detail
│   ├── metrics.md                  # "So what" interpretation guide for each metric
│   └── integrations.md             # How to pull from Linear, Asana, GitHub, Jira, ADO
└── assets/
    └── tracker_template.csv        # Blank tracker to fill in and upload
```

---

## Contributing

This is an open framework. Contributions welcome:

- **New integrations** — Monday.com, Shortcut, Notion, ClickUp
- **Example sprints** — Real anonymised data showing the framework in action
- **Translations** — The framework in other languages
- **Locale variants** — Adaptations for specific industries (healthcare, finance, gov)

Open a PR or issue. The framework is IP of Harveer Singh; the skill implementation is MIT licensed.

---

## License

**Framework IP:** © Harveer Singh. The Earned vs Burned Framework, Outcome Hierarchy, and associated concepts are original intellectual property of Harveer Singh

**Skill code:** MIT License. Use, fork, adapt, and build on the implementation freely. Attribution appreciated.

---

## About the Author

Harveer Singh is a former Fortune 500 Chief Data Officer (Truist Bank, Western Union), founder of [Rizz Wireless](https://rizzwireless.com), and author of *[When Data Moves](https://whendatamoves.com/)*.

[LinkedIn](https://www.linkedin.com/in/harveer/) | [Newsletter: When Data Moves](https://www.linkedin.com/newsletters/) | [Book](https://www.amazon.com/When-Data-Moves-Harveer-Singh/dp/B0GLFTWZCR)