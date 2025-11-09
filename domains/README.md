# Domain Rules - Instance Layer
### Domain-Specific Implementations of Co-agenticOS Principles

**Purpose**: This directory contains domain-specific implementations of abstract core rules. Each domain adapts universal principles to its specific context, requirements, and constraints.

---

## 📁 Directory Structure

```
domains/
├── research-engineering/          ← Research and academic projects
│   ├── abstract.md               ← Domain overview and principles
│   ├── data-processing.md        ← Data processing rule
│   ├── project-management.md     ← Project management patterns
│   └── examples/
│       └── Agent-dev-GIS-Research/  ← Complete GIS platform reference
├── financial-analysis/           ← Financial and tax processing
│   ├── abstract.md               ← Domain overview with security focus
│   ├── tax-data-processing.md    ← Tax processing with PII protection
│   └── examples/
│       └── Personal-Tax-Assistant/  ← Complete tax assistant reference
└── software-development/         ← Software engineering (structure established)
```

---

## 🎯 What Are Domain Rules?

### Definition
**Domain Rules** are **instance rules** that implement **abstract core principles** in specific professional contexts.

| Layer | Type | Example |
|-------|------|---------|
| **Core** | Abstract | "Documentation is Dialogue" (universal principle) |
| **Domain** | Instance | "Tax processing requires IRS-compliant audit trails" (specific implementation) |

### Relationship to Core
```
Core Principle → Domain Adaptation → Practical Implementation
     ↓                    ↓                     ↓
  Manifesto    →  Domain Abstract  →  Domain Rules + Examples
```

---

## 📚 Available Domains

### 1. Research Engineering
**Status**: ✅ Complete with production reference implementation

**Overview**: Human-AI collaboration in research processes, data collection, processing, analysis, and validation.

**Key Files**:
- **[abstract.md](research-engineering/abstract.md)** - Domain principles
  - Reproducibility First
  - Data Integrity
  - Transparent Methodology
  - Continuous Learning

- **[data-processing.md](research-engineering/data-processing.md)** - Data processing patterns
- **[project-management.md](research-engineering/project-management.md)** - Research project workflows

**Reference Implementation**:
- **[Agent-dev-GIS-Research/](research-engineering/examples/Agent-dev-GIS-Research/)** - FIU GIS Platform
  - **Context**: Florida International University GIS research department
  - **Problem**: Knowledge loss when programmers leave (hire-train-leave cycle)
  - **Solution**: AI agent system with vector database for institutional knowledge preservation
  - **Innovation**: ~2 weeks development eliminated months of repeated training
  - **Features**: Modular rule system, 4-phase documentation lifecycle, vector DB integration
  - **Impact**: Breaks hire-train-leave knowledge loss cycle

**When to Use**:
- Academic research projects
- Scientific data processing
- Research tool development
- Institutional knowledge management

---

### 2. Financial Analysis
**Status**: ✅ Complete with production reference implementation

**Overview**: AI-assisted financial data processing, tax preparation, risk assessment, and compliance validation with highest security standards.

**Key Files**:
- **[abstract.md](financial-analysis/abstract.md)** - Domain principles with security focus
  - Security and Privacy First
  - Accuracy and Compliance
  - Transparent Methodology
  - Continuous Validation

- **[tax-data-processing.md](financial-analysis/tax-data-processing.md)** - Tax processing with PII protection

**Reference Implementation**:
- **[Personal-Tax-Assistant/](financial-analysis/examples/Personal-Tax-Assistant/)** - Production Tax System
  - **Context**: Personal U.S. federal tax filing (2023-2025+)
  - **Problem**: Emotional burden and time consumption of annual tax preparation
  - **Solution**: AI-powered automation from raw PDFs to CPA-ready reports
  - **Innovation**: LLM as universal PDF format adapter (handles varying bank formats)
  - **Security**: Zero PII exposures in 3+ years, critical-priority data privacy rules
  - **Impact**: 80% time reduction (10 hours → 2 hours), 100% CPA acceptance rate
  - **Breakthrough**: Non-finance professional producing professional-quality tax reports

**When to Use**:
- Financial data processing
- Tax preparation and filing
- Compliance-heavy workflows
- High-security data handling
- Professional reporting requirements

