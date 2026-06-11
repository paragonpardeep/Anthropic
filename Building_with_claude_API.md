# Claude API + MCP Course Summary (Simple Notes)

## 1. What is Claude API?
Claude API lets you use Claude (AI model) in your applications.

You can:
- Send messages to Claude
- Get responses
- Build chatbots, tools, and automation systems

---

## 2. Basic API Concepts

### API Key
- A secret key used to access Claude API
- Like a password for your app

### Request
- You send input (prompt)
- Claude returns output (response)

### Multi-turn chat
- Claude remembers conversation context in a session
- Used for chatbots

---

## 3. System Prompt
- Hidden instructions for Claude
- Defines behavior (tone, rules, role)

Example:
> “You are a helpful DevOps assistant”

---

## 4. Temperature
Controls randomness:
- Low (0–0.3) → strict, factual
- Medium (0.5–0.7) → balanced
- High (0.8–1) → creative

---

## 5. Prompt Engineering (How to ask properly)

Good prompts are:
- Clear
- Specific
- Structured

Techniques:
- Use examples
- Use XML tags (<task>, <input>)
- Break complex instructions

---

## 6. Tool Use (Very Important)

Claude can use **tools** to do actions.

Examples:
- Read files
- Search web
- Call APIs
- Run commands

Flow:
1. Claude decides tool needed
2. Tool runs
3. Result sent back to Claude
4. Claude responds

---

## 7. MCP (Model Context Protocol)

MCP = Standard way to connect Claude with external tools

### MCP has 3 parts:

### 1. Tools
Do actions
- edit file
- read document
- call API

### 2. Resources
Provide data
- documents
- files
- database info

### 3. Prompts
Pre-built instructions/templates

---

## 8. MCP Server
- Backend that exposes tools, resources, prompts
- Written in Python (FastMCP SDK)

Example tools:
- read_doc()
- edit_doc()

---

## 9. MCP Client
- Connects app to MCP server
- Sends requests
- Gets results
- Passes data to Claude

---

## 10. MCP Inspector
- Testing UI for MCP server
- Used to:
  - test tools
  - check resources
  - debug server

---

## 11. Resources in MCP

Used to GET data (no action)

Types:
- Static resource → docs://list
- Dynamic resource → docs://{doc_id}

Example:
- fetch document content
- list files

---

## 12. Prompts in MCP

Pre-made prompt templates.

Why use them?
- Better results than user prompts
- Reusable instructions

Example:
- format document to markdown
- summarize report

---

## 13. Workflows vs Agents

### Workflows
- Fixed steps
- You define the process
- Predictable

Example:
1. Read file
2. Extract info
3. Generate report

---

### Agents
- Flexible
- Claude decides steps
- Uses tools dynamically

Example:
- “Solve this problem” → Claude figures out steps

---

## 14. Parallelization Workflow
- Split task into multiple parts
- Run them in parallel
- Combine results

Example:
- Check multiple material types separately
- Then decide best option

---

## 15. Chaining Workflow
- Step-by-step process
- Output of one step → input of next

Example:
1. Research topic
2. Write script
3. Generate video
4. Post content

---

## 16. Routing Workflow
- Classify input first
- Send to correct pipeline

Example:
- Educational request → education prompt
- Comedy request → humor prompt

---

## 17. Claude Code
- Terminal-based AI assistant
- Helps with coding

Features:
- Read/edit files
- Run commands
- Debug code
- Manage projects

---

## 18. Computer Use (Advanced)
Claude can:
- Use browser
- Control apps
- Interact with UI
- Perform real-world tasks

---

## 19. Key Idea Summary

- MCP connects Claude to tools, data, and prompts
- Tools = actions
- Resources = data
- Prompts = templates
- Agents = flexible decision-making system
- Workflows = fixed step system

---

## 20. Final Mental Model

Think like this:

Claude = Brain  
MCP Tools = Hands  
Resources = Memory  
Prompts = Instructions  
Agents = Autonomous worker  
Workflows = Step-by-step checklist
