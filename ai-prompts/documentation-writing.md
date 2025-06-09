# AI Prompts for Documentation Writing

Optimized prompts for creating, editing, and improving Coder documentation. Use these prompts along with the knowledge base files for best results.

---

## General Documentation Writing

### Creating New Documentation
```
You are writing documentation for Coder, the open-source platform for remote development environments. 

Task: Create documentation for [TOPIC]

Requirements:
1. Follow the Coder documentation style guide strictly
2. Use the appropriate content pattern for this type of documentation
3. Include working, tested examples
4. Reference official docs at https://coder.com/docs when relevant
5. Use Coder-specific terminology consistently

Context from knowledge base:
- How Coder works mentally
- Documentation standards and patterns
- Common user workflows and pain points

Structure the content to be:
- Scannable with clear headings
- Actionable with step-by-step instructions
- Complete with prerequisites and verification steps
- Helpful with troubleshooting guidance

Do not use emojis in headings or list items. Focus on clarity and technical accuracy.
```

### Editing Existing Documentation
```
You are improving existing Coder documentation.

Task: Review and improve the following documentation

Improvement areas to focus on:
1. Style guide compliance (formatting, tone, terminology)
2. Content completeness (missing steps, examples, context)
3. Technical accuracy (commands, configurations, workflows)
4. User experience (clarity, organization, helpful details)
5. Cross-references (links to related documentation)

Use the Coder knowledge base to:
- Ensure technical accuracy against how Coder actually works
- Apply consistent terminology and patterns
- Add missing context that users need
- Improve examples with real-world scenarios

Maintain the existing structure unless reorganization significantly improves usability.
```

---

## Specific Documentation Types

### How-To Guides
```
Create a how-to guide for Coder that follows this structure:

1. Brief description of what this accomplishes
2. Prerequisites (what users need before starting)
3. Step-by-step instructions with commands and examples
4. Verification steps to confirm success
5. Troubleshooting for common issues
6. Next steps or related tasks

Requirements:
- Every command must be tested and accurate
- Include expected output for key commands
- Explain what each step accomplishes
- Use the imperative mood ("Create a file" not "You should create")
- Link to related documentation
- Address the most common user path first, then variations

Focus on practical, actionable guidance that gets users to their goal efficiently.
```

### Reference Documentation
```
Create reference documentation for [COMMAND/FEATURE] that includes:

1. Brief description of purpose
2. Syntax with all parameters
3. Parameter table with types, requirements, and descriptions
4. Multiple examples from basic to advanced
5. Related commands or features
6. Common error messages and solutions

Format requirements:
- Use tables for parameters and options
- Include working code examples with language tags
- Show both successful and error scenarios
- Link to conceptual documentation for context
- Maintain alphabetical or logical ordering

This should be comprehensive enough that users don't need to look elsewhere for syntax details.
```

### Troubleshooting Guides
```
Create a troubleshooting guide for [PROBLEM AREA] that helps users diagnose and fix issues.

Structure:
1. Quick diagnosis steps (commands to run first)
2. Common issues with symptoms, causes, and solutions
3. Advanced troubleshooting for complex scenarios
4. When to escalate or get additional help
5. Prevention tips to avoid future issues

For each issue include:
- Clear symptoms (what the user sees)
- Root cause explanation
- Step-by-step solution with commands
- How to verify the fix worked

Use the Coder mental model to help users understand why issues occur and how the fix addresses the root cause.
```

---

## Content Enhancement Prompts

### Adding Examples
```
Improve this documentation by adding practical examples.

For each concept or instruction:
1. Add a basic example that most users will need
2. Add an advanced example for complex scenarios
3. Include realistic parameter values and configurations
4. Show expected output when helpful
5. Explain what each example demonstrates

Examples should:
- Use realistic names and values (not "foo", "bar", "example")
- Work in a real Coder environment
- Progress from simple to complex
- Cover common variations and edge cases

Focus on examples that users can copy, paste, and adapt for their needs.
```

