# MCP Advanced Topics – Simple Summary

This document summarizes key concepts of the Model Context Protocol (MCP) in simple words.

---

# 1. Sampling

Sampling allows an MCP server to ask the client to call a language model (like Claude).

### Why it is useful:
- Server does NOT need its own API key
- Client handles AI calls and cost

### Flow:
1. Server creates a prompt
2. Server sends request to client
3. Client calls Claude
4. Client returns result to server

---

# 2. Log and Progress Notifications

Used to improve user experience during long tasks.

### Features:
- Shows real-time progress updates
- Sends logs like “step 1 done”, “processing...”

### Methods:
- `context.info()` → send logs
- `context.report_progress()` → send progress %

---

# 3. Roots

Roots control file system access for MCP servers.

### Why it is needed:
- Prevents access to unwanted files
- Helps Claude find files easily

### Benefits:
- Better security
- Easier file search
- Controlled access to folders

---

# 4. MCP JSON Message Types

All MCP communication happens using JSON messages.

### Two main types:

## 1. Request–Response
- Client asks, server replies
- Example: tool call → result

## 2. Notifications
- One-way messages
- Example: progress updates, logs

---

# 5. STDIO Transport

Used for local development.

### How it works:
- Client runs server as a subprocess
- Communication via stdin and stdout
- Both sides send JSON messages

### Key point:
- Works only on same machine
- Very fast and simple

---

# 6. Streamable HTTP Transport

Used for remote (cloud) MCP servers.

### How it works:
- Communication happens over HTTP
- Uses SSE (Server-Sent Events) for streaming

### Key idea:
- Enables real-time updates over internet

### Limitation:
- HTTP is not naturally bidirectional

---

# 7. Streamable HTTP (In Depth)

Uses SSE to simulate real-time communication.

### Flow:
1. Client initializes connection
2. Server gives session ID
3. Client opens SSE connection
4. Server sends updates through SSE

### Two connections:
- Main SSE → logs, progress, notifications
- Tool SSE → tool results

---

# 8. State & Stateless HTTP

Controls how MCP behaves at scale.

## Stateless HTTP (stateless_http = true)
- No session memory
- Easier scaling with load balancers
- ❌ No progress updates
- ❌ No sampling
- ❌ No server-to-client messages

## JSON Response (json_response = true)
- No streaming
- Only final response returned

---

# 9. Key Trade-offs

| Mode | Pros | Cons |
|------|------|------|
| STDIO | Simple, fast | Local only |
| Streamable HTTP | Remote + real-time | More complex |
| Stateless HTTP | Easy scaling | Loses features |

---

# Final Summary

- MCP is a JSON-based communication system
- It supports tools, logs, prompts, and AI sampling
- STDIO = local development
- HTTP = production and remote access
- Advanced features depend on session + streaming support
