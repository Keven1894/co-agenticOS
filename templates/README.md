# Templates - Structural Scaffolds
### Standardized Patterns for Consistent Documentation and Rules

**Purpose**: This directory contains reusable templates that ensure consistency and quality across all co-agenticOS rules, documentation, and processes.

---

## 📁 Directory Contents

```
templates/
├── rule-template.md     ← Template for creating new rules
├── PLAN.md              ← Daily planning template
├── ADR.md               ← Architecture Decision Record template
└── Summary.md           ← Daily summary template
```

---

## 📚 Template Overview

### 1. Rule Template (`rule-template.md`)
**Purpose**: Standardized structure for creating domain rules

**Use When**:
- Creating new domain-specific rules
- Contributing rules to co-agenticOS
- Establishing project-specific rules
- Documenting AI collaboration patterns

**Sections Included**:
- **Metadata**: Title, type, scope, parent abstract
- **Purpose**: Clear statement of rule's intent
- **Context**: When and why to use this rule
- **Procedure**: Step-by-step implementation
- **Human-AI Collaboration**: Roles and responsibilities
- **Quality Metrics**: Success criteria and validation
- **Examples**: Real-world usage scenarios
- **Reflection**: Continuous improvement process

**Template Type**: Comprehensive, structured

**Benefits**:
- ✅ Ensures completeness
- ✅ Maintains consistency across domains
- ✅ Guides contributors
- ✅ Improves discoverability

---

### 2. Plan Template (`PLAN.md`)
**Purpose**: Daily planning structure for AI-assisted development

**Use When**:
- Starting a development session
- Planning daily work with AI agents
- Organizing tasks and priorities
- Setting up the agentic development loop

**Sections Included**:
- **Date & Goals**: Session identification and objectives
- **Tasks**: Prioritized task list
- **AI Agent Assignments**: Which AI handles which tasks
- **Success Criteria**: How to know when done
- **Blockers**: Known obstacles
- **Notes**: Additional context

**Template Type**: Operational, daily-use

**Benefits**:
- ✅ Structures AI collaboration
- ✅ Clear task allocation
- ✅ Tracks progress
- ✅ Identifies dependencies

**Related Workflow**: Phase 1 of the Agentic Development Loop (Plan)

---

### 3. Architecture Decision Record (`ADR.md`)
**Purpose**: Document significant architectural decisions

**Use When**:
- Making important technical decisions
- Choosing between design alternatives
- Documenting rationale for future reference
- AI suggests architectural changes

**Sections Included**:
- **Title**: ADR number and topic
- **Status**: Proposed, accepted, deprecated
- **Context**: Problem and background
- **Decision**: What was decided
- **Consequences**: Positive and negative impacts
- **Alternatives Considered**: Other options evaluated

**Template Type**: Archival, decision-tracking

**Benefits**:
- ✅ Captures decision context
- ✅ Explains rationale
- ✅ Prevents repeated discussions
- ✅ Helps onboard new team members

**Best Practice**: Create ADR when AI suggests significant architectural changes

---

### 4. Summary Template (`Summary.md`)
**Purpose**: Daily development summary and reflection

**Use When**:
- Ending a development session
- Documenting daily progress
- Reflecting on what was learned
- Updating team on changes

**Sections Included**:
- **Date & Summary**: Session identification and overview
- **Completed Tasks**: What was accomplished
- **Changes Made**: Code and documentation updates
- **Learnings**: Insights and discoveries
- **Next Steps**: Follow-up actions
- **AI Contributions**: What AI agents did

**Template Type**: Reflective, documentation

**Benefits**:
- ✅ Creates development history
- ✅ Facilitates knowledge transfer
- ✅ Supports continuous learning
- ✅ Improves collaboration

**Related Workflow**: Phase 4 of the Agentic Development Loop (Summarize)

---

## 🎯 Template Usage Guide

### Quick Reference Table

