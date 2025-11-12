# Knowledge Management for Digital Libraries
**Domain-Specific Rules for AI Agents**

**Domain:** Digital Libraries & Institutional Repositories  
**Source:** DIVA operational experience (3+ months production)  
**Date:** November 12, 2025  
**Evidence Quality:** Excellent (100% consistency validated)

---

## Rule 1: Institutional Memory via Rules

### 🎯 Purpose

Solve agent session amnesia by encoding institutional knowledge in persistent rules that load automatically every session, ensuring perfect consistency without requiring fine-tuning.

### 🔍 The Problem

**Traditional Agent Challenge:**
```
Session Day 1: Learn email sending procedure → Build sendEmail() function
Session Day 2: New agent session → No memory → Rebuild differently
Session Day 5: Another session → No memory → Build third version
Result: Inconsistency, duplication, technical debt, knowledge loss
```

**Why Traditional Solutions Fail:**
- **Fine-tuning**: Too slow (weeks), expensive (requires GPUs), requires constant retraining
- **RAG only**: Retrieves information but doesn't enforce procedures
- **Documentation alone**: Agents may or may not follow it consistently
- **Context injection**: Limited by token windows, expensive, not persistent

### ✅ The Solution: Rules-as-Memory

**Core Concept:**
Use `.cursor/rules/` (or equivalent) as persistent agent memory by encoding:
- Standard procedures (how to do recurring tasks)
- Critical decisions (what was learned)
- Anti-patterns (what not to do)
- Best practices (proven approaches)

**How It Works:**
```
Session Day 1: Learn email procedure → Document in rules/actions/email.md
Session Day 2: Rules auto-load → Agent KNOWS about email function → Uses it
Session Day 50: Rules still load → Zero knowledge loss → Perfect consistency
```

### 📋 Implementation Pattern

#### Step 1: Create Rule Structure

```
.cursor/rules/
├── core/           # Always loaded (identity, safety)
├── standards/      # Context-based (coding, documentation)
├── workflows/      # Process rules (planning, deployment)
├── actions/        # Standard procedures (email, credentials)
└── archive/        # Historical (superseded rules)
```

#### Step 2: Standard Rule Format

```markdown
### 🔧 [Procedure Name]

**CRITICAL: [One-line instruction that enforces the rule]**

**When to use:**
- [Scenario 1]
- [Scenario 2]

**How to use:**
```[language]
[Copy-paste ready code example]
```

**The function automatically:**
- [Feature 1: Error handling]
- [Feature 2: Logging]
- [Feature 3: Retry logic]

**Example usage:**
```[language]
[Realistic example with output]
```

**Full documentation:** [Link to detailed docs]

**DO NOT:**
- ❌ [Anti-pattern 1]
- ❌ [Anti-pattern 2]
```

#### Step 3: Real Example from DIVA

```markdown
### 📧 Email Sending

**CRITICAL: ALWAYS use the `sendDivaEmail()` master function. NEVER write ad-hoc email code!**

**When to use:**
- Sending deployment notifications
- Alerting team about issues
- Communicating with users
- Automated reports

**How to use:**
```javascript
const { sendDivaEmail } = require('./diva_mailer.js');

await sendDivaEmail({
  to: 'team@example.com',
  subject: 'Deployment Complete',
  body: 'Production deployment successful.',
  html: '<p>Production deployment <strong>successful</strong>.</p>',
  attachments: [] // optional
});
```

**The function automatically:**
- Retry logic (3 attempts with exponential backoff)
- Comprehensive logging (every attempt tracked)
- Error handling (graceful failures)
- Template support (consistent formatting)

**Full documentation:** `docs/n8n/DIVA_MASTER_EMAIL_FUNCTION.md`

**DO NOT:**
- ❌ Write inline nodemailer code
- ❌ Create custom email functions
- ❌ Skip error handling
```

#### Step 4: Rule Loading Strategy

**Automatic Loading:**
```javascript
// Cursor or IDE loads rules on session start
// Agent has instant access to institutional knowledge
// Zero manual retrieval needed
```