---

### 3. Software Development
**Status**: ⏳ Structure established, examples pending

**Overview**: General software engineering domain covering frontend, backend, DevOps, and full-stack development.

**Planned Coverage**:
- Frontend development (React, Vue, Angular)
- Backend development (Node.js, Python, Java)
- DevOps and infrastructure
- API design and development
- Testing and quality assurance

**When to Use**:
- General software projects
- Web applications
- API development
- Infrastructure management

**Status**: Awaiting community contributions and reference implementations

---

## 🔍 How to Choose a Domain

### Decision Tree

```
What type of project are you working on?

├─ Academic/Research?
│  └─ Use: research-engineering/
│     Examples: GIS platform, data analysis, scientific computing
│
├─ Financial/Compliance-Heavy?
│  └─ Use: financial-analysis/
│     Examples: Tax processing, risk analysis, audit systems
│
├─ General Software Development?
│  └─ Use: software-development/
│     Examples: Web apps, APIs, mobile apps
│
└─ Multiple Domains?
   └─ Use: Cross-domain patterns from ../examples/
      See: cross-domain-workflow-integration.md
```

---

## 📖 How to Use Domain Rules

### For New Projects

1. **Read Domain Abstract**
   - Start with `abstract.md` in your chosen domain
   - Understand domain-specific principles
   - Review success metrics

2. **Study Reference Implementation**
   - Explore `examples/` within the domain
   - See how principles are applied in production
   - Learn from real-world patterns

3. **Apply Domain Rules**
   - Use specific rule files (e.g., `data-processing.md`)
   - Adapt patterns to your context
   - Follow security and compliance guidelines

4. **Create Project Rules**
   - Use `../templates/rule-template.md`
   - Customize for your specific needs
   - Maintain alignment with domain abstract

### For Existing Projects

1. **Assess Current State**
   - Compare current practices with domain abstract
   - Identify gaps in coverage
   - Prioritize improvements

2. **Incremental Adoption**
   - Start with one rule (e.g., documentation standards)
   - Validate effectiveness
   - Expand gradually

3. **Reference Examples**
   - Compare with reference implementations
   - Adopt proven patterns
   - Customize to your needs

---

## 🎓 Domain Abstracts

Each domain has an `abstract.md` that defines:

### Required Sections
1. **Domain Definition** - What this domain encompasses
2. **Core Principles** - Fundamental beliefs and values
3. **Common Patterns** - Recurring collaboration patterns
4. **Success Metrics** - How to measure effectiveness
5. **Related Domains** - Connections to other domains
6. **Implementation Guidelines** - How to use the domain rules

### Why Abstracts Matter
- Establish domain-specific culture
- Guide rule creation
- Ensure consistency
- Enable cross-domain learning

---

## 📊 Domain Coverage Matrix

| Domain | Abstract | Rules | Examples | Production-Tested | Status |
|--------|----------|-------|----------|-------------------|--------|
| **Research Engineering** | ✅ | ✅ (2) | ✅ (1) | ✅ 3+ years | Complete |
| **Financial Analysis** | ✅ | ✅ (1) | ✅ (1) | ✅ 3+ years | Complete |
| **Software Development** | ⏳ | ⏳ | ⏳ | - | In Progress |
| **Data Science** | - | - | - | - | Planned Q1 2026 |
| **Mobile Development** | - | - | - | - | Planned Q1 2026 |
| **DevOps** | - | - | - | - | Planned Q1 2026 |

---

## 🌟 Reference Implementation Highlights

### What Makes Them Special

Both reference implementations are **real production systems** with **proven track records**:

#### GIS Agent Platform (Research Engineering)
- **Real**: FIU GIS research department production system
- **Proven**: Solved actual knowledge loss problem
- **Innovation**: Vector DB + PostgreSQL hybrid architecture
- **Impact**: Eliminated months of training time
- **Time**: ~2 weeks development for lasting institutional value

#### Personal Tax Assistant (Financial Analysis)
- **Real**: Personal tax filing system (2023-2025+)
- **Proven**: 3+ years, zero security incidents
- **Innovation**: LLM as universal PDF format adapter
- **Impact**: 80% time reduction, 100% CPA acceptance
- **Quality**: Non-professional producing professional-quality reports