### Improving Clarity
```
Rewrite this documentation to be clearer and more user-friendly.

Improvements to make:
1. Simplify complex sentences
2. Define technical terms on first use
3. Add context for why steps are necessary
4. Reorganize information in logical order
5. Remove unnecessary jargon
6. Add transitions between sections

Maintain technical accuracy while making the content accessible to users who may be new to Coder or the specific feature.

Use active voice and imperative mood for instructions. Explain the "why" behind important steps.
```

### Cross-Reference Optimization
```
Improve the cross-references and links in this documentation.

Add links to:
1. Prerequisites mentioned in the content
2. Related concepts that provide helpful context
3. Next steps or follow-up tasks
4. Troubleshooting guides for common issues
5. Reference documentation for commands used

Link guidelines:
- Use descriptive link text (not "click here")
- Link to specific sections when relevant
- Prefer official docs at https://coder.com/docs
- Ensure all links are accurate and current

Create a logical web of related information that helps users discover what they need.
```

---

## Quality Assurance Prompts

### Technical Accuracy Review
```
Review this Coder documentation for technical accuracy.

Check:
1. Command syntax and parameters
2. Configuration examples and values
3. Workflow steps and order
4. Expected outputs and results
5. Compatibility with current Coder version

Use the Coder mental model and architecture knowledge to verify:
- Commands work as described
- Configurations are valid
- Workflows align with how Coder actually operates
- Examples use realistic scenarios

Flag any inaccuracies and suggest corrections with proper syntax and examples.
```

### Style Guide Compliance
```
Review this documentation for compliance with the Coder style guide.

Check:
1. Markdown formatting (headings, lists, code blocks)
2. Terminology consistency
3. Tone and voice
4. Link formatting and descriptions
5. Image alt text and references

Specific items to verify:
- No emojis in headings or list items
- Code blocks have language specified
- Consistent use of Coder terminology
- Proper heading hierarchy
- Active voice and imperative mood for instructions

Make corrections to align with established standards while preserving the content's meaning.
```

### Completeness Review
```
Review this documentation for completeness and user experience.

Evaluate:
1. Are prerequisites clearly stated?
2. Are all necessary steps included?
3. Are examples complete and working?
4. Is troubleshooting guidance provided?
5. Are next steps or related tasks mentioned?

User experience considerations:
- Can a new user follow this successfully?
- Are common questions anticipated and answered?
- Is the content organized logically?
- Are there gaps that would cause confusion?

Suggest additions or reorganization to improve the user experience.
```

---

## Specialized Prompts

### API Documentation
```
Create API documentation for [ENDPOINT/FEATURE] that includes:

1. Endpoint description and purpose
2. HTTP method and URL pattern
3. Authentication requirements
4. Request parameters and body schema
5. Response format and status codes
6. Code examples in multiple languages
7. Error responses and troubleshooting

Format as OpenAPI/Swagger compatible where possible. Include realistic examples that developers can test immediately.
```

### Template Documentation
```
Document this Coder template with:

1. Template overview and use cases
2. Infrastructure components created
3. Required parameters and their purposes
4. Optional configurations and customizations
5. Included tools and applications
6. Workspace capabilities and limitations
7. Maintenance and update procedures

Help users understand what they get with this template and how to customize it for their needs.
```

### Migration Guides
```
Create a migration guide for [SCENARIO] that includes:

1. Overview of what's changing and why
2. Pre-migration preparation steps
3. Step-by-step migration process
4. Verification and testing procedures
5. Rollback procedures if needed
6. Common issues and solutions
7. Post-migration optimization

Focus on minimizing downtime and ensuring data safety throughout the process.
```

---

## Usage Guidelines

### Combining Prompts
- Use general prompts with specific type prompts for best results
- Always include relevant knowledge base files
- Adapt prompts based on the specific content and audience

### Iterative Improvement
- Start with content creation prompts
- Follow with quality assurance prompts
- Use enhancement prompts for final polish

### Context Loading
- Load documentation standards before writing
- Include mental models for technical accuracy
- Reference community knowledge for real-world insights

---

_These prompts should be adapted based on specific documentation needs and updated as best practices evolve._