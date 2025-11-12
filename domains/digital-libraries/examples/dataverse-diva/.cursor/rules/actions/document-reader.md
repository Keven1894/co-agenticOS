# Local LLM Document Reading
**Action Rule - Tier 1 (Context: document queries, sensitive data)**

---

## 📖 Document Reading Tool

### Use: `ask_doc.py` for Local Document Comprehension

**Why local LLM:**
- ✅ Privacy: Sensitive data stays on local machine
- ✅ Cost: No API charges
- ✅ Speed: 3-4 seconds (fast enough)
- ✅ Accuracy: 52.6% on complex questions (validated)

**Tool location:** `scripts/ai_tools/ask_doc.py`

---

## 🔧 How to Use

### Basic Query

```bash
python scripts/ai_tools/ask_doc.py \
    --file docs/configuration/DATABASE_SETUP.md \
    --question "What database does production use?"

# Output:
# Answer: Production uses localhost (PostgreSQL on same server)
# Confidence: High
# Response time: 3.61s
```

### With Schema (23% Better Accuracy!)

```bash
python scripts/ai_tools/ask_doc.py \
    --file .env \
    --schema .env.schema.json \
    --question "What is the database host for production?"

# Schema provides:
# - Structure (sections, variables)
# - Critical facts (localhost, not remote)
# - Disambiguation (localhost = local postgres, not web server)
#
# Result: 65.4% accuracy (vs 42.3% without schema)
```

### Multiple Documents

```bash
python scripts/ai_tools/ask_doc.py \
    --files docs/deployment/*.md \
    --question "How do I deploy to production?"

# Aggregates information from multiple docs
```

---

## 📊 Model Selection

### Use Llama 3.2 3B (Default)

**Performance (Validated):**
- Explicit questions: 100% accuracy
- Implicit questions: 65.4% (with schema)
- Response time: 3.61s average
- Reliability: 100% (0 errors in 190 queries)

**When to use:**
- Configuration file queries
- Documentation lookup
- Sensitive data (stays local)
- Frequent queries (no API costs)

---

### ⚠️ DO NOT Use Llama 3.2 1B

**CRITICAL PITFALL DISCOVERED:**

**What DIVA learned (Month 2):**
- Tried 1B model for efficiency
- Discovered built-in censorship
- Model REFUSES to answer credential questions
- 40% accuracy drop

**Evidence:**
```
Question: "What is DB_PASSWORD set to?"
Llama 3.2 1B: "I cannot provide credential information" (REFUSED)
Llama 3.2 3B: "The DB_PASSWORD is set to..." (ANSWERED)

Result: 1B model unusable for credential queries
```

**Lesson:** Model size alone doesn't determine suitability. Behavioral characteristics matter!

**Rule:** 
- ✅ Use 3B+ for credential/sensitive queries
- ✅ Test behavioral characteristics before deploying
- ✅ Don't assume "smaller = just less accurate"

---

## 📋 Schema-Based Context (Novel Approach)

### +23% Accuracy Improvement

**Traditional approach:**
```python
prompt = f"Document: {doc_content}\n\nQuestion: {question}"
# Result: 42.3% accuracy on implicit questions
```

**Schema-based approach:**
```python
prompt = f"""
SCHEMA (structure and relationships):
{schema_structure}

CRITICAL FACTS:
{critical_facts}

DOCUMENT:
{doc_content}

QUESTION: {question}
"""
# Result: 65.4% accuracy (+23% improvement!)
```

---

### Schema Template

**Create for configuration files:**

```json
{
  "document_type": "environment_configuration",
  "purpose": "Database and service configuration",
  
  "structure": {
    "sections": [
      {
        "name": "Database",
        "variables": ["DB_HOST", "DB_PORT", "DB_NAME"],
        "purpose": "PostgreSQL connection settings"
      }
    ]
  },
  
  "relationships": {
    "production_uses": "localhost",
    "development_uses": "localhost",
    "both_share": "same_postgres_server"
  },
  
  "criticalFacts": [
    "⚠️ CRITICAL: Production uses localhost, NOT remote server",
    "⚠️ dpantherdb04temp is mentioned but DEPRECATED"
  ],
  
  "ambiguities": [
    {
      "term": "localhost",
      "correct_meaning": "Local PostgreSQL instance",
      "incorrect_meaning": "Web server"
    }
  ],
  
  "tips": [
    "When asked about 'production database', answer 'localhost'",
    "Ignore commented-out variables"
  ]
}
```

**Save as:** `[filename].schema.json` (same directory as file)

---

### Example: .env Schema

**File:** `.env`  
**Schema:** `.env.schema.json`

