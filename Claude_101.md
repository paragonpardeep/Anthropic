# Claude 101 - Key Points You Should Know

## 1. Claude is a Thinking Partner, Not a Search Engine

* Use Claude to brainstorm, analyze, summarize, draft, and solve problems.
* Treat it as a collaborator rather than a tool that simply provides answers.

### Example

**Good:**

> Help me create an RCA template for Sev-1 incidents.

**Better:**

> Act as an SRE Manager and create an RCA template for Sev-1 incidents, including timeline, impact, root cause, and action items.

---

## 2. Context is Everything

The more context you provide, the better the response.

### Include:

* Goal
* Audience
* Background
* Format
* Constraints

### Example

> Create a leadership update for senior management in 3 bullet points. Keep it concise and business-focused.

---

## 3. Be Specific

Avoid vague prompts.

❌ Write an update.

✅ Write a 3-line project status update for leadership, highlighting progress, risks, and next steps.

---

## 4. Use Role-Based Prompting

Ask Claude to act as a specific expert.

### Examples

* SRE Manager
* DevOps Engineer
* Project Manager
* Product Owner
* Technical Writer

### Example

> Act as a Senior SRE and review this incident response plan.

---

## 5. Iterate and Refine

Your first prompt doesn't have to be perfect.

### Follow-up Examples

* Make it shorter.
* Add acceptance criteria.
* Simplify for executives.
* Convert into Jira format.
* Add risks and dependencies.

---

## 6. Verify Important Outputs

Claude can make mistakes.

### Always Verify

* Technical information
* Production changes
* Architecture decisions
* Scripts and code
* Metrics and calculations

**Trust, but verify.**

---

## 7. Use Claude for Common Work Tasks

### Documentation

* SOPs
* Runbooks
* Knowledge Articles

### Operations

* Incident Summaries
* RCA Drafts
* Change Plans

### Project Management

* Jira Stories
* Test Cases
* Project Updates
* Risk Registers

### Leadership

* Executive Summaries
* Meeting Notes
* Action Items

---

## 8. Protect Sensitive Information

Never share:

* Passwords
* Secrets
* API Keys
* Confidential Customer Data
* Proprietary Company Information

---

## 9. Ask Claude to Think Step-by-Step

For complex problems:

> Analyze this issue step-by-step and explain your reasoning.

This often produces better results.

---

## 10. Human + AI is the Winning Combination

The best outcomes come when:

* AI handles drafting, summarizing, and analysis.
* Humans provide judgment, expertise, and final approval.

---

# Claude Best-Practice Formula

Whenever you write a prompt, include:

**Role + Context + Task + Format + Constraints**

### Example

> Act as a Senior DevOps Engineer. We are migrating monitoring dashboards from Splunk to Grafana. Create a Jira story with acceptance criteria, dependencies, risks, and implementation steps. Keep it concise.

---

# Quick Notes

## Remember the 5 Cs

1. **Context** – Give background.
2. **Clarity** – Be specific.
3. **Constraints** – Define limits.
4. **Critique** – Review outputs.
5. **Collaborate** – Iterate with AI.

---

## Golden Rule

**Better Prompts → Better Outputs → Higher Productivity 🚀**
