---
title: "Code Standards and Best Practices"
description: "Code quality standards for Personal Tax Assistant"
version: "1.0.0"
last_updated: "2025-01-01"
scope: "code"
priority: "high"
tags: ["code", "standards", "python", "quality"]
---

# Code Standards and Best Practices

## 🎯 Core Principles

- **Clarity over cleverness**: Code should be easy to understand
- **Reusability**: Use tax_tools/ utilities, don't duplicate
- **Safety**: Handle sensitive data with care
- **Maintainability**: Future-you should understand it

## 🐍 Python Code Standards

### 1. Style Guide
Follow PEP 8 with these specifics:

```python
# ✅ GOOD: Clear function names
def extract_transactions_from_pdf(pdf_path: str) -> List[Dict]:
    """Extract all transactions from a PDF statement"""
    pass

# ❌ BAD: Unclear names
def process(file):
    pass
```

### 2. Type Hints
Use type hints for clarity:

```python
# ✅ GOOD
def calculate_tax(income: float, deductions: float) -> float:
    return (income - deductions) * 0.22

# ❌ BAD (no types)
def calculate_tax(income, deductions):
    return (income - deductions) * 0.22
```

### 3. Docstrings
All functions must have docstrings:

```python
# ✅ GOOD
def categorize_transaction(description: str, amount: float) -> str:
    """
    Categorize a transaction based on description and amount
    
    Args:
        description: Transaction description from bank statement
        amount: Transaction amount (positive = income, negative = expense)
        
    Returns:
        str: Category name (e.g., "income", "groceries", "transfer")
        
    Examples:
        >>> categorize_transaction("Walmart Purchase", -150.00)
        'groceries'
    """
    pass
```

### 4. Error Handling
Always handle errors gracefully:

```python
# ✅ GOOD
def extract_text_from_pdf(pdf_path: str) -> str:
    """Extract text from PDF with error handling"""
    try:
        with pdfplumber.open(pdf_path) as pdf:
            text = "\n".join(page.extract_text() or "" for page in pdf.pages)
        return text
    except FileNotFoundError:
        print(f"❌ Error: PDF file not found: {pdf_path}")
        return ""
    except Exception as e:
        print(f"❌ Error extracting text: {e}")
        return ""

# ❌ BAD (no error handling)
def extract_text_from_pdf(pdf_path: str) -> str:
    with pdfplumber.open(pdf_path) as pdf:
        return "\n".join(page.extract_text() for page in pdf.pages)
```

## 📁 File Organization

### Module Structure
```
tax_tools/
├── __init__.py          # Package exports
├── config.py            # Configuration and constants
├── utils.py             # Shared utilities
├── extract_metadata.py  # Tool 1
├── extract_transactions.py  # Tool 2
├── analyze_income.py    # Tool 3
├── calculate_tax.py     # Tool 4
└── generate_reports.py  # Tool 5
```

### Import Standards
```python
# ✅ GOOD: Import from shared utilities
from tax_tools.utils import extract_text_from_pdf, categorize_transaction
from tax_tools.config import INCOME_KEYWORDS, TAX_BRACKETS_2024_MFJ

# ❌ BAD: Duplicate implementation
def extract_text_from_pdf(pdf_path):
    # ... duplicate code ...
```

## 💰 Tax-Specific Code Standards

### 1. Financial Calculations
Always use Decimal or proper rounding:

```python
# ✅ GOOD: Proper rounding
tax = round(taxable_income * 0.22, 2)

# ✅ BETTER: Use built-in formatting
tax_formatted = f"${tax:,.2f}"

# ❌ BAD: Floating point precision issues
tax = taxable_income * 0.22  # Could be 1234.5600000001
```

### 2. Date Handling
Use consistent date formats:

```python
# ✅ GOOD: Standard format
date = "MM/DD/YYYY"
statement_period = "01/01/2024 - 12/31/2024"

# ❌ BAD: Inconsistent formats
date1 = "2024-01-01"
date2 = "1/1/24"
```

### 3. Tax Calculations
Document tax logic clearly:

```python
# ✅ GOOD: Clear tax calculation with comments
def calculate_federal_tax(taxable_income: float, tax_brackets: List[tuple]) -> float:
    """
    Calculate federal income tax using progressive tax brackets
    
    Tax Brackets (2024 MFJ):
    - $0-$23,200: 10%
    - $23,201-$94,300: 12%
    - $94,301-$201,050: 22%
    ...
    
    Args:
        taxable_income: Taxable income after deductions
        tax_brackets: List of (threshold, rate) tuples
        
    Returns:
        float: Total tax owed
    """
    tax = 0.0
    previous = 0
    
    for threshold, rate in tax_brackets:
        if taxable_income <= threshold:
            tax += (taxable_income - previous) * rate
            break
        else:
            tax += (threshold - previous) * rate
            previous = threshold
    
    return round(tax, 2)
```

## 🔧 Utility Functions

### Reuse Existing Utilities
```python
# ✅ GOOD: Use from tax_tools/utils.py
from tax_tools.utils import (
    extract_text_from_pdf,
    call_openai_api,
    categorize_transaction,
    format_currency,
)

# ❌ BAD: Reimplement
def my_extract_text(pdf_path):
    # ... duplicate code ...
```

### Add to Utils When Needed
If you create a useful function, add it to utils.py:

```python
# In tax_tools/utils.py

def validate_transaction_data(transactions: List[Dict]) -> bool:
    """
    Validate transaction data integrity
    
    Checks:
    - Required fields present (date, description, amount)
    - Amounts are numeric
    - Dates are valid
    
    Returns:
        bool: True if valid, False otherwise
    """
    required_fields = ['date', 'description', 'amount']
    
    for t in transactions:
        if not all(field in t for field in required_fields):
            return False
        if not isinstance(t['amount'], (int, float)):
            return False
    
    return True
```

## 📝 Configuration Management

### Use config.py for Constants
```python
# In tax_tools/config.py

TAX_YEAR = 2024
FILING_STATUS = "MFJ"
STANDARD_DEDUCTION_MFJ = 29200.00

INCOME_KEYWORDS = [
    "zelle payment from",
    "deposit",
    "direct dep",
]

# In your tool
from tax_tools.config import TAX_YEAR, INCOME_KEYWORDS
```

### Don't Hardcode Tax Rules
```python
# ✅ GOOD: Use config
from tax_tools.config import TAX_BRACKETS_2024_MFJ
tax = calculate_federal_tax(income, TAX_BRACKETS_2024_MFJ)

# ❌ BAD: Hardcode
if income < 23200:
    tax = income * 0.10
# ... hardcoded logic
```

## 🧪 Testing and Validation

### Validate Input
```python
# ✅ GOOD: Validate before processing
def process_year(year: int):
    if not (2020 <= year <= 2030):
        raise ValueError(f"Invalid year: {year}")
    # ... process
```

### Test with Safe Data
```python
# ✅ GOOD: Use test data
test_transaction = {
    "date": "01/15/2024",
    "description": "Test Grocery Store",
    "amount": -50.00
}
category = categorize_transaction(test_transaction['description'], 
                                  test_transaction['amount'])
assert category == "groceries"

# ❌ BAD: Test with real data
real_transaction = load_from_raw_pdf()  # Contains PII
```

## 📊 Data Processing Standards

### Pandas Operations
```python
# ✅ GOOD: Safe aggregation
import pandas as pd

df = pd.read_csv('transactions.csv')
total = df['amount'].sum()
by_category = df.groupby('category')['amount'].sum()

# ✅ GOOD: Filter without exposing
crypto = df[df['description'].str.contains('COINBASE', case=False, na=False)]
print(f"Found {len(crypto)} Coinbase transactions totaling ${crypto['amount'].sum():,.2f}")

# ❌ BAD: Display full data
print(df)  # May contain sensitive descriptions
```

### Deduplication
```python
# ✅ GOOD: Remove duplicates
df_unique = df.drop_duplicates(subset=['date', 'description', 'amount'], keep='first')

# ✅ GOOD: Report deduplication
duplicates_removed = len(df) - len(df_unique)
if duplicates_removed > 0:
    print(f"🔍 Removed {duplicates_removed} duplicate transactions")
```

## 🎨 Output Formatting

### Console Output
```python
# ✅ GOOD: Formatted output
print("="*70)
print("2024 Tax Summary")
print("="*70)
print(f"Total Income:  ${total_income:>12,.2f}")
print(f"Total Tax:     ${total_tax:>12,.2f}")
print(f"Amount Due:    ${amount_due:>12,.2f}")

# ❌ BAD: Messy output
print("Total:", total_income)
print("Tax:", total_tax)
```

### Progress Indicators
```python
# ✅ GOOD: Show progress for long operations
def print_progress(current: int, total: int, description: str = ""):
    percent = int(current / total * 100)
    bar = '█' * int(40 * current / total) + '░' * (40 - int(40 * current / total))
    print(f"\r{description} |{bar}| {percent}% ({current}/{total})", end='')
    if current == total:
        print()
```

## 🔍 Code Review Checklist

Before committing code:

- [ ] All functions have docstrings
- [ ] Type hints are used
- [ ] Error handling is present
- [ ] No hardcoded sensitive data
- [ ] No hardcoded API keys
- [ ] Uses utilities from tax_tools/
- [ ] Uses config from tax_tools/config.py
- [ ] Follows PEP 8
- [ ] Comments are in English
- [ ] No debugging print statements left

## 📚 Common Patterns

### Processing PDFs
```python
from tax_tools.utils import extract_text_from_pdf, call_openai_api

def process_statement(pdf_path: str) -> Dict:
    # Extract text
    text = extract_text_from_pdf(pdf_path)
    
    # Call API
    prompt = f"Extract transactions from: {text[:5000]}"
    response = call_openai_api(prompt, response_format={"type": "json_object"})
    
    # Parse and return
    return json.loads(response)
```

### Generating Reports
```python
from tax_tools.utils import markdown_to_html

def generate_report(data: Dict, year: int):
    # Create markdown
    md = f"# {year} Tax Report\n\n"
    md += f"Total: ${data['total']:,.2f}\n"
    
    # Save markdown
    md_file = f"report_{year}.md"
    with open(md_file, 'w', encoding='utf-8') as f:
        f.write(md)
    
    # Convert to HTML
    html = markdown_to_html(md, f"{year} Tax Report")
    html_file = f"report_{year}.html"
    with open(html_file, 'w', encoding='utf-8') as f:
        f.write(html)
```

---

**Core Standard**: Write code that is secure, accurate, reusable, and maintainable.
