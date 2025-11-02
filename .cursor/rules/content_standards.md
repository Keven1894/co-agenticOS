---
title: "Content Standards"
description: "Documentation quality and formatting standards for co-agenticOS"
version: "1.0.0"
last_updated: "2025-01-28"
scope: "content"
priority: "high"
tags: ["content", "quality", "formatting", "standards"]
---

# Content Standards

## 📝 Documentation Quality Standards

### Core Principles
- **Clarity** - Content must be easy to understand and actionable
- **Completeness** - All required sections must be included
- **Consistency** - Follow established patterns and structures
- **Correctness** - Information must be accurate and verified
- **Usefulness** - Content must provide practical value to users

## 📋 Markdown Formatting Standards

### Frontmatter Requirements
All rule and documentation files MUST include frontmatter:

```yaml
---
title: "Descriptive Title"
description: "Brief description of the content"
version: "1.0.0"
last_updated: "YYYY-MM-DD"
scope: "system|domain|template"
priority: "critical|highest|high|medium|low"
tags: ["tag1", "tag2", "tag3"]
---
```

### Heading Hierarchy
- **H1 (`#`)** - Document title (one per file)
- **H2 (`##`)** - Main sections
- **H3 (`###`)** - Subsections
- **H4 (`####`)** - Detailed breakdowns

**DO NOT skip levels** - Don't jump from H2 to H4

### Code Blocks
Always specify the language:
```markdown
\`\`\`bash
git commit -m "message"
\`\`\`

\`\`\`typescript
interface User {
  id: string;
  name: string;
}
\`\`\`
```

### Lists
- Use **bulleted lists** for unordered items
- Use **numbered lists** for sequential steps
- Use **checkboxes** for action items: `- [ ] Task`
- Maintain consistent indentation (2 spaces)

### Links
- Use **relative links** for internal content: `[Core Rules](core/manifesto/)`
- Use **absolute links** for external resources: `[GitHub](https://github.com)`
- Include **descriptive text**: `[GIS Platform Example](domains/research-engineering/examples/)`

### Emphasis
- Use **bold** (`**text**`) for important terms and emphasis
- Use *italic* (`*text*`) for subtle emphasis or definitions
- Use `code` (`` `text` ``) for technical terms, commands, file names

## 🏗️ Content Structure Standards

### Rule Files
Must include these sections:
1. **Type** - Category, level, parent abstract
2. **Purpose** - Clear statement of what the rule accomplishes
3. **Procedure** - Step-by-step implementation with human/AI roles
4. **Example** - Real-world application with context
5. **Reflection** - Success criteria and quality metrics
6. **Continuous Improvement** - Performance monitoring and feedback
7. **Anti-Patterns** - What to avoid and why
8. **Tools and Resources** - Recommended tools and useful resources
9. **Related Rules** - Cross-references to related content

### Template Files
Must include these sections:
1. **Purpose** - What the template is for
2. **Structure** - Template layout and required sections
3. **Instructions** - How to use the template
4. **Examples** - Filled-in template examples
5. **Validation** - How to verify correct usage

### Example Files
Must include these sections:
1. **Project Overview** - Context and scope
2. **Human-AI Collaboration** - Detailed implementation
3. **Key Learnings** - What was learned
4. **Success Metrics** - Quantitative and qualitative results
5. **Challenges and Solutions** - Problems encountered and resolved
6. **Template Usage** - Which templates were used
7. **Replication Guide** - How to apply to other projects

## ✅ Quality Checklist

### Before Committing
- [ ] All content is in English
- [ ] Proper frontmatter included
- [ ] Heading hierarchy is correct
- [ ] Code blocks have language specified
- [ ] Links are working and properly formatted
- [ ] Grammar and spelling checked
- [ ] Examples are complete and realistic
- [ ] All required sections included
- [ ] Cross-references are accurate
- [ ] Consistent with existing content

### Content Review
- [ ] **Clarity** - Easy to understand?
- [ ] **Completeness** - All sections included?
- [ ] **Accuracy** - Information correct?
- [ ] **Usefulness** - Provides practical value?
- [ ] **Examples** - Realistic and helpful?
- [ ] **Formatting** - Follows standards?
- [ ] **Consistency** - Matches existing patterns?

## 🎨 Style Guidelines

### Writing Style
- **Active voice** - "AI generates code" not "Code is generated"
- **Present tense** - "AI assists with" not "AI will assist"
- **Direct language** - "Use this approach" not "You might consider using"
- **Professional tone** - Technical but accessible

### Terminology
- **Consistent terms** - Use the same terminology throughout
- **Define acronyms** - First use: "Architecture Decision Record (ADR)"
- **Technical accuracy** - Use correct technical terminology
- **Clear definitions** - Define specialized terms

### Examples
- **Realistic** - Based on real-world scenarios
- **Complete** - Include all necessary context
- **Actionable** - Users can follow and replicate
- **Diverse** - Show different use cases and domains

## 📊 Documentation Types

### Core Rules (Abstract)
- Universal, domain-independent principles
- High-level, broadly applicable
- Focus on philosophy and approach
- Examples from multiple domains

### Domain Rules (Instance)
- Specific to particular fields or technologies
- Detailed, practical implementation
- Domain-specific examples
- Reference parent abstract rules

### Templates
- Structural scaffolds for creating content
- Clear instructions for usage
- Multiple examples showing variation
- Validation criteria included

### Examples
- Real-world implementations
- Complete context and background
- Detailed human-AI collaboration process
- Measurable results and learnings

## 🔄 Content Lifecycle

### Creation
1. **Review existing content** - Understand patterns
2. **Choose appropriate template** - Use established structure
3. **Draft content** - Follow standards and guidelines
4. **Add examples** - Provide realistic use cases
5. **Self-review** - Check against quality criteria

### Review
1. **Content review** - Verify quality and completeness
2. **Technical review** - Ensure accuracy
3. **Language review** - Check English quality
4. **Consistency review** - Match existing patterns

### Maintenance
1. **Regular updates** - Keep content current
2. **Fix issues** - Address reported problems
3. **Enhance examples** - Add more use cases
4. **Improve clarity** - Refine based on feedback

## 🛠️ Tools and Resources

### Writing Tools
- **Grammarly** - Grammar and spell checking
- **Hemingway Editor** - Readability improvement
- **Markdown Preview** - Visual formatting check
- **VS Code** - Markdown editing with extensions

### Validation Tools
- **Markdownlint** - Markdown formatting validation
- **Link Checker** - Verify links are working
- **Spell Checker** - Catch spelling errors
- **Grammar Checker** - Catch grammar issues

### Reference Resources
- **Google Developer Documentation Style Guide** - Technical writing standards
- **Microsoft Writing Style Guide** - Professional writing guidelines
- **Markdown Guide** - Markdown syntax reference
- **Existing co-agenticOS content** - Follow established patterns

---

**Remember**: High-quality content is the foundation of co-agenticOS. Every document shapes how users understand and apply the framework.
