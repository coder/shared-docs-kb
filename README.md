# AI Memory System for Coder Documentation & Support

## For Human Contributors

This repository serves as a **persistent memory system** for AI assistants working on Coder documentation and user support. When you start a new AI chat session (like `@blink` in Slack), use this prompt to give the AI access to its "memory":

```md
You are Blink, an AI assistant with persistent memory for Coder documentation and support. You have access to comprehensive knowledge about Coder stored in the shared-docs-kb repository.

## Your Knowledge Base Includes:
- Complete Coder architecture and component understanding
- CLI commands, options, and usage patterns
- Documentation structure and current content
- Common user questions and solutions
- Repository ecosystem and relationships
- Style guides and contribution workflows

## Your Primary Functions:
1. **Answer Questions**: Provide accurate answers by referencing official docs at https://coder.com/docs
2. **Identify Documentation Gaps**: Detect when information is missing from official docs
3. **Facilitate Contributions**: Help users contribute to the official Coder documentation
4. **Maintain Knowledge**: Update your reference knowledge about where information exists

## Question-Answering Workflow:
1. **Search your knowledge** for the answer in these files:
   - `cli-reference.md` - Complete CLI command documentation
   - `common-questions.md` - Frequently asked questions and answers
   - `architecture-notes.md` - Technical system understanding
   - `repo-navigation.md` - Repository and code location guide

2. **Provide comprehensive answers** including:
   - Direct answer with reference to official docs
   - Links to specific pages at https://coder.com/docs
   - Code examples from official documentation
   - Context about where to find more information

3. **Identify documentation gaps** by checking:
   - Is this information available at https://coder.com/docs?
   - Is the official documentation complete and easy to find?
   - Would this help other users if added to official docs?

4. **Offer to contribute** when gaps are found:
   - "I notice this isn't documented at https://coder.com/docs. Would you like me to help create a contribution?"
   - Suggest specific locations in the official docs
   - Offer to help create a PR to the main Coder repository

## Memory Management:
- Update `common-questions.md` with new questions you encounter
- Add missing CLI commands to `cli-reference.md`
- Track documentation gaps in `documentation-gaps.md`
- Log significant interactions in `ai-project-notes.md`

## Response Style:
- Be helpful and accurate
- Provide working examples
- Explain context and reasoning
- Offer to improve documentation when gaps are found
- Use Coder terminology consistently

Start by reading your current knowledge state, then help with whatever questions come up.
```

**Important**: This repository should be cloned alongside your main Coder repositories. The AI will read from and write to these files to maintain persistent knowledge across sessions.

---

## What This Repository Does

This is a **living memory system** that enables AI assistants to:

1. **Answer user questions** accurately with working examples
2. **Identify documentation gaps** through user interactions
3. **Facilitate documentation contributions** by offering to add missing information
4. **Learn continuously** from user questions and codebase changes
5. **Maintain consistency** across all documentation and support interactions

Unlike traditional knowledge bases, this system is designed to be **actively maintained by AI assistants** and **improved through user interactions**.

---

## Memory System Structure

```text
shared-docs-kb/
├── README.md                      # This guide for human contributors
├── cli-reference.md               # Complete CLI command documentation
├── common-questions.md            # FAQ with answers and documentation status
├── documentation-gaps.md          # Tracked missing or incomplete documentation
├── repo-navigation.md             # Guide to Coder's public repositories
├── style-guide.md                # Documentation standards and conventions
├─��� architecture-notes.md         # Technical understanding of Coder systems
├── ai-project-notes.md           # Session logs and learning history
├── templates/
│   ├── doc-template.md           # Documentation structure templates
│   ├── snippet-library.md        # Reusable code/config blocks
│   └── session-template.md       # Template for AI session tracking
├── integration/
│   ├── claude-code-config.md     # Claude-specific behavior guidelines
│   ├── chatgpt-config.md         # ChatGPT workflow configuration
│   ├── slack-workflow.md         # Guidelines for Slack Q&A interactions
│   └── memory-management.md      # Guidelines for AI memory updates
```

### Key Relationships
- **Main Coder repo**: `../coder/` (source code and primary docs)
- **Documentation content**: `../coder/docs/` 
- **Image assets**: `../coder/docs/images/`
- **Website code**: `../coder.com/` (rendering and site structure)
- **This memory system**: `../shared-docs-kb/` (AI persistent memory)

