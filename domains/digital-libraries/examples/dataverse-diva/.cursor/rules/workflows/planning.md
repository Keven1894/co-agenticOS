# Plan-First Discipline
**Workflow Rule - Tier 1 (Always enforced)**

---

## 📋 Core Principle

### CRITICAL: You MUST create a plan before implementation!

**No exceptions unless explicitly overridden by team lead.**

**Why this rule exists:**
- **Quality:** Thoughtful design prevents rework (80% reduction validated)
- **Communication:** Team knows what to expect
- **Learning:** Lessons captured in summaries
- **DIVA learned:** Month 1 resisted → Month 3 team insisted on plans

---

## ✅ Requires a Plan

**You MUST create plan for:**
- ✅ New features
- ✅ Significant bug fixes (> 1 hour estimated work)
- ✅ Architecture changes
- ✅ System modifications
- ✅ Database schema changes
- ✅ Security updates
- ✅ API changes
- ✅ Deployment procedures
- ✅ Integration work

---

## ❌ Does NOT Require Plan

**You can proceed immediately for:**
- ❌ Typo fixes
- ❌ Documentation-only updates
- ❌ Trivial code cleanup (< 15 minutes)
- ❌ Emergency hotfixes (but document after!)
- ❌ Answering questions
- ❌ Explaining code

**When unsure: Create a plan. Better safe than sorry.**

---

## 📝 Plan Template

### Required Sections

```markdown
# [Feature/Fix Name]

## Objective
[What we're trying to achieve - 1-2 sentences, clear and specific]

## Context
[Why this is needed, current state, background information, related work]

## Implementation Steps
1. **Step 1:** [What and how, technical details]
   - Substep 1.1: [Specific action]
   - Substep 1.2: [Specific action]
   
2. **Step 2:** [What and how]
   - Substep 2.1
   - Substep 2.2
   
3. **Step 3:** [What and how]
   ...

## Risk Assessment
- **Risk 1:** [Potential issue description]
  - **Mitigation:** [How to prevent/address]
  - **Probability:** Low/Medium/High
  - **Impact:** Low/Medium/High
  
- **Risk 2:** [Description]
  - **Mitigation:** [Solution]
  - **Probability:** Low/Medium/High
  - **Impact:** Low/Medium/High

## Dependencies
- [External system/service needed]
- [Component that must be ready]
- [Required access/permissions]
- [Team member expertise needed]

## Testing Strategy
- **Unit tests:** [What functionality to test]
- **Integration tests:** [What interactions to test]
- **Manual verification:** [What to check manually]
- **Edge cases:** [What scenarios to validate]
- **Rollback plan:** [How to undo if issues]

## Expected Outcomes
- ✅ Success criterion 1 (specific, measurable)
- ✅ Success criterion 2
- ✅ Acceptance criterion (how user validates)

## Documentation Requirements
- **Code comments:** [What needs inline documentation]
- **README updates:** [What sections to update]
- **API docs:** [What endpoints/functions to document]
- **User guides:** [What user-facing changes need docs]

## Estimated Effort
- Development: [X hours/days]
- Testing: [X hours/days]
- Documentation: [X hours/days]
- **Total:** [X hours/days]

## Approval
- [ ] Reviewed by: [Team member]
- [ ] Technical concerns addressed
- [ ] Security reviewed (if needed)
- [ ] **Approved to proceed:** [Date]
```

---

## 🚀 Workflow

### Step 1: Create Plan

```
User: "Can you add rate limiting to the API?"

You: "I'd be happy to add that! Let me create a plan first 
     so we can review the approach together.
     
     [Create file: docs/plan/todo/api-rate-limiting.md]
     
     I've created a plan that covers:
     - Implementation using Redis for distributed rate limiting
     - Risk: Need Redis installation
     - Testing: Load testing to verify limits
     - Timeline: ~3-4 hours
     
     The plan is at docs/plan/todo/api-rate-limiting.md
     
     Would you like to review it, or shall I proceed with this approach?"
```

---

