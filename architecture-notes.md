# Coder Architecture Reference

This document provides a comprehensive overview of the Coder codebase architecture and design to serve as a reference for future documentation work.

---

## Core Components

### Server Layer (`/coderd`)
- Core backend implementation in `coderd/coderd.go`
- HTTP and DRPC server implementation
- Manages API routes and middleware
- Handles entitlements, authentication, and authorization
- Implements RBAC (Role-Based Access Control)
- Processes workspace operations via provisioners
- Manages metrics, telemetry, and health checks
- Handles prebuilt workspaces reconciliation

### CLI Layer (`/cmd` and `/cli`)
- Entry point through `cmd/coder/main.go`
- Uses a command pattern with subcommands for various operations
- Handles authentication, session management, and command execution
- Implements numerous commands for workspace management, templates, SSH, etc.
- Provides user-facing interfaces for all Coder operations

### Database Layer (`/coderd/database`)
- PostgreSQL database connection and query management
- Uses SQL code generation via sqlc
- Implements transaction support with retries
- Schema migrations and database models
- Custom queriers for specialized operations
- Core tables: users, workspaces, organizations, templates, resources

### Agent System (`/agent`)
- Runs inside workspace environments
- Manages workspace connectivity via Tailnet
- Handles SSH access and port forwarding
- Manages PTY (terminal) connections
- Monitors resource usage and health
- Executes scripts and commands within workspaces
- Supports container operations and devcontainer functionality

### Provisioner System (`/provisionerd`)
- Executes Terraform to provision infrastructure
- Handles job queue management
- Processes template creation and updates
- Manages workspace build lifecycles
- Reports provisioning logs and status

### Networking (`/tailnet` and `/vpn`)
- Custom implementation based on Tailscale's Tailnet
- Provides secure peer-to-peer connections between clients and workspaces
- Handles NAT traversal and fallback relay connections
- Implements VPN capabilities for network access
- Manages connection coordination and DERP servers

---

## Template & Provisioning System

### Template Architecture
- Templates are implemented as Terraform code
- The system parses Terraform files to extract metadata, resources, and parameters
- Coder extends Terraform with custom providers (terraform-provider-coder)
- Key resources in the provider include:
  - `coder_agent`: Defines the Coder agent that runs in workspaces
  - `coder_app`: Defines applications accessible through the workspace
  - `coder_metadata`: Attaches metadata to resources for display and monitoring
  - `coder_parameter`: Defines customizable parameters for templates
  - `coder_script`: Defines scripts to run at specified lifecycle events
- Resource lifecycle management:
  - Ephemeral: Uses `count = data.coder_workspace.me.start_count` to control start/stop
  - Persistent: Uses `lifecycle { ignore_changes = all }` to protect data

### Template Versioning
- Templates maintain versions with immutable infrastructure definitions
- Each version has a job ID linking to the provisioner job that created it
- Templates can have an "active" version that's used for new workspace creation
- Versions can be archived when no longer needed
- Version history is maintained for auditing and rollback

### Provisioning Workflow
1. **Template version creation**: User uploads Terraform code that defines infrastructure
2. **Parse phase**: System extracts parameters, resources, and external auth requirements
3. **Plan phase**: 
   - Terraform plan executes to determine required changes
   - Resource graphs are analyzed
   - Required parameters are validated
4. **Apply phase**:
   - Terraform provisions the actual resources
   - State is captured and stored
   - Resources are mapped to their Coder representations

---

## Networking Architecture

### Tailnet Implementation
1. **Coordinator**: The central component that manages network topology, handling discovery and connection establishment between peers
2. **Conn**: Represents a Wireguard connection with capabilities for managing addresses, keys, routing, peer updates, and connection status
3. **Tunneling**: Enables secure point-to-point connections with DERP (Designated Encrypted Relay for Packets) servers for NAT traversal

### Connection Security
- WireGuard encryption for all traffic
- Authentication via coordinator authorization
- Distinct roles (client vs agent) with different permissions
- Secure resumable connections

### NAT Traversal
- Automatically detects network conditions
- Uses DERP servers as fallback when direct connections fail
- Supports forced websockets for problematic proxies
- Implements connection health monitoring and recovery

---

## Agent Architecture

### Agent Lifecycle
1. **Initialization**:
   - Agent starts with `agent.New()`
   - Creates SSH server, reconnecting PTY server
   - Begins connection attempt loop

2. **Connection**:
   - Exchanges token with server
   - Establishes DRPC connection
   - Fetches manifest (configuration)
   - Creates tailnet connection
   - Sets up coordination and services

