# Coder CLI Reference

Comprehensive reference for Coder CLI commands, organized by use case. This serves as the AI's primary source for CLI-related questions.

---

## Template Management

### `coder templates`
List available templates
```bash
coder templates
```

### `coder templates create`
Create a new template from a directory
```bash
coder templates create [template-name] [source-directory]

# Create from current directory
coder templates create my-template .

# Create from GitHub repository
coder templates create my-template https://github.com/user/repo

# Create from specific branch/tag
coder templates create my-template https://github.com/user/repo --ref main
```

**Common Options:**
- `--ref <branch>` - Specify Git branch, tag, or commit
- `--directory <path>` - Subdirectory within the repository
- `--variables-file <file>` - File containing template variables

### `coder templates pull`
Update template from source
```bash
coder templates pull [template-name]
```

### `coder templates push`
Push template changes
```bash
coder templates push [template-name]
```

---

## Workspace Management

### `coder create`
Create a new workspace
```bash
coder create [workspace-name] --template [template-name]

# Create with specific parameters
coder create my-workspace --template docker-template --parameter instance_type=large
```

### `coder start`
Start a workspace
```bash
coder start [workspace-name]
```

### `coder stop`
Stop a workspace
```bash
coder stop [workspace-name]
```

### `coder delete`
Delete a workspace
```bash
coder delete [workspace-name]
```

### `coder list`
List workspaces
```bash
coder list

# List all workspaces (including others')
coder list --all
```

---

## SSH and Access

### `coder ssh`
SSH into a workspace
```bash
coder ssh [workspace-name]

# SSH with specific user
coder ssh [workspace-name] --user root

# Execute command via SSH
coder ssh [workspace-name] -- ls -la
```

### `coder config-ssh`
Configure SSH for workspaces
```bash
coder config-ssh

# Configure for specific workspace
coder config-ssh --workspace [workspace-name]
```

### `coder port-forward`
Forward ports from workspace
```bash
coder port-forward [workspace-name] --tcp 8080:8080

# Forward multiple ports
coder port-forward [workspace-name] --tcp 8080:8080 --tcp 3000:3000
```

---

## Authentication

### `coder login`
Authenticate with Coder deployment
```bash
coder login [deployment-url]

# Login with token
coder login [deployment-url] --token [token]
```

### `coder logout`
Log out of current session
```bash
coder logout
```

---

## File Operations

### `coder stat`
Show workspace connection info
```bash
coder stat [workspace-name]
```

### `coder ping`
Test connectivity to workspace
```bash
coder ping [workspace-name]
```

---

## Common Patterns and Examples

### Creating Template from GitHub Repository
**Question**: "How do I copy a template from a GitHub repo?"
**Answer**: Use `coder templates create` with the GitHub URL:
```bash
coder templates create my-template https://github.com/coder/coder

# For specific subdirectory
coder templates create my-template https://github.com/coder/coder --directory examples/templates/docker

# For specific branch
coder templates create my-template https://github.com/user/repo --ref feature-branch
```

### Working with Template Parameters
```bash
# Create workspace with parameters
coder create dev-env --template kubernetes --parameter cpu=4 --parameter memory=8Gi

# Use variables file
coder templates create my-template . --variables-file vars.yaml
```

### SSH Configuration
```bash
# Configure SSH for all workspaces
coder config-ssh

# Then use regular SSH
ssh coder.my-workspace
```

---

## Documentation Status

### Well Documented
- ✅ Basic workspace operations (create, start, stop, delete)
- ✅ SSH configuration and access
- ✅ Template creation from local directories

### Needs Documentation
- ❌ Template creation from GitHub repositories (common question)
- ❌ Advanced parameter passing
- ❌ Port forwarding examples
- ❌ Troubleshooting connection issues
- ❌ Template versioning and updates

### Common Questions Not in Docs
1. "How do I copy a template from GitHub?" → `coder templates create`
2. "How do I update a template from its source?" → `coder templates pull`
3. "How do I pass parameters when creating a workspace?" → `--parameter` flag
4. "How do I SSH with a specific user?" → `--user` flag
5. "How do I forward multiple ports?" → Multiple `--tcp` flags

---

## AI Assistant Notes

When answering CLI questions:
1. **Check this reference first** for accurate command syntax
2. **Provide working examples** with actual command syntax
3. **Mention relevant flags and options**
4. **Check documentation status** - offer to add missing info
5. **Update this file** when you learn about new commands or options

---

_Last updated: 2025-01-15_
_Source: Coder CLI help output and community questions_