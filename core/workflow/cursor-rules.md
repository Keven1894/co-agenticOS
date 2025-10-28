# Cursor Rules for co-agenticOS
### Human-AI Collaboration Guidelines

## Core Principles

### 1. Co-Creation over Automation
- AI agents are collaborators, not replacements
- Every AI suggestion should be reviewed and contextualized
- Human judgment always has the final say on architectural decisions

### 2. Transparency over Speed
- All AI actions must be explainable and traceable
- Document the reasoning behind AI-generated code
- Include comments explaining AI-assisted decisions

### 3. Continuous Reflection
- End each coding session with a summary of changes
- Document what was learned from AI collaboration
- Reflect on the effectiveness of AI assistance

## Code Generation Rules

### Component Creation
```typescript
// Always include this header for AI-generated components
/**
 * @ai-generated
 * @reasoning: [Brief explanation of why this component was created]
 * @human-review: [Date and reviewer name]
 */
```

### Function Documentation
```typescript
/**
 * @ai-assisted
 * @purpose: [What this function does]
 * @collaboration: [How AI helped create this]
 * @review-status: [pending | approved | needs-changes]
 */
```

### Error Handling
- Always implement proper error boundaries
- Include AI-generated error messages with human context
- Log AI assistance in error reports for debugging

## Review Process

### AI Code Review Checklist
- [ ] Is the code readable and well-documented?
- [ ] Are there any security vulnerabilities?
- [ ] Does the code follow established patterns?
- [ ] Are there any performance concerns?
- [ ] Is the AI reasoning clearly documented?

### Human Review Requirements
- [ ] Verify AI suggestions align with project goals
- [ ] Check for business logic correctness
- [ ] Ensure code meets quality standards
- [ ] Validate security and performance implications
- [ ] Confirm documentation is complete

## Daily Workflow Integration

### Morning Setup
1. Review yesterday's AI collaboration summary
2. Set daily AI agent focus areas
3. Establish communication protocols

### During Development
1. Use AI for code generation and suggestions
2. Document AI assistance in real-time
3. Maintain continuous human oversight

### End of Day
1. Generate daily summary with AI assistance
2. Reflect on collaboration effectiveness
3. Plan tomorrow's AI agent assignments

## Communication Protocols

### AI Prompting Guidelines
- Be specific about context and constraints
- Include relevant background information
- Ask for explanations of AI reasoning
- Request multiple approaches when appropriate

### Documentation Standards
- Document all AI-assisted decisions
- Include reasoning and context
- Maintain traceability of AI contributions
- Update documentation with AI assistance

## Quality Assurance

### Code Quality Metrics
- Maintain 90%+ test coverage
- Ensure all AI-generated code is reviewed
- Document all architectural decisions
- Track AI collaboration effectiveness

### Continuous Improvement
- Weekly review of AI agent performance
- Monthly assessment of collaboration patterns
- Quarterly evaluation of workflow effectiveness
- Annual review of co-agentic principles

---

*These rules embody the co-agenticOS culture of human-AI collaboration, transparency, and continuous learning.*