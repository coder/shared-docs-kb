# Documentation Gaps & Improvement Opportunities

This file tracks missing or incomplete documentation that AI assistants have identified through user questions and interactions.

---

## High Priority Gaps

### 1. Template Creation from GitHub Repositories
**Gap**: No clear documentation on creating templates from GitHub repos  
**User Question**: "What option do I use with coder cli to copy a template from a github repo?"  
**Frequency**: Very High  
**Impact**: Blocks new users from using community templates  

**Suggested Solution**:
- Add section to `/docs/templates/creating-templates.md`
- Include examples with different GitHub scenarios
- Cover subdirectories, branches, and authentication

**Content Outline**:
```markdown
## Creating Templates from GitHub

### Basic GitHub Template
coder templates create my-template https://github.com/user/repo

### From Subdirectory
coder templates create my-template https://github.com/user/repo --directory examples/docker

### From Specific Branch
coder templates create my-template https://github.com/user/repo --ref feature-branch

### Private Repositories
# Authentication methods and examples
```

### 2. Comprehensive Troubleshooting Guide
**Gap**: No centralized troubleshooting documentation  
**User Questions**: "Why can't I connect to my workspace?", "My workspace won't start"  
**Frequency**: High  
**Impact**: High support burden, user frustration  

**Suggested Solution**:
- Create `/docs/troubleshooting/` directory
- Add workspace connectivity guide
- Include common error messages and solutions

### 3. Multi-Cloud Template Patterns
**Gap**: No guidance on creating cloud-agnostic templates  
**User Question**: "How do I make my template work with different cloud providers?"  
**Frequency**: Medium  
**Impact**: Enterprise adoption blocker  

**Suggested Solution**:
- Add `/docs/templates/multi-cloud-patterns.md`
- Include Terraform conditional patterns
- Provide examples for AWS, GCP, Azure

---

## Medium Priority Gaps

### 4. Template Versioning and Updates
**Gap**: No documentation on template lifecycle management  
**User Questions**: "How do I update a template?", "How do I version templates?"  
**Frequency**: Medium  
**Impact**: Operational complexity  

**Suggested Solution**:
- Add section to `/docs/templates/managing-templates.md`
- Cover `coder templates pull` workflow
- Document versioning strategies

### 5. Performance Optimization Guide
**Gap**: No performance tuning documentation  
**User Question**: "My workspace is slow, how do I optimize it?"  
**Frequency**: Medium  
**Impact**: User experience degradation  

**Suggested Solution**:
- Create `/docs/admin/performance-optimization.md`
- Cover resource allocation, storage, networking
- Include monitoring and debugging tips

### 6. Advanced VS Code Integration
**Gap**: Limited documentation on VS Code extension management  
**User Question**: "How do I add VS Code extensions to my template?"  
**Frequency**: Medium  
**Impact**: Developer workflow friction  

**Suggested Solution**:
- Enhance `/docs/user-guides/ides.md`
- Add extension installation patterns
- Cover workspace-specific configurations

---

## Low Priority Gaps

### 7. Advanced Parameter Patterns
**Gap**: Limited examples of complex template parameters  
**User Question**: "How do I create conditional parameters?"  
**Frequency**: Low  
**Impact**: Power user limitation  

### 8. Custom Agent Configurations
**Gap**: No documentation on advanced agent setup  
**User Question**: "How do I customize the Coder agent?"  
**Frequency**: Low  
**Impact**: Advanced use case blocker  

---

## Documentation Quality Issues

### Incomplete Sections
1. **CLI Reference**: Missing many command examples
2. **Template Examples**: Limited real-world scenarios
3. **Error Messages**: No error code reference
4. **API Documentation**: Incomplete endpoint coverage

### Outdated Content
1. **Installation guides**: Some cloud provider steps outdated
2. **Template examples**: Using older Terraform patterns
3. **Screenshots**: UI has changed since capture

---

## Contribution Opportunities

### Quick Wins (1-2 hours)
- [ ] Add GitHub template creation examples
- [ ] Create CLI command cheat sheet
- [ ] Add common error messages and solutions
- [ ] Update outdated screenshots

### Medium Effort (1-2 days)
- [ ] Write comprehensive troubleshooting guide
- [ ] Create multi-cloud template examples
- [ ] Document performance optimization patterns
- [ ] Enhance VS Code integration guide

### Large Projects (1+ weeks)
- [ ] Complete CLI reference documentation
- [ ] Create interactive troubleshooting tool
- [ ] Build template gallery with examples
- [ ] Develop video tutorial series

---

## AI Assistant Workflow

When identifying documentation gaps:

1. **Record the gap** in this file with:
   - User question that revealed the gap
   - Frequency estimate
   - Impact assessment
   - Suggested solution

2. **Offer immediate help** to the user:
   - Provide the answer based on your knowledge
   - Explain where the information should be documented
   - Offer to create the documentation

3. **Track patterns** in user questions:
   - Update frequency estimates
   - Note related questions
   - Identify documentation themes

4. **Prioritize contributions**:
   - High frequency + High impact = High priority
   - Consider user journey and onboarding flow
   - Focus on areas that reduce support burden

---

## Metrics

**Total Gaps Identified**: 8  
**High Priority**: 3  
**Medium Priority**: 3  
**Low Priority**: 2  

**Most Common Question Types**:
1. CLI usage (40%)
2. Template creation (25%)
3. Troubleshooting (20%)
4. Configuration (15%)

**Documentation Coverage**:
- ✅ Well covered: Installation, basic operations, authentication
- ⚠️ Partially covered: Templates, IDE integration, admin tasks
- ❌ Missing: Troubleshooting, advanced patterns, performance

---

_Last updated: 2025-01-15_  
_Gaps tracked: 8_  
_Contributions suggested: 12_