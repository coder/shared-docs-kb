# Coder Documentation Style Guide

This guide defines the preferred conventions, formatting patterns, and stylistic choices for writing and editing documentation in `../coder/docs/`. It’s used by both human collaborators and AI assistants.

---

## Tone and Voice

- Use a **direct, clear, and instructional tone**
- Assume a **developer or technical admin** as your reader
- Avoid jargon unless necessary — explain new terms when introduced
- Prioritize **user actions** and outcomes

---

## Markdown Formatting Rules

### Headings
- Use `#`, `##`, `###` — avoid going deeper than `####`
- Top-level headings (H1) should only appear once per file
- Prefer heading structure over bold for organization
- **Do not use emojis in headings**

### Lists
- Always use `1.` for **ordered lists**
- Use `-` for **unordered lists**
- Do not use emojis to start list items
- Keep list items as short as possible — use full sentences only when needed

### Code and Inline Elements
- Use backticks for:
  - File names (`manifest.json`)
  - CLI flags (`--debug`)
  - Inline code (`coder templates create`)
  - Environment variables (`CODER_AGENT_LOG`)
- Include a language tag on all code blocks (e.g., `bash`, `json`, `md`)
- Examples:
  ```bash
  coder templates create --name dev --template ./terraform
  ```

### Links
- Use relative paths for internal links (e.g., `../admin/configure-firewall.md`)
- Avoid linking directly to headings — unless persistent
- Use link text that describes the destination purpose

---

## Visual Standards

### Alerts and Admonitions
- Use GitHub-flavored Markdown extensions:
  ```md
  > [!NOTE]
  > This feature requires version 2.1.0 or later.
  ```

### Images
- Store images in `../coder/docs/images/`
- Reference with relative paths and use `<Image>`:
  ```md
  <Image src="../../../images/template/setup-ui.png" alt="Template setup UI" width="700px" align="center" />
  ```
- Don’t use percent widths (`100%`) — use pixel widths only

---

## Terminology Consistency

| Preferred Term       | Avoid                     |
|----------------------|---------------------------|
| workspace            | dev environment, container |
| template             | config, environment       |
| admin                | administrator, ops        |
| provisioner          | builder, terraform system |
| agent                | runtime, runner           |

Refer to:
- `.markdownlint.jsonc` for rule enforcement
- [Google style guide](https://developers.google.com/style/)
- [GitLab doc style](https://docs.gitlab.com/ee/development/documentation/styleguide/)

---

## Document Hygiene

- Avoid TODOs or placeholders in merged docs
- Update `manifest.json` whenever you add/move docs
- Check anchor links if you rename headings or move files
- Run:
  ```bash
  make lint
  make fmt
  ```

---

## AI Guidance Notes

When pasting this file into Claude or ChatGPT, include a prompt like:
> “Use this style guide to review or generate documentation. Focus on formatting, clarity, and tone. Don’t override structure unless requested.”

---

_Last updated: 2025-05-05_
