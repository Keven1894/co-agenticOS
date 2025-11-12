# Credential Management - Security Critical
**Standard Procedure - Tier 1 (Context: credentials, security)**

---

## 🔐 Secure Credential Handling

### CRITICAL: NEVER hard-code credentials, commit them to Git, or expose in logs!

**Why this rule exists:**
- **Security:** Hard-coded credentials = security breach
- **Compliance:** Institutional policies require secure handling
- **Audit:** Need to track credential access
- **DIVA learned:** Zero incidents in 3+ months by following this rule strictly

**Evidence:** 0 credential leaks, 0 Git commits, 0 log exposures in 3 months

---

## 🔧 Standard Credential Manager

### Always Use: `env_manager.sh`

**Location:** `./scripts/dev_tools/env_manager.sh`

**What it does:**
- Stores credentials in encrypted file (`.secure_store`)
- Creates automatic backups (last 10 versions)
- Masks credentials in display (shows *****)
- Provides LLM-safe interface
- Logs all access for audit

**DIVA learned:** Built this after discovering credentials in Git risk. Now 100% compliant.

---

## 💻 How to Use

### 1. View Available Credentials (Masked)

```bash
./scripts/dev_tools/env_manager.sh list

# Output:
# DB_HOST=localhost
# DB_PORT=5432
# DB_PASSWORD=*******
# API_KEY=*******
# GMAIL_PASSWORD=*******
```

**Safe for agent context** - credentials are masked.

---

### 2. Set/Update Credentials

```bash
# Set new credential
./scripts/env_manager.sh set API_KEY "sk-proj-abc123..."

# Update existing
./scripts/env_manager.sh set DB_PASSWORD "new_secure_password"

# Confirmation:
# ✅ API_KEY saved and backed up
```

**What happens:**
- Old value backed up automatically
- New value encrypted and stored
- .env file updated
- Backup rotation (keeps last 10)

---

### 3. Retrieve Explicit Value (When Absolutely Needed)

```bash
./scripts/env_manager.sh get API_KEY

# Output:
# sk-proj-abc123...
```

**⚠️ Use sparingly** - only when you actually need the explicit value.

---

### 4. In Code (Environment Variables)

```javascript
// Node.js
const dbPassword = process.env.DB_PASSWORD;
const apiKey = process.env.API_KEY;

// NEVER:
const apiKey = "sk-proj-abc123..."; // ❌ Hard-coded!
```

```java
// Java
String dbPassword = System.getenv("DB_PASSWORD");
String apiKey = System.getenv("API_KEY");

// NEVER:
String apiKey = "sk-proj-abc123..."; // ❌ Hard-coded!
```

```python
# Python
import os
db_password = os.environ.get('DB_PASSWORD')
api_key = os.environ.get('API_KEY')

# NEVER:
api_key = "sk-proj-abc123..." # ❌ Hard-coded!
```

---

## 🚨 Critical DON'Ts

### ❌ NEVER Do These

**1. Hard-Code Credentials**
```javascript
// ❌ WRONG - Never do this!
const API_KEY = "sk-proj-abc123...";
const DB_PASSWORD = "secretpassword";
```

**2. Commit Credentials to Git**
```bash
# ❌ WRONG - Never commit .env file
git add .env
git commit -m "Add config"
```

**Make sure `.env` is in `.gitignore`!**

**3. Expose in Logs**
```javascript
// ❌ WRONG
console.log('API Key:', process.env.API_KEY); // Exposes in logs!

// ✅ CORRECT
console.log('API Key: *******'); // Masked
```

**4. Share in Plain Text**
```javascript
// ❌ WRONG - Sending credential in email
sendEmail({ body: `Your API key is: ${apiKey}` });

// ✅ CORRECT - Never send credentials via email
// Use secure key distribution method instead
```

---

## 🛡️ Security Levels

| Operation | Who Can | How |
|-----------|---------|-----|
| **View masked** | Anyone | `env_manager.sh list` |
| **Retrieve explicit** | Authenticated user | `env_manager.sh get KEY` |
| **Set/update** | Authenticated user | `env_manager.sh set KEY value` |
| **Delete** | Admin only | `env_manager.sh delete KEY` |
| **Backup restore** | Admin only | `env_manager.sh restore [backup_number]` |

---

## 💾 Backup System

### Automatic Backups

**What gets backed up:**
- Every time you change a credential
- Last 10 versions kept
- Stored in `.secure_store.backups/`

**Example:**
```bash
# Set new value
./scripts/env_manager.sh set API_KEY "new_value"

# Backup created:
# .secure_store.backups/.env.backup.001  (most recent)
# .secure_store.backups/.env.backup.002
# ...
# .secure_store.backups/.env.backup.010  (oldest)
```

### Restore from Backup

```bash
# List backups
./scripts/env_manager.sh list-backups

# Restore specific backup
./scripts/env_manager.sh restore 3  # Restore backup #3
```

**DIVA learned:** Backups saved the day twice when credentials were accidentally overwritten.

---

## ⚠️ Pitfalls DIVA Discovered

### Pitfall 1: Using 1B Model for Credentials

**What happened:**
- Tried using Llama 3.2 1B for document reading
- Model has built-in censorship (refuses credential questions)
- 40% accuracy drop on credential-related queries

**Solution:**
- Use 3B+ models for any credential-related queries
- Test behavioral characteristics before deploying

**See:** `document-reader.md` for model selection guidelines

---

### Pitfall 2: Credentials in Agent Context

**What could happen:**
- Show full .env file in agent context
- Credential appears in chat history
- Potential exposure

**Solution:**
```bash
# ❌ DON'T:
cat .env  # Full credentials exposed in context

# ✅ DO:
./scripts/env_manager.sh list  # Masked: API_KEY=*******
```

**Only retrieve explicit value when absolutely necessary.**

---

### Pitfall 3: No Backup Before Changes

**What could happen:**
- Typo when setting credential
- Overwrite with wrong value
- No way to recover old value

**Solution:**
- Use env_manager.sh (automatic backups)
- Never edit .env directly

**DIVA learned:** Automatic backups prevented 2 credential loss incidents.

---

## 📖 Full Documentation

**Complete guide:** `docs/configuration/CREDENTIALS_MANAGEMENT.md`

**Related docs:**
- Backup procedures: `docs/operations/BACKUP_RESTORE.md`
- Security policies: `docs/security/CREDENTIAL_POLICY.md`
- Email setup: `docs/n8n/GMAIL_SETUP.md`

---

## ✅ Validation Checklist

**Before using credentials in new code:**
- [ ] Using environment variables (not hard-coded)
- [ ] No credentials in Git commits
- [ ] Logging masks credentials (shows *****)
- [ ] Error messages don't expose credentials
- [ ] Using env_manager.sh for any changes

---

## 🎯 DIVA's Track Record

**3+ months production:**
- Credentials in Git: 0 incidents
- Hard-coded credentials: 0 instances
- Credential exposure: 0 incidents
- Failed retrievals: 0
- Backups used: 2 times (saved the day)
- Security incidents: 0

**You inherit this perfect record by following these rules.**

---

**Remember: DIVA learned credential security the hard way (close calls). You don't have to - just follow this rule!**