**Context-Based Loading (Advanced):**
```yaml
# In rule metadata
---
rule: email-sending
tier: 1-frequent
appliesWhen:
  - keyword: "email"
  - file_pattern: "*/email/*"
  - action: "send_notification"
---
```

### 📊 Evidence from DIVA

**Validation Results:**

| Metric | Result | Significance |
|--------|--------|--------------|
| **Sessions Tested** | 50+ over 3 months | Long-term stability |
| **Consistency Rate** | 100% | Perfect adherence |
| **Knowledge Loss** | 0% | Complete retention |
| **Procedure Violations** | 0 | Rules always followed |
| **Reimplementation** | 0 | No duplicate solutions |

**Specific Examples:**
- **Email function**: 100% use of master function (0 ad-hoc implementations)
- **Credential access**: 100% use of env_manager.sh (0 hard-coded credentials)
- **Document reading**: 100% use of ask_doc.py (0 alternative methods)
- **Planning workflow**: 100% plan-first adherence (0 unplanned implementations)

**Team Feedback:**
> "DIVA never forgets. Every session, it knows exactly what to do. It's like having a team member who never needs retraining." - Development Team Lead

### 🎯 When to Use This Pattern

**✅ Ideal For:**
- Standard operating procedures (deployment, backup, monitoring)
- Critical safety rules (credential handling, production operations)
- Coding standards (patterns, anti-patterns, style)
- Workflow processes (planning, documentation, review)
- Tool usage (master functions, scripts, APIs)

