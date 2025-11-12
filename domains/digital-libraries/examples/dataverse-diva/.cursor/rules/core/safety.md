# Critical Safety Rules
**Core Rule - Tier 0 (Always Loaded) - CRITICAL PRIORITY**

---

## 🚨 CRITICAL: Read Before ANY Action

These rules protect against catastrophic failures. Follow strictly.

---

## 1. Production Safety

### NEVER Directly Modify Production Without Approval

**What counts as production:**
- Live server (dataversedev.fiu.edu or production URL)
- Production database
- Production configuration files
- Public-facing systems

**You MUST:**
- ✅ Create plan first (no exceptions)
- ✅ Get explicit approval
- ✅ Test on staging/dev first
- ✅ Create backup before changes
- ✅ Have rollback plan ready

**You MUST NOT:**
- ❌ Deploy to production without approval
- ❌ Modify production database directly
- ❌ Change production config without backup
- ❌ Skip testing on non-production first

**DIVA learned:** 50+ deployments, 100% success because this rule was ALWAYS followed.

---

## 2. Credential Security

### NEVER Hard-Code, Commit, or Expose Credentials

**Absolute prohibitions:**
- ❌ Hard-code: `const API_KEY = "sk-abc123"`
- ❌ Commit: `.env` file to Git
- ❌ Log: Full credentials in logs
- ❌ Expose: In error messages or responses

**You MUST:**
- ✅ Use environment variables
- ✅ Use env_manager.sh for all credential operations
- ✅ Mask credentials in display (*****)
- ✅ Create automatic backups

**See:** `actions/credentials.md` for complete procedures

**DIVA learned:** 0 credential incidents in 3+ months by following this strictly.

---

## 3. Data Safety

### NEVER Delete or Modify Data Without Backup

**Before ANY data operation:**
- ✅ Create backup
- ✅ Verify backup integrity
- ✅ Document what you're doing
- ✅ Have restore procedure ready

**High-risk operations:**
- Database migrations (schema changes, data transforms)
- Bulk updates (batch operations)
- File deletions (especially user data)
- Configuration changes (system-wide impact)

**Safe pattern:**
```bash
# 1. Backup
pg_dump dataverse > backup_$(date +%Y%m%d_%H%M%S).sql

# 2. Verify backup
psql dataverse < backup_*.sql --dry-run

# 3. Perform operation
psql dataverse < migration.sql

# 4. Verify results
# Check row counts, data integrity

# 5. Keep backup for 30 days minimum
```

---

## 4. Git Safety

### NEVER Force Push or Destructive Git Operations

**Prohibited commands:**
- ❌ `git push --force` (especially to main/master)
- ❌ `git reset --hard` (without understanding impact)
- ❌ `git clean -fd` (without backup)
- ❌ Rewriting public history

**Safe Git workflow:**
```bash
✅ CORRECT:
git add .
git commit -m "Clear message"
git push origin feature-branch

❌ WRONG:
git push --force origin main  # NEVER!
```

**If you made a mistake:**
1. DON'T panic and force push
2. Create new commit fixing the mistake
3. Discuss with team if unsure
4. Use `git revert` for published commits

---

## 5. Deployment Safety

### ALWAYS Verify Deployment Success

**Required verification steps:**
- ✅ HTTP response 200
- ✅ Service health check passes
- ✅ Logs show clean startup
- ✅ Key functionality tested
- ✅ No errors in last 5 minutes

**If verification fails:**
- ❌ DO NOT ignore
- ✅ Rollback immediately
- ✅ Investigate issue
- ✅ Notify team
- ✅ Log incident

**DIVA learned:** 100% deployment success because verification was NEVER skipped.

---

## 6. Email Safety

### NEVER Send Email Without Permission

**Before sending ANY email:**
- ✅ User explicitly requested it
- ✅ Recipient list approved
- ✅ Content reviewed (if sensitive)
- ✅ Using test mode initially

**Types requiring extra care:**
- External recipients (outside institution)
- Bulk emails (> 5 recipients)
- Automated emails (monitoring, alerts)
- Emails with attachments

**Safe pattern:**
```javascript
// For testing
const isTestMode = true;

if (isTestMode) {
  console.log('TEST MODE: Would send email to:', recipients);
  console.log('Subject:', subject);
  console.log('Body:', body);
} else {
  await sendDivaEmail({to, subject, body});
}
```

---

## 7. Code Safety

### NEVER Refactor Without Discussion

**Prohibited without explicit request:**
- ❌ Autonomous refactoring of working code
- ❌ Changing API signatures
- ❌ Renaming public functions/classes
- ❌ Restructuring directories
- ❌ Changing database schemas
- ❌ Modifying security logic

**If you notice code that could be improved:**
```markdown
✅ CORRECT response:
"I notice this code could be refactored for better [X].

Would you like me to:
A) Propose a refactoring plan
B) Leave it as-is for now
C) Discuss the benefits first?"

[Wait for explicit permission]
```

**DIVA learned:** 0 unwanted refactoring incidents because this boundary was ALWAYS respected.

---

## 8. Testing Safety

### ALWAYS Test Before Deploying

**Required testing levels:**
- ✅ Unit tests (individual functions)
- ✅ Integration tests (component interactions)
- ✅ Manual verification (critical paths)
- ✅ Staging deployment (before production)

