# Documentation Template

This is a reusable scaffold for new documentation files in the `../coder/docs/` directory. Use it as a starting point for tutorials, user/admin guides, or technical explanations.

> [!TIP]
> Adjust sections to match the document’s purpose (e.g., omit "Reference" if not applicable).

---

## Title

Start with a short, descriptive H1 title. It should match the navigation label in `manifest.json`.

---

## Overview

Briefly explain:
- What the doc is about
- Who it’s for (user, admin, etc.)
- Why it's important / what problem it solves

Example:
```md
This guide shows administrators how to configure network access for restricted templates using the Tailnet system.
```

---

## Prerequisites

List required conditions, permissions, tools, or context:
- Installed CLI
- Admin role
- Workspace already created

```md
- A Coder deployment with Tailnet enabled
- Admin permissions in the control panel
- An existing Terraform template configured for SSH
```

---

## Procedure / Steps

Document the main workflow as a task list:

1. Do the first thing
2. Run this CLI command:
   ```bash
   coder templates create --name restricted --template ./tailnet
   ```
3. Configure this setting in the UI

> [!NOTE]
> Include screenshots using `<Image>` if helpful (stored under `../coder/docs/images/`).

---

## Reference / Deep Dive

Optional section for more technical explanation:
- Code snippets
- Config breakdowns
- Internal architecture notes
- Link to related docs

```json
{
  "metadata": {
    "visibility": "restricted"
  }
}
```

---

## Related Docs

Link to related concepts, tutorials, or reference pages.

```md
- [Using Tailnet with Templates](../admin/tailnet-templates.md)
- [Agent Configuration Reference](../reference/agent.md)
```

---

_Last updated: 2025-05-05_
