# Common Questions Reference

This file tracks frequently asked questions about Coder and maps them to official documentation at https://coder.com/docs. When information is missing from official docs, we track it as a contribution opportunity.

**Purpose**: Help AI assistants quickly find the right official documentation to reference when answering questions.

---

## CLI Questions

### Q: "What option do I use with coder cli to copy a template from a github repo?"
**Official Documentation**: https://coder.com/docs/templates/creating-templates  
**Quick Answer**: `coder templates create my-template https://github.com/user/repo`  
**Documentation Status**: ❌ GitHub template creation not clearly documented  
**Gap**: Official docs don't clearly show GitHub repo usage  
**Suggested Enhancement**: Add GitHub examples to existing template creation docs  
**Priority**: High (very common question)

### Q: "How do I update a template from its GitHub source?"
**Answer**: Use `coder templates pull`:
```bash
coder templates pull my-template
```
This fetches the latest changes from the original source repository.

**Documentation Status**: ❌ Missing from official docs  
**Suggested Location**: `/docs/templates/managing-templates.md`  
**Priority**: Medium

### Q: "How do I pass parameters when creating a workspace?"
**Answer**: Use the `--parameter` flag:
```bash
coder create my-workspace --template my-template --parameter cpu=4 --parameter memory=8Gi

# Or use a variables file:
coder create my-workspace --template my-template --variables-file vars.yaml
```

**Documentation Status**: ✅ Partially documented  
**Needs Enhancement**: More examples and common parameter patterns  
**Priority**: Medium

---

## Template Questions

### Q: "How do I make my template work with different cloud providers?"
**Answer**: Use Terraform variables and conditional resources:
```hcl
variable "cloud_provider" {
  description = "Cloud provider (aws, gcp, azure)"
  type        = string
  default     = "aws"
}

resource "aws_instance" "dev" {
  count = var.cloud_provider == "aws" ? 1 : 0
  # AWS configuration
}

resource "google_compute_instance" "dev" {
  count = var.cloud_provider == "gcp" ? 1 : 0
  # GCP configuration
}
```

**Documentation Status**: ❌ Missing from official docs  
**Suggested Location**: `/docs/templates/multi-cloud-templates.md`  
**Priority**: High

### Q: "How do I add VS Code extensions to my template?"
**Answer**: Use the `coder_app` resource with VS Code:
```hcl
resource "coder_app" "code-server" {
  agent_id     = coder_agent.main.id
  slug         = "code-server"
  display_name = "VS Code"
  url          = "http://localhost:13337/?folder=/home/coder"
  icon         = "/icon/code.svg"
  subdomain    = false
  share        = "owner"

  healthcheck {
    url       = "http://localhost:13337/healthz"
    interval  = 5
    threshold = 6
  }
}
```

For extensions, install them in your Dockerfile or startup script:
```bash
# In Dockerfile or startup script
code-server --install-extension ms-python.python
code-server --install-extension golang.go
```

**Documentation Status**: ✅ Partially documented  
**Needs Enhancement**: Extension installation patterns  
**Priority**: High

---

## Workspace Questions

### Q: "Why can't I connect to my workspace?"
**Answer**: Check these common issues:
1. **Agent status**: `coder stat workspace-name`
2. **Network connectivity**: `coder ping workspace-name`
3. **SSH configuration**: `coder config-ssh`
4. **Workspace state**: `coder list` (should show "Running")

Common fixes:
```bash
# Reconfigure SSH
coder config-ssh

# Restart workspace
coder stop workspace-name
coder start workspace-name

# Check logs
coder logs workspace-name
```

**Documentation Status**: ❌ Missing comprehensive troubleshooting guide  
**Suggested Location**: `/docs/troubleshooting/workspace-connectivity.md`  
**Priority**: High

### Q: "How do I access a web app running in my workspace?"
**Answer**: Use `coder_app` resource in your template:
```hcl
resource "coder_app" "my-app" {
  agent_id     = coder_agent.main.id
  slug         = "my-app"
  display_name = "My Application"
  url          = "http://localhost:3000"
  icon         = "/icon/web.svg"
  subdomain    = true
  share        = "owner"
}
```

Or use port forwarding:
```bash
coder port-forward workspace-name --tcp 3000:3000
```

**Documentation Status**: ✅ Well documented  
**Location**: `/docs/user-guides/workspace-apps.md`

---

## Installation & Setup Questions

### Q: "How do I install Coder on Kubernetes?"
**Answer**: Use Helm chart:
```bash
helm repo add coder-v2 https://helm.coder.com/v2
helm repo update
helm install coder coder-v2/coder
```

**Documentation Status**: ✅ Well documented  
**Location**: `/docs/install/kubernetes.md`

### Q: "How do I set up external authentication (OIDC)?"
**Answer**: Configure OIDC in Coder deployment:
```yaml
# In Helm values or environment
OIDC_ISSUER_URL: "https://your-provider.com"
OIDC_CLIENT_ID: "your-client-id"
OIDC_CLIENT_SECRET: "your-client-secret"
```

**Documentation Status**: ✅ Well documented  
**Location**: `/docs/admin/auth.md`

---

## Performance Questions

### Q: "My workspace is slow, how do I optimize it?"
**Answer**: Check these areas:
1. **Resource allocation**: Increase CPU/memory in template
2. **Disk I/O**: Use faster storage classes
3. **Network**: Check latency to Coder deployment
4. **Agent overhead**: Monitor agent resource usage

```hcl
# Increase resources in template
resource "kubernetes_deployment" "main" {
  spec {
    template {
      spec {
        container {
          resources {
            requests = {
              cpu    = "2"
              memory = "4Gi"
            }
            limits = {
              cpu    = "4"
              memory = "8Gi"
            }
          }
        }
      }
    }
  }
}
```

**Documentation Status**: ❌ Missing performance optimization guide  
**Suggested Location**: `/docs/admin/performance-optimization.md`  
**Priority**: Medium

---

## Documentation Gap Analysis

### High Priority Gaps
1. **Template creation from GitHub** - Very common question, no clear docs
2. **Multi-cloud template patterns** - Enterprise need, not documented
3. **Workspace connectivity troubleshooting** - Support burden, needs comprehensive guide
4. **VS Code extension management** - Developer workflow, partially documented

### Medium Priority Gaps
1. **Template versioning and updates** - Operational need
2. **Performance optimization** - Scaling concern
3. **Advanced parameter patterns** - Power user feature

### Well Documented Areas
1. **Basic workspace operations** - Good coverage
2. **Installation methods** - Comprehensive
3. **Authentication setup** - Well covered
4. **Basic template creation** - Adequate

---

## AI Assistant Guidelines

When answering questions:
1. **Check this file first** for known answers
2. **Provide complete, working examples**
3. **Note documentation status** in your response
4. **Offer to add missing documentation** when gaps are identified
5. **Update this file** with new questions you encounter
6. **Cross-reference** with `cli-reference.md` for command syntax

### Response Template for Documentation Gaps
```
[Provide the answer with examples]

I notice this information isn't clearly documented in the official Coder docs. This seems like it would be helpful for other users. Would you like me to:
1. Add this to the documentation at [suggested location]
2. Create a PR with this information
3. Add it to the FAQ section

This would help other users who have the same question!
```

---

_Last updated: 2025-01-15_  
_Questions tracked: 12_  
_Documentation gaps identified: 8_