# The Earned vs Burned Framework — Full Reference

## The Core Principle

Value is only **EARNED** when a tangible, verifiable business outcome is achieved.  
Until that point, all effort — human hours, AI tokens, lines of code, story points — is only **BURNED**.

This is not a new idea. It is a first-principles return to what technology programs exist to do: deliver outcomes, not activity.

---

## Origin Story — The 2010 Proof Point

This framework is not theoretical. It was operationalised at industrial scale in 2010.

At Deloitte, working on the Sysco Foods GS1 SKU enrichment program, Harveer Singh designed an Earned vs Burned measurement model to manage a data factory processing over one million product SKUs.

The challenge: how do you measure the productivity of a hybrid team of people, automation scripts, web scrapers, and validation macros — when the work has five discrete quality levels and partial completion produces zero business value?

The answer was the Earned vs Burned model:
- A SKU only EARNED full value (1.0) when all five GS1 classification levels were completed to accuracy standard
- Partial completion burned effort but earned nothing
- Touching a record at Level 1 consumed resource but created no value the business could use

That model used scraping tools, JavaScript macros, test validation scripts, and human-in-the-loop review — a human-AI hybrid workflow that predated the term by a decade.

This framework is the modern generalisation of that model, applied to software delivery in the age of generative AI.

---

## The Outcome Hierarchy — Five Levels

| Level | Gate Name | Earned | Definition |
|-------|-----------|--------|------------|
| 0 | Not Started | 0.00 | Task exists in backlog. No work begun. Burn has not yet started. |
| 1 | In Progress | 0.00 | Work is active. Effort is accumulating. No value is earned until a gate is passed. |
| 2 | Dev Complete | 0.25 | Code written, unit tests pass. Significant effort burned — not yet proven outside development environment. |
| 3 | QA Passed | 0.60 | Tested, defects resolved, acceptance criteria met. Meaningful — but outcome not yet in users' hands. |
| 4 | Deployed to Prod | 0.85 | Running in production. Near-full earn — but business outcome not yet verified. |
| 5 | Outcome Verified | 1.00 | KPI moved. User accepted. Revenue impacted. Defect resolved in production. **THIS IS THE ONLY FULL EARN.** |

**Why partial credit at Levels 2–4?**  
Because some value has been created — a tested, deployed feature has more value than nothing. But the earn weights are deliberately conservative: 0.25, 0.60, 0.85. The message is clear: you are not done until Level 5.

---

## Why Traditional Measures Fail

| Current Measure | Why It Fails |
|----------------|-------------|
| AI Token Usage | Measures compute consumed. A model that hallucinates in 100 tokens produces less value than one that solves the problem correctly in 10,000. Token count says nothing about outcome. |
| Lines of Code | 500 lines that don't pass QA earns nothing. 50 lines that resolve a production defect earns everything. Activity is not outcome. |
| Story Points / Velocity | Measures throughput of tasks against arbitrary estimates. A team can close 40 points of work that never reaches production. Points do not verify business value. |
| Hours Burned | The oldest wrong measure. Time spent is not value created. An offshore team burning 200 hours on rework earns nothing. |
| Test Coverage % | Measures the presence of tests, not the quality of outcomes. 95% coverage with badly-written tests produces false confidence. |

---

## Why AI Makes This Urgent

**AI generates output, not outcomes.**  
A model produces a thousand lines of code in seconds. None of it earns value until it passes QA, deploys, and verifies a business outcome. Speed of generation creates an illusion of productivity.

**Token cost is invisible until it isn't.**  
Teams rarely see cumulative prompt-response loop costs. A poorly-scoped agentic workflow burns thousands of dollars of compute on work that earns nothing — because the outcome was never defined before tokens started flowing.

**Agentic AI compounds the risk at machine speed.**  
AI agents executing across systems generate enormous burn across dozens of tasks simultaneously. Without earned value gates, waste compounds at a rate no human team could match.

The Earned Value Framework does not slow AI delivery down. It defines what "done" means before the first token is consumed — and measures delivery efficiency as earned value per token burned, not tokens consumed in isolation.

---

## The Coaching Principle

This framework is not primarily a measurement system. It is a coaching instrument.

The question it trains teams to ask before starting any work is:

> **"What is the verifiable outcome that will confirm this work is done? And how will we know when we have earned it?"**

That question, asked consistently at the start of every story, sprint, and program — before AI agents are activated, before the first token is spent — is what transforms a technology delivery team into an outcome-delivery machine.

---

## Application to Outsourcing and Offshoring

The framework applies identically to external teams. Hours burned by an outsourced vendor still earn nothing until Level 5.

The practical implication: contracts and SLAs that define acceptance at Level 4 (Deployed) are accepting partial earn as final payment. The framework argues that **Level 5 — Outcome Verified — must be the contractual acceptance criterion** for any AI-native delivery engagement.

This is the transparency differentiator. As enterprises increase scrutiny of AI spend, vendors who can report Earn Rate, E/H Ratio, and Earned per AI Token — rather than hours delivered and tokens consumed — will win.
