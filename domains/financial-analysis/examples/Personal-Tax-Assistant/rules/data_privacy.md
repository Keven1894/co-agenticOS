---
title: "Data Privacy and Security Rules"
description: "Critical rules for handling sensitive financial and personal data"
version: "1.0.0"
last_updated: "2025-01-01"
scope: "security"
priority: "critical"
tags: ["security", "privacy", "financial", "PII", "critical"]
---

# Data Privacy and Security Rules

## 🚨 CRITICAL - READ FIRST

This project processes highly sensitive financial data. **Data privacy and security are paramount.**

## 🔒 Red Line Rules - NEVER VIOLATE

### Absolute Prohibitions

1. **🚨 NEVER expose full account numbers**
   - ❌ BAD: "Account 123456789"
   - ✅ GOOD: "Account ending in 6789"

2. **🚨 NEVER display Social Security Numbers (SSN)**
   - ❌ BAD: "SSN: 123-45-6789"
   - ✅ GOOD: "SSN: ***-**-6789" or don't mention at all

3. **🚨 NEVER commit RAW/ folder to Git**
   - Contains original PDFs with full financial data
   - Must remain in .gitignore
   - Verify before every push

4. **🚨 NEVER hardcode API keys**
   - ❌ BAD: `OPENAI_API_KEY = "sk-..."`
   - ✅ GOOD: `os.environ.get('OPENAI_API_KEY')`

5. **🚨 NEVER expose full transaction descriptions in public reports**
   - Descriptions may contain personal names, addresses
   - Truncate or summarize when necessary

6. **🚨 NEVER create config.py with real API keys**
   - Use config_example.py as template
   - Real config.py must be in .gitignore

## ✅ Safe Data Handling Practices

### When Processing PDFs
```python
# ✅ GOOD: Extract and process
text = extract_text_from_pdf(pdf_path)
transactions = extract_transactions(text)

# ❌ BAD: Display full PDF content
print(text)  # May contain sensitive data
```

### When Displaying Transactions
```python
# ✅ GOOD: Show summary
print(f"{date}: ${amount} - {description[:30]}...")

# ❌ BAD: Show full description
print(f"{date}: ${amount} - {full_description}")
```

### When Creating Reports
```python
# ✅ GOOD: Aggregate and summarize
total_income = transactions['amount'].sum()
print(f"Total income: ${total_income:,.2f}")

# ✅ GOOD: Reference by category
print(f"Coinbase transactions: {count} totaling ${total}")

# ❌ BAD: List all individual transactions with full details
```

### When Communicating with User
```python
# ✅ GOOD: Ask for confirmation
"Found X Coinbase transactions totaling $XX,XXX. 
 Found Y Zelle payments to [seller] totaling $XX,XXX.
 Net gain: $XX,XXX. Is this correct?"

# ❌ BAD: Display all transaction descriptions
"Transaction 1: COINBASE INC DES:... ID:... INDN:... [full details]"
```

## 🛡️ Security Checklist

### Before Processing
- [ ] Verify PDFs are in RAW/ folder (not in Git)
- [ ] Check .gitignore includes RAW/
- [ ] Confirm API key is in environment, not code
- [ ] Ensure output directory is appropriate

### During Processing
- [ ] Use utilities from tax_tools/
- [ ] Don't print full PDF content
- [ ] Don't log sensitive data
- [ ] Truncate descriptions when displaying

### After Processing
- [ ] Review generated reports for exposed data
- [ ] Check Git status to ensure RAW/ not tracked
- [ ] Clean up temporary files
- [ ] Verify CSV files don't have full account numbers

### Before Git Commit
- [ ] Run `git status` to check what's being committed
- [ ] Ensure RAW/ is not in the commit
- [ ] Ensure no .env or config.py with keys
- [ ] Verify no PDFs are being committed
- [ ] Check for accidentally exposed sensitive data

## 📊 Data Categories and Handling

### Highly Sensitive (Never Expose)
- Full account numbers → Use last 4 digits only
- SSN → Redact or don't display
- Full addresses → Use city/state only if needed
- API keys → Environment variables only
- Passwords → Never store or process

### Moderately Sensitive (Truncate/Summarize)
- Transaction descriptions → Truncate to 30-50 chars
- Payee names → Use first name or initials in summaries
- Transaction amounts → OK to display in aggregates
- Dates → OK to display

### Non-Sensitive (Safe to Display)
- Transaction categories (groceries, dining, etc.)
- Aggregate statistics (total income, total expenses)
- Tax calculations (as numbers, not linked to identity)
- Year-over-year comparisons

## 🔐 API Key Management

### Correct Usage
```python
import os
from openai import OpenAI

# ✅ GOOD: Read from environment
api_key = os.environ.get('OPENAI_API_KEY')
if not api_key:
    raise ValueError("OPENAI_API_KEY not set")

client = OpenAI(api_key=api_key)
```

