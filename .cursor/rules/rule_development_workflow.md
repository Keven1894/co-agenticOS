---
title: "Rule Development Workflow"
description: "Process for creating and updating rules in co-agenticOS"
version: "1.0.0"
last_updated: "2025-01-28"
scope: "workflow"
priority: "high"
tags: ["workflow", "development", "rules", "process"]
---

# Rule Development Workflow

## 🎯 Core Principles

### Framework Development Philosophy
- **Quality over quantity** - Better to have few excellent rules than many mediocre ones
- **Pattern consistency** - Follow established structures and formats
- **User-focused** - Rules must be practical and actionable
- **Documentation-first** - Every rule is thoroughly documented

## 📋 Rule Development Process

### Phase 1: Research & Planning
**Before creating a new rule:**

1. **Review Existing Content**
   - Check if similar rule already exists
   - Study related rules in same domain
   - Review reference implementations (e.g., GIS Platform example)
   - Understand established patterns

2. **Define Scope and Purpose**
   - What specific problem does this rule solve?
   - Who is the target audience?
   - What domain does it belong to?
   - Is it abstract (universal) or instance (domain-specific)?

3. **Identify Parent Abstractions**
   - Does this rule extend an abstract rule?
   - What core principles does it implement?
   - How does it relate to other rules?

### Phase 2: Rule Creation

1. **Choose Appropriate Template**
   ```bash
   # Copy rule template
   cp templates/rule-template.md domains/{domain}/{rule-name}.md
   ```

2. **Fill Required Sections**
   - **Frontmatter** - Complete all metadata fields
   - **Type** - Category, level, parent abstract
   - **Purpose** - Clear, concise statement
   - **Procedure** - Step-by-step with human/AI roles
   - **Example** - Real-world implementation
   - **Reflection** - Success criteria and metrics
   - **Anti-Patterns** - What to avoid
   - **Tools** - Recommended resources
   - **Related Rules** - Cross-references

3. **Add Comprehensive Examples**
   - Provide realistic context
   - Show human-AI collaboration in detail
   - Include specific outputs and deliverables
   - Demonstrate success metrics

### Phase 3: Quality Assurance

1. **Self-Review Checklist**
   - [ ] All content in English
   - [ ] Frontmatter complete and accurate
   - [ ] All required sections included
   - [ ] Examples are realistic and complete
   - [ ] Anti-patterns clearly explained
   - [ ] Cross-references accurate
   - [ ] Formatting consistent with standards
   - [ ] Grammar and spelling checked

2. **Technical Validation**
   - [ ] Rule is actionable and practical
   - [ ] Examples can be replicated
   - [ ] Success criteria are measurable
   - [ ] Tools and resources are relevant
   - [ ] Integrates with existing framework

3. **Consistency Check**
   - [ ] Follows established patterns
   - [ ] Uses consistent terminology
   - [ ] Matches directory structure
   - [ ] Aligns with framework philosophy

### Phase 4: Integration

1. **Update Related Documentation**
   - Add cross-references from related rules
   - Update domain abstract if needed
   - Add to relevant examples
   - Update README if significant

2. **Create Example Implementation** (if applicable)
   - Develop complete example showing rule application
   - Place in appropriate examples directory
   - Follow example template structure

3. **Commit and Document**
   ```bash
   git add domains/{domain}/{rule-name}.md
   git commit -m "Add: {Rule Name} for {domain}
   
   - Complete rule implementation
   - Includes realistic examples
   - Comprehensive anti-patterns
   - Integration with existing framework"
   ```

## 🔄 Rule Update Process

### Minor Updates
For small corrections or enhancements:
1. Make necessary changes
2. Update `last_updated` in frontmatter
3. Update `version` if needed (patch: x.x.1)
4. Commit with clear description

### Major Updates
For significant changes:
1. Review impact on related rules
2. Update cross-references
3. Update examples if needed
4. Increment minor version (x.1.0)
5. Document changes in commit message

### Breaking Changes
If rule fundamentally changes:
1. Consider creating new rule instead
2. If updating, increment major version (2.0.0)
3. Update all references
4. Provide migration guide
5. Document rationale thoroughly

## 📁 Rule Organization

### Directory Structure
```
domains/
├── {domain-name}/
│   ├── abstract.md          # Domain overview
│   ├── {rule-1}.md          # Specific rule
│   ├── {rule-2}.md          # Specific rule
│   └── examples/            # Domain examples
│       └── {example}/       # Complete implementation
```

### File Naming
- Use **kebab-case**: `data-processing.md`
- Be descriptive: `project-management.md`
- Avoid abbreviations: `architecture-decision-record.md` not `adr.md`
- Use singular form: `rule-development-workflow.md`

## 🎯 Rule Quality Standards

### Essential Qualities
1. **Clarity** - Easy to understand and follow
2. **Actionability** - Provides concrete steps
3. **Completeness** - Includes all necessary information
4. **Examples** - Shows realistic application
5. **Validation** - Defines success criteria

### Warning Signs
- ❌ Too abstract without concrete steps
- ❌ Missing examples or using placeholders
- ❌ Inconsistent with existing patterns
- ❌ Not actionable or practical
- ❌ Poor integration with framework

## 🧩 Rule Types

### Abstract Rules (Core)
**Location**: `core/`
**Purpose**: Universal, domain-independent principles
**Characteristics**:
- High-level concepts
- Broadly applicable
- Foundation for instance rules
- Multiple domain examples

**Example**: AI Routing Rules, Workflow Standards

### Instance Rules (Domains)
**Location**: `domains/{domain}/`
**Purpose**: Domain-specific implementations
**Characteristics**:
- Practical, detailed guidance
- Domain-specific examples
- References parent abstract
- Actionable procedures

**Example**: Data Processing for Research, Frontend Development Rules

## 🔍 Review Criteria

### Content Review
- **Purpose clarity** - Is the problem well-defined?
- **Procedure completeness** - Are steps clear and actionable?
- **Example quality** - Are examples realistic and helpful?
- **Integration** - Does it fit the framework?

### Technical Review
- **Accuracy** - Is information correct?
- **Practicality** - Can users actually follow this?
- **Metrics** - Are success criteria measurable?
- **Tools** - Are recommended tools appropriate?

### Language Review
- **English quality** - Professional and clear?
- **Grammar** - Free of errors?
- **Terminology** - Consistent and accurate?
- **Readability** - Easy to understand?

## 📊 Success Metrics

### Rule Effectiveness
- **Adoption** - How many users apply the rule?
- **Clarity** - Do users understand it easily?
- **Results** - Does it improve outcomes?
- **Feedback** - What do users say about it?

### Framework Health
- **Consistency** - Does it enhance framework coherence?
- **Usability** - Does it make framework more useful?
- **Quality** - Does it maintain high standards?
- **Growth** - Does it enable new applications?

## 🛠️ Tools and Resources

### Development Tools
- **VS Code** - Markdown editing
- **Markdownlint** - Format validation
- **Grammarly** - Language checking
- **Git** - Version control

### Reference Materials
- **Existing Rules** - Learn from established patterns
- **GIS Platform Example** - Quality benchmark
- **Rule Template** - Structural guide
- **Content Standards** - Quality guidelines

---

**Remember**: Every rule you create becomes part of how engineers worldwide collaborate with AI. Quality and care matter.
