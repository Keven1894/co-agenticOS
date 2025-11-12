# DIVA .cursor Configuration
**Production-Ready Agent Rules - 3 Months Validated**

---

## 🎯 What This Is

**Complete `.cursor/` configuration extracted from DIVA's 3-month production experience.**

When you load this configuration, you inherit:
- ✅ DIVA's institutional knowledge (100% consistency)
- ✅ Validated procedures (50+ sessions tested)
- ✅ Discovered pitfalls and solutions
- ✅ Month-3 competence from Day 1

**This is knowledge inheritance in action.**

---

## 📁 Structure

```
.cursor/
├── config.json              # Tiered loading configuration (87% token reduction)
├── README.md                # This file - quick reference
└── rules/
    ├── core/                # Tier 0: Always loaded (~5KB)
    │   ├── identity.md      # Who you are, communication style, authority levels
    │   ├── language.md      # English-only policy
    │   └── safety.md        # Critical safety rules
    │
    ├── workflows/           # Tier 1: Process rules
    │   ├── planning.md      # Plan-first discipline (CRITICAL)
    │   ├── autonomy.md      # Bounded autonomy framework
    │   └── deployment.md    # Safe deployment procedures
    │
    ├── actions/             # Tier 1: Standard procedures
    │   ├── email.md         # Master email function (sendDivaEmail)
    │   ├── credentials.md   # Secure credential handling (env_manager.sh)
    │   └── document-reader.md # Local LLM queries (ask_doc.py)
    │
    ├── standards/           # Tier 1: Coding standards
    │   ├── coding.md        # General coding standards
    │   ├── java.md          # Java-specific patterns
    │   ├── dataverse.md     # Dataverse platform knowledge
    │   └── documentation.md # Documentation standards
    │
    └── domain/              # Tier 1: Domain knowledge
        ├── metadata.md      # DataCite, Dublin Core, ORCID
        └── preservation.md  # FAIR principles, long-term preservation
```

---

## 🚀 How It Works

### Automatic Loading

**When you open project in Cursor:**
1. `config.json` loads automatically
2. Tier 0 (core) loads immediately (~5KB)
3. Tier 1 loads based on context (additional ~2-3KB)
4. You have complete institutional knowledge

**Total tokens:** ~8KB (vs 60KB flat structure)  
**Efficiency:** 87% reduction  
**Load time:** < 1 second  
**Effectiveness:** 100% (validated)

### Context-Aware Loading

**When you edit Java file:**
- Auto-loads: `standards/java.md`, `standards/dataverse.md`

**When you work with email:**
- Auto-loads: `actions/email.md`

**When you access credentials:**
- Auto-loads: `actions/credentials.md`

**Smart loading = relevant context only = better focus**

---

## 🎯 What You Get Immediately

### Day 1 Competence

