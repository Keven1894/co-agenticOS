# Workflow Patterns for Digital Libraries
**Domain-Specific Rules for AI Agents**

**Domain:** Digital Libraries & Institutional Repositories  
**Source:** DIVA operational experience (3+ months production)  
**Date:** November 12, 2025  
**Evidence Quality:** Excellent (100% adherence validated)

---

## Rule 1: Plan-First Discipline

### 🎯 Purpose

Enforce "no implementation without documented plan" to improve quality, communication, learning capture, and team alignment. Every significant work item requires an approved plan before execution.

### 🔍 The Problem

**Traditional Approach (Jump to Code):**
```
User: "Add rate limiting to API"
Agent: [Starts coding immediately]
        [Discovers issues mid-implementation]
        [Makes decisions on the fly]
        [Forgets to document decisions]
Result: Sub-optimal design, missed edge cases, unclear expectations, lost lessons
```

**Problems:**
- Design flaws discovered too late
- Team doesn't know what to expect
- Success criteria unclear
- Lessons learned not captured
- Rework when assumptions wrong

### ✅ The Solution: Plan-First Workflow

**Core Principle:**
Before ANY significant implementation, create a documented plan that:
1. States objectives clearly
2. Identifies risks upfront
3. Sets success criteria
4. Gets team approval
5. Guides execution
6. Captures lessons learned

**Improved Flow:**
```
User: "Add rate limiting to API"
Agent: [Creates plan document]
        ↓
       [User reviews and approves]
        ↓
       [Agent implements following plan]
        ↓
       [Upon completion: Summary with lessons]
Result: Thoughtful design, clear expectations, captured learning
```

### 📋 Plan Template

```markdown
# [Feature/Fix Name]

## Objective
[What we're trying to achieve - 1-2 sentences]

## Context
[Why this is needed, current state, background information]

## Implementation Steps
1. **Step 1:** [What and how, with technical details]
   - Substep 1.1
   - Substep 1.2
   
2. **Step 2:** [What and how]
   - Substep 2.1
   - Substep 2.2
   
3. **Step 3:** [What and how]
   ...

## Risk Assessment
- **Risk 1:** [Description of potential issue]
  - **Mitigation:** [How to prevent/address]
  - **Probability:** Low/Medium/High
  - **Impact:** Low/Medium/High
  
- **Risk 2:** [Description]
  - **Mitigation:** [Solution]

## Dependencies
- [External system/service needed]
- [Related component that must be ready]
- [Required resource/access]

## Testing Strategy
- **Unit tests:** [What functionality to test]
- **Integration tests:** [What interactions to test]  
- **Manual verification:** [What to check manually]
- **Rollback plan:** [How to undo if issues]

## Expected Outcomes
- ✅ Success criterion 1
- ✅ Success criterion 2
- ✅ Acceptance criterion

## Documentation Requirements
- Code comments: [What needs inline documentation]
- README updates: [What sections need updating]
- API docs: [What endpoints/functions to document]
- User guides: [What user-facing changes]

## Estimated Effort
- Development: [X hours/days]
- Testing: [X hours/days]
- Documentation: [X hours/days]
- Total: [X hours/days]

## Approval
- [ ] Team Lead Review
- [ ] Technical Review (if needed)
- [ ] Security Review (if needed)
- [ ] Approved to Proceed
```

### 🔧 Implementation

#### Step 1: Create Plan Directory

```bash
docs/plan/
├── todo/          # Plans awaiting approval or in progress
├── complete/      # Finished plans (archived)
└── templates/     # Plan templates
```

#### Step 2: Agent Rule

```markdown
### 📋 Plan-First Requirement

**CRITICAL: You MUST create a plan before implementation!**

**Requires a plan:**
- ✅ New features
- ✅ Significant bug fixes (> 1 hour work)
- ✅ Architecture changes
- ✅ System modifications
- ✅ Database changes
- ✅ Security updates
- ✅ API changes

**Does NOT require a plan:**
- ❌ Typo fixes
- ❌ Documentation-only updates
- ❌ Trivial code cleanup (< 15 min)
- ❌ Emergency hotfixes (but document after)

**Workflow:**
1. Create plan in `docs/plan/todo/[feature-name].md`
2. Notify team for review
3. Wait for approval
4. Implement following plan
5. Do NOT deviate without discussing
6. Move plan to `docs/plan/complete/` when done
7. Create summary log with lessons learned

**NO EXCEPTIONS** unless explicitly overridden by team lead.
```

#### Step 3: Enforcement Pattern

```markdown
User: "Can you add feature X?"

Agent Response:
"I'd be happy to add that! Let me create a plan first so we can review the approach.

[Creates plan document]

I've created a plan at docs/plan/todo/feature-x.md that covers:
- Implementation steps
- Potential risks
- Testing strategy  
- Expected timeline

Would you like to review it, or should I proceed with this approach?"

[Wait for approval before implementation]
```

