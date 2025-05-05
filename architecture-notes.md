# Coder Architecture Reference

This document provides a high-level overview of the Coder backend, CLI, agent system, and documentation layout to support consistent and technically accurate documentation.

---

## 🏛️ Core Components

### Server Layer (`/coderd`)
- HTTP + DRPC server defined in `coderd/coderd.go`
- Manages API routes, authN/authZ, middleware, RBAC
- Handles workspace operations, telemetry, and metrics

### CLI Layer (`/cmd`, `/cli`)
- Entry point: `cmd/coder/main.go`
- Uses command pattern for subcommands
- Supports auth, session management, workspace & template ops

### Database Layer (`/coderd/database`)
- PostgreSQL backend managed with `sqlc`
- Implements retries, transactions, and migrations
- Core tables: users, orgs, workspaces, templates, resources

### Agent System (`/agent`)
- Runs in workspaces to manage connectivity and execution
- Features: SSH, port forwarding, PTY sessions, metrics, script execution
- Lifecycle: `init` → `connect` → `operate` → `shutdown`

### Provisioner System (`/provisionerd`)
- Terraform-driven provisioning backend
- Manages job queue, logs, build lifecycle, status updates

### Networking Stack (`/tailnet`, `/vpn`)
- P2P networking via custom Tailscale-based Tailnet
- Supports NAT traversal, DERP relays, VPN fallback
- Provides secure agent–client tunnels via WireGuard

---

## 🧱 Template & Provisioning System

### Template Architecture
- Templates = Terraform modules with Coder extensions
- Key custom resources:
  - `coder_agent`, `coder_app`, `coder_script`, `coder_parameter`, `coder_metadata`
- Versioned: Each version is immutable and linked to a provisioner job

### Provisioning Workflow
1. **Version upload**: Terraform code added
2. **Parse phase**: Metadata, parameters extracted
3. **Plan phase**: Graph analysis, validation
4. **Apply phase**: Provisioning, state capture, workspace mapping

---

## 🌐 Networking Details

### Tailnet Architecture
- **Coordinator**: Peer connection orchestration
- **Conn**: WireGuard session management and state
- **Tunneling**: Secure connections w/ fallback to DERP

### Security Model
- WireGuard encryption
- DRPC token-based handshake
- Auth scopes for client vs agent

### NAT Traversal
- Auto-detects proxy behavior
- Falls back to WebSockets or DERP
- Monitors connection health + logs state

---

## ⚙️ Agent Lifecycle

1. **Init**: `agent.New()` starts services, sets up PTY, SSH
2. **Connect**: Token exchange → DRPC → manifest fetch → tailnet join
3. **Operate**: Connection handling, metrics, logs
4. **Shutdown**: Graceful termination, shutdown scripts

Agent responsibilities include:
- Shell and port access
- Health checks
- Scripted automation (startup/shutdown)
- Resource monitoring

---

## 📁 Documentation Structure

Docs live in `../coder/docs/`, with sections:
1. `about/` – What Coder is
2. `install/` – Platform install guides
3. `guides/` – End-user guidance
4. `admin/` – Admin + template authoring docs
5. `tutorials/` – Task-based guides, KB
6. `reference/` – CLI + API docs (auto-generated)
7. `contributing/` – Maintainer and contributor guide

The Coder website itself is rendered from `../coder.com/`.

---

## 🔁 Entity Relationships

- **Users → Organizations**: Each user can belong to many orgs
- **Orgs → Templates**: Orgs own templates
- **Templates → Workspaces**: Workspaces are created from template versions
- **Workspaces → Agents**: Agents live in workspaces
- **Agents → Resources**: Agents manage CPU/mem/disk/port/etc.

---

This reference should guide Claude and collaborators to accurately reason about Coder’s internals and reflect the architecture correctly in user-facing documentation.