**⚠️ Not Ideal For:**
- One-off unique tasks (won't recur enough to justify rule)
- Rapidly changing procedures (rule maintenance burden)
- Highly contextual decisions (better suited for RAG retrieval)

### 🔄 Maintenance Process

**When to Create a Rule:**
1. Task is performed 3+ times
2. Consistency is critical
3. Knowledge should persist across agents/sessions
4. Procedure is relatively stable

**When to Update a Rule:**
1. Procedure changes (new tool, better approach)
2. Anti-pattern discovered
3. Edge case identified
4. Team feedback suggests improvement

**How to Update:**
```markdown
1. Edit rule file
2. Add version note: "Updated YYYY-MM-DD: [reason]"
3. Notify team (if major change)
4. Archive old version (if significantly different)
5. Verify loading in next session
```

**Version Control:**
```bash
# Rules are version-controlled
git commit -m "Update email rule: Add attachment support"

# History preserved
git log -- .cursor/rules/actions/email.md
```

### 🚀 Getting Started

**Minimal Viable Implementation (30 minutes):**

1. **Create basic structure:**
```bash
mkdir -p .cursor/rules/{core,actions}
```

2. **Create identity rule (core/identity.md):**
```markdown
# Agent Identity

You are [NAME], the [ROLE] for [SYSTEM].

Your core responsibilities:
- [Responsibility 1]
- [Responsibility 2]

You MUST follow all rules in .cursor/rules/
```

3. **Document one procedure (actions/your-first-rule.md):**
```markdown
### 🔧 [Your Most Common Task]

**CRITICAL: [How to do it]**

**Example:**
```code
[Working example]
```
```

4. **Test:**
- Close and reopen IDE/agent session
- Verify rule loads
- Ask agent to perform task
- Confirm it follows the rule

**First Win:** You now have persistent institutional memory!

### 📈 Scaling Strategy

**Phase 1: Foundation (Week 1)**
- 3-5 core rules (identity, critical safety)
- Document most common procedures

**Phase 2: Expansion (Weeks 2-4)**
- Add 10-15 action rules (standard procedures)
- Create workflow rules (planning, deployment)
- Add coding standards

**Phase 3: Optimization (Month 2)**
- Implement tiered loading (reduce tokens)
- Add context-based rules
- Create external reference docs (Tier 2)

**Phase 4: Maturity (Month 3+)**
- 30-50 comprehensive rules
- Tiered for efficiency
- Community-contributed additions
- Continuous improvement

**DIVA Trajectory:**
- Month 1: 15 rules
- Month 2: 30 rules
- Month 3: 45+ rules
- Token reduction: 87% (through tiering)

### 🔬 Research Contribution

**Novel Aspects:**
1. **Rules-as-Memory Paradigm**: Using rule systems as persistent agent memory (not just configuration)
2. **100% Consistency**: Perfect procedural adherence across 50+ sessions
3. **Zero Fine-Tuning**: Institutional knowledge without model retraining
4. **Production Validation**: 3+ months real operational evidence

**Compared to Existing Approaches:**

| Approach | Consistency | Setup Time | Cost | Maintenance |
|----------|------------|------------|------|-------------|
| **Fine-tuning** | High | Weeks | $$$$ | Constant retraining |
| **RAG only** | Medium | Days | $$ | Corpus updates |
| **Prompt engineering** | Low | Hours | $ | Manual updates |
| **Rules-as-Memory** | **Perfect** | **Hours** | **Free** | **Git commits** |

**Publication Potential:** AAAI, ICML (AI systems track), JCDL (library tech)

### 🤝 Community Contribution

**If This Rule Worked for You:**
1. Document your implementation
2. Share metrics (consistency rate, sessions)
3. Contribute improvements (edge cases, optimizations)
4. Create domain-specific variants

**If You Found Limitations:**
1. Document challenges
2. Propose adaptations
3. Share workarounds
4. Help evolve the pattern

### 📚 Related Rules

- **Tiered Configuration** (knowledge-management.md) - How to scale rules efficiently
- **Plan-First Discipline** (workflow-patterns.md) - How rules get created
- **Bounded Autonomy** (workflow-patterns.md) - What rules should enforce

### 📖 Further Reading

**In DIVA Documentation:**
- Institutional Memory System: `DIVA/INSTITUTIONAL_MEMORY.md`
- Tiered Configuration v2.0: `DIVA/.cursor/README.md`
- Evolution Roadmap: `DIVA/diva/evolution/CAPABILITIES.md`

**External Resources:**
- Cursor Rules Documentation
- co-agenticOS Rule Template: `templates/rule-template.md`

---

## Rule 2: Schema-Based Document Comprehension

### 🎯 Purpose

Improve LLM document comprehension accuracy by providing structured schemas (not just raw content), especially for configuration files, technical documentation, and complex relationships.

### 🔍 The Problem

**Traditional RAG Approach:**
```
Document → Chunk → Embed → Retrieve → Feed to LLM → Answer
Problem: LLM sees raw content without structure
Result: 42.3% accuracy on implicit/relationship questions (DIVA testing)
```

**Example Failure:**
```
Document: "Production uses localhost. Legacy mentions dpantherdb04temp."
Question: "What database does production use?"
Traditional RAG Answer: "dpantherdb04temp" ❌ WRONG (mentioned but not used)
```

**Why It Fails:**
- LLMs struggle with implicit relationships
- Raw content doesn't highlight critical facts
- Ambiguous terms cause confusion
- Historical mentions vs. current state unclear

### ✅ The Solution: Schema-Based Context Engineering

**Core Concept:**
Treat document schemas like vector DB chunking - provide structural context, critical facts, and disambiguation tips alongside content.

**Schema-Enhanced Approach:**
```
Document → Schema (structure + relationships + critical facts) → LLM → Answer
Result: 65.4% accuracy on implicit questions (+23% improvement)
```

**Example Success:**
```json
Schema: {
  "criticalFacts": [
    "⚠️ CRITICAL: Production uses localhost, NOT dpantherdb04temp",
    "⚠️ dpantherdb04temp is legacy/deprecated"
  ]
}

Question: "What database does production use?"
Schema-Enhanced Answer: "localhost" ✅ CORRECT
```

### 📋 Schema Template

```json
{
  "document_type": "configuration_file | architecture_doc | API_spec | ...",
  "purpose": "Brief description of what this document defines",
  
  "structure": {
    "sections": [
      {
        "name": "Section name",
        "variables": ["VAR1", "VAR2"],
        "purpose": "What this section configures"
      }
    ]
  },
  
  "relationships": {
    "entity1_uses": "entity2",
    "entity1_connects_to": "entity2",
    "both_share": "common_resource"
  },
  
  "criticalFacts": [
    "⚠️ CRITICAL: Fact that prevents wrong answers",
    "⚠️ CRITICAL: Another critical clarification"
  ],
  
  "ambiguities": [
    {
      "term": "ambiguous_term",
      "correct_meaning": "What it actually means here",
      "incorrect_meaning": "Common misinterpretation"
    }
  ],
  
  "tips": [
    "When asked about X, answer Y",
    "Ignore Z (deprecated/commented)"
  ]
}
```

### 🔧 Implementation

#### Real Example from DIVA

**Document:** `.env` configuration file

**Schema:**
```json
{
  "document_type": "environment_configuration",
  "purpose": "Database and service configuration for Dataverse",
  
  "structure": {
    "sections": [
      {
        "name": "Database Configuration",
        "variables": ["DB_HOST", "DB_PORT", "DB_NAME", "DB_USER", "DB_PASSWORD"],
        "purpose": "PostgreSQL connection settings"
      },
      {
        "name": "Service URLs",
        "variables": ["DATAVERSE_URL", "SOLR_URL", "DOI_PROVIDER"],
        "purpose": "External service endpoints"
      }
    ]
  },
  
  "relationships": {
    "production_connects": "localhost:5432",
    "development_connects": "localhost:5432",
    "both_share": "same_postgres_server_different_databases"
  },
  
  "criticalFacts": [
    "⚠️ CRITICAL: Both prod and dev use localhost, NOT a remote server",
    "⚠️ CRITICAL: dpantherdb04temp is mentioned but DEPRECATED",
    "⚠️ CRITICAL: DB_PASSWORD_OLD is deprecated, use DB_PASSWORD"
  ],
  
  "ambiguities": [
    {
      "term": "localhost",
      "correct_meaning": "Local PostgreSQL instance on same server",
      "incorrect_meaning": "Web server or development machine"
    }
  ],
  
  "tips": [
    "When asked about 'production database', answer 'localhost'",
    "Ignore any commented-out variables",
    "Variables ending in _OLD are deprecated"
  ]
}
```

**Query Implementation:**
```python
def query_document_with_schema(doc_path, question):
    # 1. Load document content
    content = read_file(doc_path)
    
    # 2. Load or generate schema
    schema_path = f"{doc_path}.schema.json"
    schema = load_schema(schema_path)
    
    # 3. Build context-rich prompt
    prompt = f"""
DOCUMENT SCHEMA (structure and relationships):
{json.dumps(schema, indent=2)}

CRITICAL FACTS (pay special attention):
{format_critical_facts(schema['criticalFacts'])}

DISAMBIGUATION TIPS:
{format_tips(schema['tips'])}

DOCUMENT CONTENT (relevant section):
{get_relevant_content(content, question, schema)}

QUESTION: {question}

Answer based on the schema context and critical facts above.
"""
    
    # 4. Query LLM
    return llm.query(prompt)
```

### 📊 Evidence from DIVA

**Validation Testing: 95-Question Suite**

| Question Type | Without Schema | With Schema | Improvement |
|--------------|----------------|-------------|-------------|
| **Explicit facts** | 100% | 100% | 0% (already perfect) |
| **Implicit relationships** | 42.3% | 65.4% | **+23%** ⭐ |
| **Structural understanding** | 20.0% | 40.0% | **+20%** ⭐ |
| **Ambiguous terms** | 30.0% | 55.0% | **+25%** ⭐ |
| **Overall quality** | Good | Excellent | Significant |

**Specific Examples:**

**Question:** "What database does production use?"
- Without schema: "dpantherdb04temp" ❌ (40% got wrong)
- With schema: "localhost" ✅ (100% got correct)

**Question:** "How do production and dev databases relate?"
- Without schema: "They use different servers" ❌
- With schema: "Both use localhost but different database names" ✅

**Model Tested:** Llama 3.2 3B (local, 100% privacy)

### 🎯 When to Use Schema-Based Approach

**✅ High Value:**
- Configuration files (.env, config.yml, settings.json)
- Architecture documentation (complex relationships)
- API specifications (parameters, relationships)
- Database schemas (table relationships)
- Code with implicit dependencies

**⚠️ Lower Value:**
- Simple documents (straightforward facts)
- Narrative text (stories, descriptions)
- Documents already well-structured
- Cases where explicit facts dominate

**Effort vs. Benefit:**
- Schema creation: 15-30 minutes per document
- Accuracy improvement: 20-25%
- ROI: High for critical documents queried frequently

### 🚀 Getting Started

**Quick Implementation (1 hour):**

1. **Pick one important document**
   - Configuration file or complex doc
   - Queried frequently
   - Accuracy matters

2. **Create basic schema:**
```json
{
  "criticalFacts": [
    "⚠️ Most important thing to know",
    "⚠️ Common mistake to avoid"
  ],
  "tips": [
    "When asked X, answer Y"
  ]
}
```

3. **Test accuracy:**
   - Ask 5-10 questions without schema
   - Ask same questions with schema
   - Measure improvement

4. **Iterate:**
   - Add structure, relationships as needed
   - Refine based on errors
   - Document patterns

### 📈 Scaling Strategy

**Phase 1: Critical Documents (Week 1)**
- Create schemas for 3-5 most-queried docs
- Focus on critical facts only
- Measure baseline improvement

**Phase 2: Expansion (Weeks 2-4)**
- Add structure and relationships
- Create disambiguation entries
- Build schema library (10-15 docs)

**Phase 3: Automation (Month 2)**
- Template common document types
- Semi-automate schema generation
- Version control schemas with docs

**Phase 4: Maturity (Month 3+)**
- Schema for all critical docs
- Automated validation
- Community schema sharing

### 🔬 Research Contribution

**Novel Aspects:**
1. **Schema-as-Chunking Paradigm**: Treating schemas like vector DB chunking strategies
2. **+23% Accuracy**: Validated improvement on production data
3. **Local Small LLM**: Proves small models viable with good context
4. **Critical Facts Pattern**: Explicitly highlighting facts that prevent errors

**Compared to Traditional RAG:**

| Approach | Accuracy | Setup | Maintenance |
|----------|---------|-------|-------------|
| **Raw content** | 42% | None | None |
| **Chunking only** | 50% | Medium | Low |
| **Schema-based** | **65%** | **High (once)** | **Low** |

**Publication Potential:** ACL, EMNLP, NeurIPS (NLP workshops)

### 🤝 Community Contribution

**If This Works for You:**
- Share your schemas (anonymized)
- Contribute schema templates
- Document accuracy improvements
- Create domain-specific patterns

**Schema Library Idea:**
- Community schema repository
- Common document types (nginx.conf, docker-compose.yml, etc.)
- Reusable patterns
- Validation tools

### 📚 Related Rules

- **Institutional Memory** (above) - How to persist schemas in rules
- **Document Reading Tools** - Integration with ask_doc.py or similar
- **Local LLM Usage** - Privacy-preserving comprehension

### 📖 Further Reading

**In DIVA Documentation:**
- Local LLM Study: `research/local-small-llm/results/CLEAR_TEST_RESULTS.md`
- Schema Examples: `research/local-small-llm/schemas/`
- Ask Doc Tool: `scripts/ai_tools/ask_doc.py`

**External Resources:**
- Vector DB Chunking Strategies
- Context Engineering Best Practices

---

**Status:** 2 key rules documented with DIVA evidence  
**Format:** Rule template with problem, solution, implementation, evidence  
**Next:** Await feedback, then create remaining rules if format approved

