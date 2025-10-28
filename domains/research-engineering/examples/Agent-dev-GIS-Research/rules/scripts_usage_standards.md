---
title: "Scripts Usage Standards"
description: "Standards for using FIU GIS Agent Platform scripts and tools"
version: "1.0.0"
last_updated: "2025-01-25"
scope: "scripts"
priority: "high"
tags: ["scripts", "tools", "cli", "automation", "development"]
---

# Scripts Usage Standards

## 🎯 Overview

The FIU GIS Agent Platform uses a unified script system with reusable tools and CLI interfaces.

## 📁 Script Organization

```
scripts/
├── data_processing/        # Data processing scripts
├── database/              # Database management scripts
├── testing/               # Testing scripts
└── validation/            # Validation scripts
```

## 🔧 Common Scripts

### Database Management
- `scripts/database/setup_database.py` - Initialize database
- `scripts/database/migrate_database.py` - Run migrations
- `scripts/backup_database.py` - Create backups
- `scripts/restore_database.py` - Restore from backup

### Data Processing
- `scripts/data_processing/import_core_data.py` - Import core data
- `scripts/data_processing/analyze_and_organize_data.py` - Data analysis
- `scripts/data_processing/export_git_data.py` - Export git data

### Testing
- `scripts/testing/test_database_only.py` - Database tests
- `scripts/testing/test_unified_search.py` - Search tests
- `scripts/testing/verify_rag_setup.py` - RAG verification

## 📋 Usage Guidelines

### Running Scripts
```bash
# Database setup
python scripts/database/setup_database.py

# Data import
python scripts/data_processing/import_core_data.py

# Testing
python scripts/testing/test_database_only.py
```

### Environment Setup
- Ensure virtual environment is activated
- Check `.env` file for required variables
- Verify database connection
- Install required dependencies

### Error Handling
- Check logs for detailed error messages
- Verify environment variables
- Ensure database is accessible
- Check file permissions

## ⚠️ Important Notes

- Always backup database before running migration scripts
- Test scripts in development environment first
- Check script dependencies before running
- Monitor script execution for errors

## 🔍 Troubleshooting

### Common Issues
- **Database connection errors**: Check `.env` variables
- **Permission errors**: Verify file/directory permissions
- **Import errors**: Check Python path and dependencies
- **Timeout errors**: Check database performance

### Debug Mode
```bash
# Enable debug logging
export DEBUG=true
python script_name.py
```