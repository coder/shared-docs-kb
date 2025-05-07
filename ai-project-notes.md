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

## [2025-05-07] Coder Template Structure Investigation

- Coder templates require a specific structure not fully explained in documentation:
  - Registry modules use `agent_id` parameter, not `agent` (important distinction for claude-code module)
  - Modules function differently than raw resources (parameters don't match Terraform registry docs)
  - Docker templates should use `codercom/enterprise-base:ubuntu` for broader compatibility
  - Templates must include `data.coder_workspace.me.start_count` for proper lifecycle management
  - Claude Code module documentation incomplete - parameters not fully documented in examples
- Documentation should explain that modules from registry.coder.com use different parameters than raw resources
- AI integration documentation needs clearer examples showing correct module parameter syntax

## [2025-05-07] Claude Code Module Parameter Correction

- Major discovery: Claude Code module doesn't accept `anthropic_api_key` or `model` parameters directly
- These parameters should instead be passed through environment variables via the `coder_env` resource
- Required corrections:
  - Use `CLAUDE_API_KEY` env var instead of module parameter
  - Use `CLAUDE_MODEL` env var instead of module parameter
  - Use `CODER_MCP_CLAUDE_SYSTEM_PROMPT` for custom instructions
  - Use `CODER_MCP_INSTRUCTIONS` for tool configuration
- Module documentation needs updates to clarify the proper usage pattern with `coder_env`
- All AI integration examples should show this pattern to avoid confusion

---

## [TEMPLATE]

## [YYYY-MM-DD] Topic or Focus

- Bullet 1
- Bullet 2
- Optional action item or idea to follow up on

---

_Last updated: 2025-05-06_