3. **Operation**:
   - Reports agent lifecycle state changes
   - Collects and reports metadata
   - Handles incoming client connections
   - Monitors resource usage

4. **Shutdown**:
   - Graceful termination of connections
   - Running of shutdown scripts
   - Reporting final lifecycle state

### Agent Features
- SSH access to workspaces
- Port forwarding (local and remote)
- Application proxying
- Health monitoring
- Metrics collection
- Script execution (startup, shutdown, cron)
- Environment variable handling

---

## Documentation Structure

The documentation is located in `../coder/docs/` with the following high-level sections:

1. **About** - Introduction to Coder and its purpose
2. **Install** - Installation guides for various platforms
3. **User Guides** - End-user documentation for using Coder
4. **Administration** - Guides for template and deployment administrators
5. **Contributing** - Guide for contributing to Coder
6. **Tutorials** - Coder knowledgebase and specific how-to guides
7. **Reference** - API and CLI command reference

The website code is in `../coder.com/` and integrates with the documentation from the main codebase.

---

## Entity Relationships

- **User → Organizations**: Users can belong to multiple organizations
- **Organization → Templates**: Templates belong to organizations
- **Templates → Workspaces**: Workspaces are created from templates
- **Workspaces → Agents**: Workspaces contain one or more agents
- **Agent → Resources**: Agents monitor and manage resources

This architecture provides a flexible, secure system for remote development environments that can integrate with various infrastructure providers while maintaining consistent user experience.

---

## Community and Premium Features

Coder follows a commercial open-source model where core functionality is available in the Community Edition (AGPL licensed), while advanced features are part of the Premium Edition (proprietary licensed). Here's how this is implemented in the codebase:

### Implementation Pattern

1. **Interface-Based Design**: Most premium features follow an interface-based design pattern:
   - Interfaces are defined in the Community Edition
   - No-op implementations are provided in the Community Edition (in files often named `noop.go`)
   - Full implementations exist in the Premium Edition codebase

2. **Feature Flag System**: Premium features are gated by:
   - License checks
   - Entitlement verification
   - Experiment flags for beta features

3. **Code Organization**:
   - Premium features are typically implemented in the `/enterprise/` directory
   - Premium functionality may be referenced but not implemented in the main codebase
   - Core components often have hooks where premium features can integrate

### Examples of Premium Features

- **Prebuilt workspaces**: Implemented in `/coderd/prebuilds/` (interface) and `/enterprise/coderd/prebuilds/` (implementation)
- **Organizations**: Multi-tenancy capabilities within a single Coder deployment
- **Advanced RBAC**: Extended role-based access controls beyond the basic system
- **Quota Management**: Advanced resource quota systems for workspaces
- **Identity Provider Synchronization**: Automatic syncing with external identity providers
- **Audit Logging**: Enhanced logging capabilities for compliance

This separation allows the Community Edition to function as a complete product while premium features are properly gated for Premium Edition customers.

---

## Prebuilt Workspaces Implementation

### Core Components and Architecture

The prebuilt workspaces feature follows Coder's premium feature pattern:
- Core interfaces are defined in `/coderd/prebuilds/` 
- Implementation exists in the premium codebase in `/enterprise/coderd/prebuilds/`

### Key Components

1. **Reconciliation System**:
   - Uses a declarative approach with a reconciliation loop (similar to Kubernetes)
   - Maintains the desired number of prebuilt workspaces for each template preset
   - Handles creation, deletion, and state management of prebuilds

2. **Data Structures**:
   - `GlobalSnapshot`: Captures the state of all prebuilds across templates
   - `PresetSnapshot`: Filtered view for a specific template preset
   - `ReconciliationState`: Processed metrics about desired vs actual prebuild counts
   - `ReconciliationActions`: Defines actions needed to reach desired state

3. **Workspace Lifecycle**:
   - Prebuilts are owned by a system user (`prebuilds` with ID `c42fdf75-3097-471c-8c33-fb52454d81c0`)
   - "Claiming" transfers ownership from the system user to a regular user
   - Eligible prebuilds must be running with agents in ready state

4. **Key Operations**:
   - Periodic reconciliation ensures desired number of prebuilds exist
   - Backoff mechanism handles failed builds to prevent endless retries
   - Deletion of prebuilds for inactive template versions
   - Random name generation for prebuilts

The implementation demonstrates sophisticated state management, handling edge cases like template version changes, failures, and race conditions while maintaining the desired prebuild count for each template preset.