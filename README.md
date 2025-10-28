# co-agenticOS  
### The Culture of AI-Involved Software Engineering  

**co-agenticOS** is a living operating system for human–AI collaboration in software development.  
It defines the culture, workflows, and shared rituals that allow engineers and agents to co-create, iterate, and document software continuously.

> *"Culture is the new compiler."*  
> — co-agenticOS Manifesto

---

## ⚠️ Important: This is NOT a Codebase

**co-agenticOS is not a codebase.**  
It's a **Rule & Template Framework** — you import its structure into your own repo to build your AI collaboration culture.

### How to Use co-agenticOS

```bash
# Initialize a new project's rule system
curl -O https://raw.githubusercontent.com/your-org/co-agenticOS/main/templates/rule-template.md

# Then create your domain-specific rules:
mkdir -p rules/domains/research-engineering
cp templates/rule-template.md rules/domains/research-engineering/data-processing.md
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

See [`core/manifesto/00-principles.md`](core/manifesto/00-principles.md) for the full cultural manifesto and philosophical foundation.

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
        └── research-engineering/
            └── Agent-dev-GIS-Research/ ← Complete reference implementation
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
- `domains/financial-analysis/` - Risk assessment and data validation rules

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
2. **Study GIS Example**: Explore `domains/research-engineering/examples/Agent-dev-GIS-Research/`
3. **Choose Domain**: Select relevant rules from `domains/`
4. **Use Templates**: Copy templates from `templates/`

### For Teams
1. **Review Core Principles**: Go through `core/workflow/agentic-development-loop.md`
2. **Study Reference Implementation**: Analyze the GIS platform example
3. **Establish Domain Rules**: Create team-specific rules using templates
4. **Implement Workflows**: Use the agentic development loop

### For Organizations
1. **Assess Domains**: Review all available domain rules
2. **Study Cross-Domain Patterns**: Learn from `examples/cross-domain-workflow-integration.md`
3. **Create Standards**: Use core rules to establish organization-wide standards
4. **Implement Training**: Use examples and templates for team training

---

## 📜 License

MIT License — open and remixable.  
If you use or adapt co-agenticOS in your org, please credit:

*"Based on co-agenticOS: The Culture of AI-Involved Software Engineering"*

---

## 🌐 Learn More

- [Core Manifesto](core/manifesto/00-principles.md) - Cultural foundation
- [Reference Implementation](domains/research-engineering/examples/Agent-dev-GIS-Research/) - Complete GIS platform example
- [Cross-Domain Patterns](examples/cross-domain-workflow-integration.md) - Pattern transferability
- [Domain Rules](domains/) - Domain-specific implementations
- [Rule Templates](templates/) - Structural scaffolds

---

## 👨‍💻 Author

**Boyuan (Keven) Guan**  
📧 keven1894@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/boyuan-keven-guan/)  

*Creator of co-agenticOS: The Culture of AI-Involved Software Engineering*

For more information about the author, see [AUTHOR.md](AUTHOR.md).

---

**co-agenticOS** — where engineers and agents build together.