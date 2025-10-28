# Contributing Guidelines
## Guidelines for contributing to co-agenticOS

We welcome contributions from the community! This document provides guidelines for contributing to the co-agenticOS **Rule & Template Framework**.

## What is co-agenticOS?

**co-agenticOS is NOT a codebase.**  
It's a **Rule & Template Framework** — a collection of reusable human–AI collaboration behavior patterns, templates, and examples that teams can import into their own projects to build AI collaboration culture.

## Types of Contributions

### 1. Domain Rules (Instance Rules)
Create new domain-specific rules for specific fields:

- **Research Engineering**: Data processing, collection, analysis rules
- **Software Development**: Frontend, backend, DevOps rules  
- **Financial Analysis**: Risk assessment, data validation rules
- **Other Domains**: Your specialized field

### 2. Core Rules (Abstract Rules)
Enhance universal, domain-independent rules:

- **Workflow Rules**: Universal agentic processes
- **AI Routing Rules**: AI model allocation patterns
- **Standards**: Quality and documentation standards
- **Manifesto**: Cultural principles and ethics

### 3. Templates
Improve or create new structural scaffolds:

- **Rule Templates**: Templates for writing rules
- **Planning Templates**: Daily planning structures
- **Reflection Templates**: Post-task reflection formats
- **Documentation Templates**: Standard documentation formats

### 4. Examples
Provide real-world demonstrations:

- **Rule Examples**: How rules are applied in practice
- **Workflow Examples**: Complete workflow implementations
- **Template Examples**: Template usage demonstrations

## Quick Start

### 1. Fork and Clone
```bash
# Fork the repository on GitHub
git clone https://github.com/your-username/co-agenticOS.git
cd co-agenticOS
```

### 2. Choose Contribution Type
```bash
# For domain rules
mkdir -p domains/your-domain
cp templates/rule-template.md domains/your-domain/your-rule.md

# For core rules
# Edit files in core/ directory

# For templates
# Edit files in templates/ directory

# For examples
# Add files to examples/ directory
```

### 3. Follow the Template
Use the provided templates to ensure consistency:

- **Rule Template**: [`templates/rule-template.md`](templates/rule-template.md)
- **Planning Template**: [`templates/plan-template.md`](templates/plan-template.md)
- **Reflection Template**: [`templates/reflection-template.md`](templates/reflection-template.md)

### 4. Submit a Pull Request
- Provide a clear description of your contribution
- Reference any related issues
- Include examples if applicable
- Ensure all content follows the framework

## Rule Writing Guidelines

### Required Elements
Each rule must include:

1. **Title, Scope, Purpose** - What the rule covers
2. **Abstract Rationale** - Why this rule exists
3. **Example Instance** - How it's applied in practice
4. **Reflection Metric** - How to know if it worked
5. **Template Integration** - How it fits with existing templates

### Rule Structure
```markdown
# Rule: [Descriptive Title]

## 🧩 Type
- **Category:** [Domain/Abstract]
- **Level:** [Instance Rule/Abstract Rule]
- **Parent Abstract:** [If applicable]

## 🎯 Purpose
[Clear statement of what this rule accomplishes]

## 🔧 Procedure
[Step-by-step implementation]

## 📘 Example
[Real-world application example]

## 📈 Reflection
[Success metrics and validation criteria]
```

### Quality Standards
- **Clarity**: Rules must be clear and actionable
- **Completeness**: Include all necessary sections
- **Examples**: Provide realistic examples
- **Consistency**: Follow established patterns
- **Usability**: Rules must be practical to implement

## Domain Organization

### Domain Structure
```
domains/
├── research-engineering/
│   ├── abstract.md              # Domain overview
│   ├── data-processing.md       # Specific rule
│   ├── data-collection.md       # Specific rule
│   └── examples/                # Domain examples
├── software-development/
│   ├── abstract.md
│   ├── frontend-development.md
│   └── backend-development.md
└── financial-analysis/
    ├── abstract.md
    ├── risk-assessment.md
    └── data-validation.md
```

### Domain Abstract Requirements
Each domain must have an `abstract.md` that includes:

- **Domain Definition**: What this domain covers
- **Core Principles**: Fundamental beliefs and values
- **Common Patterns**: Recurring collaboration patterns
- **Success Metrics**: How to measure effectiveness
- **Related Domains**: Connections to other domains

## Review Process

### Automated Checks
- **Formatting**: Check markdown formatting
- **Links**: Verify all links are working
- **Templates**: Validate template usage
- **Structure**: Check required sections

### Content Review
- **Clarity**: Is the rule clear and actionable?
- **Completeness**: Are all required sections included?
- **Examples**: Are examples realistic and helpful?
- **Consistency**: Does it follow established patterns?
- **Usability**: Can teams actually implement this?

### Review Criteria
- **Purpose**: Clear and well-defined
- **Implementation**: Practical and actionable
- **Examples**: Realistic and comprehensive
- **Integration**: Fits with existing framework
- **Impact**: Will improve AI collaboration

## Community Guidelines

### Communication
- Be respectful and constructive
- Provide helpful feedback and suggestions
- Ask questions when clarification is needed
- Share knowledge and best practices

### Collaboration
- Work together to improve the framework
- Share ideas and suggestions openly
- Help others learn and contribute
- Recognize and appreciate contributions

## Getting Help

### Resources
- **Documentation**: Check existing rules and templates
- **Issues**: Search existing issues for similar problems
- **Discussions**: Use GitHub Discussions for questions
- **Examples**: Study real-world implementations

### Contact
- **Issues**: Use GitHub Issues for bug reports and feature requests
- **Discussions**: Use GitHub Discussions for questions and ideas
- **Author**: Boyuan (Keven) Guan - keven1894@gmail.com
- **LinkedIn**: [@boyuan-keven-guan](https://www.linkedin.com/in/boyuan-keven-guan/)

## License

By contributing to this project, you agree that your contributions will be licensed under the same license as the project (MIT License).

## Thank You

Thank you for contributing to co-agenticOS! Your contributions help make AI-assisted development more effective and accessible for everyone.

---

For detailed contribution guidelines, see [docs/contribution-guidelines.md](docs/contribution-guidelines.md).