### Step 2: Get Approval

```
User: "Looks good, but use memory-based rate limiting instead 
      of Redis for simplicity."

You: "Great feedback! I'll update the plan to use memory-based 
     rate limiting instead.
     
     [Update plan]
     
     Updated! Now using memory-based approach. Shall I proceed?"

User: "Approved."
```

---

### Step 3: Implement Following Plan

```
You: [Implement exactly as planned]
    [If you discover better approach mid-work]
    
    "While implementing, I noticed we could also add rate-limit 
     headers (X-RateLimit-Remaining, etc.) for better client UX.
     
     This isn't in the original plan. Want me to:
     A) Stick with the plan
     B) Add rate-limit headers too
     C) Discuss further?"
    
    [Wait for decision before deviating]
```

---

### Step 4: Complete and Summary

```
[When work complete]

You: "Rate limiting is complete! Moving the plan to docs/plan/complete/
     and creating a summary log.
     
     [Move plan file]
     [Create summary at docs/plan/complete/api-rate-limiting-summary.md]
     
     Summary created with:
     - What was built
     - Key decisions (memory-based vs Redis)
     - Challenges (had to adjust limits after testing)
     - Lessons learned (start with conservative limits)
     
     All done!"
```

---

## 📊 Summary Template

### Required After Completion

```markdown
# [Feature Name] - Summary Log

## Completion Date
[YYYY-MM-DD]

## Original Objective
[From plan - what we planned to achieve]

## What Was Actually Built
[Actual implementation - note deviations from plan]

## Key Decisions Made
- **Decision 1:** [What you decided and why]
  - Reason: [Rationale]
  - Alternative considered: [What else was considered]
  
- **Decision 2:** [What you decided]
  - Reason: [Why]

## Deviations from Plan
- **Deviation 1:** [What changed]
  - Why: [Reason for change]
  - Impact: [How it affected outcome]
  
[Or "None - followed plan exactly"]

## Challenges Faced
- **Challenge 1:** [Description of difficulty]
  - **Solution:** [How you overcame it]
  - **Lesson:** [What you learned]
  
- **Challenge 2:** [Description]
  - **Solution:** [How solved]

## Lessons Learned
- ✅ **What worked well:** [Success patterns]
- ⚠️ **What to do differently:** [Improvements for next time]
- 💡 **Unexpected insight:** [Surprises]
- 📚 **Knowledge gained:** [New understanding]

## Metrics
- **Time estimated:** X hours
- **Time actual:** Y hours
- **Accuracy:** [Actual vs estimate]
- **Tests created:** Z tests (all passing)
- **Lines of code:** ~N lines
- **Documentation:** [What was documented]

## Future Improvements
- [Enhancement idea 1]
- [Technical debt to address]
- [Optimization opportunity]

## Artifacts
- **Code commits:** [commit hashes or PR links]
- **Documentation:** [links to new/updated docs]
- **Tests:** [test file locations]
- **Plan:** docs/plan/complete/[this-plan].md
```

---

## ⚠️ Common Pitfalls (DIVA Learned These)

### Pitfall 1: "This is too small for a plan"

**Temptation:**
"It's just a small fix, I'll skip the plan..."

**Reality:**
- "Small" fixes often have hidden complexity
- Even simple changes need clear success criteria
- Learning happens in small tasks too

**DIVA learned:**
- Month 1: Skipped plan for "simple" email update → 2 hours of rework
- Month 2: Created plan even for small tasks → caught issues early
- Month 3: Team never skips plans

**Solution:**
- Create plan if > 30 minutes work
- Can be brief, but still structured
- 5 minutes planning > 1 hour rework

---

### Pitfall 2: "Planning slows us down"

**Team resistance (Month 1):**
- "Can't we just fix it quickly?"
- "Planning takes too much time"
- "We know what we're doing"

**Data proved otherwise:**

| Approach | Plan Time | Dev Time | Rework Time | Total |
|----------|-----------|----------|-------------|-------|
| **No plan** | 0 min | 2 hours | 2 hours | **4 hours** |
| **With plan** | 20 min | 1.5 hours | 15 min | **2.25 hours** |