| Template | Phase | Frequency | Primary User | AI Involvement |
|----------|-------|-----------|--------------|----------------|
| **rule-template.md** | Setup | Once per rule | Contributor | High (drafting) |
| **PLAN.md** | Start | Daily | Developer | High (planning) |
| **ADR.md** | Decision | As needed | Architect | Medium (analysis) |
| **Summary.md** | End | Daily | Developer | High (documentation) |

---

## 📖 How to Use Templates

### For New Rules

1. **Copy the Template**
   ```bash
   cp templates/rule-template.md domains/your-domain/your-rule.md
   ```

2. **Fill in All Sections**
   - Don't skip sections (use "N/A" if truly not applicable)
   - Provide concrete examples
   - Define clear success metrics

3. **Review Against Checklist**
   - [ ] All required sections complete
   - [ ] Examples are realistic
   - [ ] Success criteria measurable
   - [ ] Links to related rules

4. **Submit for Review**
   - Follow `../CONTRIBUTING.md`
   - Respond to feedback
   - Update as needed

### For Daily Workflow

#### Morning (Planning)
```bash
cp templates/PLAN.md daily-plans/2025-11-09-plan.md
# Fill in today's goals and tasks
# Assign tasks to AI agents
```

#### During Development
- Work through planned tasks
- Create ADRs for significant decisions
- Update plan with new findings

#### Evening (Summary)
```bash
cp templates/Summary.md daily-summaries/2025-11-09-summary.md
# Document what was accomplished
# Reflect on learnings
# Plan next steps
```

### For Architectural Decisions

```bash
cp templates/ADR.md docs/adr/001-database-choice.md
# Document decision context
# Record considered alternatives
# Explain rationale
```

---

## 🔄 Template Lifecycle

### Creation
Templates are created when:
- ✅ Pattern emerges across multiple uses
- ✅ Consistency is needed
- ✅ Community requests standardization

### Evolution
Templates evolve through:
- Community feedback
- Usage patterns
- Changing best practices
- Tool improvements

### Versioning
- Templates follow semantic versioning
- Major changes create new template files
- Old templates maintained for compatibility

---

## 📊 Template Quality Standards

### Completeness Checklist
- [ ] Clear purpose statement
- [ ] Target audience identified
- [ ] All sections explained
- [ ] Examples provided
- [ ] Integration guidance included
- [ ] Markdown formatting correct

### Usability Criteria
- [ ] Can be used without additional context
- [ ] Sections are self-explanatory
- [ ] Examples are realistic
- [ ] Instructions are clear
- [ ] Related templates referenced

---

## 🎓 Template Philosophy

### Design Principles

1. **Completeness Without Overwhelming**
   - Include all necessary sections
   - Keep instructions concise
   - Provide examples for clarity

2. **Flexibility Within Structure**
   - Templates guide, not constrain
   - Allow customization where appropriate
   - Support different use cases

3. **AI-Friendly Design**
   - Clear section markers
   - Consistent formatting
   - Explicit instructions
   - Machine-parseable structure

4. **Human-Readable First**
   - Natural language
   - Logical flow
   - Visual hierarchy
   - Searchable content

---

## 🔍 Template Selection Guide

### "I'm creating a new rule"
→ Use **rule-template.md**

### "I'm planning today's work"
→ Use **PLAN.md**

### "I'm making an architectural decision"
→ Use **ADR.md**

### "I'm ending my development session"
→ Use **Summary.md**

### "None of these fit my need"
→ Consider creating a new template (see Contributing)

---

## 🤝 Contributing New Templates

### When to Create a Template

Create new template when:
- ✅ Pattern used frequently across projects
- ✅ Consistency would add value
- ✅ Clear structure can be defined
- ✅ Benefits multiple users

**Don't create when**:
- ❌ Used only once or rarely
- ❌ Too specific to single project
- ❌ Existing template can be adapted
- ❌ Structure is too flexible to standardize

### Template Contribution Process

1. **Validate Need**
   - Check existing templates
   - Discuss in GitHub Issues
   - Get community feedback

