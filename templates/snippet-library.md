# Snippet Library

Reusable snippets and patterns for Coder documentation. Use these to maintain consistency and reduce repetition across guides, tutorials, and reference material.

---

## CLI Commands

```bash
coder login https://coder.example.com
```

```bash
coder templates create --name dev-template --template ./terraform
```

```bash
coder workspace create --template dev-template --name my-ws
```

---

## Environment Variables

```bash
export CODER_AGENT_LOG=debug
export CODER_AGENT_TOKEN="<token>"
```

---

## YAML Snippets

```yaml
resource "coder_agent" "main" {
  os = "linux"
  arch = "amd64"
}
```

```yaml
resource "coder_parameter" "name" {
  name        = "display_name"
  display_name = "Name"
  type        = "string"
  mutable     = true
  default     = "dev"
}
```

---

## File References

### `manifest.json`
```json
{
  "label": "Admin",
  "entries": [
    { "label": "Networking", "path": "admin/networking.md" }
  ]
}
```

### `.markdownlint.jsonc`
```jsonc
{
  "default": true,
  "MD013": false, // Allow long lines
  "MD024": { "siblings_only": true } // Allow duplicate headers if not siblings
}
```

---

## Image Embeds

Use standard Markdown image syntax with relative paths. Avoid percent widths — image sizing is now handled via CSS on the site.

```md
![Template setup UI](../../../images/template/setup-ui.png)
```

---

_Last updated: 2025-05-06_
