# Language Standards - English Only
**Core Rule - Tier 0 (Always Loaded) - CRITICAL PRIORITY**

---

## 🌍 Absolute Requirement

### CRITICAL: All technical communication must be in English!

**No exceptions for:**
- Code and comments
- Documentation
- Commit messages
- Pull requests
- Issue discussions
- Technical plans
- Error messages
- Log output
- API responses
- Configuration files
- Email communication (technical)

---

## ✅ What MUST Be in English

### Code & Comments

```java
// ✅ CORRECT - English
/**
 * Authenticates user credentials against Shibboleth provider.
 * @param username User's institutional ID
 * @return Authentication token if successful
 */
public String authenticateUser(String username) {
    // Verify user exists in database
    User user = userService.findByUsername(username);
    ...
}
```

```java
// ❌ WRONG - Other language in comments
/**
 * 验证用户凭据
 */
public String authenticateUser(String username) {
    // 检查用户是否存在
    ...
}
```

### Documentation

```markdown
✅ CORRECT:
# Email Configuration

This document explains how to configure email settings...

❌ WRONG:
# Configuration du courrier électronique

Ce document explique comment configurer...
```

### Commit Messages

```bash
✅ CORRECT:
git commit -m "Add rate limiting to API endpoints"

❌ WRONG:
git commit -m "Agregar limitación de velocidad a API"
```

### Error Messages

```javascript
✅ CORRECT:
throw new Error('Database connection failed: timeout after 30 seconds');

❌ WRONG:
throw new Error('Conexão com banco de dados falhou');
```

---

## ❌ What CAN Be in Other Languages

**Non-technical content only:**
- User-facing content (if internationalized)
- Help text for non-English users
- Translated UI strings (in separate i18n files)
- Cultural/regional content

**Example:**
```javascript
// ✅ CORRECT - Technical in English, user content translated
const messages = {
  en: "Welcome to Dataverse",
  es: "Bienvenido a Dataverse",  // UI translation OK
  fr: "Bienvenue à Dataverse"
};

// Code comment in English
// Retrieve message based on user's locale preference
const welcomeMessage = messages[userLocale] || messages.en;
```

---

## 🎯 Why English-Only?

### Reasons from DIVA Experience

**1. Global Collaboration**
- Team may include international members
- English is common technical language
- Enables broader collaboration

**2. Tool Compatibility**
- Most development tools expect English
- Better IDE support
- Better LLM understanding

**3. Knowledge Sharing**
- Documentation accessible globally
- Research publications require English
- Community contributions easier

**4. Consistency**
- One language = one source of truth
- No translation drift
- Clearer communication

**5. Professional Standards**
- Academic institutions use English for technical work
- Industry standard for international projects
- Library technology community expects English

---

## 🔧 Implementation

### Agent Rule

```markdown
## Language Policy

You MUST use English for all technical communication:

**Always English:**
- All code you write
- All comments you add
- All documentation you generate
- All commit messages
- All technical discussions
- All error messages
- All log output

**Check before committing:**
- No non-English comments in code
- No non-English documentation
- No non-English commit messages

**If user writes in another language:**
- Respond politely in English
- Offer to continue in English
- Translate if requested (but explain English policy)
```

---

## 🚨 Common Violations to Avoid

### Violation 1: Mixed-Language Comments

```java
❌ WRONG:
public void processData() {
    // Procesar los datos del usuario
    // Process user data
    ...
}

✅ CORRECT:
public void processData() {
    // Process user data
    ...
}
```

### Violation 2: Non-English Variable Names

```javascript
❌ WRONG:
const nombreUsuario = user.name;
const fechaCreación = new Date();

✅ CORRECT:
const username = user.name;
const createdDate = new Date();
```

**Exception:** Domain terms that are inherently non-English (rare)

### Violation 3: Non-English Documentation

```markdown
❌ WRONG:
# Configuración del Sistema

Para configurar el sistema...

✅ CORRECT:
# System Configuration

To configure the system...
```

---

## 🌐 Working with Non-English Speakers

### Respectful Response Pattern

**If user communicates in another language:**

```markdown
User: "¿Puedes ayudarme con la configuración?"

Agent: "I'd be happy to help with the configuration! 

(Note: Our project follows English-only policy for technical 
communication to ensure global collaboration and consistency.)

What specifically would you like to configure?"
```

**Key points:**
- Be respectful and helpful
- Explain policy briefly
- Continue conversation productively in English
- Offer assistance with English if needed

---

## ✅ Validation Checklist

**Before committing any work:**
- [ ] All code comments in English
- [ ] All documentation in English
- [ ] Commit message in English
- [ ] Variable names in English (domain terms excepted)
- [ ] Error messages in English
- [ ] No mixed-language content

---

## 📊 DIVA Evidence

**3+ months operation:**
- English-only compliance: 100%
- Mixed-language incidents: 0
- Communication clarity: Improved
- Global accessibility: Achieved

**Team feedback:**
- Consistent documentation appreciated
- Easier for international collaborations
- Professional standards maintained

---

## 🎓 Best Practices

### Writing Clear English

**For Non-Native English Speakers:**
- Use simple, clear sentences
- Avoid idioms and slang (technical English)
- Use grammar checkers (Grammarly, etc.)
- Ask for review if uncertain
- It's okay if not perfect - clarity matters most

**For Technical Writing:**
- Be precise and specific
- Use standard terminology
- Follow documentation templates
- Check spelling and grammar
- Clarity over complexity

---

**Remember: This policy ensures global accessibility and professional standards. When in doubt, use English!**

