# Integration Guide — Pulling Task Data from Project Tools

## How to map tool statuses to Outcome Levels

Each tool uses different status terminology. Use the mappings below to translate tool status → Outcome Level. When a status is ambiguous, apply the lower of the two possible levels.

---

## Linear

**MCP tool:** `mcp__linear__list_issues` or `mcp__linear__get_project_issues`

**Status → Level mapping:**

| Linear Status | Outcome Level |
|--------------|---------------|
| Backlog / No Status | 0 |
| Todo | 0 |
| In Progress | 1 |
| In Review (Code Review) | 2 |
| Done (without deployment note) | 3 |
| Done (with deployment confirmed) | 4 |
| Done (with outcome verified note) | 5 |

**What to look for:** Check the issue description and comments for mentions of deployment, production, KPIs, or user confirmation. Labels like "verified", "outcome-confirmed", or custom fields if the team has added them.

**Hours:** Linear doesn't natively track hours. Ask the user or skip E/H metric.

**Tokens:** Not tracked in Linear. Ask the user or skip Earned per Token metric.

---

## Asana

**MCP tool:** `mcp__asana__get_project_tasks` or `mcp__asana__search_tasks`

**Status → Level mapping:**

| Asana Status | Outcome Level |
|-------------|---------------|
| Not started | 0 |
| In progress | 1 |
| Waiting on review | 2 |
| On hold (in QA) | 3 |
| Complete (no verification) | 4 |
| Complete (with outcome field populated) | 5 |

**What to look for:** Custom fields named "Outcome Verified", "Business Impact", or similar. Also check task descriptions and comments for production deployment notes or KPI mentions.

**Hours:** Check the "Estimated time" or "Actual time" fields if the team uses them.

---

## GitHub Issues / Pull Requests

**MCP tool:** `mcp__github__list_issues`, `mcp__github__list_pull_requests`

**Status → Level mapping:**

| GitHub State | Outcome Level |
|-------------|---------------|
| Open (no activity) | 0 |
| Open (with commits) | 1 |
| PR Open / In Review | 2 |
| PR Merged to main | 3 (assume QA in CI/CD) |
| Closed (issue) without production note | 4 |
| Closed with production deployment confirmed | 4 |
| Closed with outcome/KPI confirmed in comments | 5 |

**What to look for:** Check issue/PR comments for deployment confirmations, monitoring links, or business outcome statements. Labels like "deployed", "verified", "closed-with-evidence" are strong signals.

**Note:** For repos with CI/CD pipelines, PR merge to main often implies Level 3 (QA passed via pipeline). Confirm with the user.

---

## Jira

Jira is highly customisable — status names vary by team. Use these general mappings, and confirm with the user for any custom statuses.

**Status → Level mapping:**

| Typical Jira Status | Outcome Level |
|--------------------|---------------|
| To Do / Backlog / Open | 0 |
| In Progress / In Development | 1 |
| Code Review / PR Raised | 2 |
| In Testing / QA / In Review | 2–3 (ask) |
| QA Done / Ready for Release | 3 |
| Released / Done (no verification) | 4 |
| Done (with verification comment/field) | 5 |

**What to look for:** Custom fields added by the team — "Outcome Verified (Y/N)", "Business Impact", "Production Confirmed". Also check comments on Done tickets.

**No MCP available:** Ask the user to export a CSV from Jira (Backlog → Export) and upload it. The CSV will include status, assignee, story points, and any custom fields.

---

## Azure DevOps

**No standard MCP connector.** Ask the user to export a work item query as CSV or paste the relevant work items.

**Status → Level mapping:**

| ADO State | Outcome Level |
|----------|---------------|
| New / Proposed | 0 |
| Active / In Progress | 1 |
| Resolved (dev complete) | 2 |
| Closed (QA passed) | 3 |
| Done / Released | 4 |
| Done with acceptance criteria verified | 5 |

---

## No Tool — Paste or CSV

Accept any format the user provides. Common patterns:

**Pasted task list:**
```
- User auth flow — Done (deployed last Tuesday)
- Payment gateway — In QA
- Dashboard redesign — In Progress
```
Map each to a level based on the description. Ask targeted questions only where the level is genuinely unclear.

**CSV upload:**  
Look for columns: Task/Story, Status, Assignee, Hours, Points, Done/Verified. Map status column to levels. If an "Outcome Verified" column exists with Y/N values, that directly determines Level 5 eligibility.

**Provide the blank template:**  
If the user has no existing data, offer `assets/tracker_template.csv` as a starting point. Tell them to fill it in and re-upload — even a partial fill (just Task + Status + Outcome Verified Y/N) is enough to run Earn Rate % and Outcome Verification %.

---

## Recommending tracking improvements

After scoring any project, if key data was missing (hours, tokens, outcome verification), close with a practical recommendation:

- **For hours:** "Add a time-tracking field to your tickets, or use your sprint tool's built-in time logging. Even rough estimates are enough to trend the E/H ratio over time."
- **For tokens:** "Most AI coding tools (Copilot, Cursor, Claude) expose usage data. Consider logging tokens per story in a custom ticket field or a shared sheet alongside the tracker."
- **For outcome verification:** "The most impactful change: add a mandatory 'Level 5 Definition' field to every new story before it enters a sprint. One sentence: what is the verifiable outcome? Who will confirm it?"
