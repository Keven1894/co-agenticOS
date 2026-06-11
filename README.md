# co-agenticOS  
### The Culture of AI-Involved Software Engineering  

[![Part of Agentic-AI Ecosystem](https://img.shields.io/badge/Ecosystem-Agentic--AI-blue)](https://github.com/Keven1894/Agentic-AI-Research-Roadmap)
[![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.14279004-blue)](https://doi.org/10.5281/zenodo.14279004)
[![Framework](https://img.shields.io/badge/Framework-Research--Roadmap-green)](https://github.com/Keven1894/Agentic-AI-Research-Roadmap)

> **Part of the [Agentic-AI Engineering Framework](https://github.com/Keven1894/Agentic-AI-Research-Roadmap)**  
> This repository implements the **runtime and behavioral rule system** proposed in the Agentic-AI Engineering Framework.  
> **Framework DOI**: [10.5281/zenodo.14279004](https://doi.org/10.5281/zenodo.14279004)

---

**co-agenticOS** is a living operating system for human–AI collaboration in software development.  
It defines the culture, workflows, and shared rituals that allow engineers and agents to co-create, iterate, and document software continuously.

> *"Culture is the new compiler."*  
> — co-agenticOS Manifesto

---

## 🔗 Relationship to the AgentLoom Family

Four repos, four roles — split by *what they are* and by *agent lifecycle phase*:

| Repo | Role | Lifecycle phase |
|------|------|-----------------|
| **co-agenticOS** (this repo) | Governance **spec** — rules, coordination, memory boundaries, verification | sets the rules |
| [**AgentLoom**](https://github.com/Keven1894/AgentLoom) | Build **framework** — KG governance, validators, propose-review-accept | **authoring time** (build & govern the agent) |
| **AgentLoom Runtime** | Runtime **library** — layered memory, graph-first retrieval, file→DB sync | **run time** (the deployed agent remembers & retrieves) |
| [**ucgis-agentloom-2026-workshop**](https://github.com/Keven1894/ucgis-agentloom-2026-workshop) | A concrete **instance** — a worked, forkable example | a use of all of the above |

> co-agenticOS sets the rules → AgentLoom is the framework you build and govern
> an agent with (authoring time) → AgentLoom Runtime is the library the deployed
> agent uses to remember and retrieve (run time) → the workshop repo is one
> concrete instance that puts all of them to work.

Theory and methodology lineage: [Agentic-AI Research Roadmap](https://github.com/Keven1894/Agentic-AI-Research-Roadmap).

**Framework Citation**:
```
Guan, B. K. (2025). Agentic-AI Engineering: A Structured Framework for Context Management, 
    Documentation Standards, and Intelligent Retrieval in LLM-Powered Systems (Version 1.0.0). 
    Zenodo. https://doi.org/10.5281/zenodo.14279004
```

---

## ⚠️ Important: This is NOT a Codebase

**co-agenticOS is not a codebase.**  
It's a **Rule & Template Framework** — you import its structure into your own repo to build your AI collaboration culture.

### 🤖 AI Agent-Friendly Repository

This repository is designed to be **equally accessible to both human engineers and AI agents**. Contributions can come from:
- 👤 **Human Contributors** - Engineers, researchers, and practitioners
- 🤖 **AI Agents** - Cursor, Claude, GPT, and other AI coding assistants
- 🤝 **Human-AI Pairs** - Collaborative contributions following co-agenticOS principles

### Quick Start for Different Users

#### For Human Contributors
```bash
# Clone and explore the repository
git clone https://github.com/Keven1894/co-agenticOS.git
cd co-agenticOS

# Study the reference implementation
cat domains/research-engineering/examples/Agent-dev-GIS-Research/README.md

# Use templates for your own projects
cp templates/rule-template.md your-project/rules/your-rule.md
```

#### For AI Agents (Cursor, Claude, etc.)
```bash
# When opening this project in Cursor:
# 1. Cursor automatically loads rules from .cursor/rules/
# 2. Follow system_behavior.md for project identity
# 3. Follow language_standards.md for English-only requirement
# 4. Follow content_standards.md for quality guidelines
# 5. Follow contribution_workflow.md for submitting changes

# Quick reference:
cat .cursor/README.md
```

#### For Human-AI Collaboration
```bash
# Initialize a new project with co-agenticOS patterns
curl -O https://raw.githubusercontent.com/Keven1894/co-agenticOS/main/templates/rule-template.md

# Create your domain-specific rules
mkdir -p rules/domains/research-engineering
cp templates/rule-template.md rules/domains/research-engineering/data-processing.md

# AI agents will follow .cursor/ rules when contributing
```

---

## Why It Matters

co-agenticOS turns AI coding assistants into true engineering collaborators — combining code, documentation, and culture into one continuous system. While most engineering practices were designed for human-only teams, co-agenticOS redefines this foundation for the AI-involved era.

## 🧭 Vision

Software is no longer written *by* humans alone — it's *co-created* by humans and AI agents.  
Yet most engineering practices, from Agile to DevOps, were designed for human-only teams.  
**co-agenticOS** redefines this foundation: it is an **Operating System for the culture of AI-involved software engineering.**

---

## 🧩 Core Principles

1. **Co-Creation over Automation**  
   AI agents are collaborators, not replacements.  
2. **Transparency over Speed**  
   Every agentic action must be observable, traceable, and explainable.  
3. **Continuous Reflection**  
   Every iteration includes documentation, reasoning, and summary.  
4. **Culture-Driven Development**  
   The most sustainable system is one that nurtures shared values and rituals.  
5. **Decentralized Self-Regulation over Top-Down Control**  
   Bottom-up ethical practice through shared cultural norms is more effective than waiting for centralized regulation that arrives too late.

> "In the absence of effective top-down regulation, bottom-up self-regulation  
>  through shared cultural norms is our best defense against AI risks."

See [`core/manifesto/00-principles.md`](core/manifesto/00-principles.md) for the complete cultural manifesto and philosophical foundation.

---

## ⚙️ Framework Structure

```
co-agenticOS/
│
├── core/                         ← Abstract Rules (Domain-independent)
│   ├── manifesto/                ← Core culture & behavior principles
│   ├── workflow/                 ← Universal agentic processes
│   ├── ai-routing/               ← AI model allocation rules
│   └── standards/                ← Universal quality standards
│
├── domains/                      ← Instance Rules (Domain-specific)
│   ├── research-engineering/     ← Research engineering rules
│   ├── software-development/    ← Software development rules
│   └── financial-analysis/      ← Financial analysis rules
│
├── templates/                    ← Structural scaffolds
│   ├── rule-template.md          ← Template for writing rules
│   ├── plan-template.md          ← Planning templates
│   └── reflection-template.md    ← Reflection templates
│
└── examples/                     ← Real-world demonstrations
    ├── cross-domain-workflow-integration.md ← Cross-domain pattern application
    └── domains/                   ← Domain-specific examples
        ├── research-engineering/
        │   └── Agent-dev-GIS-Research/ ← Complete GIS platform example
        └── financial-analysis/
            └── Personal-Tax-Assistant/ ← Complete tax processing example
```

---

## 🧠 Concept Hierarchy

| Concept | Meaning |
|---------|---------|
| **Rule** | A reusable human–AI collaboration behavior pattern |
| **Abstract Rule** | Domain-independent best practice |
| **Instance Rule** | Domain-specific implementation |
| **Template** | Structural scaffold for writing rules |
| **Example** | Real-world demonstration of applying a rule |

---

## 🔁 The Agentic Development Loop

1. **Plan** → AI drafts daily plan based on issues.  
2. **Implement** → Engineers and agents co-edit code in IDEs like Cursor.  
3. **Refactor** → Agents propose structural improvements; humans review.  
4. **Summarize** → Agents document and log daily changes automatically.  

This loop runs continuously — forming the "co-agentic flywheel."

---

## 🧰 Tooling Matrix

| Role | Tool | Function |
|------|------|-----------|
| Code Generation | **GPT-5 / Cursor** | Implement, test, refactor |
| Design & Docs | **Claude 4.5** | Architecture, risk, rationale |
| Long Context | **Gemini 1.5** | Research synthesis, multi-doc context |
| Automation | **n8n / MCP Server** | Daily summary, changelog sync |
| Docs Site | **MkDocs / Docusaurus** | Publish living documentation |

---

## 🧱 Getting Started

### Step 1: Understand the Framework
co-agenticOS is a **Rule & Template Framework** — not a codebase. You import its patterns into your own projects to build AI collaboration culture.

### Step 2: Study the Reference Example
Start with the **FIU GIS Agent Platform** example:
```bash
# Explore the complete reference implementation
domains/research-engineering/examples/Agent-dev-GIS-Research/
```

This example demonstrates:
- **System Behavior Rules**: Environment management, language policy, engineering standards
- **Development Workflow**: Four-phase lifecycle with strict documentation separation
- **Quality Standards**: Comprehensive code and documentation requirements
- **AI Collaboration**: Effective human-AI partnership patterns

### Step 3: Choose Your Domain
Select rules that match your project type:

**For Research Projects:**
- `domains/research-engineering/project-management.md` - Complete project management framework
- `domains/research-engineering/data-processing.md` - Data processing with AI assistance

**For Software Development:**
- `domains/software-development/` - Frontend, backend, and DevOps rules

**For Financial Analysis:**
- `domains/financial-analysis/tax-data-processing.md` - Tax data processing with AI assistance
- `domains/financial-analysis/examples/Personal-Tax-Assistant/` - Complete tax assistant example

### Step 4: Use Templates
Copy and customize templates for your project:
```bash
# Copy rule template
cp templates/rule-template.md your-project/rules/your-domain-rule.md

# Copy planning template
cp templates/PLAN.md your-project/plans/daily-plan.md

# Copy summary template
cp templates/Summary.md your-project/summaries/daily-summary.md
```

### Step 5: Implement the Workflow
Follow the **Agentic Development Loop**:
1. **Plan** → AI drafts daily plan, humans refine
2. **Implement** → Human-AI co-edit in Cursor
3. **Refactor** → AI suggests improvements, humans review
4. **Summarize** → AI documents changes, humans reflect

### Step 6: Learn from Cross-Domain Patterns
Study how patterns transfer across domains:
- `examples/cross-domain-workflow-integration.md` - How GIS patterns apply to financial analysis

---

## 🎯 Quick Start Examples

### For Individual Developers
1. **Browse Core Rules**: Start with `core/manifesto/00-principles.md`
2. **Study Reference Examples**: 
   - GIS Platform: `domains/research-engineering/examples/Agent-dev-GIS-Research/`
   - Tax Assistant: `domains/financial-analysis/examples/Personal-Tax-Assistant/`
3. **Choose Domain**: Select relevant rules from `domains/`
4. **Use Templates**: Copy templates from `templates/`

### For Teams
1. **Review Core Principles**: Go through `core/workflow/agentic-development-loop.md`
2. **Study Reference Implementations**: 
   - Research projects: GIS platform example
   - Financial projects: Personal Tax Assistant example
3. **Establish Domain Rules**: Create team-specific rules using templates
4. **Implement Workflows**: Use the agentic development loop

### For Organizations
1. **Assess Domains**: Review all available domain rules
2. **Study Cross-Domain Patterns**: Learn from `examples/cross-domain-workflow-integration.md`
3. **Create Standards**: Use core rules to establish organization-wide standards
4. **Implement Training**: Use examples and templates for team training

---

## 📜 License & Citation

MIT License — open and remixable.  

**If you use or adapt co-agenticOS**, please credit:
*"Based on co-agenticOS: The Culture of AI-Involved Software Engineering by Boyuan (Keven) Guan (2025)"*

**For academic papers, presentations, or articles**, see [CITATION.md](CITATION.md) for proper citation formats.

### Quick Citation (APA)
```
Guan, B. K. (2025). co-agenticOS: The Culture of AI-Involved Software Engineering 
    (Version 1.0.0) [Software framework]. GitHub. 
    https://github.com/Keven1894/co-agenticOS
```

---

## 🌐 Learn More

### Parent Framework
- [Agentic-AI Engineering Framework](https://github.com/Keven1894/Agentic-AI-Research-Roadmap) - Theoretical foundation and methodology
- [Framework DOI: 10.5281/zenodo.14279004](https://doi.org/10.5281/zenodo.14279004) - Permanent academic reference
- [Ecosystem Integration Guide](docs/ecosystem-integration.md) - How co-agenticOS fits into the broader framework

### co-agenticOS Documentation
- [Core Manifesto](core/manifesto/00-principles.md) - Cultural foundation and principles
- [GIS Platform Example](domains/research-engineering/examples/Agent-dev-GIS-Research/) - Research engineering reference
- [Tax Assistant Example](domains/financial-analysis/examples/Personal-Tax-Assistant/) - Financial analysis reference  
- [Cross-Domain Patterns](examples/cross-domain-workflow-integration.md) - Pattern transferability
- [Domain Rules](domains/) - Domain-specific implementations
- [Rule Templates](templates/) - Structural scaffolds
- [Roadmap](docs/roadmap.md) - Future vision and development plans
- [Project Evolution](docs/project-evolution.md) - The story of how co-agenticOS came to be
- [Contributors](docs/contributors.md) - Recognition of all contributors
- [Citation Guide](CITATION.md) - How to cite co-agenticOS in academic and professional work

---

## 👨‍💻 Author

**Boyuan (Keven) Guan**  
📧 keven1894@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/boyuan-keven-guan/)  

*Creator of co-agenticOS: The Culture of AI-Involved Software Engineering*

For more information about the author, see [AUTHOR.md](AUTHOR.md).

---

**co-agenticOS** — where engineers and agents build together.