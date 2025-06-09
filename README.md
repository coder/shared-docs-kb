# Coder AI Knowledge Base

## Purpose

This repository provides AI assistants with instant Coder expertise without requiring formal training on the codebase. Upload these files to give any AI comprehensive knowledge about Coder's architecture, commands, patterns, and documentation standards.

The official Coder documentation at https://coder.com/docs is the single source of truth. This knowledge base provides AI-optimized knowledge that complements the official docs with mental models, patterns, and standards.

## Quick Start

When starting an AI session, upload relevant files from this repository and use this prompt:

```
You are now an expert on Coder, the open-source platform for provisioning remote development environments. You have access to AI-optimized knowledge that complements the official documentation at https://coder.com/docs.

Your expertise includes:
- Coder architecture and internal workings
- Documentation standards and markdown conventions
- Common patterns and troubleshooting approaches
- Community best practices and real-world usage
- Cross-cutting knowledge that spans multiple doc sections

When helping with documentation tasks:
1. Follow the documentation standards strictly for consistency
2. Reference official docs at https://coder.com/docs as the authoritative source
3. Use the mental models and patterns from this knowledge base for context
4. Suggest improvements to both official docs and this knowledge base when gaps are identified
5. Never use emojis in headings or list items
6. Always maintain technical accuracy and follow established style conventions

Contribute updates to both official docs (primary) and this knowledge base (auxiliary) when gaps are identified.
```

---

## Knowledge Base Structure

### Documentation Standards
**Essential for consistent contributions**
- `style-guide.md` - Markdown formatting, tone, and conventions
- `templates/doc-template.md` - Content structure scaffolds
- `templates/snippet-library.md` - Reusable CLI/YAML/config blocks

### Architecture and Mental Models
**High-level understanding of how Coder works**
- `architecture-notes.md` - Technical understanding of Coder systems
- `repo-navigation.md` - Guide to Coder's public repositories

### AI Integration and Workflows
**Optimized for AI assistance**
- `integration/claude-code-config.md` - Claude-specific behavior guidelines
- `integration/chatgpt-config.md` - ChatGPT workflow configuration
- `ai-project-notes.md` - Session logs and accumulated learnings

### Reference and Support
**Quick access to common information**
- `cli-reference.md` - CLI command documentation and examples
- `common-questions.md` - FAQ with answers and documentation status
- `documentation-gaps.md` - Tracked missing or incomplete documentation

---

## Use Cases

### Documentation Writing
1. Upload `style-guide.md` for formatting consistency
2. Upload `architecture-notes.md` for technical context
3. Upload relevant templates for structure guidance
4. AI produces consistent, accurate documentation

### User Support
1. Upload `common-questions.md` for known issues and solutions
2. Upload `cli-reference.md` for command syntax
3. Upload `architecture-notes.md` for system understanding
4. AI provides knowledgeable, consistent help

### Code Review
1. Upload `architecture-notes.md` for design context
2. Upload `style-guide.md` for consistency checks
3. AI reviews code against established patterns

---

## Key Principles

### Complement, Don't Duplicate
- Official docs at https://coder.com/docs are the authoritative source
- This knowledge base provides context, patterns, and AI optimization
- When gaps are found, contribute to both official docs and this knowledge base

### Documentation Standards First
- Consistency in style, tone, and formatting is critical
- AI should follow established conventions strictly
- All contributions should meet quality standards
- Never use emojis in headings or list items

### Shared Resource
- Multiple teams can use this for different purposes
- Contributions welcome from all Coder community members
- Maintain broad utility while staying focused

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
