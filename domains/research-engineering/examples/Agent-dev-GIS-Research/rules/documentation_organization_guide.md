---
title: "Documentation Organization Guide"
description: "Quick reference for organizing documentation in the FIU GIS Agent Platform"
version: "1.0.0"
last_updated: "2025-01-25"
scope: "documentation"
priority: "high"
tags: ["documentation", "organization", "guide", "quick-reference"]
---

# Documentation Organization Guide

## 📁 Directory Structure

```
docs/
├── api/                    # API documentation
├── architecture/           # System architecture
├── development/           # Development guides
├── features/             # Feature documentation
├── frontend/              # Frontend guides
├── getting-started/       # Getting started guides
├── plan/                  # Planning documents
│   ├── todo/             # TODO plans
│   └── complete/         # Completed plans + sum-logs
├── reference/             # Reference materials
└── testing/               # Testing documentation
```

## 🎯 Quick Reference

| Document Type | Location | Naming Convention |
|---------------|----------|-------------------|
| **API docs** | `docs/api/` | `{api_name}.md` |
| **Architecture** | `docs/architecture/` | `{system_name}.md` |
| **Development guides** | `docs/development/` | `{guide_name}.md` |
| **Feature docs** | `docs/features/` | `{feature_name}.md` |
| **Frontend guides** | `docs/frontend/` | `{component_name}.md` |
| **Getting started** | `docs/getting-started/` | `{topic_name}.md` |
| **TODO plans** | `docs/plan/todo/` | `{feature_name}_{timestamp}.md` |
| **Completed plans** | `docs/plan/complete/` | `{feature_name}_{timestamp}.md` |
| **Sum-logs** | `docs/plan/complete/` | `{feature_name}_{timestamp}_sum-log.md` |
| **Reference** | `docs/reference/` | `{topic_name}.md` |
| **Testing** | `docs/testing/` | `{test_name}.md` |

## 📝 Document Selection Rules

### Choose the Right Directory
- **API documentation** → `docs/api/`
- **System architecture** → `docs/architecture/`
- **Development guides** → `docs/development/`
- **Feature documentation** → `docs/features/`
- **Frontend guides** → `docs/frontend/`
- **Getting started guides** → `docs/getting-started/`
- **Planning documents** → `docs/plan/todo/` or `docs/plan/complete/`
- **Reference materials** → `docs/reference/`
- **Testing documentation** → `docs/testing/`

### Naming Conventions
- **Use lowercase with underscores**: `api_endpoints.md`
- **Include timestamps for plans**: `feature_name_20251026_120000.md`
- **Be descriptive**: `database_schema.md` not `db.md`
- **Use consistent prefixes**: `guide_`, `api_`, `test_`

## 🔗 Cross-References
- Link related documents using relative paths
- Use consistent anchor links for sections
- Maintain a master index in `docs/README.md`

## 📋 Quality Checklist
- [ ] Document is in the correct directory
- [ ] Naming follows conventions
- [ ] Content is clear and complete
- [ ] Links are working and relevant
- [ ] Document follows project standards