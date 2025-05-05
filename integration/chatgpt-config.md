# ChatGPT Configuration for Coder Documentation

This file outlines how ChatGPT should assist with documentation tasks for the Coder project. It also explains the current limitations and expectations around updating this knowledgebase.

---

## Role and Behavior

ChatGPT should:

- Prioritize **clarity, technical accuracy, and structure** in all documentation tasks
- Use the following context files when available:
  - `style-guide.md`
  - `architecture-notes.md`
  - `snippet-library.md`
  - `ai-project-notes.md`
  - `templates/doc-template.md`
  - `integration/claude-code-config.md` (for architectural overlap)
- Suggest alternatives when uncertain, and highlight assumptions
- Defer editorial tone, IA decisions, or final content placement to the human writer

---

## Preferred Prompting Strategy

Use these prompts when working with ChatGPT:

> “Use my style guide and architecture notes to review the following doc…”

> “Based on ai-project-notes.md, summarize recent changes that should be reflected in the installation guides.”

> “Use doc-template.md as the base for a new tutorial about X.”

---

## How ChatGPT Can Update Files

ChatGPT **cannot directly write to your local filesystem** or Git repository. Instead, use the following workflow:

### 1. Manual Paste
- After generating content, copy the result into the appropriate `.md` file in your local `coder-docs-writing/` repo

### 2. Use ChatGPT Canvas (ChatGPT Pro)
- If working inside a persistent chat with Canvas enabled:
  - Ask ChatGPT to update a file (e.g. “Update `style-guide.md` to include image guidance.”)
  - It will modify the file in-place using the Canvas backend

### 3. Scripting (Optional Future Workflow)
- You can build a wrapper around ChatGPT’s API that:
  - Reads from this repo
  - Appends or rewrites `ai-project-notes.md`
  - Commits changes or opens a draft PR for review

---

## Limitations

- ChatGPT has no access to your local filesystem or shell
- Changes are non-persistent unless you manually save them
- No access to your GitHub repo unless explicitly integrated via script or plugin
- ChatGPT has no long-term memory between sessions (unless you manually upload or paste in files)

---

## Guidance on Markdown and Style

- Use `style-guide.md` to format headings, code blocks, and terminology
- Avoid emojis and stylistic icons in all headings and list items
- Use proper language identifiers for code blocks (e.g. `bash`, `json`, `md`)
- Link internal files using relative paths (e.g., `../admin/networking.md`)

---

_Last updated: 2025-05-06_
