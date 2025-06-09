# Coder Documentation Style Guide

This guide ensures consistency across all Coder documentation. AI assistants should follow these standards strictly when creating or editing documentation.

---

## Critical Rules

### No Emojis in Headings or List Items
**This is non-negotiable**
- Never use emojis in headings: `# Getting Started` not `# 🚀 Getting Started`
- Never use emojis to start list items: `- Install Coder` not `- 🔧 Install Coder`
- Emojis may be used sparingly in body text for emphasis, but avoid in structural elements

### Markdown Formatting
- Use `#` for page titles (H1) - only one per document
- Use `##` for main sections (H2)
- Use `###` for subsections (H3)
- Avoid going deeper than `####` (H4)
- Use sentence case: "Creating templates" not "Creating Templates"

### Code Blocks
- Always specify language: ````bash`, `json`, `yaml`, `hcl`, `go`
- Use `bash` for command-line examples
- Use `console` for command output
- Include comments for complex examples

```bash
# Create a new template from GitHub
coder templates create my-template https://github.com/user/repo

# Create from specific directory
coder templates create my-template https://github.com/user/repo --directory examples/docker
```

### Lists
- Use `-` for unordered lists (not `*` or `+`)
- Use `1.` for ordered lists
- Keep list items concise
- Use parallel structure (all items same format)

### Links
- Use relative paths for internal links: `../admin/configure.md`
- Use descriptive link text: `[template creation guide](../templates/creating.md)`
- Avoid "click here" or "read more"
- Link to specific sections when helpful: `[SSH configuration](../user-guides/ssh.md#configuration)`

### Inline Code
- Use backticks for:
  - Commands: `coder create`
  - File names: `main.tf`
  - Environment variables: `CODER_ACCESS_URL`
  - Code snippets: `resource "coder_agent"`
  - UI elements: **Settings** > **Templates**

---

## Content Structure

### Page Organization
1. **Title** (H1)
2. **Brief description** of what this page covers
3. **Prerequisites** (if any)
4. **Main content** with clear sections
5. **Related topics** or next steps

### Section Flow
- Start with overview/context
- Provide step-by-step instructions
- Include working examples
- Address common issues
- Link to related information

### Examples
- Always provide working, tested examples
- Include both basic and advanced usage
- Show expected output when helpful
- Explain what each example demonstrates

---

## Tone and Voice

### Writing Style
- **Direct and clear**: Get to the point quickly
- **Instructional**: Focus on what the user should do
- **Helpful**: Anticipate questions and provide context
- **Professional**: Avoid casual language or jokes

### Audience
- **Primary**: Developers and system administrators
- **Assume**: Basic familiarity with development tools
- **Don't assume**: Deep knowledge of Coder internals

### Language
- Use active voice: "Create a template" not "A template can be created"
- Use imperative mood for instructions: "Run the command" not "You should run"
- Be specific: "Set CPU to 2 cores" not "Increase CPU"
- Avoid filler words: "simply", "just", "easily"

---

## Terminology

### Coder-Specific Terms
- **workspace** (not "environment" or "container")
- **template** (not "config" or "definition")
- **agent** (not "runner" or "daemon")
- **provisioner** (not "builder" or "executor")
- **deployment** (for Coder server installation)

### Consistent Usage
- **Coder** (not "coder" unless in code)
- **VS Code** (not "VSCode" or "Visual Studio Code")
- **GitHub** (not "Github")
- **Terraform** (not "terraform" unless in code)
- **Kubernetes** (not "K8s" in documentation)

### Technical Terms
- Define terms on first use
- Link to glossary when available
- Use consistent definitions across docs

---

## Code Examples

### Command-Line Examples
```bash
# Good: Include context and expected outcome
coder templates create docker-template ./docker-template
# Output: Template "docker-template" created successfully

# Show common variations
coder templates create docker-template https://github.com/coder/coder --directory examples/templates/docker
```

### Configuration Examples
```hcl
# Good: Include comments explaining key parts
resource "coder_agent" "main" {
  # Agent runs on the workspace instance
  arch           = data.coder_provisioner.me.arch
  os             = data.coder_provisioner.me.os
  
  # Startup script configures the environment
  startup_script = """
    #!/bin/bash
    # Install development tools
    sudo apt-get update && sudo apt-get install -y git
  """
}
```

### Error Examples
```console
# Show actual error messages users might see
Error: Template validation failed
  on main.tf line 15:
  15: resource "coder_agent" "main" {
  
Agent resource requires 'arch' and 'os' parameters.
```

---

## Images and Media

### Screenshots
- Use consistent browser/OS when possible
- Highlight relevant UI elements
- Keep images up-to-date with current UI
- Store in `/docs/images/` directory
- Use descriptive filenames: `template-creation-form.png`

### Image References
```markdown
![Template creation form](../images/template-creation-form.png)
```

### Alt Text
- Describe what the image shows
- Include relevant text from the image
- Keep concise but descriptive

---

## Admonitions and Callouts

### GitHub-Flavored Markdown
```markdown
> [!NOTE]
> This feature requires Coder v2.1.0 or later.

> [!WARNING]
> Deleting a template will stop all workspaces using that template.

> [!TIP]
> Use `coder templates pull` to update templates from their source.
```

### When to Use
- **NOTE**: Additional context or clarification
- **WARNING**: Potential data loss or breaking changes
- **TIP**: Helpful suggestions or best practices
- **IMPORTANT**: Critical information that affects functionality

---

## Quality Checklist

Before publishing documentation:

### Content
- [ ] Information is accurate and tested
- [ ] Examples work as written
- [ ] Links are valid and point to correct locations
- [ ] Prerequisites are clearly stated
- [ ] Common issues are addressed

### Style
- [ ] Follows markdown formatting rules
- [ ] Uses consistent terminology
- [ ] Maintains appropriate tone
- [ ] **No emojis in headings or list items**
- [ ] Code blocks have language specified

### Structure
- [ ] Clear headings and organization
- [ ] Logical flow from simple to complex
- [ ] Related topics are linked
- [ ] Page fits within overall doc structure

### Accessibility
- [ ] Images have descriptive alt text
- [ ] Links have meaningful text
- [ ] Content is scannable with headings
- [ ] Code examples are readable

---

## AI Assistant Guidelines

When using AI to create or edit documentation:

1. **Always reference this style guide** before writing
2. **Follow formatting rules strictly** for consistency
3. **Use established terminology** from this guide
4. **Include working examples** that have been tested
5. **Maintain the appropriate tone** for technical documentation
6. **Check against the quality checklist** before submitting
7. **Never use emojis in headings or list items**

### Common AI Pitfalls to Avoid
- Adding emojis to headings or lists
- Using inconsistent terminology
- Creating examples that haven't been tested
- Writing in overly casual tone
- Forgetting to specify code block languages
- Using "click here" or vague link text

---

## Interactive Q&A Guidelines

When AI assistants answer questions about Coder:

### Response Structure
1. **Direct answer** with working command or solution
2. **Reference to official docs** at https://coder.com/docs
3. **Additional context** when helpful
4. **Documentation gap identification** if information is missing

### Example Response Format
```
To copy a template from a GitHub repo, use:

`coder templates create my-template https://github.com/user/repo`

For complete documentation on template creation, see:
https://coder.com/docs/templates/creating-templates

I notice the official docs could use clearer GitHub examples. Would you like me to help create a contribution to improve this section?
```

### Gap Detection and Contribution
- Always check if information exists in official docs
- Offer to contribute missing information to official documentation
- Update this knowledge base with new patterns and insights
- Track common questions that aren't well documented

---

_This style guide should be updated as documentation standards evolve._