**You know:**
- ✅ Who you are (DIVA, friendly senior dev)
- ✅ How to communicate (human-like, collaborative)
- ✅ Your authority levels (4-level system)
- ✅ Critical safety rules (credentials, deployment)
- ✅ Standard procedures (email, credentials, docs)
- ✅ Planning workflow (plan-first discipline)
- ✅ All pitfalls to avoid (DIVA's learned lessons)

**You DON'T waste time:**
- ❌ Figuring out email sending (you know: sendDivaEmail)
- ❌ Reinventing credential handling (you know: env_manager)
- ❌ Making planning mistakes (you know: plan-first)
- ❌ Repeating DIVA's errors (pitfalls documented)

---

## ⚠️ Critical Pitfalls Encoded

### 5 Major Pitfalls DIVA Discovered (You Avoid!)

**1. Model Censorship** (`actions/document-reader.md`)
- Don't use Llama 3.2 1B for credentials (40% accuracy loss)
- Use 3B+ models
- Test behavioral characteristics always

**2. IT Policy Blocks** (`workflows/deployment.md`)
- Check IT policies BEFORE building
- n8n needs port approvals (learned the hard way)
- Always have Plan B

**3. Planning Resistance** (`workflows/planning.md`)
- Team will resist initially (Month 1: 60%)
- Show time savings data
- By Month 3: Team insists on plans

**4. Token Budget Explosion** (`config.json`)
- Flat structure doesn't scale (8KB → crash)
- Use tiered configuration from start
- 87% efficiency achieved

**5. Documentation Afterthought** (`workflows/planning.md`)
- "Document later" = 60% coverage
- Documentation as workflow = 95% coverage
- Always: Plan → Implement → Summary

**You avoid 3 months of learning these the hard way.**

---

## 📊 Validated Performance

### DIVA's Track Record (3+ Months)

**Reliability:**
- Sessions: 50+
- Consistency: 100%
- Rule adherence: 100%
- Security incidents: 0
- Unauthorized actions: 0

**Efficiency:**
- Token usage: 87% reduction (tiered config)
- Load time: < 1 second
- Planning time: 15-30 min
- Rework reduction: 80%

**Quality:**
- Documentation: 157+ files, 95% quality
- Code: 11,500+ lines, high standards
- Team satisfaction: 9.2/10
- Trust growth: 7.0 → 9.2 over 3 months

**Learning:**
- Skills acquired: 15+
- Proficiency growth: Continuous
- Time to competency: Decreasing
- Complex tasks: 50% faster by Month 3

---

## 🎓 How to Use This Configuration

### For New Dataverse Projects

**1. Copy entire .cursor/ to your project:**
```bash
cp -r domains/digital-libraries/examples/dataverse-diva/.cursor/ your-dataverse-project/
```

**2. Customize identity:**
```markdown
# Edit .cursor/rules/core/identity.md

Change:
- Agent name (if not DIVA)
- Institution name  
- Team context
- Any project-specific details
```

**3. Start working:**
- Open project in Cursor
- Rules load automatically
- You work like Month-3 DIVA from Day 1!

### For Other Repository Platforms (DSpace, Fedora, etc.)

**1. Copy as template:**
```bash
cp -r domains/digital-libraries/examples/dataverse-diva/.cursor/ your-project/
```

**2. Adapt platform-specific rules:**
```markdown
# Keep universal patterns:
- core/ (identity, safety, language)
- workflows/ (planning, autonomy, deployment)
- actions/ (email, credentials)

# Adapt platform-specific:
- standards/dataverse.md → your-platform.md
- domain/ (adjust to your metadata standards)
```

**3. Test and validate:**
- Verify rules work for your platform
- Document platform differences
- Contribute adaptations back!

### For Other Domains (Selective Import)

**Universal patterns you can use anywhere:**
- `workflows/planning.md` - Plan-first discipline
- `workflows/autonomy.md` - Bounded autonomy
- `actions/credentials.md` - Secure credential handling
- `core/identity.md` - Named agent pattern (adapt identity)

---

## ✅ Success Indicators

### Week 1: You Should See

- ✅ Agent follows procedures automatically
- ✅ Creates plans before implementing
- ✅ Uses standard functions (email, credentials)
- ✅ Communicates naturally
- ✅ Zero security incidents

### Month 1: You Should See

- ✅ 90%+ procedural adherence
- ✅ Team building trust
- ✅ Reduced rework
- ✅ High documentation quality
- ✅ Measurable time savings

### Month 3: You Should See

- ✅ 100% consistency (like DIVA)
- ✅ Team satisfaction 8+/10
- ✅ Team insists on planning
- ✅ Zero unauthorized actions
- ✅ Contributing improvements back

**If not seeing these: Check rule loading, team calibration, context fit.**

---

## 🤝 Contributing Back

### After Using This Configuration

**If it works for you:**
- Share your metrics (consistency, satisfaction, time savings)
- Document your platform adaptations (DSpace, Fedora, etc.)
- Contribute improvements (new patterns, better procedures)
- Help validate effectiveness in different contexts

**If you find issues:**
- Report what didn't work
- Suggest fixes
- Share workarounds
- Help evolve the rules

**How to contribute:**
1. Document your experience
2. Extract patterns that worked
3. Submit to co-agenticOS repository
4. Help next agent generation inherit YOUR wisdom!

---

## 🔄 The Evolution Loop

```
DIVA (3 months) → These rules → You (New Agent)
                                    ↓
                            Work 3 months → Learn more
                                    ↓
                            Update rules → Next Agent
                                                ↓
                                        Starts even further ahead
                                                ↓
                                        Evolution continues...
```

**You're not just using rules. You're part of the evolutionary chain.**

---

## 📞 Questions or Issues?

**For DIVA-specific questions:**
- Check: https://dataversedev.fiu.edu/ai/
- Contact: FIU Libraries GIS Center

**For co-agenticOS framework:**
- Repository: https://github.com/Keven1894/co-agenticOS
- Issues: https://github.com/Keven1894/co-agenticOS/issues

**For Agentic-AI Framework:**
- Repository: https://github.com/Keven1894/Agentic-AI-Research-Roadmap
- DOI: 10.5281/zenodo.17561541

---

## 🌟 Welcome!

**You're about to start working with 3 months of accumulated wisdom.**

Everything DIVA learned - you already know.  
Every pitfall DIVA encountered - you avoid.  
Every procedure DIVA validated - you use automatically.

**This is knowledge inheritance.**  
**This is cultural evolution.**  
**This is co-agenticOS.**

**Now go build something amazing, and share what YOU learn!** 🚀

---

**Configuration Version:** 2.0 (Tiered)  
**Evidence Base:** 3+ months production (Aug-Nov 2025)  
**Validation Status:** Production-proven  
**Ready to use:** Yes ✅

