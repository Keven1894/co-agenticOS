---
title: "Environment Tools Checklist"
description: "Mandatory checklist for environment variable management with dual .env support"
version: "2.0.0"
last_updated: "2025-10-27"
scope: "environment"
priority: "critical"
tags: ["environment", "tools", "checklist", "critical", "dual-env"]
---

# Environment Tools Checklist - MANDATORY (Dual .env Support)

## 🚨 BEFORE ANY ENVIRONMENT-RELATED ACTION

### ✅ STEP 1: Check Both Environments
```bash
# Check both .env files
python scripts/manage_env.py list-both

# Or check specific target
python scripts/manage_env.py list root    # Backend
python scripts/manage_env.py list client  # Frontend
```

### ✅ STEP 2: Validate Configuration
```bash
# Validate backend email config
python scripts/manage_env.py validate-email root

# Validate frontend config (if needed)
python scripts/manage_env.py show client
```

### ✅ STEP 3: View Details (if needed)
```bash
# Show both with values
python scripts/manage_env.py show-both

# Or show specific target
python scripts/manage_env.py show root
python scripts/manage_env.py show client
```

## 🚫 ABSOLUTELY FORBIDDEN ACTIONS

- ❌ Creating `.env` files
- ❌ Modifying `.env` files  
- ❌ Overwriting `.env` files
- ❌ Copying from `.env.example`
- ❌ Assuming `.env` doesn't exist
- ❌ Generating environment variable content

## ✅ CORRECT WORKFLOW

1. **Environment Issue Detected** → Use `python scripts/manage_env.py list`
2. **Email Configuration Issue** → Use `python scripts/manage_env.py validate-email`
3. **Need to See Values** → Use `python scripts/manage_env.py show`
4. **Still Having Issues** → Ask user for help, DO NOT create files

## 🔧 Available Commands (Dual .env Support)

### Dual Environment Commands
| Command | Purpose | When to Use |
|---------|---------|-------------|
| `python scripts/manage_env.py list-both` | List both .env files (masked) | First check |
| `python scripts/manage_env.py show-both` | Show both with values | Debugging |
| `python scripts/manage_env.py sync` | Sync common variables | Configuration sync |

### Single Environment Commands
| Command | Purpose | When to Use |
|---------|---------|-------------|
| `python scripts/manage_env.py list <target>` | List variables (masked) | Target-specific check |
| `python scripts/manage_env.py show <target>` | Show variables with values | Target debugging |
| `python scripts/manage_env.py validate-email <target>` | Validate email config | Email issues |
| `python scripts/manage_env.py get <target> <key>` | Get specific variable | Need specific value |
| `python scripts/manage_env.py add <target> <key> <value>` | Add/update variable | Configuration changes |
| `python scripts/manage_env.py remove <target> <key>` | Remove variable | Cleanup |

### Targets
- **`root`**: Backend .env file (server configuration)
- **`client`**: Frontend .env file (React app configuration)

## ⚠️ CRITICAL REMINDERS

- **Two `.env` files EXIST** - root/.env (backend) and client/.env (frontend)
- **Root .env**: 30+ variables (database, API keys, email, server config)
- **Client .env**: 8+ variables (React app config, API URLs, document URLs)
- **Email configuration is VALID** - Gmail setup is complete in root
- **Database configuration is VALID** - PostgreSQL connection works
- **API keys are CONFIGURED** - OpenAI and Anthropic keys exist in root
- **Frontend URLs are CONFIGURED** - API and document URLs in client

## 🚨 RED LINE VIOLATION CONSEQUENCES

Creating `.env` files violates:
1. **Project Security Policy** - Environment variables are sensitive
2. **Development Workflow** - Breaks established tool chain
3. **Team Collaboration** - Conflicts with existing configuration
4. **System Architecture** - Bypasses proper management system

## 📋 MANDATORY CHECKLIST

Before any environment-related debugging:

- [ ] Ran `python scripts/manage_env.py list-both` (or specific target)
- [ ] Ran `python scripts/manage_env.py validate-email root` (if email related)
- [ ] Confirmed both configurations are valid
- [ ] Asked user for help if issues persist
- [ ] **NEVER** created `.env` files manually
- [ ] **NEVER** modified existing `.env` files manually
- [ ] **NEVER** assumed `.env` files don't exist
- [ ] Used proper target (`root` or `client`) for commands

## 🎯 SUCCESS CRITERIA

Environment debugging is successful when:
- ✅ Used project tools to diagnose issues
- ✅ Confirmed existing configuration
- ✅ Resolved issues without creating files
- ✅ Maintained project security standards
