## Model Context Protocol (MCP) – 5 Line Summary

- MCP (Model Context Protocol) is an open standard that connects AI applications like Claude, ChatGPT, and AI agents to external tools, data sources, APIs, databases, and workflows.
- Think of it as a USB-C for AI — one standard way to connect AI to many different systems.
- MCP uses a client-server architecture, where AI clients communicate with MCP servers that expose tools and data.
- It eliminates the need for custom integrations between every AI model and every tool, reducing development effort and improving interoperability.
- MCP enables AI agents to perform real-world actions such as reading files, querying databases, accessing Jira/Slack, using GitHub, and automating workflows securely.

## MCP Simple Example

Imagine Claude is like a smart employee sitting in an office.

Without MCP:

👨‍💼 You: "Check my Jira tickets."

🤖 Claude: "I can't access Jira directly. Please copy and paste the tickets here."

With MCP:

👨‍💼 You: "Check my Jira tickets and summarize the high-priority ones."

🤖 Claude:

Connects to Jira through an MCP server.
Reads your assigned tickets.
Finds high-priority items.
Creates a summary.

All automatically.


---------------


# MCP (Model Context Protocol) – Quick Notes

## What is MCP?
MCP is a standard way for AI models (Claude, ChatGPT, etc.) to connect with external tools, data, and services without writing custom integrations.

**Simple Formula:**
AI ↔ MCP Client ↔ MCP Server ↔ External Service

Example:
Claude → GitHub MCP Server → GitHub API

---

## Why MCP?

Without MCP:
- You create APIs
- Write tool definitions
- Maintain integrations
- Handle authentication

With MCP:
- MCP Server already provides tools
- Reuse existing integrations
- Faster development
- Less maintenance

---

## Core Components

### 1. MCP Client
Acts as a bridge between AI and MCP Server.

Responsibilities:
- Discover tools
- Call tools
- Read resources
- Get prompts

Example:
Claude asks:
"Show my GitHub repositories"

Client:
- Finds available tools
- Executes tool
- Returns result to Claude

---

### 2. MCP Server
Provides capabilities to AI.

Contains:
- Tools
- Resources
- Prompts

Examples:
- GitHub MCP Server
- Google Drive MCP Server
- Jira MCP Server
- Custom Document MCP Server

---

## MCP Communication Flow

1. User asks question
2. Client requests available tools
3. Claude selects tool
4. Client calls tool
5. Server executes action
6. Result returned
7. Claude generates answer

---

# MCP Primitives (Most Important)

## 1. Tools (Model Controlled)

Used when AI needs to perform an action.

Examples:
- Read a file
- Update a document
- Create Jira ticket
- Query GitHub

Python Example:

```python
@mcp.tool()
def read_document(doc_id):
    return docs[doc_id]
```

Remember:

**Tool = AI performs an action**

---

## 2. Resources (App Controlled)

Used to fetch data.

Examples:
- List documents
- Fetch document contents
- Load configuration

Python Example:

```python
@mcp.resource("docs://documents")
def list_docs():
    return list(docs.keys())
```

Remember:

**Resource = Read/Get data**

---

## 3. Prompts (User Controlled)

Reusable prompt templates.

Examples:
- Summarize document
- Convert to Markdown
- Review code

Python Example:

```python
@mcp.prompt()
def format_document(doc_id):
    return [UserMessage(...)]
```

Remember:

**Prompt = Reusable workflow**

---

# Easy Way to Remember

| Need | Use |
|--------|--------|
| Perform action | Tool |
| Read data | Resource |
| Reusable workflow | Prompt |

---

# MCP Python SDK

Instead of writing JSON schemas manually:

```python
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("MyServer")
```

Benefits:
- Simple decorators
- Auto schema generation
- Type validation
- Less code

---

# MCP Inspector

Used to test MCP Servers.

Start:

```bash
mcp dev mcp_server.py
```

Open browser:

```text
http://127.0.0.1:6274
```

Can:
- List tools
- Test tools
- Test resources
- Test prompts
- Debug issues

---

# Client Functions

### List Tools

```python
list_tools()
```

Gets all available tools.

### Call Tool

```python
call_tool()
```

Executes a tool.

### List Prompts

```python
list_prompts()
```

Gets available prompts.

### Get Prompt

```python
get_prompt()
```

Loads a prompt with variables.

---

# Real-World Example

Question:

"Show all GitHub repositories."

Flow:

User
↓
Claude
↓
MCP Client
↓
GitHub MCP Server
↓
GitHub API
↓
Results
↓
Claude Answer

---

# Interview One-Liner

**Model Context Protocol (MCP) is an open standard that allows AI models to securely interact with external tools, resources, and workflows through MCP servers, eliminating the need for custom integrations.**

---

# 30-Second Revision

- MCP = Standard way for AI to connect with external systems
- MCP Client = Bridge
- MCP Server = Provides capabilities
- Tool = Perform action
- Resource = Read data
- Prompt = Reusable workflow
- Inspector = Test MCP Server
- SDK = Create tools/resources/prompts using decorators
- Goal = Reduce custom integration work
