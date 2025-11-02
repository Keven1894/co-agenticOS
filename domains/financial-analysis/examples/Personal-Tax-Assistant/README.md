# Personal Tax Assistant - Cursor AI Rules

## 🎯 Quick Reference

This project uses modular AI rules for personal tax processing and financial analysis.

### 📋 Core Rules
- **`rules/system_behavior.md`** - Core behavior and tax processing principles
- **`rules/code_standards.md`** - Python code standards and best practices
- **`rules/documentation_standards.md`** - Documentation guidelines
- **`rules/tax_processing_workflow.md`** - Tax data processing workflow

### 🔒 Security Rules
- **`rules/data_privacy.md`** - Handling sensitive financial data

## 🚀 How It Works

Cursor automatically loads these rules when opening the project.

- **Auto-detection**: Cursor scans `.cursor/rules/` directory
- **Context integration**: Rules are merged into system context
- **Smart application**: Rules are applied based on file type and context
- **Priority system**: Security and privacy rules have highest priority

## 📁 Project Structure

```
.cursor/
├── config.json          # Cursor configuration
├── README.md            # This file
└── rules/               # Modular rule files
    ├── README.md        # Detailed rules overview
    ├── system_behavior.md
    ├── code_standards.md
    ├── documentation_standards.md
    ├── tax_processing_workflow.md
    └── data_privacy.md
```

## 🔧 Configuration

The `config.json` file specifies:
- **Rules loading**: `rules/*.md` pattern
- **Ignore patterns**: RAW/, .venv/, __pycache__/
- **Context limits**: Optimized for tax document processing
- **Priority system**: Security and data privacy highest priority

---

*This configuration ensures secure, accurate, and efficient tax processing and financial analysis.*