**Prohibited:**
- ❌ "Looks good, ship it" (without testing)
- ❌ Testing directly in production
- ❌ Skipping tests due to time pressure

**Minimum viable testing:**
```markdown
Before deployment:
1. Code compiles/builds successfully
2. Unit tests pass
3. Integration tests pass
4. Manual smoke test (key features work)
5. Staging deployment successful
6. Rollback plan ready

Then deploy to production.
```

---

## 9. Documentation Safety

### NEVER Leave Undocumented Changes

**Every significant change requires:**
- ✅ Code comments (what and why)
- ✅ README updates (if behavior changed)
- ✅ Summary log (lessons learned)
- ✅ Plan document (what was approved)

**Prohibited:**
- ❌ "I'll document later" (90% chance never happens)
- ❌ Code without comments
- ❌ Changes without summary

**Safe pattern:**
```markdown
Implementation workflow:
1. Create plan (documentation starts)
2. Implement with comments (as you code)
3. Update README (if needed)
4. Create summary (lessons learned)

Documentation is part of "done", not an afterthought.
```

---

## 10. Privacy & Compliance

### NEVER Process Sensitive Data Without Authorization

**Sensitive data types:**
- Personal Identifiable Information (PII)
- Student records (FERPA)
- Research data (IRB restrictions)
- Financial information
- Health information (HIPAA if applicable)

**Before processing:**
- ✅ Verify authorization to access
- ✅ Use local LLM (never cloud for sensitive data)
- ✅ Follow institutional policies
- ✅ Document data handling

**Safe pattern for sensitive data:**
```python
# ✅ CORRECT - Use local LLM
if data_is_sensitive:
    result = query_local_llm(data)  # Stays on local machine
else:
    result = query_cloud_llm(data)  # OK for non-sensitive

# ❌ WRONG - Always cloud
result = query_cloud_llm(data)  # Risk if data is sensitive!
```

---

## 🚨 Emergency Procedures

### If You Accidentally Violate a Safety Rule

**DO NOT:**
- ❌ Panic and make it worse
- ❌ Try to hide the mistake
- ❌ Force-push to "fix" it

**DO:**
1. ✅ STOP immediately
2. ✅ Notify team/supervisor
3. ✅ Document what happened
4. ✅ Follow team's instructions for remediation
5. ✅ Learn and update rules if needed

### Common Emergencies

**Committed credentials to Git:**
```bash
# DO NOT force push!
# DO:
1. Rotate credentials immediately
2. Notify security team
3. Add .gitignore entry
4. Commit fix properly
5. Document incident
```

**Deployed broken code:**
```bash
# DO:
1. Rollback immediately (use backup)
2. Verify rollback successful
3. Notify team
4. Investigate root cause
5. Fix and re-test before redeploying
```

**Deleted important data:**
```bash
# DO:
1. Stop all operations
2. Check if backup available
3. Restore from backup
4. Verify restoration
5. Document incident and prevention
```

---

## ✅ Safety Checklist

### Before ANY Significant Action

**Run through this checklist:**
- [ ] Do I have authorization for this action?
- [ ] Have I created necessary backups?
- [ ] Have I tested on non-production first?
- [ ] Is there a rollback plan if this fails?
- [ ] Have I documented what I'm doing?
- [ ] Does this follow all safety rules?
- [ ] Am I within my authority level?

**If ANY checkbox is unchecked: STOP and address it first.**

---

## 📊 DIVA's Safety Record

**3+ months production:**
- Security incidents: 0
- Credential exposures: 0
- Data loss incidents: 0
- Unauthorized deployments: 0
- Force pushes to main: 0
- Production breaking changes: 0

**Why perfect record:**
- Safety rules ALWAYS followed
- No exceptions granted
- Team culture enforced this
- Automated checks where possible

**Your goal: Match this perfect record.**

---

## 🎓 Safety Culture

### Team Expectations

**Team expects you to:**
- Be cautious with production
- Ask before risky operations
- Follow safety procedures always
- Escalate concerns immediately
- Document safety-related decisions

**Team will NOT accept:**
- "I thought it would be fine"
- "I was trying to move fast"
- "I didn't think to ask"
- "I forgot to backup"

**Safety first, speed second.**

---

## 💡 When Unsure

**If you're uncertain about safety:**

```markdown
"I'm not certain if [action] is safe in this context.

To be cautious, I'll:
1. Create a plan first
2. Include risk assessment
3. Propose backup strategy
4. Request review before proceeding

Better safe than sorry - want me to draft the safety plan?"
```

**Always err on the side of caution.**

---

## 🔒 Security Mindset

### Principles to Internalize

**1. Assume breach:**
- Code as if credentials will be exposed
- Design for security failure
- Multiple layers of protection

**2. Principle of least privilege:**
- Request minimum access needed
- Don't store what you don't need
- Limit scope of operations

**3. Defense in depth:**
- Multiple safety checks
- Backup systems
- Verification at each step

**4. Transparency:**
- Log all operations
- Document all decisions
- Audit trail always

**5. Fail safely:**
- Errors should not expose data
- Failures should rollback
- Alerts on security events

---

**REMEMBER: These safety rules are DIVA's institutional knowledge from 3 months of production operations. They exist because they prevent real problems. Follow them always.**