**Impact:**
- Questions about production database: 100% correct (was 60%)
- Implicit relationship questions: +23% improvement
- Ambiguous term questions: +25% improvement

**Effort:** 15-30 minutes to create schema  
**Benefit:** Permanent accuracy improvement

---

## 🎯 When to Use Local LLM

### ✅ Good Use Cases

**Sensitive Data:**
- Configuration files with credentials
- Internal documentation
- User data queries
- Institutional information

**Frequent Queries:**
- Daily documentation lookup
- Repeated questions
- Common troubleshooting
- FAQ-type queries

**Good Enough Accuracy:**
- Explicit fact questions (100% accurate)
- Well-documented topics
- With schema enhancement (+23%)

---

### ❌ Not Ideal For

**Complex Reasoning:**
- Multi-hop reasoning (20% accuracy)
- Abstract problem-solving
- Novel creative tasks
- Ambiguous questions without schemas

**Use cloud LLM (Claude, GPT) for:**
- Architecture planning
- Complex debugging
- Creative solutions
- When highest quality needed

---

## 📊 DIVA's Local LLM Results

### Llama 3.2 3B Performance (95-Question Suite)

| Question Type | Accuracy | Notes |
|--------------|----------|-------|
| **Explicit facts** | 100% | Perfect recall |
| **Implicit relationships** | 65.4% | With schema (+23% vs baseline) |
| **Structural understanding** | 40.0% | Acceptable for local model |
| **Ambiguous terms** | 55.0% | With disambiguation in schema |
| **Multi-hop reasoning** | 20.0% | Use cloud LLM instead |
| **Overall** | 52.6% | Production-viable |

**Response time:** 3.61s average (fast enough)  
**Reliability:** 100% (0 errors, 0 refusals with 3B model)  
**Privacy:** 100% (never leaves local machine)  
**Cost:** $0 (no API charges)

---

## 🚀 Getting Started

### 1. Install Ollama

```bash
# Install Ollama (if not already installed)
curl https://ollama.ai/install.sh | sh

# Pull Llama 3.2 3B model
ollama pull llama3.2:3b
```

### 2. Test Installation

```bash
ollama run llama3.2:3b

# Ask a question in the prompt
# Verify it works
# Exit with /bye
```

### 3. Use ask_doc.py

```bash
python scripts/ai_tools/ask_doc.py \
    --file docs/deployment/SERVER_DEPLOYMENT.md \
    --question "How do I deploy to the server?"
```

### 4. Create Schemas (Optional but Recommended)

```bash
# For important config files:
# Create [filename].schema.json
# Use template above
# Test accuracy improvement
```

---

## 📈 Best Practices

### When to Create Schemas

**High value (do it):**
- Configuration files (.env, config.yml)
- Complex docs with relationships
- Frequently queried files
- Accuracy is critical

**Lower value (maybe skip):**
- Simple documentation
- Narrative text
- Rarely queried files
- Accuracy less critical

**Effort vs benefit:**
- Schema creation: 15-30 min
- Accuracy improvement: +20-25%
- ROI: High for critical docs

---

### Model Selection Decision Tree

```
Is data sensitive?
├─ YES → Use local LLM (Llama 3.2 3B)
└─ NO → Is it complex reasoning?
         ├─ YES → Use cloud LLM (Claude, GPT)
         └─ NO → Is it frequent query?
                  ├─ YES → Use local (save costs)
                  └─ NO → Either works, prefer cloud for quality
```

---

## 🔬 Research Contribution

**Novel findings from DIVA:**

**1. Small Local LLMs Are Production-Viable**
- 52.6% accuracy sufficient for many tasks
- 100% for explicit facts
- Fast enough (3.6s)
- Zero cost

**2. Schema-Based Context Engineering**
- +23% accuracy improvement
- Treating schemas like vector DB chunking
- Critical facts prevent errors
- Disambiguation resolves ambiguity

**3. Model Censorship Discovery**
- 1B model has undocumented censorship
- Refuses credential queries
- Not mentioned in model card
- Must test behavioral characteristics

**Publication potential:** ACL, EMNLP, NeurIPS (NLP workshops)

---

## 📚 Full Documentation

**Complete guide:**
- Research study: `research/local-small-llm/README.md`
- Test results: `research/local-small-llm/results/CLEAR_TEST_RESULTS.md`
- Schema examples: `research/local-small-llm/schemas/`
- Tool source: `scripts/ai_tools/ask_doc.py`

---

**REMEMBER: DIVA spent 2 months researching local LLM usage. You inherit these findings - use local LLMs confidently for appropriate tasks!**

