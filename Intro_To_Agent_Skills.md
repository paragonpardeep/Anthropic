# Introduction to Agent Skills - Quick Notes

## What Are Skills?

Skills are reusable instructions that teach Claude how to perform specific tasks automatically.

Instead of repeating the same instructions every time, create a skill once and Claude will use it whenever relevant.

### Examples

* PR reviews
* Commit messages
* Documentation templates
* Code review checklists

---

# How Skills Work

1. Claude scans available skills at startup.
2. It loads only the skill name and description.
3. When your request matches a skill description, Claude activates the skill.
4. Claude loads the full instructions and follows them.

---

# Skill Structure

Each skill lives in a folder and contains a `SKILL.md` file.

```yaml
---
name: pr-description
description: Creates pull request descriptions.
---
```

The description tells Claude when to use the skill.

---

# Where Skills Live

## Personal Skills

```text
~/.claude/skills
```

* Available across all projects
* Used for personal preferences

## Project Skills

```text
.claude/skills
```

* Stored inside a repository
* Shared with the entire team through Git

---

# Skill Metadata

Required:

```yaml
name:
description:
```

Optional:

```yaml
allowed-tools:
model:
```

Example:

```yaml
---
name: code-review
description: Reviews code quality and best practices
allowed-tools: Read, Grep, Glob
model: sonnet
---
```

---

# Writing Good Skill Descriptions

A good description answers:

1. What does the skill do?
2. When should Claude use it?

Example:

```text
Reviews pull requests for code quality. Use when reviewing PRs or checking code changes.
```

More specific descriptions result in better matching.

---

# Restricting Tools

Use `allowed-tools` to limit what Claude can do.

Example:

```yaml
allowed-tools: Read, Grep, Glob, Bash
```

Useful for:

* Read-only tasks
* Security-sensitive workflows
* Controlled access

---

# Progressive Disclosure

Keep `SKILL.md` focused and small.

Store additional content separately:

```text
skill-name/
├── SKILL.md
├── references/
├── scripts/
└── assets/
```

### References

Additional documentation.

### Scripts

Automation scripts.

### Assets

Templates, images, and files.

Recommended:

```text
SKILL.md < 500 lines
```

---

# Scripts

Instead of storing complex logic in prompts:

* Put logic into scripts.
* Claude executes the script.
* Only script output uses context.

Benefits:

* Faster
* Cleaner
* More efficient

---

# Skills vs Other Claude Features

| Feature     | Purpose                            |
| ----------- | ---------------------------------- |
| CLAUDE.md   | Always-on project rules            |
| Skills      | Task-specific expertise            |
| Subagents   | Delegated work in separate context |
| Hooks       | Event-driven automation            |
| MCP Servers | External integrations              |

---

## CLAUDE.md

Loads in every conversation.

Use for:

* Project standards
* Coding conventions
* Global instructions

---

## Skills

Load only when relevant.

Use for:

* Reviews
* Templates
* Specialized workflows

---

## Subagents

Run tasks in a separate context.

Use when:

* Delegating work
* Isolating tasks

---

## Hooks

Triggered by events.

Examples:

* File save
* Validation
* Automated checks

---

## MCP Servers

Connect Claude to external systems and tools.

Examples:

* GitHub
* APIs
* Browsers

---

# Sharing Skills

## Option 1: Git Repository

Store skills in:

```text
.claude/skills
```

Benefits:

* Shared automatically
* Version controlled
* Easy team collaboration

---

## Option 2: Plugins

Package skills as plugins.

Benefits:

* Reusable across projects
* Easy distribution

---

## Option 3: Enterprise Skills

Organization-wide deployment.

Benefits:

* Highest priority
* Enforces company standards
* Supports compliance requirements

---

# Skill Priority

When multiple skills have the same name:

```text
Enterprise
↓
Personal
↓
Project
↓
Plugins
```

Higher priority always wins.

---

# Skills and Subagents

Important:

Subagents do NOT automatically inherit skills.

You must explicitly assign skills.

Example:

```yaml
skills:
  - accessibility-audit
  - performance-check
```

Built-in agents cannot use skills.

Custom subagents can.

---

# Troubleshooting Skills

## Step 1: Run the Validator

Always validate before debugging.

Checks:

* Structure
* YAML syntax
* Missing files
* Configuration issues

---

## Skill Doesn't Trigger

Cause:

* Description is too vague

Fix:

* Add better keywords
* Include common trigger phrases

---

## Skill Doesn't Load

Check:

```text
.claude/skills/
  skill-name/
    SKILL.md
```

Requirements:

* Correct folder structure
* File name exactly `SKILL.md`
* Restart Claude Code

Use:

```bash
claude --debug
```

to view loading errors.

---

## Wrong Skill Gets Used

Cause:

* Similar descriptions

Fix:

* Make descriptions more specific
* Use unique skill names

---

## Priority Conflict

Cause:

* Higher-priority skill has the same name

Fix:

* Rename your skill
* Check priority hierarchy

---

## Plugin Skills Missing

Fix:

1. Clear cache
2. Restart Claude Code
3. Reinstall plugin

---

## Runtime Errors

### Missing Dependencies

Install required packages.

### Permission Issues

```bash
chmod +x script.sh
```

### Path Problems

Use forward slashes:

```text
folder/file.txt
```

---

# Quick Checklist

Before creating a skill:

* Clear name
* Clear description
* Proper folder structure
* Keep SKILL.md small
* Use references for large content
* Validate before sharing

---

# 10 Things to Remember

1. Skills = Reusable instructions
2. SKILL.md is required
3. Description controls matching
4. Skills load only when needed
5. Personal and Project skills exist
6. Use allowed-tools for restrictions
7. Keep skills small and organized
8. Share through Git, Plugins, or Enterprise
9. Subagents need skills assigned manually
10. Use the validator before troubleshooting

---

# One-Line Summary

**Agent Skills allow Claude to automatically apply reusable, task-specific instructions, making workflows faster, more consistent, and easier to scale across projects and teams.**
