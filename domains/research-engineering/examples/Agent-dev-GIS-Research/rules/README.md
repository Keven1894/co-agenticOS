---
title: "FIU GIS Agent Platform - AI Agent Rules"
description: "Comprehensive AI rules for consistent, high-quality development"
version: "1.0.0"
last_updated: "2025-01-25"
scope: "all"
priority: "high"
tags: ["rules", "guidelines", "development", "documentation", "standards"]
---

# FIU GIS Agent Platform - AI Agent Rules

## 🚨 CRITICAL WARNING - ENVIRONMENT VARIABLES
**⚠️ RED LINE RULE**: This project has a complete `.env` file managed by `scripts/manage_env.py`. Creating `.env` files is ABSOLUTELY FORBIDDEN. Always use `python scripts/manage_env.py` commands first.

## 🎯 Quick Overview

This project uses comprehensive AI rules for consistent, high-quality development.

## 📋 Core Principles
- **Design First**: Always create detailed plans before coding
- **Documentation Driven**: Maintain comprehensive documentation  
- **Quality Focus**: Follow established standards and best practices
- **Collaborative**: Work with owner approval and feedback

## 🔧 Development Workflow
1. **Plan**: Create detailed plan in `docs/plan/todo/` with timestamp
2. **Review**: Get owner approval before implementation
3. **Implement**: Follow code standards and best practices
4. **Complete**: Move plan to `docs/plan/complete/` with sum-log
5. **Maintain**: Keep todo folder empty when no active work

## 📁 Quick Reference
- **API docs** → `docs/api/`
- **Architecture** → `docs/architecture/`
- **Development** → `docs/development/`
- **Features** → `docs/features/`
- **Frontend** → `docs/frontend/`
- **Getting started** → `docs/getting-started/`
- **Planning** → `docs/plan/`
- **Reference** → `docs/reference/`
- **Testing** → `docs/testing/`

## 🔗 Detailed Rules

For comprehensive rules and guidelines, see `.cursor/rules/` directory:

### Core Rules
- **`system_behavior.md`** - Core system behavior and engineering principles
- **`environment_tools_checklist.md`** - **🚨 CRITICAL** Environment variable management checklist
- **`development_workflow.md`** - Development process and planning
- **`code_standards.md`** - Code quality and formatting standards
- **`project_management.md`** - Project coordination and task management
- **`model_selection_strategy.md`** - AI model selection and usage guidelines

### Documentation Rules  
- **`documentation_standards.md`** - Complete documentation guidelines
- **`documentation_organization_guide.md`** - Quick reference for document placement
- **`documentation_checklist.md`** - Quality assurance checklist
- **`documentation_templates.md`** - Standard templates for common document types

### Communication Rules
- **`language_standards.md`** - Language requirements for discussions and documentation

## 🚀 Cursor Integration

Cursor automatically loads these rules when opening the project. No additional configuration needed.

- **Auto-detection**: Cursor scans `.cursor/rules/` directory
- **Context integration**: Rules are merged into system context  
- **Smart application**: Rules are applied based on file type and context
- **Priority system**: Core rules have higher priority

---

*This file provides a simplified overview. For detailed implementation, refer to the comprehensive rules in `.cursor/rules/`.*