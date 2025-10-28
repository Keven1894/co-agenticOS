---
title: "Code Standards and Best Practices"
description: "Code quality and formatting standards for the FIU GIS Agent Platform"
version: "1.0.0"
last_updated: "2025-01-25"
scope: "code"
priority: "high"
tags: ["code", "standards", "quality", "formatting", "best-practices"]
---

# Code Standards and Best Practices

## 🎯 **Code Quality Standards**

### **1. Code Style**
- **Language**: All code comments, documentation, variable names must be in English
- **Format**: Follow existing project code style
- **Naming**: Use meaningful variable and function names
- **Comments**: Critical logic must have English comments

### **2. File Organization**
- **Modularity**: Organize functionality by modules, avoid oversized single files
- **Imports**: Use relative imports, avoid circular dependencies
- **Structure**: Maintain clear directory structure

### **3. Error Handling**
- **Exception Handling**: Appropriate exception handling and error logging
- **User Friendly**: Error messages should be clear and understandable
- **Logging**: Important operations must have logging

## 🔧 **Technical Standards**

### **1. Database Operations**
- **Connection Management**: Use connection pooling, avoid connection leaks
- **Transaction Handling**: Use transactions for important operations
- **SQL Security**: Use parameterized queries to prevent SQL injection

### **2. API Design**
- **RESTful**: Follow REST API design principles
- **Status Codes**: Use correct HTTP status codes
- **Response Format**: Unified response format

### **3. Performance Optimization**
- **Query Optimization**: Database queries must be efficient
- **Caching Strategy**: Use caching appropriately
- **Resource Management**: Release resources promptly

## 📝 **Documentation Requirements**

### **1. Code Documentation**
- **Function Comments**: Every function must have docstring
- **Parameter Description**: Parameter types and purposes must be clear
- **Return Values**: Return value types and meanings must be explained

### **2. API Documentation**
- **Interface Description**: Every API must have detailed description
- **Parameter Documentation**: Request parameters and response format
- **Example Code**: Provide usage examples

### **3. Deployment Documentation**
- **Environment Requirements**: Runtime environment requirements
- **Configuration Description**: Configuration file description
- **Deployment Steps**: Detailed deployment steps

## ⚠️ **Prohibited Items**

### **1. Code Quality**
- **Prohibited**: Hardcoding sensitive information
- **Prohibited**: Ignoring exception handling
- **Prohibited**: Using deprecated APIs

### **2. Security Requirements**
- **Prohibited**: Directly executing user input
- **Prohibited**: Exposing sensitive information
- **Prohibited**: Using insecure encryption methods

### **3. Performance Requirements**
- **Prohibited**: Executing database queries in loops
- **Prohibited**: Ignoring memory leaks
- **Prohibited**: Using blocking operations

## 🔍 **Code Review**

### **1. Review Points**
- **Functional Correctness**: Whether code implements expected functionality
- **Code Quality**: Whether it meets project standards
- **Performance Impact**: Whether it affects system performance
- **Security**: Whether there are security risks

### **2. Review Process**
- **Self-check**: Check code before submission
- **Peer Review**: Important features require peer review
- **Test Verification**: Ensure functionality works correctly

## 📊 **Quality Metrics**

### **1. Code Coverage**
- **Target**: Key functionality test coverage > 80%
- **Tools**: Use appropriate testing frameworks
- **Reports**: Generate coverage reports regularly

### **2. Performance Metrics**
- **Response Time**: API response time < 500ms
- **Concurrency**: Support appropriate concurrent users
- **Resource Usage**: Reasonable memory and CPU usage

### **3. Security Metrics**
- **Vulnerability Scanning**: Regular security scanning
- **Dependency Updates**: Update dependencies promptly
- **Access Control**: Appropriate permission management