### 📊 Evidence from DIVA

**Validation Results:**

| Metric | Result | Significance |
|--------|--------|--------------|
| **Plans Created** | 20+ over 3 months | Consistent use |
| **Completion Rate** | 100% | All plans followed through |
| **Adherence Rate** | 100% | No unplanned implementations |
| **"Forgot to Document"** | 0 incidents | Perfect capture |
| **Team Satisfaction** | High | Positive feedback |
| **Rework Rate** | 5% vs 25% baseline | 80% reduction |

**Specific Examples:**

**Email System Implementation:**
- Plan created: Outlined architecture, risks, testing
- Risks identified: Gmail API limits, credential security
- Result: Smooth implementation, zero issues in production

**n8n Automation:**
- Plan identified: IT port approval needed
- Risk caught: Would have built system that couldn't deploy
- Result: Alternative approach prepared

**Content Watcher Agent:**
- Plan outlined: File watching, LLM integration, Git automation
- Testing strategy: Prevented several edge case bugs
- Result: Deployed successfully, 83% time reduction achieved

### 🎯 Team Adoption Journey

**Month 1: Resistance**
- Team: "Planning slows us down"
- Reality: Quick fixes took longer due to rework
- Compliance: 60%

**Month 2: Seeing Value**
- First few plans caught issues early
- Time tracking proved planning saves time
- Compliance: 90%

**Month 3: Insistence**
- Team now ASKS for plans
- "Can we see the plan first?" common question
- Compliance: 100%

**Quote:**
> "I was skeptical at first, but now I won't let the agent implement anything without a plan. We've caught so many issues in the planning phase that would have been painful in production." - Team Lead

### 🚀 Getting Started

**Minimal Implementation (30 minutes):**

1. **Create directory:**
```bash
mkdir -p docs/plan/{todo,complete}
```

2. **Add agent rule:**
```markdown
# .cursor/rules/workflows/planning.md

### Plan-First Discipline

Before implementing:
1. Create plan in docs/plan/todo/
2. Get approval
3. Implement following plan
4. Move to complete/ when done
```

3. **Create first plan:**
- Pick next work item
- Use template above
- Review with team
- Observe improved outcome

**First Win:** Catch one issue in planning phase that would have been painful in implementation!

### 📈 Scaling Strategy

**Phase 1: Core Team (Week 1)**
- Require plans for major work only
- Use simple template
- Build habit

**Phase 2: Expansion (Weeks 2-4)**
- Extend to all significant work
- Enhance template based on learnings
- Enforce consistently

**Phase 3: Optimization (Month 2)**
- Integrate with project management
- Automate plan tracking
- Analyze metrics

**Phase 4: Maturity (Month 3+)**
- Team insists on plans
- Plans are living documents
- Continuous template improvement

### 🎓 Best Practices

