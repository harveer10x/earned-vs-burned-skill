# Metric Interpretation Guide — "So What" Layer

A number without direction and correlation is noise. Hemoglobin is 11 — so what? That number means nothing without knowing whether it is trending up or down, what the other markers show, and what the next action is.

For each metric below: what it means when high, what it means when low, which metrics to read alongside it, and what the next action is when something is off.

---

## Earn Rate %
**Formula:** Level 5 outcomes ÷ Total stories × 100  
**Target:** 70%+ per sprint

**▲ When HIGH**  
Team consistently converting work into verified business value. Healthy delivery culture. The outcome definition habit is working.

**▼ When LOW**  
Work completing delivery steps but outcomes not being verified. Classic activity-not-outcome trap. Often the gap is L4→L5, not L3→L4.

**⟷ Read alongside**  
Outcome Verification %. If Earn Rate is low but Deployment Rate is high — the gap is at the verification step, not the delivery step. The team is shipping; nobody is confirming it landed.

**→ Next action**  
Audit Level 4 stories first. Ask: Is there a named success metric? Is there a named owner of outcome verification? Is L5 verification a step in the team's workflow, or an afterthought?

---

## Earned / Hours Ratio
**Formula:** Total Earned Value ÷ Total Hours Burned  
**Target:** >0.10 per sprint

**▲ When HIGH**  
High value per unit of human effort. Team working on the right things with clear outcome definitions. Well-scoped stories, minimal rework.

**▼ When LOW**  
Effort burning without outcomes. Causes: rework from unclear requirements, wrong work being prioritised, outcomes undefined before start, or scope that keeps expanding.

**⟷ Read alongside**  
Story Points / Velocity. If velocity is high but E/H is low — the team is moving fast on the wrong things. High throughput is masking low value delivery.

**→ Next action**  
Review the top 10% of stories by hours burned with the lowest earn. Were outcomes defined at Level 5 before work started? If not, that's the upstream fix — not a people problem.

---

## Earned per AI Token
**Formula:** Total Earned Value ÷ Total AI Tokens Burned  
**Target:** Any positive value; track trend over sprints

**This is the primary AI efficiency metric.** It replaces token volume, token cost, and "AI lines written" entirely.

**▲ When HIGH**  
AI used precisely on well-scoped, outcome-defined tasks. Prompt engineering is mature. Teams are defining outcomes before engaging AI — not the reverse.

**▼ When LOW**  
AI used exploratorily or in looping prompt cycles generating output without earning value. Common pattern: AI activated before the problem is scoped, producing output that needs rework.

**⟷ Read alongside**  
Earned / Hours Ratio. If E/H is healthy but Earned per AI Token is low — humans are efficient but AI is undirected. The bottleneck is AI governance, not team performance.

**→ Next action**  
Audit the top 20% of token-burning stories. Were outcomes defined before AI was engaged? The rule: **define first, activate second.** If AI is being used to figure out what to build, that's exploratory cost — it should be budgeted separately, not counted against delivery efficiency.

---

## Outcome Verification %
**Formula:** Level 5 verified ÷ (Level 4 + Level 5) deployed × 100

**▲ When HIGH**  
Deployments reliably converting to confirmed business outcomes. Strong engineering-to-business feedback loops. The team has a named process for closing the L4→L5 gap.

**▼ When LOW**  
Deployments happening but outcomes not confirmed. Either: (a) no measurement step exists in the workflow, or (b) the success metrics were never defined, so nobody knows how to verify.

**⟷ Read alongside**  
Earn Rate %. Low Outcome Verification % suppresses Earn Rate even when the delivery team is performing well. The fix is upstream of the team — in how stories are defined and who owns verification.

**→ Next action**  
Two mandatory changes: (1) Define success metrics before work starts — write the Level 5 definition in the ticket. (2) Assign a named business owner for Level 5 verification. Without a human accountable for confirming the outcome, L4 becomes the de facto ceiling forever.

---

## Team Effectiveness (E/B per person)
**Formula:** Individual's Total Earned ÷ Individual's Hours Burned

**▲ When HIGH**  
Individual converting effort into verified outcomes consistently. Well-matched to their work type and working with clearly defined outcome criteria.

**▼ When LOW**  
Individual burning effort without outcomes. Before concluding anything about the person — check story quality.

**⟷ Read alongside**  
Story assignment patterns. A low-E/B person working on poorly-defined, poorly-scoped stories is facing an upstream problem, not a performance problem.

**→ Next action**  
Check story definition quality first. Then check skill-to-task fit. Only then consider individual performance. Most low E/B individuals are working on broken stories — fixing the story quality will fix the metric faster than any coaching conversation.

---

## Reading Multiple Metrics Together

| Pattern | What it likely means |
|---------|---------------------|
| Low Earn Rate + High Deployment Rate | L4→L5 gap. Verification step is missing. |
| High Earn Rate + Low E/H Ratio | Few stories, all verified — but each one took too long. Rework or scope issues. |
| High E/H + Low Earned per Token | Humans efficient, AI wasteful. Prompt engineering or AI scoping problem. |
| Low Earn Rate + Low E/H + Low Earned per Token | Systemic: outcomes not defined before work starts. Framework adoption is the fix, not individual changes. |
| High everything | Healthy team. Document what's working and scale it. |
