# Development Workflow Rules - COMPREHENSIVE VERSION

## 🎯 **Core Principles**
Design features first, do not code directly. Generate TODO plans for owner review before implementation. Follow the complete documentation lifecycle from planning to architecture integration.

## 📋 **Complete Workflow Process**

### **Phase 1: Daily Planning & Implementation**
- [ ] **Requirements Analysis**: Clarify functional requirements and objectives
- [ ] **Technical Solution**: Design technical implementation approach
- [ ] **Create TODO Plan**: Create timestamped plan document in `docs/plan/todo/`
- [ ] **Owner Review**: Wait for owner review and approval
- [ ] **Plan Approval**: Proceed to coding phase after owner confirmation
- [ ] **Execute According to Plan**: Strictly follow the approved plan
- [ ] **Step-by-step Implementation**: Verify after each step completion

### **Phase 2: Completion & Documentation**
- [ ] **Function Verification**: Test if functionality works as expected
- [ ] **Move Original Plan**: Move original plan to `docs/plan/complete/` folder **WITHOUT MODIFICATION**
- [ ] **Generate Sum-Log**: Create corresponding sum-log document recording specific deployment process
- [ ] **Documentation Update**: Update relevant technical documentation

### **Phase 3: Development Logging (Every 1-2 Days)**
- [ ] **Review Complete Sum-Logs**: Analyze all sum-logs in `docs/plan/complete/`
- [ ] **Create Development Log**: Generate `devlog_{date}_{content}.md` in `docs/development/`
- [ ] **Consolidate Achievements**: Summarize technical improvements and architectural changes
- [ ] **Document Lessons Learned**: Record insights and future development opportunities

### **Phase 4: Architecture Integration (Periodic)**
- [ ] **Review Development Logs**: Analyze accumulated development logs
- [ ] **Update Architecture Docs**: Integrate findings into `docs/architecture/`
- [ ] **Update Feature Docs**: Update `docs/features/` with new capabilities
- [ ] **Update Frontend Docs**: Update `docs/frontend/` if applicable
- [ ] **Update API Docs**: Update `docs/api/` with new endpoints and capabilities

## 📁 **File Management Rules**

### **TODO Plans**
- **Location**: `docs/plan/todo/`
- **Naming**: `{feature_name}_{timestamp}.md`
- **Content**: Detailed task breakdown, technical solutions, risk assessment
- **Status**: Planning Phase
- **Lifecycle**: todo → complete (unchanged)

### **Completed Plans**
- **Location**: `docs/plan/complete/`
- **Naming**: `{feature_name}_{timestamp}.md`
- **Content**: **ORIGINAL plan content WITHOUT modification**
- **Status**: **Keep original status (Planning Phase)**
- **Purpose**: Historical record of the original plan

### **Sum-Logs**
- **Location**: `docs/plan/complete/`
- **Naming**: `{feature_name}_{timestamp}_sum-log.md`
- **Content**: Specific deployment process, issues encountered, solutions
- **Status**: Completed
- **Purpose**: Detailed execution record
- **Lifecycle**: Created after plan completion

### **Development Logs**
- **Location**: `docs/development/`
- **Naming**: `devlog_{YYYYMMDD}_{content_description}.md`
- **Content**: Consolidated summary of multiple sum-logs
- **Frequency**: Every 1-2 days
- **Purpose**: High-level development progress and architectural insights

### **Architecture Documentation**
- **Location**: `docs/architecture/`, `docs/features/`, `docs/frontend/`, `docs/api/`
- **Content**: Final consolidated documentation
- **Frequency**: Periodic (after significant development phases)
- **Purpose**: Official system documentation and reference

## 🔄 **Workflow Examples**

### **Daily Development Cycle**
1. **Morning**: Analyze requirements → Create plan → Owner review → Get approval → Start coding
2. **Afternoon**: Complete coding → Test verification → Move plan to complete → Generate sum-log
3. **Evening**: Update technical documentation

### **Development Logging Cycle (Every 1-2 Days)**
1. **Review**: Analyze all sum-logs in `docs/plan/complete/`
2. **Consolidate**: Create development log with technical achievements
3. **Document**: Record architectural insights and lessons learned

### **Architecture Integration Cycle (Periodic)**
1. **Review**: Analyze accumulated development logs
2. **Integrate**: Update architecture, features, frontend, and API documentation
3. **Consolidate**: Create comprehensive system documentation

## ⚠️ **Important Reminders**

### **Plan Document Handling**
- **✅ DO**: Move original plan to complete folder
- **✅ DO**: Keep original plan content unchanged
- **✅ DO**: Keep original plan status unchanged
- **❌ DON'T**: Modify the original plan content
- **❌ DON'T**: Change the original plan status to "completed"

### **Sum-Log Document Handling**
- **✅ DO**: Create detailed sum-log with execution details
- **✅ DO**: Reference the original plan document
- **✅ DO**: Mark sum-log as "COMPLETED SUCCESSFULLY"
- **✅ DO**: Include all technical achievements and issues