**Savings:** 43% time reduction (validated over 20+ tasks)

**Month 3 reality:**
Team now says: "Wait, let's see the plan first!"

**Solution:**
- Track time to prove value
- Show issue caught in planning vs implementation
- Enforce consistently

---

### Pitfall 3: Plans Not Updated When Reality Changes

**What happened:**
- Created plan
- During implementation, discovered better approach
- Implemented new approach
- Plan still shows old approach

**Problem:**
- Plan and reality diverge
- Lessons learned unclear
- Future reference misleading

**Solution:**
```markdown
## Deviations from Plan

- **Deviation:** Used approach B instead of planned approach A
- **Why:** Discovered [reason] during implementation
- **Impact:** Better performance, simpler code
- **Lesson:** Always consider [factor] in planning phase next time
```

**Document deviations in summary, update plan if major change.**

---

## 🎯 When to Skip Planning

### Emergency Situations Only

**Production down:**
- Quick hotfix allowed
- But create summary immediately after
- Document what happened, why, how fixed

**Example:**
```
User: "Production is down! Fix immediately!"

You: [Fix immediately without plan]
    
    [After fix deployed]
    
    "Emergency fix deployed. Creating post-mortem summary now..."
    
    [Create summary: docs/plan/complete/emergency-fix-YYYY-MM-DD.md]
    
    Summary includes:
    - What failed
    - Root cause
    - Quick fix applied
    - Proper fix needed
    - How to prevent
```

**Still capture lessons - even more important for emergencies!**

---

## 📈 Evolution: How Team Adopted This

### Month 1: Resistance (60% Compliance)

**Team:** "Too slow, we're experienced developers"  
**DIVA:** Enforced consistently  
**Evidence:** 3 rework incidents (could have been prevented by plans)

### Month 2: Seeing Value (90% Compliance)

**Team:** "Okay, the plan caught that database issue..."  
**DIVA:** Continued enforcement + showed time savings data  
**Evidence:** Rework incidents dropped to 1

### Month 3: Insistence (100% Compliance)

**Team:** "Wait, where's the plan? I want to review it first."  
**DIVA:** Mission accomplished  
**Evidence:** 0 rework incidents, 0 "forgot to plan"

**Quote:**
> "I was skeptical, but planning has caught SO many issues early. I won't let DIVA implement without a plan now." - Team Lead

---

## 🎓 Best Practices

### What Makes a Good Plan

**✅ Clear and Specific:**
- Objective is concrete, measurable
- Steps are actionable
- Success criteria are testable

**✅ Risk-Aware:**
- Identifies what could go wrong
- Has mitigation strategies
- Considers dependencies

**✅ Right-Sized:**
- Detailed enough to guide
- Flexible enough to adapt
- Not micromanaging

**✅ Test-Focused:**
- Clear testing strategy
- Rollback plan if issues
- Verification steps

### Common Mistakes to Avoid

**❌ Too Vague:**
"Improve the system" → What specifically?

**❌ Too Detailed:**
Micromanaging every line of code

**❌ No Risks:**
Overconfident, ignores what could go wrong

**❌ No Tests:**
Hope it works, no verification strategy

**❌ No Success Criteria:**
How do you know when you're done?

---

## 📚 Examples

### Good Plan Example

```markdown
# Add API Rate Limiting

## Objective
Prevent API abuse by limiting requests to 1000/hour per IP address.

## Implementation Steps
1. Add rate-limit middleware (express-rate-limit package)
2. Configure Redis for distributed limiting (if multiple servers)
3. Add rate-limit headers to responses
4. Create tests for limit enforcement
5. Document in API guide

## Risk Assessment
- **Risk:** Redis dependency adds complexity
  - **Mitigation:** Use memory-based for MVP, migrate to Redis later
  - **Probability:** Medium
  - **Impact:** Low

## Testing
- Unit test: Verify limit calculation
- Integration test: Exceed limit, verify 429 response
- Load test: Verify Redis performance under load

## Expected Outcome
- ✅ API returns 429 when limit exceeded
- ✅ Rate-limit headers present in all responses
- ✅ Tests pass

## Estimated Effort
- Development: 3 hours
- Testing: 1 hour
- Documentation: 30 minutes
- **Total:** 4.5 hours
```

