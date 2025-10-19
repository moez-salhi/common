Purpose:
Normalize any raw or messy idea into a structured SSOT-ready Markdown file (00_APP-IDEA_<slug>.md) that feeds Stage 2.

Prompt:
# 🧩 App Idea Reformatter Prompt (Stage 1)

**Objective:**  
Transform an unstructured idea into a clean, machine-readable SSOT draft (`00_APP-IDEA_<slug>.md`) following the standardized format.

---

## Step 1 — Input
Paste the raw idea or note below (any format, long or short).

---

## Step 2 — Process Rules

1. Extract key intent:
   - Problem / Pain Point  
   - Target Users / Personas  
   - Desired Outcome / Value Proposition  
   - Constraints or technologies mentioned  
   - Success criteria (if any)

2. Infer missing fields → mark as `PROVISIONAL`.

3. Generate a **draft SSOT file** in Markdown:
   - include version = `0.1.0`  
   - status = `draft`  
   - owner = user name (ask if missing)  
   - current_phase = `initialization`

4. Add a **clarification checklist** at the end for unknowns.

5. Detect any **benchmark leads** (libraries, APIs, frameworks, or competing apps) and list under `Benchmark Leads`.

---

## Step 3 — Output Format
Return only Markdown, no prose. Example:

```markdown
---
ssot_type: APP_IDEA
id: app-smarttask-mentor
version: 0.1.0
status: draft
owner: "moez salhi"
created_at: 2025-10-18
current_phase: initialization
tags: [AI, productivity, benchmark, TTV]
---

# 0. Executive Snapshot
Goal: Help teams automatically summarize and prioritize daily tasks.  
Users: team leads / project managers.  
Value Proposition: Reduce meetings by generating AI task updates.  
Success Metrics: usable MVP in ≤14 days | 80 % task coverage.

# 1. Initial Requirement
Problem Statement: manual task reporting wastes time.  
Scope: integrate with Slack + Asana first.  
Constraints: must run serverless and respect privacy rules.  
Assumptions (PROVISIONAL): uses OpenAI API.

# 2. Benchmark & Reuse First
| Candidate | Type | License | Maturity | Fit | Effort | Notes |
|------------|------|----------|-----------|------|---------|-------|
| Zapier | automation | commercial | high | 4 | M | limited custom logic |
| n8n | open-source | Apache 2.0 | medium | 5 | M | self-hostable |
Feature Gaps / Opportunities: missing AI summarization step.  
Decision: Integrate n8n + build custom summary module.

# 3. Next Actions
- Confirm target user segment (size/industry).  
- Decide deployment (web app / integration / plugin).  
- Validate data privacy needs.  
```

---

## Step 4 — Handoff
Once confirmed ✅, the file becomes  
`ssot/00_APP-IDEA_<slug>.md` → ready for Stage 2 Initialization Prompt.
