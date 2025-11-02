---
title: "Documentation Standards"
description: "Documentation guidelines for Personal Tax Assistant"
version: "1.0.0"
last_updated: "2025-01-01"
scope: "documentation"
priority: "high"
tags: ["documentation", "standards", "markdown"]
---

# Documentation Standards

## 🎯 Documentation Philosophy

- **Comprehensive**: Cover all tools and workflows
- **Clear**: Easy to understand for future use
- **Practical**: Include real examples
- **Bilingual**: Support both Chinese and English users

## 📁 Documentation Structure

```
docs/
├── README.md                    # Project overview (from old version)
├── QUICKSTART_TAX_TOOLS.md      # Quick start guide
├── PROJECT_SUMMARY.md           # Technical summary
├── USAGE.md                     # Detailed usage
└── ANALYSIS_REPORT.md           # General analysis

tax_tools/
└── README.md                    # Tool documentation

Root level:
├── README.md                    # Git repository main README
├── README_PROJECT.md            # Complete project overview
├── TAX_TOOLS_INDEX.md           # Complete index
└── DIRECTORY_STRUCTURE.md       # Directory structure
```

## 📝 Document Types and Templates

### 1. Tool Documentation

Every tool should have:

**Header**:
```python
"""
Tax Tools - [Tool Name]
[Brief description]

功能:
  - [Feature 1]
  - [Feature 2]

使用:
  python tax_tools/[tool_name].py [arguments]

示例:
  python tax_tools/[tool_name].py 2024 "path/to/data"
"""
```

**Main Function**:
```python
def main():
    """Main entry point"""
    parser = argparse.ArgumentParser(description="[Tool purpose]")
    # ... argument parsing
    # ... processing
    print("✅ Done!")
```

### 2. Tax Reports

Structure:
```markdown
# [Year] Tax Report - [Purpose]

**Tax Year**: YYYY
**Prepared**: YYYY-MM-DD

---

## 📋 Summary

- Total Income: $XXX,XXX
- Total Tax: $XX,XXX
- Amount Due: $X,XXX

## 💰 Income Details

[Table with income breakdown]

## 📊 Tax Calculation

[Step-by-step calculation]

## 📁 Attachments

[List of supporting documents]
```

### 3. Analysis Reports

Structure:
```markdown
# [Person] [Year] Income Analysis

**Prepared**: YYYY-MM-DD

---

## 🔍 Income Sources

### Category 1
[Details with table]

### Category 2
[Details with table]

## 💡 Tax Implications

[Explanation of tax treatment]

## 📊 Summary

[Key takeaways]
```

### 4. README Files

Essential sections:
1. **Purpose**: What is this folder/tool for?
2. **Quick Start**: How to use it immediately
3. **File List**: What files are included
4. **Examples**: Common use cases
5. **Notes**: Important reminders

## 🌐 Language Guidelines

### Technical Content (English)
- Code comments
- Function names
- Variable names
- Git commit messages
- API documentation
- Error messages

### User-Facing Content (Bilingual)
- README files (Chinese or English based on audience)
- Tax reports (both Chinese and English versions)
- Analysis reports (both versions when possible)
- User prompts in tools (support both)

### Examples

**Tool Output** (Bilingual):
```python
print(f"✅ Success! / 成功!")
print(f"Processed {count} files / 已处理{count}个文件")
```

**Documentation** (Choose one language per file):
- README.md (English - for Git)
- README_PROJECT.md (Chinese - for user)
- Tool READMEs (English with Chinese examples)

## 📊 Report Standards

### CSV Files
- Use English headers
- Include all necessary columns
- Format numbers consistently (2 decimal places)
- Sort by date or amount as appropriate

Example:
```csv
Category,Amount,Note
W-2 Wages,96562.74,Employee wages
Cryptocurrency Net Gain,24800.87,Schedule D
Total,133177.42,
```

### HTML Reports
- Include CSS styling
- Responsive design
- Print-friendly
- Clear section headers
- Highlight key numbers

### Markdown Reports
- Use tables for structured data
- Use sections (##, ###) clearly
- Include emojis for visual cues (💰, 📊, ⚠️)
- Add horizontal rules (---) between sections

## 🔄 Updating Documentation

### When Adding New Tools
1. Update tax_tools/README.md
2. Update QUICKSTART_TAX_TOOLS.md
3. Update TAX_TOOLS_INDEX.md
4. Add to config.py if needed

### When Changing Workflows
1. Update tax_processing_workflow.md
2. Update QUICKSTART_TAX_TOOLS.md
3. Update examples in tool files

### When Tax Rules Change (e.g., new year)
1. Update config.py with new tax brackets
2. Update documentation with new year examples
3. Note changes in CHANGELOG (if created)

## ✅ Documentation Checklist

Before finalizing:

- [ ] All tools have docstrings
- [ ] README files explain purpose clearly
- [ ] Examples are up-to-date
- [ ] Links work (relative paths)
- [ ] No sensitive data in examples
- [ ] Both English and Chinese versions (if applicable)
- [ ] Git repository README is clear
- [ ] File structure is documented

## 📋 Special Documentation Needs

### For CPA Reports
- Include data sources
- Explain calculation methods
- Reference IRS forms
- Highlight special circumstances
- Provide contact info (if needed)

### For User Reference
- Explain tax implications
- Show examples from actual data (anonymized)
- Provide comparisons (year-over-year)
- Include action items

### For Future Maintenance
- Document assumptions
- Explain complex logic
- Note edge cases handled
- List dependencies
- Include version information

## 🎨 Formatting Standards

### Markdown
```markdown
# H1 for main title
## H2 for major sections
### H3 for subsections

Use **bold** for emphasis
Use `code` for technical terms
Use tables for structured data
Use lists for items
Use --- for section breaks
```

### Code Blocks
````markdown
```python
# Code with syntax highlighting
def example():
    pass
```

```bash
# Shell commands
python tool.py
```
````

### Emojis (Optional but Helpful)
- 📊 Data/Statistics
- 💰 Money/Financial
- ✅ Success/Complete
- ❌ Error/Prohibited
- ⚠️ Warning/Attention
- 🔒 Security/Privacy
- 🚀 Quick Start/Action
- 💡 Tips/Insights

---

**Goal**: Documentation should make the project easy to use, maintain, and expand for years to come.
