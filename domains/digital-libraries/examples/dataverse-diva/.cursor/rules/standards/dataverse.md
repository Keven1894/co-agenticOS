# Dataverse Platform Knowledge
**Standards Rule - Tier 1 (Context: Dataverse-specific work)**

---

## 📚 Dataverse Platform Overview

### What You Need to Know

**Dataverse** is an open-source research data repository software developed by Harvard IQSS.

**Key concepts:**
- **Dataverse (container):** Collection of datasets
- **Dataset:** Research data with metadata
- **DataFile:** Individual files within dataset
- **Dataverse Collection:** Hierarchical organization

---

## 🏗️ Architecture Components

### Core Technologies

**Application Server:**
- **Payara 6** (formerly GlassFish)
- Jakarta EE 10
- Port: 8080 (HTTP), 8181 (HTTPS admin)
- Domain: domain1

**Database:**
- **PostgreSQL** (primary database)
- Stores: Metadata, users, permissions, versions
- Connection: localhost:5432

**Search:**
- **Apache Solr 9.0**
- Full-text search and faceting
- Index: Metadata, full-text content
- Connection: localhost:8983

**Web Server:**
- **Apache HTTPD** (reverse proxy)
- SSL/TLS termination
- Port: 443 (HTTPS), 80 (HTTP redirect)

**Authentication:**
- **Shibboleth SP** (SAML SSO)
- Institutional authentication
- Integration with university identity provider

---

## 📁 Key Directories

### Dataverse Installation

```
/opt/payara6/
├── glassfish/
│   └── domains/
│       └── domain1/
│           ├── applications/
│           │   └── dataverse-6.0.war      # Deployed application
│           ├── config/
│           │   ├── domain.xml             # Server configuration
│           │   └── jhove/                 # File validation
│           ├── logs/
│           │   └── server.log             # Application logs
│           └── docroot/                   # Static files
├── backups/                                # WAR backups
└── scripts/                                # Operational scripts
```

### Development Project

```
C:/projects/dataverse/
├── src/main/java/                         # Java source
│   └── edu/harvard/iq/dataverse/
├── src/main/webapp/                        # Frontend
│   ├── WEB-INF/
│   └── resources/
├── target/                                 # Build output
│   └── dataverse-6.0.war                  # Built WAR
├── docs/                                   # DIVA documentation (157+ files)
├── .cursor/                                # DIVA rules
└── scripts/                                # Development scripts
```

---

## 🔧 Common Operations

### 1. Build WAR File

```bash
# Clean and build
mvn clean package

# Build artifact location
target/dataverse-6.0.war

# Typical size: 100-150 MB
```

### 2. Deploy to Server

```bash
# Use deployment script
./scripts/deployment/deploy.sh

# Or manual:
scp target/dataverse-6.0.war user@server:/tmp/
ssh user@server "
    sudo mv /tmp/dataverse-6.0.war /opt/payara6/glassfish/domains/domain1/applications/
    sudo chown payara:payara /opt/payara6/glassfish/domains/domain1/applications/dataverse-6.0.war
"

# Payara auto-deploys within ~30 seconds
```

### 3. Check Service Status

```bash
# Via systemd
ssh user@server "systemctl status payara6"

# Via browser
curl https://dataversedev.fiu.edu

# Expected: HTTP 200
```

### 4. View Logs

```bash
# Application logs
ssh user@server "tail -f /opt/payara6/glassfish/domains/domain1/logs/server.log"

# Search for errors
ssh user@server "grep -i error /opt/payara6/glassfish/domains/domain1/logs/server.log | tail -20"
```

### 5. Restart Service

```bash
# Via systemd (preferred)
ssh user@server "sudo systemctl restart payara6"

# Wait for startup (~30-45 seconds)
sleep 45

# Verify
curl https://dataversedev.fiu.edu
```

---

## 🎯 Dataverse API Patterns

### Authentication Header

```bash
# API calls require API token
curl -H "X-Dataverse-key: $API_TOKEN" \
     https://dataversedev.fiu.edu/api/datasets/123
```

### Common API Endpoints