---

## How AI Q&A Works

### Example Interaction Flow

**User in Slack**: `@blink what option do I use with coder cli to copy a template from a github repo`

**AI Response Process**:
1. **Search knowledge**: Check `common-questions.md` for official doc references
2. **Provide answer**: 
   ```
   To copy a template from a GitHub repo, use:
   `coder templates create my-template https://github.com/user/repo`
   
   For complete documentation on template creation, see:
   https://coder.com/docs/templates/creating-templates
   ```
3. **Check documentation**: Notice GitHub examples aren't clear in official docs
4. **Identify gap**: This common pattern needs better examples in official docs
5. **Offer contribution**: "I notice the official docs could use clearer GitHub examples. Would you like me to help create a contribution to improve this section?"

### Documentation Contribution Flow

When user says "Yes" to documentation help:
1. **AI identifies specific gap** in official documentation
2. **AI creates contribution** to the main Coder repository docs
3. **AI submits PR** to https://github.com/coder/coder/docs
4. **AI updates memory** with reference to new official documentation

---

## For Different Use Cases

### Slack Support (`@blink` mentions)
- **Instant answers** to common questions
- **Working examples** with proper syntax
- **Documentation gap identification** and contribution offers
- **Knowledge base updates** from interactions

### Documentation Writing Sessions
- **Persistent memory** of style preferences and patterns
- **Architecture understanding** for technical accuracy
- **Cross-session learning** and decision tracking
- **Template and snippet libraries** for consistency

### Community Contributions
- **Gap identification** from user questions
- **Contribution facilitation** with proper templates
- **Quality assurance** through style guide adherence
- **Knowledge sharing** across contributors

---

## Memory Update Workflow

### After Each User Interaction
1. **Update `common-questions.md`** with new Q&A patterns
2. **Update `cli-reference.md`** with command usage examples
3. **Track gaps** in `documentation-gaps.md`
4. **Log insights** in `ai-project-notes.md`

### Documentation Contribution Process
1. **Identify gap** through user question
2. **Offer to contribute** with specific location suggestion
3. **Create content** following established style guide
4. **Submit PR** with clear description and examples
5. **Update memory** with new documentation

### Quality Control
- **Validate technical accuracy** against actual codebase
- **Check consistency** with existing documentation
- **Follow style guidelines** for all contributions
- **Cross-reference** related information

---

## Getting Started

### For Human Contributors
1. Clone this repository alongside your Coder workspace:
   ```bash
   git clone git@github.com:coder/shared-docs-kb.git
   ```

2. Use the provided prompt when starting AI sessions

3. Review AI updates to memory files and commit valuable changes

4. Monitor documentation gaps and contribution opportunities

### For AI Assistants
1. **Read current memory state** from all knowledge files
2. **Answer user questions** using comprehensive knowledge
3. **Identify and track** documentation gaps
4. **Offer contributions** when gaps are found
5. **Update memory** with new learnings

---

## Current Knowledge State

**CLI Commands Documented**: 15+ core commands with examples  
**Common Questions Tracked**: 12 with documentation status  
**Documentation Gaps Identified**: 8 high-priority areas  
**Repository Coverage**: 50+ public Coder repositories mapped  
**Last Updated**: 2025-01-15

### High-Impact Areas
- ✅ **Well Covered**: Basic workspace operations, authentication, installation
- ⚠️ **Partially Covered**: Template creation, IDE integration, troubleshooting
- ❌ **Missing**: GitHub template workflows, multi-cloud patterns, performance optimization

---

## Contributing to the Memory System

### For Human Contributors
1. **Review AI updates** for accuracy before merging
2. **Add domain expertise** that AI might miss
3. **Validate technical content** against actual codebase
4. **Provide feedback** on AI response quality

### For AI Assistants
1. **Always check existing memory** before responding
2. **Update memory incrementally** with new learnings
3. **Track conversation patterns** for documentation insights
4. **Maintain technical accuracy** through code verification

### Git Practices
1. Use descriptive commit messages explaining what was learned
2. Include session IDs when relevant
3. Keep memory updates focused and atomic
4. Tag human reviewers for significant changes

---

**Maintainer**: Edward Angert  
**Purpose**: AI persistent memory for Coder documentation and support  
**Status**: Active learning and contribution system  
**Integration**: Slack, documentation workflows, community support