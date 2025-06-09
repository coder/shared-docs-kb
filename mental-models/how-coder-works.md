# How Coder Works: Mental Model

This document provides a high-level mental model of how Coder works internally. Use this to understand the system architecture and component relationships when writing documentation or helping users.

---

## Core Concept

Coder is a **platform for provisioning remote development environments**. Think of it as "infrastructure as code for developer workspaces."

```
Template (Terraform) → Workspace (Infrastructure) → Developer Access
```

---

## The Big Picture

### 1. Templates Define Infrastructure
- **Templates** are Terraform configurations that define workspace infrastructure
- They specify what resources to create (VMs, containers, storage, networking)
- Templates are versioned and can be updated over time
- One template can create many workspaces

### 2. Workspaces Are Live Environments
- **Workspaces** are individual instances created from templates
- Each workspace gets its own isolated infrastructure
- Workspaces have lifecycles: create → start → stop → delete
- Users can have multiple workspaces from different templates

### 3. Agents Enable Access
- **Agents** run inside workspaces to enable connectivity
- They provide secure tunneling without exposing infrastructure
- Agents handle SSH, web apps, port forwarding, and file sync
- The agent is the bridge between Coder server and workspace

### 4. Server Orchestrates Everything
- **Coder server** manages templates, workspaces, users, and policies
- It runs Terraform to provision infrastructure
- Provides web UI, CLI, and API for user interaction
- Handles authentication, authorization, and resource management

---

## Component Relationships

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Developer     │    │   Coder Server   │    │   Workspace     │
│                 │    │                  │    │                 │
│ • CLI/Web UI    │◄──►│ • Templates      │◄──►│ • Agent         │
│ • IDE           │    │ • Provisioner    │    │ • Dev Tools     │
│ • Local Tools   │    │ • Database       │    │ • Applications  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                              │
                              ▼
                       ┌──────────────────┐
                       │  Infrastructure  │
                       │                  │
                       │ • Cloud Provider │
                       │ • Kubernetes     │
                       │ • Docker         │
                       └──────────────────┘
```

---

## Key Mental Models

### Templates Are Blueprints
- Think of templates like Docker images or VM templates
- They define what infrastructure gets created
- Multiple workspaces can be created from one template
- Templates can be updated, and workspaces can be rebuilt

### Workspaces Are Instances
- Each workspace is an isolated environment
- Workspaces have their own compute, storage, and network
- They can be started/stopped like VMs
- Data persistence depends on template configuration

### Agents Are Connectors
- The agent is like an SSH daemon with superpowers
- It runs inside the workspace and connects back to Coder
- Enables secure access without VPNs or exposed ports
- Handles multiple connection types (SSH, web, ports)

### Server Is Mission Control
- Central orchestrator for all Coder operations
- Manages the lifecycle of templates and workspaces
- Provides user interface and API
- Handles security, policies, and resource limits

---

## Data Flow

### Workspace Creation
1. User selects template and provides parameters
2. Coder server validates request and user permissions
3. Provisioner runs Terraform to create infrastructure
4. Agent starts inside workspace and connects to server
5. User can access workspace through various methods

### Daily Usage
1. User starts workspace (if stopped)
2. Agent establishes connection to Coder server
3. User accesses workspace via SSH, web apps, or IDE
4. Agent handles all connectivity and tunneling
5. User stops workspace when done (optional)

### Template Updates
1. Template author updates Terraform configuration
2. New template version is pushed to Coder
3. Existing workspaces can be rebuilt with new version
4. Users get updated infrastructure and tools

---

## Security Model

### Network Security
- Workspaces don't need public IPs or open ports
- All connections go through Coder server
- Agent establishes outbound connection to server
- Traffic is encrypted and authenticated

### Access Control
- Users authenticate with Coder server
- RBAC controls who can create/access workspaces
- Template authors control workspace capabilities
- Audit logs track all user actions

### Isolation
- Each workspace is isolated from others
- Resource limits prevent resource exhaustion
- Network policies can restrict workspace connectivity
- Templates define security boundaries

---

## Resource Management

### Compute Resources
- Templates specify CPU, memory, and storage
- Workspaces can be right-sized for their purpose
- Auto-stop policies save resources when idle
- Resource quotas prevent overuse

### Storage
- Workspace storage can be persistent or ephemeral
- Templates define storage configuration
- Home directories often persist across rebuilds
- Shared storage can be mounted if needed

### Networking
- Workspaces get private networking by default
- Internet access depends on template configuration
- Internal services can be exposed via Coder apps
- Port forwarding enables local development workflows

---

## Common Patterns

### Development Workflows
- **Personal workspaces**: Individual dev environments
- **Project workspaces**: Shared environments for teams
- **Staging workspaces**: Testing and review environments
- **Training workspaces**: Standardized learning environments

### Infrastructure Patterns
- **Container-based**: Fast startup, ephemeral storage
- **VM-based**: Full OS control, persistent storage
- **Kubernetes**: Scalable, cloud-native deployments
- **Hybrid**: Mix of containers and VMs as needed

### Access Patterns
- **SSH**: Terminal access for command-line work
- **Web apps**: Browser-based IDEs and tools
- **Port forwarding**: Local development with remote compute
- **File sync**: Hybrid local/remote development

---

## Troubleshooting Mental Model

When issues occur, think in layers:

1. **User Layer**: CLI, web UI, IDE connections
2. **Server Layer**: Authentication, API, database
3. **Provisioner Layer**: Terraform execution, infrastructure
4. **Agent Layer**: Workspace connectivity, tunneling
5. **Infrastructure Layer**: Cloud provider, networking, compute

Most issues can be isolated to one of these layers, which helps focus troubleshooting efforts.

---

## Key Takeaways for Documentation

- **Templates are central**: Most user tasks involve creating or using templates
- **Workspaces are temporary**: Emphasize proper data persistence patterns
- **Agent connectivity is critical**: Many issues relate to agent connection
- **Security is built-in**: Highlight the secure-by-default architecture
- **Flexibility is key**: Coder adapts to many different infrastructure patterns

This mental model should inform how you structure documentation, explain concepts, and help users understand how Coder fits into their workflows.

---

_This mental model should be updated as Coder's architecture evolves._