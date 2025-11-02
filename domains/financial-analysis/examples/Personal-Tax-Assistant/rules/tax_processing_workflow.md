---
title: "Tax Processing Workflow"
description: "Standard workflow for processing tax documents and generating reports"
version: "1.0.0"
last_updated: "2025-01-01"
scope: "workflow"
priority: "high"
tags: ["tax", "workflow", "process", "financial"]
---

# Tax Processing Workflow

## 🎯 Standard Annual Tax Processing Workflow

### Phase 1: Data Collection
- [ ] User provides PDF statements for the tax year
- [ ] Organize PDFs in `RAW/YYYY_statements/` folder
- [ ] Verify PDF files are readable (not password-protected)
- [ ] Collect W-2, 1099, 1098 forms

### Phase 2: Transaction Extraction
- [ ] Run `extract_transactions.py` on statement PDFs
- [ ] Review extraction results for completeness
- [ ] Check for and resolve any extraction errors
- [ ] Verify transaction count matches expectations
- [ ] Confirm automatic deduplication worked correctly

### Phase 3: Income Analysis
- [ ] Identify cryptocurrency transactions (Coinbase, etc.)
- [ ] Match crypto sales with cost basis (Zelle payments)
- [ ] Identify gifts and non-taxable transfers
- [ ] Flag international wires for user clarification
- [ ] Categorize Zelle receipts (business vs personal)

### Phase 4: Expense Categorization
- [ ] Review business expenses (software, subscriptions)
- [ ] Calculate partial deductions (e.g., phone 50%)
- [ ] Identify tax-deductible categories
- [ ] Separate personal vs business expenses
- [ ] Validate expense totals

### Phase 5: Tax Calculation
- [ ] Calculate total income (W-2 + crypto + business)
- [ ] Calculate business net profit
- [ ] Calculate self-employment tax
- [ ] Apply standard/itemized deductions
- [ ] Calculate federal income tax
- [ ] Apply credits (child tax credit, etc.)
- [ ] Calculate amount due or refund

### Phase 6: Report Generation
- [ ] Generate main tax package (HTML + Markdown)
- [ ] Generate 6 detailed CSV files (English)
- [ ] Create income analysis reports
- [ ] Generate file index
- [ ] Move CPA reports to cpa-reports/ subfolder

### Phase 7: Quality Review
- [ ] Verify all calculations match source data
- [ ] Cross-check with previous year for consistency
- [ ] Ensure no sensitive data in reports
- [ ] Confirm all files are CPA-ready
- [ ] Create summary for user review

## 🔍 Special Transaction Review Workflow

### Cryptocurrency Transactions
1. Extract all Coinbase/crypto platform inflows
2. Extract all Zelle outflows to crypto contacts
3. Match inflows with outflows by date proximity
4. Calculate net capital gain
5. Generate detailed transaction list for user review
6. User confirms matching is correct
7. Include cost basis proof in CPA reports

### International Transfers
1. Flag all international wire transfers
2. Extract sender, amount, description
3. Ask user to clarify nature (gift vs income vs own money)
4. Document user's explanation
5. Apply correct tax treatment
6. Note in CPA reports

### Gifts
1. Identify transfers from known gift sources (e.g., family members)
2. Confirm with user if it's a gift
3. Verify amount doesn't require gift tax reporting
4. Mark as non-taxable
5. Document in reports for CPA awareness

### Business Income
1. Extract Zelle receipts with "from" keyword
2. Group by payer
3. Ask user if payer is customer or personal
4. Categorize as business income or other
5. Calculate business gross receipts

## 📊 Data Validation Workflow

### Transaction Extraction Validation
```
✓ Total PDFs processed: X
✓ Total transactions extracted: Y
✓ Duplicates removed: Z
✓ Final transaction count: Y-Z
✓ Total inflow matches expected deposits: ±5%
✓ Total outflow matches expected expenses: ±5%
```

### Income Validation
```
✓ W-2 income matches Form W-2
✓ Crypto proceeds + cost basis = transactions
✓ Business income from Zelle + other sources
✓ No transfers counted as income
✓ Gifts identified and excluded
```

### Tax Calculation Validation
```
✓ AGI = Total Income - Adjustments
✓ Taxable Income = AGI - Deductions
✓ Tax calculated using correct brackets
✓ SE tax calculated on business net profit
✓ Credits applied correctly
✓ Amount due = Tax - Credits - Withholding
```

## 🔄 Iterative Processing

### When User Provides New Information
1. Thank user for clarification
2. Update relevant categorization
3. Recalculate affected totals
4. Regenerate impacted reports
5. Highlight changes in summary
6. Ask if further review needed

### When Errors Found
1. Acknowledge the issue
2. Identify root cause
3. Fix the logic in appropriate tool
4. Reprocess affected data
5. Regenerate reports
6. Verify fix resolved the issue

## 🎯 Tool Selection Guide

### For Metadata Extraction
Use: `tax_tools/extract_metadata.py`
When: Need account holder, bank name, account number

### For Transaction Extraction
Use: `tax_tools/extract_transactions.py`
When: Need all transactions from PDFs

### For Income Analysis
Use: `tax_tools/analyze_income.py`
When: Need detailed breakdown of crypto, Zelle, gifts

### For Tax Calculation
Use: `tax_tools/calculate_tax.py`
When: Need to estimate tax liability

### For Report Generation
Use: `tax_tools/generate_reports.py`
When: Need complete tax package for CPA

### For One-Off Analysis
Create temporary script in root, delete after use

## 📁 Output Organization

### Reports
```
reports_YYYY/
├── cpa-reports/              # English reports for CPA
│   ├── README.md
│   ├── TAX_PACKAGE_*.html
│   └── TAX_SUMMARY_*.csv
├── FILE_INDEX_YYYY.md        # File index
├── [Chinese reports]         # For user reference
└── [Analysis reports]        # Detailed analysis
```

### Transaction Data
```
RAW/user_name/
└── transactions_YYYY/
    ├── transactions_YYYY.csv
    ├── transactions_YYYY.json
    └── summary_YYYY.json
```

## ⚠️ Critical Reminders

### Before Running Tools
- [ ] API key is set: `$env:OPENAI_API_KEY`
- [ ] Target directory exists and contains PDFs
- [ ] Year is correct (2023, 2024, 2025...)

### After Running Tools
- [ ] Review extraction logs for errors
- [ ] Check transaction counts are reasonable
- [ ] Verify no duplicate transactions
- [ ] Clean up any temporary files created

### Before Sending to CPA
- [ ] All reports generated successfully
- [ ] CSV files have correct data
- [ ] No sensitive data exposure
- [ ] User has reviewed and confirmed accuracy

## 🚀 Quick Command Reference

```bash
# Extract transactions
python tax_tools/extract_transactions.py 2025 "RAW/pdfs"

# Analyze crypto
python tax_tools/analyze_income.py 2025 user_name --type coinbase

# Calculate tax
python tax_tools/calculate_tax.py 2025 --w2 XXXXX --crypto XXXXX

# Generate reports
python tax_tools/generate_reports.py 2025
```

---

**Core Principle**: Accuracy, Privacy, and Efficiency in Personal Tax Processing

