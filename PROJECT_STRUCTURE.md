# co-agenticOS - Project Structure

**Created by:** Boyuan (Keven) Guan  
**Contact:** keven1894@gmail.com | [LinkedIn](https://www.linkedin.com/in/boyuan-keven-guan/)

> **Part of the [Agentic-AI Engineering Framework](https://github.com/Keven1894/Agentic-AI-Research-Roadmap)**  
> **Framework DOI**: [10.5281/zenodo.14279004](https://doi.org/10.5281/zenodo.14279004)

This document provides an overview of the co-agenticOS **Rule & Template Framework** structure.

## 🔗 Position in Agentic-AI Ecosystem

co-agenticOS implements the **execution and governance layer** of the Agentic-AI Engineering Framework:

- **Parent Framework**: Defines theoretical methodology (Context → Documentation → Indexing → RAG → Fine-tuning)
- **co-agenticOS**: Implements runtime behavior, agent coordination, and cultural practices
- **Domain Applications**: Real-world implementations combining both framework and OS

## 🏗️ Core Four-Layer Architecture

co-agenticOS follows a clear architectural philosophy with four distinct layers:

```
co-agenticOS/
├── core/                         ← Abstract Rules (Domain-independent)
│   ├── manifesto/                ← Core culture & behavior principles
│   ├── workflow/                 ← Universal agentic processes
│   ├── ai-routing/               ← AI model allocation rules
│   └── standards/                ← Universal quality standards
│
├── domains/                      ← Instance Rules (Domain-specific)
│   ├── research-engineering/     ← Research engineering rules
│   ├── software-development/     ← Software development rules
│   └── financial-analysis/       ← Financial analysis rules
│
├── templates/                    ← Structural scaffolds
│   ├── rule-template.md          ← Template for writing rules
│   ├── plan-template.md          ← Planning templates
│   └── reflection-template.md    ← Reflection templates
│
└── examples/                     ← Real-world demonstrations
    ├── example-data-rule.md      ← Data processing example
    └── example-ai-routing.md     ← AI routing example
```

### Layer 1: Core (Abstract Rules)
- **Purpose:** Universal, domain-independent principles and processes
- **Content:** Manifesto, workflows, AI routing, standards
- **Impact:** Provides foundation for all domain-specific rules

### Layer 2: Domains (Instance Rules)  
- **Purpose:** Domain-specific implementations of abstract rules
- **Content:** Research engineering, software development, financial analysis
- **Impact:** Practical application of core principles in specific contexts

### Layer 3: Templates (Structural Scaffolds)
- **Purpose:** Standardized patterns for creating rules and documentation
- **Content:** Rule templates, planning templates, reflection templates
- **Impact:** Ensures consistency and quality across all rules

### Layer 4: Examples (Real-world Demonstrations)
- **Purpose:** Practical examples of rule implementation
- **Content:** Real-world case studies and implementations
- **Impact:** Demonstrates practical application and provides learning resources

---

## 📁 Detailed Directory Structure

```
co-agenticOS/
├── 📄 README.md                    # Framework overview and usage guide
├── 📄 LICENSE                      # MIT License
├── 📄 CONTRIBUTING.md              # Rule contribution guidelines
├── 📄 AUTHOR.md                    # Author information
├── 📄 PROJECT_STRUCTURE.md         # This document
├── 📁 core/                        # Abstract rules (universal principles)
│   ├── 📁 manifesto/              # Cultural foundation
│   │   └── 📄 00-principles.md    # Core cultural principles
│   ├── 📁 workflow/               # Universal processes
│   │   ├── 📄 agentic-development-loop.md # The 4-phase development process
│   │   └── 📄 cursor-rules.md     # Cursor IDE configuration
│   ├── 📁 ai-routing/             # AI model allocation
│   │   └── 📄 universal-routing.md # Universal AI routing rules
│   └── 📁 standards/              # Quality standards
├── 📁 domains/                     # Instance rules (domain-specific)
│   ├── 📁 research-engineering/   # Research engineering domain
│   │   ├── 📄 abstract.md         # Domain overview and principles
│   │   └── 📄 data-processing.md  # Data processing rule
│   ├── 📁 software-development/   # Software development domain
│   └── 📁 financial-analysis/     # Financial analysis domain
├── 📁 templates/                   # Structural scaffolds
│   ├── 📄 rule-template.md        # Template for creating rules
│   ├── 📄 plan-template.md        # Daily planning template
│   ├── 📄 ADR.md                  # Architecture Decision Record template
│   └── 📄 Summary.md              # Daily summary template
├── 📁 examples/                    # Real-world demonstrations
│   └── 📄 cross-domain-workflow-integration.md # Cross-domain pattern application
└── 📁 docs/                        # Additional documentation
    ├── 📄 getting-started.md      # Getting started guide
    ├── 📄 quick-start.md          # Quick start guide
    ├── 📄 contribution-guidelines.md # Detailed contribution guide
    └── 📄 documentation-guidelines.md # Documentation standards
```

---

## 📋 File Descriptions

### Core Files

#### `README.md`
The main framework documentation that provides:
- Framework overview and purpose
- Usage instructions (NOT a codebase)
- Structure explanation
- Getting started guide

#### `LICENSE`
MIT License file that defines the terms under which the framework is distributed.

#### `CONTRIBUTING.md`
Guidelines for contributing rules and templates to the framework.

#### `AUTHOR.md`
Information about the framework creator and contact details.

### Core Directory (`core/`)

#### `core/manifesto/`
Contains the cultural foundation and philosophical principles:
- **`00-principles.md`**: Core cultural principles and manifesto

#### `core/workflow/`
Contains universal agentic processes:
- **`agentic-development-loop.md`**: The 4-phase development process
- **`cursor-rules.md`**: Cursor IDE configuration rules

#### `core/ai-routing/`
Contains AI model allocation rules:
- **`universal-routing.md`**: Universal AI routing patterns

#### `core/standards/`
Contains universal quality standards:
- Quality guidelines and validation criteria

### Domains Directory (`domains/`)

#### `domains/research-engineering/`
Contains research engineering specific rules:
- **`abstract.md`**: Domain overview and principles
- **`data-processing.md`**: Data processing rule example

#### `domains/software-development/`
Contains software development specific rules:
- Frontend, backend, and DevOps rules

#### `domains/financial-analysis/`
Contains financial analysis specific rules:
- Risk assessment and data validation rules

### Templates Directory (`templates/`)

#### `templates/rule-template.md`
Comprehensive template for creating new rules with:
- Required sections and structure
- Human-AI collaboration patterns
- Quality metrics and validation
- Continuous improvement processes

#### `templates/plan-template.md`
Template for daily planning with AI agent assignments

#### `templates/ADR.md`
Template for Architecture Decision Records

#### `templates/Summary.md`
Template for daily development summaries

### Examples Directory (`examples/`)

#### `examples/project-setup-example.md`
Complete example of implementing co-agenticOS in a real project

### Documentation Directory (`docs/`)

#### `docs/getting-started.md`
Comprehensive getting started guide

#### `docs/quick-start.md`
Quick start guide for immediate usage

#### `docs/contribution-guidelines.md`
Detailed guidelines for contributing to the framework

#### `docs/documentation-guidelines.md`
Standards for framework documentation

---

## 🎯 Usage Patterns

### For Individual Developers
1. **Browse Core Rules**: Start with `core/manifesto/00-principles.md`
2. **Choose Domain**: Select relevant rules from `domains/`
3. **Use Templates**: Copy templates from `templates/`
4. **Study Examples**: Learn from real-world implementations

### For Development Teams
1. **Review Core Principles**: Go through `core/workflow/agentic-development-loop.md`
2. **Establish Domain Rules**: Create team-specific rules using templates
3. **Implement Workflows**: Use the agentic development loop
4. **Customize**: Adapt rules to your specific needs

### For Organizations
1. **Assess Domains**: Review all available domain rules
2. **Create Standards**: Use core rules to establish organization-wide standards
3. **Implement Training**: Use examples and templates for team training
4. **Monitor Usage**: Track adoption and effectiveness of AI workflows

---

## 🔧 Framework Customization

### Creating New Domain Rules
1. **Use Domain Abstract**: Start with domain abstract template
2. **Follow Rule Template**: Use `templates/rule-template.md`
3. **Include Examples**: Provide real-world examples
4. **Validate Quality**: Ensure rules meet quality standards

### Modifying Existing Rules
1. **Review Current Rule**: Understand existing structure
2. **Make Changes**: Follow established patterns
3. **Update Examples**: Ensure examples reflect changes
4. **Test Thoroughly**: Verify all modifications work

### Creating New Templates
1. **Follow Structure**: Use established template patterns
2. **Include Guidelines**: Provide clear usage instructions
3. **Add Examples**: Include template usage examples
4. **Validate Completeness**: Ensure all necessary sections included

---

## 📈 Framework Evolution

### Planned Additions
- **More Domain Rules**: Additional technology-specific rules
- **Advanced Templates**: More sophisticated template patterns
- **Integration Tools**: Tools for easier rule management
- **Community Features**: Enhanced collaboration features

### Long-term Goals
- **AI Model Integration**: Direct integration with AI models
- **Automated Rule Generation**: AI-generated rules based on codebases
- **Performance Analytics**: Track and optimize AI workflow performance
- **Enterprise Features**: Advanced features for large organizations

---

## 🚀 Getting Started

1. **Explore**: Browse the framework structure to understand the organization
2. **Read**: Start with `README.md` for framework overview
3. **Choose**: Select relevant rules and templates for your needs
4. **Customize**: Adapt templates to your specific requirements
5. **Contribute**: Share your improvements with the community

This framework structure is designed to be modular, extensible, and easy to navigate, allowing you to find and use exactly what you need for your AI-assisted development workflow.

---

*This framework structure embodies the co-agenticOS culture of continuous collaboration, reflection, and improvement between humans and AI agents.*