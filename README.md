# Doc Writer Knowledgebase for Coder.com

## Suggested Prompt for Claude Code and ChatGPT

To ensure consistent and context-aware assistance from ChatGPT or Claude Code, use the following prompt when starting a session:

```md
You are assisting with technical documentation for the open source Coder project (https://github.com/coder/coder).

You should follow the rules and preferences outlined in these files in the `shared-docs-kb` directory:

1. style-guide.md (formatting and tone rules)
2. architecture-notes.md (high-level architecture of the product)
3. templates/doc-template.md (content structure scaffolds)
4. templates/snippet-library.md (reusable CLI/YAML/config blocks)
5. ai-project-notes.md (recent work log and in-progress ideas)
6. claude-code-config.md (rules for Claude's behavior)

You are not responsible for copyediting or tone unless asked; focus on:

1. technical accuracy (based on the codebase and documented architecture)
2. adherence to file placement and structure
3. verifying commands, parameters, and file references
4. following our markdown and terminology conventions

Do not use emojis in headings or list items.  Do not flatter me. Use relative paths in links. If you're unsure, ask before making assumptions.

When an issue arises, before you attempt to fix the issue, consult the Coder codebase for examples of potential fixes or for other examples that might work towards the same purpose.
```

You can paste this prompt directly into Claude Code or ChatGPT (Pro) and then upload or paste relevant files as needed.

---

Welcome to your personal and collaborative documentation-sidecar knowledgebase. This repo is intended to assist and streamline your work on [Coder documentation](https://github.com/coder/coder), especially in collaboration with AI tools like ChatGPT and Claude Code.

This directory — `shared-docs-kb/` — is meant to live alongside the `coder/` and `coder.com/` repositories within your local workspace.

---

## Purpose

This repo acts as a **persistent memory store** for markdown/style preferences, architectural understanding, and AI-generated notes. It is designed to:

1. Serve as a **sidecar knowledgebase** for the primary maintainer (Edward Angert)

1. Act as an **AI Subject Matter Expert (AI-SME)** for use in LLM workflows

1. Be a **shared workspace** for coworkers to contribute insights, style clarifications, architecture notes, and documentation patterns

The goal is to reduce context-switching, enforce style and consistency, and enable teammates or AI to step in seamlessly.

---

## Structure

```text
shared-docs-kb/
├── README.md                      # This file
├── style-guide.md                # Markdown and tone/style preferences
├── architecture-notes.md         # Evolving notes about the Coder architecture
├── templates/
│   ├── doc-template.md           # Skeletons or starter templates
│   └── snippet-library.md        # Reusable markdown/YAML/code blocks
├── ai-project-notes.md           # AI-writable log for evolving notes
├── integration/
│   ├── chatgpt-config.md         # Guidance for using ChatGPT effectively
│   └── claude-code-config.md     # SME config for Claude (merged from CLAUDE.md + CLAUDE_DOCS_GUIDELINES.md)
```

Documentation paths should refer to content under `../coder/docs/`. Image assets are under `../coder/docs/images/`. Website rendering code is in `../coder.com/`.

---

## Getting Started

1. Clone the repo locally (or fork it for sandboxed edits):

    ```bash
    git clone git@github.com:coder/shared-docs-kb.git ~/.shared-docs-kb
    ```

1. Review or contribute to the shared files:

    1. Use `style-guide.md` to guide any edits or submissions.

    1. Use `architecture-notes.md` to share system behavior or insights.

    1. Use `ai-project-notes.md` for project context and session memory.

    1. Use `claude-code-config.md` to align Claude’s output with established documentation expectations and Git/image handling workflows.

1. For AI usage, upload or reference the relevant files during prompts to ChatGPT or Claude.

---

## Example Use Case

Say you're documenting a new Coder feature and want to ensure style consistency:

1. Upload `style-guide.md` and `architecture-notes.md` to your LLM session.

1. Paste in raw markdown from a WIP doc.

1. Prompt: _"Review this content using my style guide and Coder architecture notes."_

Or:

1. After wrapping a long LLM session:

    Prompt: _"Summarize what we just discussed and add it to `ai-project-notes.md` in today's date section."_

Coworkers can also use the same context files when jumping in to help maintain consistency.

---

## Next Steps

1. Populate `style-guide.md` and `doc-template.md` based on current habits

1. Start using `ai-project-notes.md` as a running journal with daily notes

1. Invite team members to contribute and update key files collaboratively

1. Optionally script or automate note updates from PRs, commits, or AI output

1. Claude config now reflects all previous Claude-specific guidance (including Git/image behavior and prompt strategy)

---

## Contributing to This Knowledgebase

This repo is meant to be shared across documentation contributors and AI assistants. Please follow these guidelines when editing or proposing changes:

### General Rules

1. **Do not use emojis** in headings or list items

1. **Use relative paths** for internal links and image references

1. All code blocks should have a language identifier (e.g., `bash`, `json`, `md`)

1. Refer to `style-guide.md` before formatting or revising content

### File Guidelines

1. `style-guide.md`: Contribute formatting rules, tone notes, or markdown patterns

1. `architecture-notes.md`: Document internal behavior of the Coder system

1. `ai-project-notes.md`: Add time-stamped entries summarizing decisions, quirks, or updates

1. `templates/`: Extend with new skeletons or reusable snippets

1. `integration/`: Do not remove AI configuration files — update with care

### Git Practices

1. Always branch from `main`

1. Use descriptive branch names (e.g., `fix/agent-notes`, `feat/add-provisioning-snippets`)

1. Keep PRs focused and small when possible

This keeps the repo clean, traceable, and AI-friendly.

---

Happy documenting — and collaborating!

---

**Maintainer:** Edward Angert
**Context:** Coder.com Documentation
**Last updated:** 2025-05-07