### **Development Log Handling**
- **✅ DO**: Create every 1-2 days
- **✅ DO**: Use standardized naming: `devlog_{YYYYMMDD}_{content}.md`
- **✅ DO**: Consolidate multiple sum-logs
- **✅ DO**: Focus on architectural insights and technical improvements

### **Document Separation**
- **Original Plan**: Historical record of what was planned
- **Sum-Log**: Detailed record of what was actually done
- **Development Log**: High-level consolidation of multiple implementations
- **Architecture Docs**: Final official system documentation
- **Four separate document types**: Each serves different purposes in the lifecycle

## 📝 **Clear Document Templates**

### **TODO Plan Template**
```markdown
# {Feature Name} Plan - {YYYYMMDD_HHMMSS}

**Created:** {Date}
**Status:** 📋 Planning
**Priority:** {Priority}
**Estimated Time:** {Time}

## 🎯 Objective
{Clear description of what needs to be implemented}

## 📋 Task List
- [ ] Task 1
- [ ] Task 2

## 🔧 Technical Solution
{Technical implementation details}

## ⚠️ Risk Assessment
{Potential risks and solutions}
```

### **Sum-Log Template**
```markdown
# {Feature Name} Summary Log - {YYYYMMDD_HHMMSS}

## 1. Plan Reference
- **Plan Document**: `docs/plan/complete/{feature_name}_{timestamp}.md`

## 2. Objective Achieved
{Summary of what was accomplished}

## 3. Execution Details
{Detailed implementation steps}

## 4. Technical Achievements
{Technical accomplishments}

## 5. Issues Encountered
{Problems and solutions}

## 6. Final Results
{Completion status and verification}

**Final Status**: ✅ COMPLETED SUCCESSFULLY
```

### **Development Log Template**
```markdown
# Development Log - {Content Description}

**Date**: {YYYY-MM-DD}  
**Type**: {Major System Implementation/Feature Enhancement/Bug Fix}  
**Status**: Completed  

## 📋 **Overview**
{High-level summary of development period}

## 🚀 **Major Development Achievements**
### **1. {Achievement Name}** ⭐⭐⭐
**Date**: {YYYY-MM-DD}  
**Reference**: `{sum_log_reference}.md`

**Achievement**: {Brief description}
- **Technical Implementation**: {Key technical details}
- **Files Created/Modified**: {List of files}
- **Impact**: {System impact}

## 🔧 **Technical Improvements**
{Consolidated technical improvements across multiple implementations}

## 📊 **Testing and Validation**
{Summary of testing results and validation}

## 🎯 **Architecture Evolution**
{How the system architecture has evolved}

## 📈 **Performance Improvements**
{Quantified improvements and metrics}

## 🔮 **Future Development Opportunities**
{Identified opportunities and next steps}

## 📋 **Development Standards Established**
{New standards and practices established}

## 🎉 **Conclusion**
{Overall assessment and status}
```

## 🎯 **Key Differences**

| Aspect | Original Plan | Sum-Log | Development Log | Architecture Docs |
|--------|---------------|---------|-----------------|-------------------|
| **Purpose** | What was planned | What was actually done | High-level consolidation | Official system reference |
| **Status** | Planning Phase | Completed | Completed | Current |
| **Content** | Original planning content | Execution details | Multiple implementations | Final documentation |
| **Modification** | Never modify | Detailed execution record | Consolidated insights | Official reference |
| **Location** | todo → complete | complete | development | architecture/features/api |
| **Naming** | `{name}_{timestamp}.md` | `{name}_{timestamp}_sum-log.md` | `devlog_{date}_{content}.md` | Various |
| **Frequency** | Per task | Per task | Every 1-2 days | Periodic |
| **Audience** | Developer | Developer | Development team | All stakeholders |

## 🔍 **Common Mistakes to Avoid**

1. **❌ Modifying original plan**: Don't change the original plan content or status
2. **❌ Mixing plan and sum-log**: Keep them as separate documents
3. **❌ Skipping sum-log**: Always create sum-log for completed work
4. **❌ Wrong naming**: Use correct naming convention for all document types
5. **❌ Wrong location**: Move plan to complete, create sum-log in complete
6. **❌ Skipping development logs**: Create devlog every 1-2 days
7. **❌ Not consolidating**: Use development logs to consolidate multiple sum-logs
8. **❌ Delaying architecture updates**: Periodically update official documentation
9. **❌ Inconsistent templates**: Use standardized templates for all document types
10. **❌ Missing references**: Always reference original plans in sum-logs

## 📅 **Documentation Lifecycle Timeline**

```
Day 1: Plan → Implementation → Sum-Log
Day 2: Plan → Implementation → Sum-Log
Day 3: Development Log (consolidates Day 1-2 sum-logs)
Day 4: Plan → Implementation → Sum-Log
Day 5: Plan → Implementation → Sum-Log
Week 2: Development Log (consolidates Day 4-5 sum-logs)
Month 1: Architecture Integration (consolidates all development logs)
```

---

**This comprehensive version establishes a complete documentation lifecycle from daily planning to final architecture integration.**