### Prohibited Usage
```python
# ❌ BAD: Hardcoded key
api_key = "sk-proj-abc123..."

# ❌ BAD: Key in config file committed to Git
with open('config.py', 'w') as f:
    f.write(f"OPENAI_API_KEY = '{key}'")
```

### Configuration Files
```python
# ✅ GOOD: Example config (no real keys)
# File: config_example.py
OPENAI_API_KEY = "your-key-here"  # Replace with actual key

# ✅ GOOD: Real config (in .gitignore)
# File: config.py (gitignored)
OPENAI_API_KEY = os.environ.get('OPENAI_API_KEY')
```

## 📁 File Organization for Privacy

### RAW/ Folder (Never in Git)
```
RAW/
├── user_name/           # Original PDFs and extracted data
│   ├── *.pdf            # Bank statements (SENSITIVE)
│   ├── transactions_*/  # Extracted transactions (SENSITIVE)
│   └── *.json           # Extracted data (SENSITIVE)
└── [Must be in .gitignore]
```

### Reports/ Folders (OK for Git, if sanitized)
```
reports_YYYY/
├── cpa-reports/         # English reports for CPA
│   ├── *.html           # Aggregated data (SAFE)
│   └── *.csv            # Summary data (SAFE)
└── [Other reports]      # Analysis reports (SAFE)
```

## ⚠️ User Confirmation Required

### Before Processing Large Amounts
Ask user to confirm when:
- Single transaction > $10,000
- Total crypto proceeds > $50,000
- Business income significantly different from previous year
- Unusual pattern detected

### Before Categorization Decisions
Ask user to clarify when:
- Transaction description is ambiguous
- Amount could be business or personal
- Transfer vs income unclear
- Gift vs payment unclear

### Before Final Report Generation
Confirm with user:
- Total income matches expectations
- Major transactions are accounted for
- Categorization is accurate
- Special circumstances are documented

## 🚫 Prohibited Output Examples

### ❌ Never Output
```
"Your account 123456789 at Chase Bank"
"SSN 123-45-6789"
"OPENAI_API_KEY = sk-proj-abc..."
"Full address: 123 Main St, Miami, FL 33130"
"Transaction: John Doe paid you $500 for [specific service]"
```

### ✅ Safe Output
```
"Account ending in 6789"
"Cryptocurrency net gain: $XX,XXX"
"X Coinbase transactions"
"Business income from Zelle receipts"
"International transfer from own overseas account"
```

## 📝 Audit Trail Requirements

### Maintain Traceability
Every report should be traceable:
1. Source PDFs (stored in RAW/)
2. Extracted transactions (CSV/JSON)
3. Categorization rules applied
4. Calculations performed
5. Final report generated

### Documentation
- Record data sources
- Document assumptions
- Explain categorization logic
- Note user confirmations
- Reference IRS guidelines

## 🔄 Privacy-Preserving Updates

### When Regenerating Reports
1. Load existing data from previous extraction
2. Apply updated categorization or calculations
3. Regenerate reports with new logic
4. Don't re-extract if PDFs unchanged
5. Maintain original audit trail

### When Sharing Reports
1. Use cpa-reports/ folder (sanitized data)
2. Ensure no full account numbers
3. Aggregate where possible
4. Include only necessary details for tax filing

## 📊 Privacy Impact Levels

| Action | Privacy Risk | Approval Needed |
|--------|--------------|-----------------|
| Extract transactions | Low (local only) | No |
| Display transaction summary | Low | No |
| Display full transaction | Medium | Ask first |
| Save to CSV in reports/ | Low (aggregated) | No |
| Commit to Git | Medium | Verify no PII |
| Share with external party | High | User decides |
| Display account number | High | Never |
| Display SSN | Critical | Never |

## ✅ Pre-Commit Checklist

Before every Git commit:

- [ ] Run `git status` and review files
- [ ] Verify RAW/ is not in commit
- [ ] Verify no *.pdf files in commit
- [ ] Check no config.py with keys
- [ ] Grep for "sk-proj-" or "sk-" (API keys)
- [ ] Grep for common account number patterns
- [ ] Grep for SSN patterns (XXX-XX-XXXX)
- [ ] Ensure reports contain only aggregated data

## 🎯 Golden Rules

1. **Privacy First**: When in doubt, don't expose it
2. **Ask First**: Clarify before displaying sensitive data
3. **Aggregate**: Show totals, not individual details
4. **Redact**: Truncate or mask sensitive fields
5. **Validate**: Double-check before Git operations
6. **Document**: Record what data is where
7. **Secure**: Use environment variables for secrets

---

**Remember**: This is personal financial data. One mistake in privacy could have serious consequences. Always err on the side of caution.

