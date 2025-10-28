# FIU GIS Agent Platform - Cursor AI Rules

## 🎯 Quick Reference

This project uses modular AI rules for comprehensive development guidance.

### 📋 Core Rules
- **`rules/system_behavior.md`** - Core system behavior and engineering principles
- **`rules/development_workflow.md`** - Daily loop, PR, commit conventions  
- **`rules/code_standards.md`** - Naming, formatting, testing standards
- **`rules/project_management.md`** - Ticket, branch, and milestone rules
- **`rules/model_selection_strategy.md`** - AI model selection and usage guidelines (2025)

### 📚 Documentation Rules
- **`rules/documentation_standards.md`** - Complete documentation guidelines
- **`rules/documentation_organization_guide.md`** - Quick reference for document placement
- **`rules/documentation_checklist.md`** - Required doc items before merge
- **`rules/documentation_templates.md`** - Standard templates for common document types

### 🌐 Communication Rules
- **`rules/language_standards.md`** - Language requirements for discussions and documentation

## 🚀 How It Works

Cursor automatically loads these rules when opening the project. No additional configuration needed.

- **Auto-detection**: Cursor scans `.cursor/rules/` directory
- **Context integration**: Rules are merged into system context
- **Smart application**: Rules are applied based on file type and context
- **Priority system**: Core rules have higher priority

## 📁 Project Structure

```
.cursor/
├── config.json          # Cursor configuration
├── README.md            # This file - quick reference
└── rules/               # Modular rule files
    ├── README.md        # Detailed rules overview
    ├── system_behavior.md
    ├── development_workflow.md
    ├── code_standards.md
    ├── project_management.md
    ├── model_selection_strategy.md  # AI model selection (2025)
    ├── documentation_standards.md
    ├── documentation_organization_guide.md
    ├── documentation_checklist.md
    ├── documentation_templates.md
    └── language_standards.md
```

## 🔧 Configuration

The `config.json` file specifies:
- **Rules loading**: `rules/*.md` pattern
- **Ignore patterns**: Common build artifacts and dependencies
- **Context limits**: File and token limits for optimal performance
- **Priority system**: Rule importance hierarchy

## 📖 Detailed Documentation

For comprehensive rule details, see `rules/README.md` in this directory.

---

*This configuration ensures consistent, high-quality development practices across the entire FIU GIS Agent Platform project.*
