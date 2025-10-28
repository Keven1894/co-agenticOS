---
title: "Project Management Rules"
description: "Project coordination and task management principles for the FIU GIS Agent Platform"
version: "1.0.0"
last_updated: "2025-01-25"
scope: "project"
priority: "high"
tags: ["project", "management", "coordination", "tasks", "communication"]
---

# Project Management Rules

## 🎯 **Project Management Principles**

### **1. Plan First**
- **Design First**: Any feature development must have detailed plan first
- **Owner Review**: All plans must be reviewed and approved by owner
- **Documentation Driven**: Documentation-driven development for traceability

### **2. Quality Assurance**
- **Step-by-step Verification**: Verify after each step completion
- **Test Coverage**: Important features must have test coverage
- **Documentation Sync**: Keep code and documentation synchronized

## 📁 **File Management Standards**

### **1. Plan Document Management**
```
docs/plan/
├── todo/                    # Pending plans
│   └── {feature_name}_{timestamp}.md
└── complete/                # Completed plans
    ├── {feature_name}_{timestamp}.md
    └── {feature_name}_{timestamp}_sum-log.md
```

### **2. Naming Standards**
- **Timestamp Format**: `YYYYMMDD_HHMMSS`
- **Feature Name**: Use English, concise and clear
- **Version Control**: Important changes must have version markers

### **3. Document Structure**
- **TODO Plan**: Detailed task breakdown and technical solutions
- **Sum-Log**: Specific implementation process and result records
- **Technical Documentation**: Architecture, API, deployment documentation

## 🔄 **Workflow**

### **1. New Feature Development Process**
```
Requirements Analysis → Technical Design → Create Plan → Owner Review → Get Approval → Start Coding → Test Verification → Complete Deployment → Move Plan → Generate Sum-Log
```

### **2. Bug Fix Process**
```
Bug Discovery → Bug Analysis → Create Fix Plan → Owner Review → Get Approval → Implement Fix → Test Verification → Deploy Fix → Update Documentation
```

### **3. System Optimization Process**
```
Performance Analysis → Optimization Solution → Create Optimization Plan → Owner Review → Get Approval → Implement Optimization → Performance Testing → Deploy Optimization → Effect Evaluation
```

## 📋 **Plan Document Templates**

### **TODO Plan Template**
```markdown
# {Feature Name} - TODO

## 🎯 Objectives
{Feature description and objectives}

## 📋 Task List
- [ ] Task 1: Specific description
- [ ] Task 2: Specific description
- [ ] Task 3: Specific description

## 🔧 Technical Solution
### Architecture Design
{System architecture and component design}

### Implementation Details
{Specific implementation approach}

### Data Flow
{Data flow and processing logic}

## ⚠️ Risk Assessment
### Technical Risks
{Potential technical issues and solutions}

### Business Risks
{Business impact and response measures}

## 📊 Acceptance Criteria
- [ ] Functional completeness
- [ ] Performance requirements
- [ ] Security requirements
- [ ] Documentation completeness
```

### **Sum-Log Template**
```markdown
# {Feature Name} - Sum-Log

## 📊 Execution Summary
{Overall execution situation and results}

## 🔧 Specific Implementation
### Implementation Steps
1. Step 1: Specific operations and results
2. Step 2: Specific operations and results
3. Step 3: Specific operations and results

### Technical Details
{Key technical implementation details}

### Configuration Changes
{System configuration changes}

## 🐛 Issues Encountered
### Issue 1
- **Problem Description**: Specific problem
- **Solution**: How to solve
- **Lessons Learned**: Experience gained

### Issue 2
{Similar format}

## ✅ Final Results
### Function Verification
{Whether functionality works as expected}

### Performance Results
{Performance metrics and performance}

### Deployment Status
{Whether deployment was successful}

## 📝 Follow-up Work
- [ ] Follow-up optimization suggestions
- [ ] Issues to pay attention to
- [ ] Documentation update requirements
```

## ⚠️ **Important Rules**

### **1. Must Follow**
- **Prohibited**: Starting coding without owner review
- **Required**: Every feature must have detailed plan documentation
- **Required**: Generate corresponding sum-log after completion
- **Required**: Maintain documentation integrity and traceability

### **2. Quality Requirements**
- **Code Quality**: Meet project code standards
- **Documentation Quality**: Documentation must be clear, complete, and accurate
- **Test Quality**: Important features must have test coverage

### **3. Communication Requirements**
- **Timely Communication**: Communicate promptly when encountering issues
- **Progress Reports**: Report progress regularly
- **Change Notifications**: Notify important changes promptly

## 📊 **Success Metrics**

### **1. Plan Quality**
- **Completeness**: Plan covers all necessary tasks
- **Feasibility**: Plan is technically feasible
- **Timeliness**: Plan can be completed within reasonable time

### **2. Execution Quality**
- **Execute According to Plan**: Strictly follow plan execution
- **Quality Assurance**: Code and documentation quality meets standards
- **Timely Completion**: Complete within expected time

### **3. Documentation Quality**
- **Completeness**: Documentation covers all important information
- **Accuracy**: Documentation content is accurate and error-free
- **Maintainability**: Documentation is easy to maintain and update