**Why this is good:**
- Specific and actionable
- Risks identified with mitigations
- Clear testing strategy
- Measurable outcomes

---

## 🎯 Your Workflow

### Standard Response Pattern

```
User: "Can you add [feature]?"

You: "I'd be happy to add that! Let me create a plan first.
     
     [Create plan in docs/plan/todo/]
     
     I've created a plan at docs/plan/todo/[feature].md
     
     It covers:
     - [Key point 1]
     - [Key point 2]
     - [Risk identified]
     - [Estimated time]
     
     Would you like to review it before I proceed?"

[WAIT FOR APPROVAL]

User: "Looks good, go ahead."

You: "Great! Starting implementation now, following the plan..."

[IMPLEMENT]

[UPON COMPLETION]

You: "Implementation complete! Moving plan to docs/plan/complete/ 
     and creating summary with lessons learned."
```

---

## 📊 DIVA's Evidence

**Validation over 3 months:**
- Plans created: 20+
- Completion rate: 100%
- Plans followed: 100%
- Rework reduction: 80% (vs no-plan baseline)
- "Forgot to document": 0 incidents
- Team satisfaction: High → Very High

**Time Investment vs. Savings:**
- Plan time: 15-30 minutes average
- Rework prevented: 2-4 hours average
- **Net savings:** 1.5-3.5 hours per task

**Team Evolution:**
- Month 1: "This slows us down" (resistant)
- Month 2: "Okay, this caught issues" (accepting)
- Month 3: "Where's the plan?" (insisting)

---

## 💡 Tips for Efficient Planning

### Quick Planning (5-10 minutes)

For smaller tasks:
```markdown
# [Task Name]

**Objective:** [One sentence]

**Steps:**
1. [Step 1]
2. [Step 2]
3. [Step 3]

**Risks:** [Main risk + mitigation]

**Testing:** [How to verify it works]

**Time:** ~[X] hours
```

### Detailed Planning (20-30 minutes)

For complex tasks:
- Use full template
- Identify all risks
- Detailed testing strategy
- Clear success criteria

---

## 🎓 Lessons DIVA Learned

### Lesson 1: Plans Catch Issues Early

**Example:**
- Plan: "Add email automation"
- Risk identified: "Need IT port approvals"
- **Caught in planning!** Would have wasted weeks building it first.

### Lesson 2: Plans Improve Estimates

**Month 1 estimates:** Off by 100-200%  
**Month 3 estimates:** Off by 10-20%

**Why:** Planning forces thinking through details

### Lesson 3: Summaries Are Valuable

**Uses discovered:**
- Onboarding new team members
- Understanding past decisions
- Research evidence
- Pattern identification
- Continuous improvement

**Create summaries ALWAYS** - they pay dividends later.

### Lesson 4: Team Culture Shift

**Unexpected benefit:**
Team discussions improved:
- "What's the plan?"
- "What are the risks?"
- "How will we test?"

**Culture of thoughtfulness emerged.**

---

## ✅ Compliance Checklist

**Before implementing ANY significant work:**
- [ ] Plan created in docs/plan/todo/
- [ ] Plan includes all required sections
- [ ] Risks identified with mitigations
- [ ] Testing strategy defined
- [ ] User approval received
- [ ] Ready to proceed

**After completing work:**
- [ ] Plan moved to docs/plan/complete/
- [ ] Summary created with lessons
- [ ] Deviations documented (if any)
- [ ] Metrics recorded (time, outcomes)
- [ ] Team notified of completion

---

**Remember: DIVA's team resisted this initially. By Month 3, they insisted on it. Trust the process - it works!**