### Why Real Examples Matter
- ✅ Demonstrate feasibility
- ✅ Validate security and compliance
- ✅ Provide learning templates
- ✅ Prove ROI and impact
- ✅ Show production challenges and solutions

---

## 🤝 Contributing New Domains

### When to Create a New Domain

Create a new domain when:
- ✅ Your field has distinct principles and patterns
- ✅ Rules don't fit existing domains
- ✅ You have production examples to share
- ✅ Domain has broad applicability

**Don't create when**:
- ❌ It's a subdomain of existing domain
- ❌ You only have theoretical rules (need examples)
- ❌ Differences are minor (use existing + customize)

### Domain Creation Process

1. **Research Phase**
   - Study existing domains and abstracts
   - Identify unique principles and patterns
   - Validate need with community

2. **Design Phase**
   - Create domain abstract using template
   - Define core principles (3-5 principles)
   - Establish success metrics
   - Map related domains

3. **Implementation Phase**
   - Write 2-3 core domain rules
   - Create reference implementation
   - Test in production (if possible)
   - Document lessons learned

4. **Contribution Phase**
   - Follow `../CONTRIBUTING.md`
   - Submit PR with complete domain
   - Engage with review feedback
   - Update domain coverage matrix

### Domain Template Structure

```
domains/your-domain/
├── abstract.md              ← Required: Domain overview
├── rule-1.md                ← At least 2-3 core rules
├── rule-2.md
└── examples/
    └── Reference-Example/   ← Recommended: Production example
        ├── README.md
        └── rules/
```

---

## 🔗 Cross-Domain Patterns

Domains share common patterns that can be transferred:

### Universal Patterns
- **Documentation Lifecycle**: 4-phase process from research-engineering
- **Security-First Design**: PII protection from financial-analysis
- **AI Routing**: Model selection strategies from core
- **Validation Workflows**: Multi-stage verification patterns

### Cross-Domain Examples
See **[../examples/cross-domain-workflow-integration.md](../examples/cross-domain-workflow-integration.md)** for how GIS patterns apply to financial analysis.

---

## 📈 Domain Evolution

### Current State (Version 1.0.0)
- 2 complete domains with production examples
- 1 domain structure established
- Strong foundation in research and financial analysis

### Near Future (Q1-Q2 2026)
- Data Science & Machine Learning
- Mobile Development
- DevOps & Infrastructure
- Healthcare (with compliance focus)

### Long Term (2026+)
- Legal & Compliance
- Education
- Gaming & Interactive Media
- IoT & Embedded Systems
- Blockchain & Web3

See **[../docs/roadmap.md](../docs/roadmap.md)** for detailed timeline.

---

## 🎯 Domain Success Criteria

### Quality Metrics
- ✅ Clear abstract with 3-5 core principles
- ✅ At least 2 specific rules with examples
- ✅ Reference implementation (production-tested preferred)
- ✅ Clear relationship to core principles
- ✅ Success metrics defined

### Community Metrics
- Adoption by 5+ projects
- Positive feedback from domain practitioners
- Contributions from domain experts
- Citations in domain-specific resources

---

## 🔍 Related Resources

### Within co-agenticOS
- **Core Rules**: [`../core/`](../core/) - Abstract principles these domains implement
- **Templates**: [`../templates/`](../templates/) - Use these to create domain rules
- **Examples**: [`../examples/`](../examples/) - Cross-domain pattern applications

### External Resources
- **Parent Framework**: [Agentic-AI Engineering Framework](https://github.com/Keven1894/Agentic-AI-Research-Roadmap)
- **Framework DOI**: [10.5281/zenodo.14279004](https://doi.org/10.5281/zenodo.14279004)

---

## 📞 Questions?

- **Domain Selection**: Not sure which domain fits? Open a GitHub Discussion
- **New Domain**: Want to contribute a domain? See `../CONTRIBUTING.md`
- **Domain Improvements**: Suggestions for existing domains? Open a GitHub Issue
- **Email**: keven1894@gmail.com for strategic domain discussions

---

*Domains are where co-agenticOS principles meet real-world practice. Each domain tells a story of how culture becomes code.*

**"From abstract principles to concrete impact."** — That's the journey from core/ to domains/.

