# Documentation Contribution Template

Use this template when creating documentation contributions based on user questions or identified gaps.

---

## PR Title Format
```
Add documentation: [Brief description]

Example: "Add documentation: CLI template creation from GitHub repositories"
```

## PR Description Template
```markdown
## What this adds
[Brief description of the documentation being added]

## Why this is needed
- User question: "[Original question that revealed the gap]"
- Documentation gap: [Reference to documentation-gaps.md entry]
- Frequency: [How often this question comes up]
- Impact: [Who this helps and why]

## What's included
- [ ] Clear explanation of the feature/command
- [ ] Working code examples
- [ ] Context about when/why to use it
- [ ] Cross-references to related documentation
- [ ] Follows style guide conventions

## Location
- File: `/docs/[path]/[filename].md`
- Section: "[Section title]"
- Rationale: [Why this location makes sense]

## Examples included
[List the specific examples provided]

## Related documentation
- Links to: [Related docs that should cross-reference this]
- Updates needed: [Any existing docs that need updates]

## AI Assistant Notes
- Session ID: [If from a tracked session]
- Knowledge base updates: [Files updated in shared-docs-kb]
- Follow-up needed: [Any additional work identified]
```

---

## Content Structure Template

### For CLI Commands
```markdown
## [Command Name]

[Brief description of what the command does]

### Basic Usage
```bash
[Basic command syntax]
```

### Common Examples

#### [Use Case 1]
```bash
[Command with explanation]
```
[When to use this variation]

#### [Use Case 2] 
```bash
[Command with explanation]
```
[When to use this variation]

### Options

- `--option1` - [Description]
- `--option2` - [Description]

### Related Commands

- [`related-command`](link) - [How it relates]

### Troubleshooting

**Common Issue**: [Problem description]
**Solution**: [How to fix it]
```

### For Concepts/Features
```markdown
## [Feature Name]

[Overview of what this feature does and why it's useful]

### How it works

[Technical explanation]

### Getting started

1. [Step 1 with code example]
2. [Step 2 with code example]
3. [Step 3 with code example]

### Examples

#### [Scenario 1]
[Code example with explanation]

#### [Scenario 2]
[Code example with explanation]

### Best practices

- [Practice 1 with rationale]
- [Practice 2 with rationale]

### Common issues

**Issue**: [Problem description]
**Cause**: [Why this happens]
**Solution**: [How to fix it]

### Related topics

- [Link to related documentation]
```

### For Troubleshooting Guides
```markdown
## [Problem Category]

[Overview of the types of issues covered]

### Quick diagnosis

1. **Check [thing 1]**: `command to check`
2. **Verify [thing 2]**: `command to verify`
3. **Test [thing 3]**: `command to test`

### Common issues

#### [Specific Issue 1]

**Symptoms**: [What the user sees]
**Cause**: [Why this happens]
**Solution**:
```bash
[Commands to fix it]
```
**Prevention**: [How to avoid this in the future]

#### [Specific Issue 2]

[Same format as above]

### When to escalate

- [Condition 1] - Contact [team/person]
- [Condition 2] - File issue at [location]

### Additional resources

- [Link to related troubleshooting]
- [Link to community discussions]
```

---

## Quality Checklist

Before submitting documentation:

### Content Quality
- [ ] **Accurate**: All commands and examples tested
- [ ] **Complete**: Covers the main use cases
- [ ] **Clear**: Easy to understand for target audience
- [ ] **Contextual**: Explains when/why to use

### Style Compliance
- [ ] **Follows style guide**: Matches existing documentation patterns
- [ ] **Proper formatting**: Headings, code blocks, lists formatted correctly
- [ ] **Consistent terminology**: Uses established Coder terms
- [ ] **No emojis**: In headings or list items

### Integration
- [ ] **Proper location**: Fits logically in documentation structure
- [ ] **Cross-references**: Links to/from related documentation
- [ ] **Navigation**: Updates manifest.json if needed
- [ ] **Images**: Added to correct location with proper references

### Examples
- [ ] **Working code**: All examples tested and functional
- [ ] **Realistic scenarios**: Examples reflect real use cases
- [ ] **Progressive complexity**: Simple to advanced examples
- [ ] **Copy-pasteable**: Users can copy and run examples

---

## Common Locations

### CLI Documentation
- **Location**: `/docs/reference/cli/`
- **When to use**: Command syntax, options, examples
- **Cross-reference**: Link from user guides

### User Guides
- **Location**: `/docs/user-guides/`
- **When to use**: Workflow-oriented documentation
- **Cross-reference**: Link to CLI reference and admin guides

### Admin Documentation
- **Location**: `/docs/admin/`
- **When to use**: Installation, configuration, management
- **Cross-reference**: Link to troubleshooting and user guides

### Tutorials
- **Location**: `/docs/tutorials/`
- **When to use**: Step-by-step learning experiences
- **Cross-reference**: Link to relevant user guides

### Troubleshooting
- **Location**: `/docs/troubleshooting/` (if it exists) or within relevant sections
- **When to use**: Problem-solving and debugging
- **Cross-reference**: Link from all related documentation

---

## AI Assistant Workflow

### When User Agrees to Documentation Addition

1. **Confirm the approach**:
   ```
   Great! I'll add this to `/docs/[location]`. I'm thinking:
   
   - Section: "[Title]"
   - Content: [Brief outline]
   - Examples: [What examples to include]
   
   Does that sound right?
   ```

2. **Create the content** using this template

3. **Submit PR** with proper description

4. **Update memory files**:
   - Add to `common-questions.md`
   - Update `documentation-gaps.md`
   - Log in `ai-project-notes.md`

5. **Follow up** with user about the contribution

---

_This template ensures consistent, high-quality documentation contributions that help users and improve the overall Coder documentation experience._