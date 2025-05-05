# AI Project Notes

This is a running log of notes, observations, decisions, and refinements related to AI-assisted documentation work for the Coder codebase and documentation site. Use this as a shared memory between yourself and tools like ChatGPT and Claude.

> All entries should be dated. Use bullet points to capture brief notes, discoveries, or things to revisit. Prefer clarity over completeness.

---

## [2025-05-05] Initial Setup

- Created `coder-docs-writing` to serve as shared SME knowledgebase and AI sidecar.
- Sourced content from existing files: `CLAUDE.md`, `CODER_ARCHITECTURE.md`, and `CLAUDE_DOCS_GUIDELINES.md`.
- Adopted rule: **no emojis** in headings or list items.
- Merged Claude-related guidelines into `integration/claude-code-config.md`.
- Moved architecture overview into `architecture-notes.md`.
- Style conventions are tracked in `style-guide.md` and adhere to markdownlint + Google + GitLab.

---

## [2025-05-06] Style & Template Refinement

- Added `doc-template.md` under `templates/` as a scaffold for new docs.
- Enforced use of `<Image>` with relative paths and fixed pixel width.
- Confirmed internal doc structure under `../coder/docs/` is stable:
  - User Guides → `guides/`
  - Admin Docs → `admin/`
  - Tutorials → `tutorials/`
  - Reference → `reference/` (auto-generated, do not edit)

---

## [TEMPLATE]

## [YYYY-MM-DD] Topic or Focus

- Bullet 1
- Bullet 2
- Optional action item or idea to follow up on

---

_Last updated: 2025-05-06_
