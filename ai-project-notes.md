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

## [Session ID: 2025-01-15-004] Combined AI Knowledge Base Approach
**Human Contributor**: User
**AI Assistant**: Claude (Blink)
**Focus Area**: Repository consolidation and documentation standards

### Context
- Two separate PRs were created in this session with different approaches
- Need to combine the best of both while maintaining strict documentation standards
- Critical requirement: never use emojis in headings or list items
- Focus on AI-optimized knowledge that complements official docs

### Discoveries
- Repository should provide instant AI expertise without formal training
- Documentation standards are critical for consistency
- Official docs at https://coder.com/docs must remain single source of truth
- This knowledge base should complement, not duplicate official documentation
- Emoji usage in headings is a major concern that must be prevented

### Decisions Made
- Combined both PR approaches into single coherent system
- Enhanced style guide with critical rules section emphasizing no emojis
- Maintained existing valuable content while improving structure
- Created clear use cases for different scenarios (documentation writing, user support, code review)
- Established principles: complement don't duplicate, documentation standards first, shared resource

### Memory Updates
- README.md: Completely rewritten to combine both approaches
- style-guide.md: Enhanced with critical rules and AI guidelines
- documentation-standards/: New directory with enhanced style guide
- Structure: Organized around documentation standards, architecture, AI integration, and reference

### Next Steps
- Close the two separate PRs and create single combined PR
- Ensure all files follow the documentation standards strictly
- Test the knowledge base with AI assistants to verify effectiveness
- Add remaining files for patterns and community knowledge as needed

---

## [TEMPLATE]

## [YYYY-MM-DD] Topic or Focus

- Bullet 1
- Bullet 2
- Optional action item or idea to follow up on

---

_Last updated: 2025-01-15_
