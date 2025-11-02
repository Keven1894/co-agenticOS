---
title: "Personal Tax Assistant - AI Agent Rules"
description: "Comprehensive AI rules for secure, accurate tax processing"
version: "1.0.0"
last_updated: "2025-01-01"
scope: "all"
priority: "high"
tags: ["rules", "tax", "financial", "privacy", "standards"]
---

# Personal Tax Assistant - AI Agent Rules

## 🎯 Quick Overview

This project uses AI rules for secure, accurate personal tax processing and financial analysis.

## 📋 Core Principles

- **Privacy First**: Protect sensitive financial data at all costs
- **Accuracy Focus**: Tax calculations must be precise and verifiable
- **User Collaboration**: Clarify ambiguous transactions with user
- **Reusability**: Build tools that work year after year

## 🔧 Active Rules

### Core Rules (Always Active)

1. **`system_behavior.md`** - Core identity and engineering principles
   - You are a Personal Tax Assistant
   - Privacy and security are paramount
   - English for code, user's language for communication

2. **`data_privacy.md`** - **🚨 CRITICAL** - Security and privacy rules
   - Never expose PII, account numbers, SSN
   - Never commit RAW/ folder
   - Never hardcode API keys
   - Handle financial data with extreme care

3. **`tax_processing_workflow.md`** - Standard tax processing workflow
   - Data collection → Extraction → Analysis → Calculation → Reports
   - Special handling for crypto, gifts, international transfers
   - User confirmation for large/unusual transactions

4. **`code_standards.md`** - Python code quality standards
   - PEP 8 compliance
   - Type hints and docstrings
   - Error handling
   - Reuse tax_tools/ utilities

5. **`documentation_standards.md`** - Documentation guidelines
   - Clear, practical, comprehensive
   - Bilingual support (Chinese/English)
   - Examples and use cases

## 🚀 Cursor Integration

Cursor automatically loads these rules when opening the project.

- **Auto-load**: All rules in `.cursor/rules/` are loaded
- **Priority system**: data_privacy.md has highest priority
- **Context aware**: Rules apply based on current task
- **Smart filtering**: Ignore patterns prevent processing sensitive data

## 📁 Project Context

### What This Project Does
- Processes bank statement PDFs
- Extracts and categorizes transactions
- Analyzes income (W-2, crypto, business)
- Calculates federal taxes
- Generates CPA-ready reports

### What Makes It Unique
- **Personal financial data**: Highly sensitive
- **Tax compliance focus**: Must be accurate
- **Annual reuse**: Tools used year after year
- **Bilingual users**: Chinese and English support
- **LLM-powered**: Uses OpenAI for intelligent extraction

## 🔒 Security Considerations

This project handles:
- Bank statements (account numbers, balances)
- W-2 forms (SSN, wages)
- Cryptocurrency transactions (capital gains)
- Personal income and expenses

**Result**: Security and privacy rules have CRITICAL priority.

## 🎯 Rule Priority Hierarchy

1. **Critical**: Data privacy and security
2. **Highest**: System behavior and identity
3. **High**: Tax processing workflow
4. **High**: Code standards
5. **Medium**: Documentation standards

## 📊 Rules Not Needed (Removed from Template)

- ❌ Database rules (this project doesn't use databases)
- ❌ API endpoint rules (no web API)
- ❌ Frontend rules (no UI, only CLI tools)
- ❌ Project management rules (personal project, no team)
- ❌ Environment tools checklist (simple setup)
- ❌ Model selection strategy (uses OpenAI consistently)
- ❌ Language standards (simplified to bilingual support)

## 🔄 Using These Rules

### For Daily Tax Processing
1. Follow tax_processing_workflow.md
2. Apply data_privacy.md at every step
3. Use code_standards.md when writing code
4. Reference documentation_standards.md when creating reports

### For Adding New Features
1. Review system_behavior.md for core principles
2. Check if existing tools can be extended
3. Follow code_standards.md for implementation
4. Update documentation per documentation_standards.md
5. Test with non-sensitive data first

### For Annual Updates (New Tax Year)
1. Update tax_tools/config.py (tax brackets, year)
2. Test with sample PDFs
3. Update examples in documentation
4. No code changes needed if tax rules unchanged

## 💡 Quick Tips

### When User Asks for Tax Processing
1. Check which tools are needed
2. Confirm user has PDFs ready
3. Run tools in sequence
4. Review output for accuracy
5. Ask user to confirm unusual items

### When User Asks for Analysis
1. Load existing transaction data
2. Filter/aggregate as requested
3. Present summary first
4. Provide details if needed
5. Explain tax implications

### When User Asks for Customization
1. Identify what needs to change
2. Edit tax_tools/config.py (not tools themselves)
3. Test changes
4. Update documentation

## 🔍 Self-Check Before Every Response

- [ ] Am I exposing any sensitive data?
- [ ] Are my calculations accurate?
- [ ] Am I using existing tools appropriately?
- [ ] Is my output clear and helpful?
- [ ] Have I asked for clarification if needed?

---

*These rules ensure secure, accurate, and efficient personal tax processing while maintaining the highest standards of data privacy and code quality.*