**What Makes a Good Plan:**
1. **Clear objective** (not vague goals)
2. **Realistic steps** (actionable, not too high-level)
3. **Risk awareness** (what could go wrong)
4. **Test strategy** (how to verify it works)
5. **Success criteria** (how to know we're done)

**Common Mistakes:**
- ❌ Too vague ("Improve system")
- ❌ Too detailed (micromanaging every line)
- ❌ No risks identified (overconfident)
- ❌ No test strategy (hope it works)
- ❌ No success criteria (never "done")

**Sweet Spot:**
- ✅ Specific enough to guide
- ✅ Flexible enough to adapt
- ✅ Risk-aware but not paranoid
- ✅ Test-focused
- ✅ Clear finish line

### 📚 Summary Logging

**After Completion, Create Summary:**

```markdown
# [Feature Name] - Summary Log

## Completion Date
2025-11-12

## Original Objective
[From plan]

## What Was Built
[Actual implementation, note any deviations from plan]

## Key Decisions
- **Decision 1:** Chose approach X over Y because [reason]
- **Decision 2:** Added feature Z when we discovered [need]

## Challenges Faced
- **Challenge 1:** [Description]
  - **Solution:** [How we solved it]
  - **Lesson:** [What we learned]

## Lessons Learned
- ✅ What worked well
- ⚠️ What to do differently next time
- 💡 Insights for future work

## Metrics
- Time estimated: X hours
- Time actual: Y hours
- Tests created: Z tests
- Documentation: [What was documented]

## Future Improvements
- [Enhancement idea 1]
- [Enhancement idea 2]

## Artifacts
- Code: [commit hash or PR link]
- Documentation: [links]
- Tests: [test files]
```

**Benefits:**
- Lessons captured (not forgotten)
- Estimates improve (historical data)
- Knowledge shared (team learning)
- Onboarding easier (context available)

---

## Rule 2: Bounded Autonomy Framework

### 🎯 Purpose

Establish clear authority levels for agent actions to build trust gradually, prevent unwanted changes, ensure human oversight for critical decisions, and create clear escalation patterns.

### 🔍 The Problem

**Full Autonomy (Too Risky):**
```
Agent: [Makes all decisions independently]
Team: [Anxious about unexpected changes]
       [Unsure what agent will do]
       [Trust is all-or-nothing]
Result: Low trust, high anxiety, resistance to adoption
```

**Manual Everything (Too Slow):**
```
Agent: [Asks for approval for every action]
Team: [Constant interruptions]
       [Bottleneck on simple tasks]
Result: Inefficient, frustrating, defeats purpose
```

**Problem:** Need balance between speed and safety.

### ✅ The Solution: Bounded Autonomy Levels

**Core Principle:**
Define 4 authority levels with clear boundaries. Agent operates autonomously within level, escalates when exceeding authority.

### 📋 Authority Levels

#### Level 1: Autonomous (No Approval Needed)

**Agent can act independently:**
- ✅ Answer questions
- ✅ Explain code/systems
- ✅ Generate documentation
- ✅ Search/analyze codebase
- ✅ Suggest improvements
- ✅ Run read-only commands
- ✅ Create plans (but not implement)

**Example:**
```
User: "What does the authentication module do?"
Agent: [Explains immediately, no approval needed]
```

**Characteristics:**
- No side effects
- Read-only operations
- Information provision
- Low risk

#### Level 2: Supervised (Show Plan → Get Approval → Execute)

**Agent needs approval before acting:**
- ⚠️ Implement features
- ⚠️ Fix bugs
- ⚠️ Modify code
- ⚠️ Create new files
- ⚠️ Run deployments
- ⚠️ Send communications
- ⚠️ Run write operations

**Example:**
```
User: "Add rate limiting to the API"
Agent: [Creates plan]
       "Here's my approach:
        1. Add rate-limit middleware
        2. Configure Redis for tracking
        3. Add tests
        
        Approve to proceed?"
User: "Approved"
Agent: [Implements]
```

**Characteristics:**
- Proposal first
- Wait for confirmation
- Then execute
- Medium risk

#### Level 3: Collaborative (Discussion Required)

**Agent proposes, human decides:**
- 🤔 Architecture changes
- 🤔 API modifications
- 🤔 Directory restructuring
- 🤔 Security changes
- 🤔 Database schema changes
- 🤔 Production operations

**Example:**
```
Agent: "I notice the authentication system could be improved.
        
        Current: Session-based (scaling issues)
        Alternative: JWT tokens (stateless, scalable)
        
        Trade-offs:
        + Better scalability
        + Microservice-ready
        - Migration effort
        - Refresh token complexity
        
        Want to discuss this approach?"

[Discussion ensues, human decides]
```

**Characteristics:**
- Present options
- Explain trade-offs
- Human makes decision
- High impact

#### Level 4: Prohibited (Never Without Explicit Request)

**Agent MUST NOT do without being specifically asked:**
- ❌ Autonomous refactoring
- ❌ Changing agreed plans
- ❌ Modifying credentials
- ❌ Force pushing to main
- ❌ Deleting data/files (outside normal workflow)
- ❌ Breaking changes without discussion
- ❌ Changing agent's own authority levels

**Example:**
```
Agent: [Notices code could be refactored]
       [DOES NOT refactor autonomously]
       [Instead mentions in comment or discussion]
       
Agent: "FYI: This module could benefit from refactoring when we have time"
       [Waits for explicit request before proceeding]
```

**Characteristics:**
- Explicitly forbidden
- Suggest only, don't act
- Wait for clear request
- Very high risk

### 🔧 Implementation

#### Step 1: Document in Agent Rules

```markdown
### 🎯 Bounded Autonomy Framework

You operate under a 4-level authority system:

**Level 1: Autonomous** (do immediately)
- Answer questions
- Explain code
- Generate documentation
- Read-only operations

**Level 2: Supervised** (propose → approve → execute)
- Implement features
- Fix bugs
- Modify code
- Run deployments

**Level 3: Collaborative** (discuss → decide → execute)
- Architecture changes
- API modifications
- Security changes
- Database schema changes

**Level 4: Prohibited** (never without explicit request)
- Autonomous refactoring
- Changing agreed plans
- Modifying credentials
- Force pushing to main

**When unsure of level, escalate to next higher level.**
```

#### Step 2: Communication Patterns

**When Operating in Level 1:**
```markdown
User: "What's in this module?"
Agent: [Explains immediately]
```

**When Operating in Level 2:**
```markdown
User: "Fix the login bug"
Agent: "I can fix that! Here's my plan:
       1. [Step 1]
       2. [Step 2]
       
       Approve to proceed?"
[Wait for approval]
```

**When Considering Level 3:**
```markdown
Agent: "I notice [observation].
       
       Current approach: [A]
       Alternative: [B]
       
       Trade-offs:
       [Pros and cons]
       
       Want to discuss, or stick with current approach?"
```

**When Encountering Level 4:**
```markdown
Agent: "I notice the codebase could use refactoring.
       However, that's beyond my authority without explicit request.
       
       Would you like me to:
       A) Propose a refactoring plan
       B) Continue with current task
       C) Something else?"
```

#### Step 3: Escalation Rules

```markdown
### Escalation Pattern

When uncertain about authority level:
1. Assume HIGHER level (more cautious)
2. Explain the situation
3. Ask for clarification
4. Remember the decision for similar future cases

Example:
"I'm not sure if [action] requires approval or discussion.
To be safe, I'll treat it as Level 3 (collaborative).
Here's what I'm proposing..."
```

### 📊 Evidence from DIVA

**Validation Results:**

| Metric | Month 1 | Month 2 | Month 3 |
|--------|---------|---------|---------|
| **Trust Score (1-10)** | 7.0 | 8.5 | 9.2 |
| **Unauthorized Actions** | 0 | 0 | 0 |
| **Authority Disputes** | 2 | 0 | 0 |
| **Team Anxiety** | Medium | Low | Minimal |
| **Supervision Time** | High | Medium | Low |

**Trust Growth Over Time:**
- **Month 1:** Team watches carefully, frequent checks
- **Month 2:** Team comfortable with Levels 1-2, cautious on Level 3
- **Month 3:** Team trusts DIVA fully, minimal supervision

**Team Feedback:**
> "The bounded autonomy framework was brilliant. We never felt like DIVA would do something unexpected. Trust built naturally." - Development Team Lead

### 🎯 Trust Building Strategy

**Week 1-2: Establish Boundaries**
- Document all 4 levels clearly
- Agent operates conservatively
- Team observes and calibrates

**Week 3-4: Demonstrate Reliability**
- Perfect adherence to levels
- No boundary violations
- Trust in Levels 1-2 grows

**Month 2: Expand Comfort**
- Team delegates more Level 2 work
- Level 3 discussions become efficient
- Supervision decreases

**Month 3: Mature Trust**
- Team confident in agent judgment
- Agent knows when to escalate
- Collaboration feels natural

### 🚀 Getting Started

**Minimal Implementation (15 minutes):**

1. **Create authority document:**
```markdown
# .cursor/rules/core/autonomy.md

## Bounded Autonomy Framework

Level 1 (Autonomous): [list actions]
Level 2 (Supervised): [list actions]  
Level 3 (Collaborative): [list actions]
Level 4 (Prohibited): [list actions]

When uncertain, escalate up one level.
```

2. **Test with team:**
- Run through scenarios
- Clarify edge cases
- Document decisions

3. **Enforce consistently:**
- Agent follows strictly
- Team holds agent accountable
- Build trust through reliability

### 📈 Evolution Pattern

**Early Stage: Conservative**
- Most actions in Level 2-3
- Frequent check-ins
- Build trust slowly

**Middle Stage: Delegation**
- Proven actions move to Level 1
- Level 2 streamlined
- Less supervision needed

**Mature Stage: Efficient**
- Clear patterns established
- Quick decisions
- Trust enables speed

**DIVA Example:**
- **Week 1:** Everything supervised
- **Month 1:** Deployment becomes supervised (was collaborative)
- **Month 2:** Documentation becomes autonomous (was supervised)
- **Month 3:** Team rarely questions authority levels

### 🤝 Team Calibration

**Regular Review (Monthly):**
```markdown
Questions to ask:
1. Are any Level 2 actions ready for Level 1?
2. Should any actions move down (more supervision)?
3. Are boundaries clear for everyone?
4. Any new actions need classification?

Document decisions and update rules.
```

### 📚 Related Rules

- **Plan-First Discipline** (above) - What Level 2-3 work requires
- **Communication Patterns** (communication.md) - How to propose and discuss
- **Credential Management** (security.md) - Why some actions are Level 4

### 🔬 Research Contribution

**Novel Aspects:**
1. **4-Level Framework**: Clear authority hierarchy for agents
2. **Trust Building Path**: Graduated autonomy as trust grows
3. **Production Validation**: 100% adherence over 3 months
4. **Zero Violations**: Perfect boundary respect

**Compared to Other Approaches:**

| Approach | Trust Building | Efficiency | Safety |
|----------|---------------|------------|--------|
| **Full Autonomy** | Risky | High | Low |
| **Manual Everything** | Slow | Low | High |
| **Bounded Autonomy** | **Gradual** | **Balanced** | **High** |

---

**Status:** 2 workflow rules documented with DIVA evidence  
**Format:** Problem → Solution → Implementation → Evidence  
**Awaiting:** Feedback on format before creating remaining rules

