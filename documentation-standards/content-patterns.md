# Documentation Content Patterns

Standardized structures for common types of Coder documentation. Use these patterns to ensure consistency and completeness.

---

## How-To Guides

### Structure
```markdown
# How to [Action]

[Brief description of what this guide accomplishes]

## Prerequisites

- [Requirement 1]
- [Requirement 2]

## Steps

### 1. [First major step]

[Explanation of what this step does]

```bash
[Command or code example]
```

[Expected output or result]

### 2. [Second major step]

[Continue pattern...]

## Verification

[How to confirm the task was completed successfully]

## Troubleshooting

**Issue**: [Common problem]
**Solution**: [How to fix it]

## Next steps

- [Related task or guide]
- [Advanced configuration]
```

### Example: How to Create a Template
```markdown
# How to Create a Template

This guide shows you how to create a Coder template from a Terraform configuration.

## Prerequisites

- Coder CLI installed and authenticated
- Basic familiarity with Terraform
- Access to create templates in your Coder deployment

## Steps

### 1. Prepare your Terraform configuration

Create a directory with your template files:

```bash
mkdir my-template
cd my-template
```

### 2. Create the template

Use the Coder CLI to create the template:

```bash
coder templates create my-template .
```

Expected output:
```console
Template "my-template" created successfully
```

## Verification

Confirm your template appears in the list:

```bash
coder templates list
```

## Next steps

- [Create a workspace from your template](../workspaces/creating.md)
- [Update your template](./updating-templates.md)
```

---

## Reference Documentation

### Structure
```markdown
# [Feature/Command] Reference

[Brief overview of the feature]

## Syntax

```bash
[command syntax with placeholders]
```

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `param1` | string | Yes | [Description] |
| `param2` | number | No | [Description] |

## Examples

### Basic usage

```bash
[simple example]
```

### Advanced usage

```bash
[complex example with explanation]
```

## Related commands

- [`related-command`](./related-command.md) - [Brief description]
```

### Example: CLI Command Reference
```markdown
# coder templates create

Create a new template from a Terraform configuration.

## Syntax

```bash
coder templates create <name> [source] [flags]
```

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name` | string | Yes | Name for the template |
| `source` | string | No | Source directory or Git URL (default: current directory) |

## Flags

| Flag | Type | Description |
|------|------|-------------|
| `--directory` | string | Subdirectory within source |
| `--ref` | string | Git branch, tag, or commit |
| `--variables-file` | string | Path to variables file |

## Examples

### Create from current directory

```bash
coder templates create my-template
```

### Create from GitHub repository

```bash
coder templates create docker-template https://github.com/coder/coder --directory examples/templates/docker
```

## Related commands

- [`coder templates list`](./templates-list.md) - List available templates
- [`coder templates push`](./templates-push.md) - Update an existing template
```

---

## Concept Explanations

### Structure
```markdown
# [Concept Name]

[High-level explanation of what this concept is]

## How it works

[Technical explanation of the mechanism]

## Key components

### [Component 1]
[Description and role]

### [Component 2]
[Description and role]

## Common use cases

- [Use case 1 with brief explanation]
- [Use case 2 with brief explanation]

## Examples

### [Scenario 1]
[Code example with explanation]

### [Scenario 2]
[Code example with explanation]

## Best practices

- [Practice 1 with rationale]
- [Practice 2 with rationale]

## Related concepts

- [Related concept 1](./concept1.md)
- [Related concept 2](./concept2.md)
```

### Example: Workspaces Concept
```markdown
# Workspaces

Workspaces are individual development environments provisioned from templates. Each workspace provides an isolated environment with its own compute resources, storage, and network access.

## How it works

When you create a workspace, Coder uses Terraform to provision infrastructure based on your chosen template. The workspace includes a Coder agent that enables secure access and management.

## Key components

### Template
Defines the infrastructure and configuration for workspaces

### Agent
Runs inside the workspace to enable connectivity and management

### Resources
The actual infrastructure (VMs, containers, storage) that make up the workspace

## Common use cases

- Development environments for specific projects
- Isolated testing environments
- Standardized onboarding for new team members
- Temporary environments for experiments

## Examples

### Basic development workspace
```hcl
resource "coder_agent" "main" {
  arch = "amd64"
  os   = "linux"
}

resource "docker_container" "workspace" {
  image = "codercom/enterprise-base:ubuntu"
  name  = "coder-${data.coder_workspace.me.name}"
}
```

## Best practices

- Use templates to standardize workspace configurations
- Include necessary development tools in your base image
- Configure automatic shutdown to save resources
- Use persistent volumes for important data

## Related concepts

- [Templates](./templates.md)
- [Agents](./agents.md)
```

---

## Troubleshooting Guides

### Structure
```markdown
# Troubleshooting [Area]

[Overview of common issues in this area]

## Quick diagnosis

1. **Check [thing 1]**: `command to check`
2. **Verify [thing 2]**: `command to verify`
3. **Test [thing 3]**: `command to test`

## Common issues

### [Specific issue 1]

**Symptoms**: [What the user sees]
**Cause**: [Why this happens]
**Solution**:

```bash
[Commands to fix]
```

**Prevention**: [How to avoid this in the future]

### [Specific issue 2]

[Same pattern...]

## Advanced troubleshooting

### [Complex scenario]

[Detailed investigation steps]

## When to get help

- [Condition 1] - Contact [team/resource]
- [Condition 2] - File issue at [location]

## Additional resources

- [Link to related troubleshooting]
- [Link to community discussions]
```

---

## Installation Guides

### Structure
```markdown
# Installing Coder on [Platform]

[Brief overview of this installation method]

## Prerequisites

### System requirements
- [Hardware requirement 1]
- [Hardware requirement 2]

### Software requirements
- [Software dependency 1]
- [Software dependency 2]

## Installation

### 1. [Preparation step]

[Explanation and commands]

### 2. [Installation step]

[Commands with expected output]

### 3. [Configuration step]

[Configuration details]

## Verification

[How to confirm installation worked]

## Configuration

### [Configuration area 1]
[Settings and options]

### [Configuration area 2]
[Settings and options]

## Next steps

- [Create your first template](../templates/creating.md)
- [Configure authentication](./authentication.md)

## Troubleshooting

[Common installation issues and solutions]
```

---

## Content Pattern Guidelines

### Choosing the Right Pattern

- **How-to guides**: Task-oriented, step-by-step instructions
- **Reference docs**: Comprehensive parameter and option listings
- **Concept explanations**: Understanding-oriented, explain the "why"
- **Troubleshooting**: Problem-solving oriented
- **Installation guides**: Getting started with setup

### Cross-References

- Link between related patterns
- Reference concepts from how-to guides
- Link to troubleshooting from other doc types
- Connect installation to next steps

### Consistency Rules

- Use the same structure for similar content types
- Maintain consistent terminology across patterns
- Follow the style guide for all patterns
- Include working, tested examples

---

_These patterns should be adapted based on specific content needs while maintaining the core structure._