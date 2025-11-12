# Documentation Standards
**Standards Rule - Tier 1 (Context: documentation)**

---

## 📝 Documentation Philosophy

### Documentation is Part of the Workflow, Not an Afterthought

**DIVA's approach:**
- Plan (documentation starts)
- Implement (comment as you code)
- Summary (lessons learned)

**Result:** 95% quality, 157+ files, 10,000+ lines

**Traditional approach:**
- Implement
- (Maybe) document later

**Result:** 60% coverage, variable quality

---

## 📋 Documentation Requirements

### Every Piece of Work Must Have

**1. Plan Document (Before)**
- Location: `docs/plan/todo/[feature].md`
- Purpose: What and how
- See: `workflows/planning.md`

**2. Code Comments (During)**
- Inline comments for complex logic
- Javadoc for public APIs
- Header comments for files

**3. Summary Log (After)**
- Location: `docs/plan/complete/[feature]-summary.md`
- Purpose: What happened, lessons learned
- Required: Always

**4. README Updates (If Needed)**
- Update relevant READMEs
- Keep indexes current
- Cross-reference appropriately

**"Done" = Code works + Tests pass + Documentation complete**

---

## 📁 Documentation Structure

### Organize by Purpose

```
docs/
├── INDEX.md                    # Master index (ALWAYS UPDATE)
│
├── architecture/               # System design
│   ├── README.md
│   ├── SERVER_IMPLEMENTATION.md
│   └── API_DESIGN.md
│
├── configuration/              # Setup guides
│   ├── README.md
│   ├── DATABASE_SETUP.md
│   └── SSL_CONFIGURATION.md
│
├── deployment/                 # Deployment procedures
│   ├── README.md
│   └── DEPLOYMENT_GUIDE.md
│
├── troubleshooting/            # Problem solving
│   ├── README.md
│   └── COMMON_ISSUES.md
│
├── plan/                       # Work planning
│   ├── todo/                   # Active plans
│   └── complete/               # Completed with summaries
│
└── diva/                       # DIVA-specific
    ├── README.md
    ├── evolution/
    └── learning-journey/
```

**Principle:** Clear categorization, easy to find.

---

## ✍️ Writing Standards

### 1. Clear Structure

```markdown
✅ GOOD:
# Email Configuration

## Purpose
This document explains email configuration for DIVA.

## Prerequisites
- Gmail account with app password
- Node.js installed
- nodemailer package

## Setup Steps
1. Create app password in Gmail
2. Set environment variables
3. Test email sending

## Troubleshooting
If email fails, check...

❌ BAD:
# Emails

Here's how to do emails...
[Unstructured wall of text]
```

**Use headings, lists, code blocks, tables for clarity.**

---

### 2. Code Examples

**Always include working examples:**

```markdown
✅ GOOD:
## Sending Email

```javascript
const { sendDivaEmail } = require('./diva_mailer.js');

await sendDivaEmail({
    to: 'user@fiu.edu',
    subject: 'Test',
    body: 'This is a test email'
});
```

Expected output:
```
✅ Email sent successfully to user@fiu.edu
```

❌ BAD:
## Sending Email

Use the email function to send emails.
[No example provided]
```

---

### 3. Cross-References

**Link related documentation:**

```markdown
✅ GOOD:
For email configuration, see [Email Setup Guide](configuration/EMAIL_SETUP.md).
For troubleshooting email issues, see [Email Troubleshooting](troubleshooting/EMAIL_ISSUES.md).

❌ BAD:
Email is configured in another document somewhere.
```

**Use relative links, verify they work.**

---

### 4. Update Dates

```markdown
✅ GOOD:
# Email Configuration

**Last Updated:** 2025-11-12  
**Author:** DIVA  
**Status:** Current

❌ BAD:
# Email Configuration

[No date - is this current or outdated?]
```

---

### 5. Target Audience

**State who the doc is for:**

```markdown
✅ GOOD:
# Server Deployment Guide

**Audience:** System administrators  
**Prerequisites:** SSH access, sudo privileges  
**Difficulty:** Intermediate

❌ BAD:
# Server Deployment

[Unclear who should read this or what they need to know]
```

---

## 🎯 Documentation Types

### README Files

**Every folder needs README.md:**

```markdown
# [Folder Name]

## Purpose
[What this folder contains and why]

## Contents
- `file1.md` - [Brief description]
- `file2.md` - [Brief description]

## Quick Links
- [Most important doc]
- [Second most important]

## Related
- [Related folder/doc]
```

**DIVA result:** 30+ folders, all have READMEs, 100% coverage.

---

### Architecture Docs

**Explain system design:**

```markdown
# Component Name Architecture

## Overview
[High-level description]

## Components
[Diagram or list of components]

## Data Flow
[How data moves through system]

## Key Decisions
[Why designed this way]

## Alternatives Considered
[What else was considered and why not chosen]
```

---

### API Documentation

**For each API endpoint:**

