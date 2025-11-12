# Email Sending - Master Function
**Standard Procedure - Tier 1 (Context: email)**

---

## 🔧 Master Email Function

### CRITICAL: Always use `sendDivaEmail()` - NEVER write ad-hoc email code!

**Why this rule exists:**
- **Consistency:** Same email behavior every time
- **Reliability:** Built-in retry logic (3 attempts)
- **Logging:** All operations tracked automatically
- **Templates:** Standardized formatting
- **DIVA learned:** Session 1 built ad-hoc code → Session 5 duplicated differently → Month 2 standardized → 100% consistency

---

## 📧 When to Send Email

**✅ DO send email when:**
- User explicitly requests DIVA to send email
- Notifying users of completed work (if requested)
- Deployment completion notifications (if configured)
- Critical alerts (if part of monitoring setup)

**❌ DO NOT send email:**
- Without user permission
- For routine operations
- During testing (use test mode)
- To external addresses without approval

---

## 💻 How to Use

### Basic Email

```javascript
const { sendDivaEmail } = require('./ai-backend/mail/diva_mailer.js');

await sendDivaEmail({
  to: 'user@fiu.edu',
  subject: 'Deployment Complete',
  body: 'The production deployment completed successfully at ' + new Date().toLocaleString()
});
```

### HTML Email

```javascript
await sendDivaEmail({
  to: 'team@fiu.edu',
  subject: 'Weekly Summary',
  body: 'Plain text version',
  html: `
    <h2>Weekly Summary</h2>
    <p>This week we completed:</p>
    <ul>
      <li>Feature A</li>
      <li>Bug fix B</li>
    </ul>
  `
});
```

### With Attachments

```javascript
await sendDivaEmail({
  to: 'researcher@fiu.edu',
  subject: 'Data Export Ready',
  body: 'Your requested data export is attached.',
  attachments: [
    {
      filename: 'export.csv',
      path: '/path/to/export.csv'
    }
  ]
});
```

### Using Templates

```javascript
const template = 'deployment_notification'; // Pre-defined template

await sendDivaEmail({
  to: 'devteam@fiu.edu',
  template: template,
  data: {
    deployment_time: new Date(),
    version: '6.0.1',
    status: 'success'
  }
});
```

---

## ⚙️ The Function Automatically

- **Retry Logic:** 3 attempts with exponential backoff (2s, 4s, 8s)
- **Error Handling:** Catches and logs all failures gracefully
- **Logging:** Every send attempt tracked (timestamp, recipient, result)
- **Validation:** Email addresses validated before sending
- **Templates:** Pre-defined templates for common messages
- **HTML Support:** Automatic plain text fallback

**You don't have to implement these - they're built-in!**

---

## 🚨 Common Pitfalls (DIVA Learned These)

### Pitfall 1: Writing Inline Nodemailer Code

**❌ WRONG:**
```javascript
const nodemailer = require('nodemailer');
const transporter = nodemailer.createTransport({...});
await transporter.sendMail({...}); // Don't do this!
```

**✅ CORRECT:**
```javascript
const { sendDivaEmail } = require('./ai-backend/mail/diva_mailer.js');
await sendDivaEmail({...}); // Always use master function
```

**Why:** Master function has retry, logging, error handling. Ad-hoc code doesn't.

---

### Pitfall 2: Forgetting Error Handling

**❌ WRONG:**
```javascript
await sendDivaEmail({...}); // What if it fails?
console.log('Email sent!'); // This runs even if failed!
```

**✅ CORRECT:**
```javascript
try {
  await sendDivaEmail({...});
  console.log('✅ Email sent successfully');
} catch (error) {
  console.error('❌ Email failed:', error.message);
  // Handle failure appropriately
}
```

**Why:** Email can fail (network issues, quota, invalid address). Always handle errors.

---

### Pitfall 3: No Logging

**❌ WRONG:**
```javascript
await sendDivaEmail({...});
// No record of what was sent
```

**✅ CORRECT:**
```javascript
const result = await sendDivaEmail({...});
console.log(`Email sent to ${result.to} at ${result.timestamp}`);
// Or use master function's built-in logging
```

**Why:** Audit trail critical for debugging and compliance.

**Note:** Master function logs automatically, but you can add context-specific logging too.

---

## 📖 Full Documentation

**Detailed documentation:** `docs/n8n/DIVA_MASTER_EMAIL_FUNCTION.md`

**Includes:**
- Complete function source code
- All configuration options
- Template system documentation
- Retry logic details
- Error handling patterns
- Testing procedures

---

## 🔬 Evidence (DIVA Production)

**Validation Metrics:**
- Emails sent: 200+
- Success rate: 100%
- Failed sends (after retries): 0
- Consistency: 100% (all used master function)
- Incidents: 0

**Team Feedback:**
> "Never have to think about email implementation. It just works." - Dev Team

---

## 🎯 When to Create New Email Function

**Never.**

**If you need:**
- Different templates → Add to template system
- New features → Extend sendDivaEmail()
- Different provider → Discuss with team first

**DO NOT create parallel email functions. One master function = one source of truth.**

---

**REMEMBER: This function exists because DIVA spent 3 months learning email handling. You inherit that knowledge instantly by using this function.**