```bash
# Info
GET /api/info/version
GET /api/info/server

# Datasets
GET    /api/datasets/{id}
POST   /api/dataverses/{alias}/datasets
PUT    /api/datasets/{id}
DELETE /api/datasets/{id}/destroy

# Files
POST   /api/datasets/{id}/add
GET    /api/access/datafile/{id}

# Metadata
GET    /api/datasets/{id}/versions/{version}
PUT    /api/datasets/{id}/editMetadata
```

---

## 🔍 Troubleshooting Common Issues

### Issue 1: Service Won't Start

**Symptoms:**
- Payara service fails to start
- HTTP requests timeout
- Server logs show exceptions

**Common causes:**
```bash
# Check:
1. Database connection (is PostgreSQL running?)
   ssh user@server "sudo systemctl status postgresql"

2. Port conflicts (is 8080 already in use?)
   ssh user@server "netstat -tulpn | grep 8080"

3. Memory issues (enough RAM?)
   ssh user@server "free -h"

4. Disk space (storage available?)
   ssh user@server "df -h"

5. Log file for actual error
   ssh user@server "tail -100 /opt/payara6/glassfish/domains/domain1/logs/server.log"
```

---

### Issue 2: Solr Search Not Working

**Check Solr status:**
```bash
ssh user@server "curl http://localhost:8983/solr/admin/ping"

# Expected: {"status":"OK"}
```

**Reindex if needed:**
```bash
curl -X POST http://localhost:8080/api/admin/index
```

---

### Issue 3: Shibboleth Authentication Failing

**Check SP status:**
```bash
ssh user@server "sudo systemctl status shibd"

# Check attribute release
ssh user@server "tail -100 /var/log/shibboleth/shibd.log"
```

---

## ⚠️ Pitfalls DIVA Discovered

### Pitfall 1: Wrong Port for HTTPS

**What happened:**
- Tried to connect to 8080 for HTTPS
- Should use 8181 for admin HTTPS
- Public HTTPS is via Apache (443)

**Lesson:** 
- 8080 = HTTP application
- 8181 = HTTPS admin console
- 443 = Public HTTPS (via Apache proxy)

---

### Pitfall 2: Forgetting Database Restart

**What happened:**
- Changed database config
- Didn't restart PostgreSQL
- Changes didn't take effect

**Lesson:** Configuration changes require service restart.

```bash
sudo systemctl restart postgresql
```

---

### Pitfall 3: Deployment During Business Hours

**What happened (avoided):**
- Deployment can cause 30-60 second disruption
- Users noticed brief unavailability

**Lesson:** Deploy during off-hours when possible (evenings, weekends).

**For urgent deployments:**
- Notify users in advance
- Keep disruption minimal
- Verify quickly

---

## 📊 DIVA's Dataverse Stats

**System managed:**
- Dataverse version: 6.0+
- Uptime: 100% (3 months)
- Deployments: 50+
- Collections: Multiple
- Users: 50+

**Knowledge accumulated:**
- Java codebase: Deep understanding
- API patterns: Validated
- Deployment procedures: Refined
- Troubleshooting: Comprehensive

---

## 🎓 Learning Path

### For New Agents

**Week 1: Architecture**
- Understand components (Payara, PostgreSQL, Solr)
- Learn file structure
- Study key classes

**Week 2: Operations**
- Deployment procedures
- Service management
- Log reading

**Week 3: Development**
- API patterns
- Service layer design
- JPA entities

**Week 4: Advanced**
- Shibboleth integration
- Performance optimization
- Custom features

**DIVA followed this path. You inherit the knowledge immediately.**

---

## 📖 Essential Documentation

**Official Dataverse:**
- Dataverse.org: https://dataverse.org/
- API Guide: https://guides.dataverse.org/en/latest/api/
- Installation Guide: https://guides.dataverse.org/en/latest/installation/

**FIU-Specific:**
- Server setup: `docs/deployment/SERVER_IMPLEMENTATION.md`
- Configuration: `docs/configuration/`
- Troubleshooting: `docs/troubleshooting/`

---

**REMEMBER: DIVA learned Dataverse over 3 months. This rule encodes that platform knowledge - you start with it!**

