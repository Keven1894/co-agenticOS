---
title: "Language Standards and Communication Rules"
description: "Language requirements for discussions and documentation in the FIU GIS Agent Platform"
version: "1.0.0"
last_updated: "2025-01-25"
scope: "communication"
priority: "high"
tags: ["language", "communication", "standards", "documentation", "discussion"]
---

# Language Standards and Communication Rules

## 🎯 **Language Policy**

### **1. Communication Language**
- **Discussion**: Can use Chinese or English for discussion
- **Formal Documents**: All generated formal documents must be in English
- **Code**: All code comments, documentation, variable names must be in English
- **API**: All API documentation and responses must be in English

### **2. Document Language Requirements**
- **Technical Documentation**: Must be in English
- **Plan Documents**: Must be in English
- **Sum-Log Documents**: Must be in English
- **Code Comments**: Must be in English
- **Variable Names**: Must be in English
- **Function Names**: Must be in English
- **Database Schema**: Must be in English

## 📝 **Language Standards by Document Type**

### **1. Code Files**
```python
# ✅ Correct - English comments
def calculate_user_score(user_id: str) -> float:
    """
    Calculate user score based on activity and performance.
    
    Args:
        user_id: Unique identifier for the user
        
    Returns:
        Calculated score as float
    """
    pass

# ❌ Incorrect - Chinese comments
def 计算用户分数(用户ID: str) -> float:
    """
    根据用户活动和表现计算用户分数
    """
    pass
```

### **2. Documentation Files**
```markdown
# ✅ Correct - English documentation
# Database Optimization Plan - TODO

## 🎯 Objectives
Optimize database structure, remove redundant tables, use LLM analysis to generate unified work summary data.

## 📋 Task List
- [ ] Delete `developer_work_content` table
- [ ] Create LLM analysis script
- [ ] Migrate data to `work_summaries`

# ❌ Incorrect - Chinese documentation
# 数据库优化计划 - 待办

## 🎯 目标
优化数据库结构，删除冗余表，使用LLM分析生成统一的工作摘要数据。
```

### **3. API Documentation**
```yaml
# ✅ Correct - English API docs
paths:
  /api/users:
    get:
      summary: Get user list
      description: Retrieve paginated list of users
      parameters:
        - name: page
          in: query
          description: Page number for pagination
          type: integer

# ❌ Incorrect - Chinese API docs
paths:
  /api/users:
    get:
      summary: 获取用户列表
      description: 获取分页的用户列表
```

## 🔧 **Implementation Guidelines**

### **1. Code Development**
- **Variable Names**: Use English, descriptive names
- **Function Names**: Use English, action-oriented names
- **Class Names**: Use English, PascalCase
- **Constants**: Use English, UPPER_SNAKE_CASE
- **Comments**: Use English, explain the "why" not just "what"

### **2. Database Schema**
- **Table Names**: Use English, snake_case
- **Column Names**: Use English, snake_case
- **Index Names**: Use English, descriptive names
- **Constraint Names**: Use English, descriptive names

### **3. API Design**
- **Endpoint Names**: Use English, RESTful conventions
- **Parameter Names**: Use English, camelCase or snake_case
- **Response Fields**: Use English, consistent naming
- **Error Messages**: Use English, user-friendly

## 📊 **Quality Checklist**

### **1. Code Quality**
- [ ] All variable names are in English
- [ ] All function names are in English
- [ ] All class names are in English
- [ ] All comments are in English
- [ ] All docstrings are in English

### **2. Documentation Quality**
- [ ] All technical documentation is in English
- [ ] All plan documents are in English
- [ ] All API documentation is in English
- [ ] All deployment guides are in English

### **3. Database Quality**
- [ ] All table names are in English
- [ ] All column names are in English
- [ ] All index names are in English
- [ ] All constraint names are in English

## ⚠️ **Important Reminders**

### **1. Consistency**
- **Naming Convention**: Maintain consistent naming across the project
- **Documentation Style**: Use consistent documentation style
- **Code Style**: Follow consistent code formatting

### **2. Clarity**
- **Descriptive Names**: Use descriptive names that explain purpose
- **Clear Comments**: Write clear comments that explain complex logic
- **Readable Documentation**: Write documentation that is easy to understand

### **3. Maintenance**
- **Regular Review**: Regularly review and update documentation
- **Version Control**: Track changes in documentation
- **Quality Assurance**: Ensure all documents meet language standards

## 🎯 **Benefits of English Standards**

### **1. International Collaboration**
- **Team Communication**: Easier communication with international team members
- **Code Review**: Easier code review for non-Chinese speakers
- **Documentation**: Accessible documentation for all team members

### **2. Technical Benefits**
- **API Consistency**: Consistent API naming across the system
- **Database Clarity**: Clear database schema for all developers
- **Code Readability**: More readable code for all team members

### **3. Maintenance Benefits**
- **Long-term Support**: Easier long-term maintenance
- **Knowledge Transfer**: Easier knowledge transfer between team members
- **Documentation Updates**: Easier documentation updates and maintenance
