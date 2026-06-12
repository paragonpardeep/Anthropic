# 🧠 Agentic Systems + Claude Code Cheat Sheet

This guide summarizes key patterns for multi-agent systems, tool design, error handling, and synthesis workflows.

---

# 1. CORE RULE: COORDINATOR IS THE BRAIN

### Golden Principle
- **Coordinator = decision maker**
- **Subagents = executors**
- **Synthesis agent = merger of results**
- **Tools = isolated capabilities**

> 🚨 Never bypass the coordinator for direct agent-to-agent communication.

---

# 2. WHEN TO USE SUBAGENTS

### Use subagents for:
- Heavy analysis tasks
- Isolated domains (web search, document analysis)
- Large or noisy workloads
- Parallel execution tasks

### Mental model:
> “Specialists work independently, coordinator integrates.”

---

# 3. ERROR HANDLING PRINCIPLE

### NEVER:
- Crash entire workflow on subagent failure
- Silently ignore failures
- Retry blindly without context

### ALWAYS:
Return **structured error context**:

Include:
- Error type (timeout, parse failure, etc.)
- Attempted input/query
- Partial results (if any)
- Suggested recovery options

> 💡 Errors are *data*, not stop signals.

---

# 4. TOOL DESIGN PRINCIPLE

### Fix misbehavior by improving tools, not prompts

### Prefer:
- Clear tool names
- Explicit tool purpose
- Input/output examples
- Boundary definitions

### Avoid:
- Over-relying on prompt instructions
- Hidden assumptions
- Ambiguous tool overlap

---

# 5. DATA FLOW PRINCIPLE

### Bad pattern:
- Passing raw 80K–150K token outputs into synthesis

### Good pattern:
- Structured outputs:
  - key facts
  - summaries
  - citations
  - metadata (confidence, source type)

> 📌 Rule: Compress before combining

---

# 6. SYNTHESIS AGENT RULES

The synthesis agent should:
- Merge findings
- Detect conflicts
- Identify missing coverage
- NOT re-run analysis

### Always include:
- Coverage gaps
- Conflicting source notes
- Attribution to sources

---

# 7. TASK DECOMPOSITION RULE

### Coordinator must:
- Break tasks into **complete domain coverage**
- Avoid narrow or biased splits

### Common failure:
- Missing domains due to incomplete decomposition

> Example failure: Only "visual arts" → ignores music, film, writing

---

# 8. OVERLAP CONTROL RULE

### Prevent duplication BEFORE execution:

Use:
- Explicit subtopic partitioning
- Clear domain assignment
- Source-type separation (web vs documents)

### Avoid:
- Post-hoc deduplication
- Uncontrolled parallel exploration

---

# 9. TOOL / AGENT SCOPE RULE

### Correct design:
- Document agent → only document tools
- Search agent → only web tools
- Coordinator → routing only

### Principle:
> Each agent should have minimal necessary permissions.

---

# 10. CONTROL FLOW PRINCIPLE

### Coordinator responsibilities:
- Task routing
- Error handling decisions
- Final orchestration

### Avoid:
- Direct agent-to-agent communication
- Autonomous cross-agent decisions

---

# 11. SYNTHESIS INPUT HANDLING

When combining results:

### Always:
- Highlight missing data
- Show conflicting sources
- Explicitly label uncertainty

### Never:
- Hide missing sources
- Assume completeness silently

> “No data is also data.”

---

# 12. 4-LAYER SYSTEM MODEL

### 🧩 Architecture:

1. **Coordinator**
   - planning, routing, control

2. **Subagents**
   - isolated execution units

3. **Synthesis Agent**
   - merges + evaluates + reports gaps

4. **Tools**
   - simple, scoped, predictable functions

---

# 🏁 FINAL MASTER RULE

If unsure, always choose options that:

✔ Keep coordinator in control  
✔ Structure outputs instead of raw text  
✔ Prevent duplication before execution  
✔ Propagate errors with context  
✔ Ensure clear separation of responsibilities  
✔ Avoid unnecessary complexity  

---

# 🧠 ONE-LINE MEMORY TRICK

> “Coordinate → Execute → Summarize → Validate”

---
