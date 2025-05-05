# Doc Writer Knowledgebase for Coder.com

## Suggested Prompt for Claude Code and ChatGPT

To ensure consistent and context-aware assistance from ChatGPT or Claude Code, use the following prompt when starting a session:

```md
You are assisting with technical documentation for the open source Coder project (https://github.com/coder/coder). You should follow the rules and preferences outlined in these files:

- style-guide.md (formatting and tone rules)
- architecture-notes.md (high-level architecture of the product)
- doc-template.md (content structure scaffolds)
- snippet-library.md (reusable CLI/YAML/config blocks)
- ai-project-notes.md (recent work log and in-progress ideas)
- claude-code-config.md (rules for Claude's behavior)

You are not responsible for copyediting or tone unless asked; focus on:
- technical accuracy (based on the codebase and documented architecture)
- adherence to file placement and structure
- verifying commands, parameters, and file references
- following our markdown and terminology conventions

Do not use emojis in headings or list items. Use relative paths in links. If you're unsure, ask before making assumptions.
```

You can paste this prompt directly into Claude Code or ChatGPT (Pro) and then upload or paste relevant files as needed.

---

Welcome to your personal and collaborative documentation-sidecar knowledgebase. This repo is intended to assist and streamline your work on [Coder documentation](https://github.com/coder/coder), especially in collaboration with AI tools like ChatGPT and Claude Code.

This directory — `coder-docs-writing/` — is meant to live alongside the `coder/` and `coder.com/` repositories within your local workspace.

---

## Purpose
This repo acts as a **persistent memory store** for markdown/style preferences, architectural understanding, and AI-generated notes. It is designed to:

- Serve as a **sidecar knowledgebase** for the primary maintainer (Edward Angert)
- Act as an **AI Subject Matter Expert (AI-SME)** for use in LLM workflows
- Be a **shared workspace** for coworkers to contribute insights, style clarifications, architecture notes, and documentation patterns

The goal is to reduce context-switching, enforce style and consistency, and enable teammates or AI to step in seamlessly.

---

## Structure

```
coder-docs-writing/
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

1. **Clone the repo locally** (or fork it for sandboxed edits):
   ```bash
   git clone git@github.com:yourusername/coder-docs-writing.git ~/.coder-docs-writing
   ```

2. **(Optional) Create a symlink for convenience**:
   ```bash
   ln -s ~/.coder-docs-writing ~/Documents/coder-docs-writing
   ```

3. **(Optional) Create a shell alias for quick access**:
   ```bash
   alias dockb='cd ~/.coder-docs-writing && nvim'
   ```

4. **Review or contribute to the shared files**:
   - Use `style-guide.md` to guide any edits or submissions.
   - Use `architecture-notes.md` to share system behavior or insights.
   - Use `ai-project-notes.md` for project context and session memory.
   - Use `claude-code-config.md` to align Claude’s output with established documentation expectations and Git/image handling workflows.

5. **For AI usage**, upload or reference the relevant files during prompts to ChatGPT or Claude.

---

## Example Use Case

Say you're documenting a new Coder feature and want to ensure style consistency:

1. Upload `style-guide.md` and `architecture-notes.md` to your LLM session.
2. Paste in raw markdown from a WIP doc.
3. Prompt: _"Review this content using my style guide and Coder architecture notes."_

Or:

4. After wrapping a long LLM session:
   Prompt: _"Summarize what we just discussed and add it to `ai-project-notes.md` in today's date section."_

Coworkers can also use the same context files when jumping in to help maintain consistency.

---

## Next Steps

- ✅ Populate `style-guide.md` and `doc-template.md` based on current habits
- ✅ Start using `ai-project-notes.md` as a running journal with daily notes
- 🔁 Invite team members to contribute and update key files collaboratively
- ⏳ Optionally script or automate note updates from PRs, commits, or AI output
- 📎 Claude config now reflects all previous Claude-specific guidance (including Git/image behavior and prompt strategy)

---

## Contributing to This Knowledgebase

This repo is meant to be shared across documentation contributors and AI assistants. Please follow these guidelines when editing or proposing changes:

### General Rules
- **Do not use emojis** in headings or list items
- **Use relative paths** for internal links and image references
- All code blocks should have a language identifier (e.g., `bash`, `json`, `md`)
- Refer to `style-guide.md` before formatting or revising content

### File Guidelines
- `style-guide.md`: Contribute formatting rules, tone notes, or markdown patterns
- `architecture-notes.md`: Document internal behavior of the Coder system
- `ai-project-notes.md`: Add time-stamped entries summarizing decisions, quirks, or updates
- `templates/`: Extend with new skeletons or reusable snippets
- `integration/`: Do not remove AI configuration files — update with care

### Git Practices
- Always branch from `main`
- Use descriptive branch names (e.g., `fix/agent-notes`, `feat/add-provisioning-snippets`)
- Keep PRs focused and small when possible

This keeps the repo clean, traceable, and AI-friendly.

---

Happy documenting — and collaborating!

---

**Maintainer:** Edward Angert
**Context:** Coder.com Documentation
**Last updated:** 2025-05-06
