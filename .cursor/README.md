# co-agenticOS - Cursor AI Rules

## 🎯 Quick Reference

This project is a **Framework Documentation & Rule Development Project** for AI-involved software engineering.

### 📋 Core Rules
- **`rules/system_behavior.md`** - Project identity and core behavior principles
- **`rules/language_standards.md`** - English-only documentation requirement
- **`rules/content_standards.md`** - Documentation quality and formatting standards
- **`rules/rule_development_workflow.md`** - Process for creating and updating rules
- **`rules/contribution_workflow.md`** - Guidelines for community contributions

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
    ├── language_standards.md
    ├── content_standards.md
    ├── rule_development_workflow.md
    └── contribution_workflow.md
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

*This configuration ensures consistent, high-quality documentation and rule development across the co-agenticOS project.*