2. **Draft Template**
   - Include purpose statement
   - Define all sections
   - Add examples
   - Document usage

3. **Test Template**
   - Use in real project
   - Get feedback from others
   - Refine based on usage

4. **Submit Template**
   - Follow contribution guidelines
   - Provide usage examples
   - Update this README

### Template Structure Requirements

Every template should include:

```markdown
# [Template Name]
### [One-line description]

**Purpose**: [Why this template exists]

**Use When**: [Specific scenarios]

---

## Sections

### 1. [Section Name]
**Purpose**: [What this section captures]

**Guidelines**:
- [How to fill this section]

**Example**:
```
[Example content]
```

---

## How to Use This Template

[Step-by-step usage instructions]
```

---

## 📈 Template Usage Statistics

### Most Used Templates
1. **rule-template.md** - Every new rule
2. **Summary.md** - Daily by active developers
3. **PLAN.md** - Daily by active developers
4. **ADR.md** - Periodic for major decisions

### Template Effectiveness
- **Rule Template**: 100% adoption for domain rules
- **Daily Templates**: High usage in active projects
- **ADR Template**: Growing adoption for architecture decisions

---

## 🔗 Integration with Workflows

### Agentic Development Loop Integration

| Phase | Template | Purpose |
|-------|----------|---------|
| **1. Plan** | PLAN.md | Structure daily work |
| **2. Implement** | (Code editing) | No template |
| **3. Refactor** | ADR.md (if needed) | Document major changes |
| **4. Summarize** | Summary.md | Reflect and document |

### Documentation Lifecycle

```
Project Start → rule-template.md (Define collaboration patterns)
       ↓
Daily Work → PLAN.md (Morning) → Summary.md (Evening)
       ↓
Major Decisions → ADR.md (As needed)
       ↓
Project Evolution → Update rules using rule-template.md
```

---

## 🎯 Template Evolution Roadmap

### Current State (v1.0.0)
- ✅ Core workflow templates (PLAN, Summary)
- ✅ Rule creation template
- ✅ Architecture decision template

### Planned Additions (2026)
- ⏳ Testing template
- ⏳ Security assessment template
- ⏳ Performance analysis template
- ⏳ Migration template
- ⏳ Retrospective template

### Future Considerations
- Interactive templates (web-based)
- Template validation tools
- Auto-generation from code
- Multi-language template versions

---

## 🔍 Related Resources

### Within co-agenticOS
- **Core Workflow**: [`../core/workflow/`](../core/workflow/) - Agentic Development Loop
- **Domains**: [`../domains/`](../domains/) - See templates in use
- **Examples**: [`../examples/`](../examples/) - Real-world template usage
- **Contributing**: [`../CONTRIBUTING.md`](../CONTRIBUTING.md) - Contribution guidelines

### External Resources
- **Parent Framework**: [Agentic-AI Engineering Framework](https://github.com/Keven1894/Agentic-AI-Research-Roadmap)

---

## 📞 Questions & Support

### Template Usage Questions
- **GitHub Discussions**: Ask about template usage
- **GitHub Issues**: Report template issues or suggest improvements

### Template Contribution
- **Email**: keven1894@gmail.com
- **Process**: Follow `../CONTRIBUTING.md`

---

## 💡 Template Best Practices

### For Users
- ✅ Start with template, customize as needed
- ✅ Don't skip sections without reason
- ✅ Provide concrete examples
- ✅ Keep templates updated with changes

### For Contributors
- ✅ Design for clarity and usability
- ✅ Test templates in real projects
- ✅ Gather feedback before finalizing
- ✅ Document usage patterns

### For Maintainers
- ✅ Review template usage regularly
- ✅ Update based on community feedback
- ✅ Maintain backward compatibility
- ✅ Version major changes

---

*Templates are the scaffolding that shapes consistent, high-quality collaboration across co-agenticOS. They embody our cultural patterns in reusable form.*

**"Documentation is Dialogue"** — Templates structure that dialogue for clarity and consistency.