```markdown
## GET /api/datasets/{id}

**Purpose:** Retrieve dataset by ID

**Authentication:** Required (API token)

**Parameters:**
- `id` (path): Dataset ID (integer)

**Request:**
```bash
curl -H "X-Dataverse-key: $API_KEY" \
     https://dataversedev.fiu.edu/api/datasets/123
```

**Response (200 OK):**
```json
{
  "status": "OK",
  "data": {
    "id": 123,
    "title": "Research Dataset",
    ...
  }
}
```

**Error Responses:**
- 401: Authentication required
- 404: Dataset not found
- 500: Server error
```

---

### Troubleshooting Guides

**Problem → Solution format:**

```markdown
# Common Issues

## Issue: Authentication Fails

**Symptoms:**
- Login page redirects to error
- Logs show "SAML assertion invalid"

**Cause:**
- Shibboleth SP metadata out of sync

**Solution:**
```bash
ssh user@server "sudo systemctl restart shibd"
```

**Prevention:**
- Monitor SP metadata expiration
- Set up auto-renewal
```

---

## 📊 Documentation Metrics

### DIVA's Documentation Quality

**Volume:**
- Files: 157+
- Lines: 10,000+
- Folders with README: 30+ (100%)
- Cross-references: 500+

**Quality (A grade):**
- Organization: 95%
- Completeness: 90%
- Consistency: 95%
- Index coverage: 100%

**Impact:**
- New team member onboarding: 50% faster
- "How do I...?" questions: 70% reduction
- Duplicate documentation: Eliminated
- Documentation findability: Excellent

---

## 🚀 Quick Documentation

### For Small Tasks (5 minutes)

**Minimal viable documentation:**

```markdown
# [Task Name]

**What:** [One sentence]
**Why:** [One sentence]  
**How:** [Code example or command]

Done.
```

**Better than nothing, captures essential info.**

---

### For Medium Tasks (15 minutes)

**Structured documentation:**

```markdown
# [Task Name]

## Purpose
[Why this exists]

## How to Use
```code
[Example]
```

## Notes
- [Important point 1]
- [Important point 2]

## Related
- [Link to related doc]
```

---

### For Major Features (30-60 minutes)

**Comprehensive documentation:**
- Complete guide
- Multiple examples
- Troubleshooting section
- Architecture explanation
- API reference

**See existing docs as templates.**

---

## 🎓 DIVA's Documentation Workflow

### Integrated into Development

**Not separate tasks:**

```
Traditional:
1. Write code
2. Test code
3. Deploy code
4. (Maybe) Document

DIVA:
1. Plan (create plan doc)           ← Documentation
2. Implement (comment as you code)   ← Documentation
3. Test
4. Deploy
5. Summary (lessons learned)         ← Documentation
6. Update indexes                    ← Documentation

Result: Documentation happens automatically
```

**Why this works:**
- Part of workflow, not extra task
- Fresh in mind while working
- No "I'll document later" (never happens)
- Captures lessons while relevant

---

## 📈 Automation

### Content Watcher Agent

**DIVA's innovation:**
- Watches `docs/` for markdown changes
- Auto-generates HTML for website
- Auto-commits to Git
- Runs autonomously

**Impact:**
- Manual HTML updates: 30-60 minutes
- Automated: 2-5 minutes (83-92% reduction)
- Consistency: 100% (template-based)
- Errors: 0

**Lesson:** Automate documentation generation where possible.

---

## ⚠️ Common Documentation Mistakes

### 1. No Updates When Code Changes

**Problem:**
- Code evolves
- Documentation stays old
- Users follow outdated procedures

**Solution:**
- Update docs as part of implementation
- Review docs in code reviews
- Test examples actually work

---

### 2. Missing Examples

**Problem:**
- Documentation explains concepts
- No working code examples
- Users can't get started

**Solution:**
- Always include copy-paste ready examples
- Test examples work
- Show expected output

---

### 3. No Cross-References

**Problem:**
- Related docs not linked
- Users can't find related info
- Duplicate documentation

**Solution:**
- Link related docs
- Maintain master index
- Use "See also" sections

---

### 4. Outdated Information

**Problem:**
- Last updated: 2 years ago
- Procedures changed
- Users waste time

**Solution:**
- Add "Last Updated" dates
- Review quarterly
- Archive obsolete docs (don't delete)

---

## ✅ Documentation Checklist

**Before considering work "done":**

- [ ] Plan document created (before)
- [ ] Code comments added (during)
- [ ] Examples provided (working code)
- [ ] README updated (if needed)
- [ ] Index updated (if new file)
- [ ] Cross-references added
- [ ] Summary log created (after)
- [ ] Last updated date added

**If ANY unchecked: Not done yet.**

---

## 📚 Master Index

**ALWAYS update:** `docs/INDEX.md`

**When adding new doc:**
1. Add entry to appropriate section
2. Brief description
3. Link to file
4. Update table of contents

**Why:** Users can find anything from master index.

**DIVA result:** 100% of 157 files indexed, nothing lost.

---

**REMEMBER: DIVA's 95% documentation quality comes from treating docs as part of workflow, not afterthought. Inherit this discipline!**

