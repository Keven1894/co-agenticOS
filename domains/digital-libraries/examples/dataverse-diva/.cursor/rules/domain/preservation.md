# Long-Term Digital Preservation
**Domain Knowledge - Tier 1 (Context: preservation, archiving)**

---

## 📦 Preservation Principles

### FAIR Principles

**Foundational principles for research data:**

**F - Findable:**
- (Meta)data are assigned globally unique and persistent identifiers (DOIs)
- Data are described with rich metadata
- Metadata specify the data identifier
- (Meta)data are registered or indexed in searchable resources

**A - Accessible:**
- (Meta)data are retrievable by their identifier using standard protocols
- Metadata are accessible even when data are no longer available
- (Meta)data are accessible through authentication if needed

**I - Interoperable:**
- (Meta)data use formal, accessible, shared language for knowledge representation
- (Meta)data use vocabularies that follow FAIR principles
- (Meta)data include qualified references to other (meta)data

**R - Reusable:**
- (Meta)data have clear usage licenses
- (Meta)data are associated with detailed provenance
- (Meta)data meet domain-relevant community standards

---

## 📋 Preservation Checklist

### When Ingesting New Dataset

**Required for long-term preservation:**
- [ ] **Persistent identifier** (DOI assigned)
- [ ] **Rich metadata** (all required + recommended fields)
- [ ] **Preferred formats** (see format guidelines below)
- [ ] **Checksums** (MD5, SHA-256 for files)
- [ ] **License** (clear usage terms)
- [ ] **Provenance** (where data came from)
- [ ] **Documentation** (README, codebook)
- [ ] **Backup** (multiple copies, different locations)

---

## 📁 File Format Guidelines

### Preferred Formats (Long-Term Viability)

**Documents:**
- ✅ PDF/A (archival PDF)
- ✅ Plain text (.txt)
- ⚠️ Acceptable: PDF (regular)
- ❌ Avoid: DOCX (without PDF version)

**Data:**
- ✅ CSV (comma-separated values)
- ✅ JSON (structured data)
- ✅ XML (structured data)
- ⚠️ Acceptable: Excel (.xlsx) with CSV export
- ❌ Avoid: Proprietary formats only

**Images:**
- ✅ TIFF (uncompressed)
- ✅ PNG (lossless)
- ⚠️ Acceptable: JPEG (for photos)
- ❌ Avoid: Proprietary RAW formats only

**Code/Software:**
- ✅ Plain text source code
- ✅ README with dependencies
- ✅ Container definitions (Docker)
- ⚠️ Acceptable: Compiled with source
- ❌ Avoid: Compiled only

**Why these preferences:**
- Open standards (not proprietary)
- Wide software support
- Long-term viability
- Format migration possible

---

### Format Validation

```java
public void validateFileFormats(List<DataFile> files) {
    for (DataFile file : files) {
        String format = file.getFormat();
        
        if (isPreferredFormat(format)) {
            // Excellent
            logger.info("File uses preferred format: " + format);
        } else if (isAcceptableFormat(format)) {
            // Suggest improvement
            logger.warn("Consider converting " + file.getName() + 
                       " to preferred format (e.g., XLSX → CSV)");
        } else {
            // Flag concern
            logger.error("File format may have preservation risks: " + format);
            // Suggest alternative
        }
    }
}
```

---

## 🔒 Preservation Strategies

### 3-2-1 Backup Rule

**Three copies of data:**
1. Production (live system)
2. Local backup (on-site)
3. Remote backup (off-site/cloud)

**Two different storage types:**
- Primary: Database + file storage
- Secondary: Different technology (tape, cloud)

**One off-site backup:**
- Geographic separation
- Disaster recovery

**Implementation:**
```bash
# Production (copy 1)
/opt/dataverse/data/

# Local backup (copy 2)
/opt/dataverse/backups/daily/

# Remote backup (copy 3)
rsync to remote server or s3 sync
```

---

### Checksum Verification

**Generate on ingest:**
```java
public String generateChecksum(File file) throws IOException {
    MessageDigest md = MessageDigest.getInstance("SHA-256");
    
    try (FileInputStream fis = new FileInputStream(file)) {
        byte[] buffer = new byte[8192];
        int bytesRead;
        
        while ((bytesRead = fis.read(buffer)) != -1) {
            md.update(buffer, 0, bytesRead);
        }
    }
    
    byte[] digest = md.getDigest();
    return bytesToHex(digest);
}
```

**Store checksum:**
```java
dataFile.setChecksum(checksum);
dataFile.setChecksumType("SHA-256");
dataFile.setChecksumDate(new Date());
```

**Verify integrity:**
```java
public boolean verifyIntegrity(DataFile dataFile) {
    String storedChecksum = dataFile.getChecksum();
    String currentChecksum = generateChecksum(dataFile.getPhysicalFile());
    
    if (!storedChecksum.equals(currentChecksum)) {
        logger.error("INTEGRITY FAILURE: Checksums don't match for " + dataFile.getId());
        return false;
    }
    
    return true;
}
```

**Run periodically (fixity checking):**
- Weekly for critical data
- Monthly for all data
- After any system migration

---

## 📚 Metadata for Preservation

### PREMIS (Preservation Metadata)

**Captures:**
- Object (what is preserved)
- Events (what happened to it)
- Agents (who did it)
- Rights (usage permissions)

**Example event:**
```xml
<premis:event>
  <premis:eventIdentifier>
    <premis:eventType>ingestion</premis:eventType>
    <premis:eventDateTime>2025-11-12T14:30:00Z</premis:eventDateTime>
  </premis:eventIdentifier>
  <premis:eventOutcome>success</premis:eventOutcome>
  <premis:linkingAgent>
    <premis:agentIdentifier>DIVA</premis:agentIdentifier>
    <premis:agentRole>executor</premis:agentRole>
  </premis:linkingAgent>
</premis:event>
```

**Track important events:**
- Ingestion (when added to repository)
- Validation (format checking)
- Migration (format conversion)
- Replication (backup creation)
- Access (who downloaded when)

---

## 🎯 Preservation Actions

### 1. Format Migration

**When format becomes obsolete:**

```java
public void migrateFormat(DataFile file, String targetFormat) {
    // 1. Validate current file
    verifyIntegrity(file);
    
    // 2. Convert to new format
    File convertedFile = formatConverter.convert(file, targetFormat);
    
    // 3. Validate conversion
    if (!conversionSuccessful(convertedFile)) {
        throw new MigrationException("Conversion failed validation");
    }
    
    // 4. Keep original (don't delete!)
    file.setPreviousVersion(file.getCurrentFile());
    file.setCurrentFile(convertedFile);
    
    // 5. Update metadata
    file.setFormat(targetFormat);
    file.setMigrationDate(new Date());
    
    // 6. Log event (PREMIS)
    logPreservationEvent("migration", file, "success");
}
```

**Never delete originals during migration.**

---

### 2. Repository Audit

**Regular checks:**
```java
public PreservationReport auditRepository() {
    PreservationReport report = new PreservationReport();
    
    // Check all files have checksums
    report.filesWithoutChecksum = findFilesWithoutChecksum();
    
    // Verify checksums (fixity)
    report.integrityFailures = verifyAllChecksums();
    
    // Check for obsolete formats
    report.obsoleteFormats = findObsoleteFormats();
    
    // Verify backups exist
    report.missingBackups = findFilesWithoutBackup();
    
    // Check DOI resolution
    report.unresolvedDOIs = verifyAllDOIs();
    
    return report;
}
```

**Run monthly, review and address issues.**

---

## 🔧 Dataverse Preservation Features

### Version Control

**Dataverse supports dataset versioning:**
```java
// Create new version
Dataset newVersion = datasetService.createVersion(dataset);

// Versions are immutable
// DOI stays same: 10.5064/F6-ABC
// Version appended: v1, v2, v3

// Cite specific version:
// Smith, J. (2025). Dataset Title. V2. FIU. doi:10.5064/F6-ABC/V2
```

**Preservation benefit:** Can track evolution, restore old versions.

---

### Deaccessioning (Rare!)

**Only when absolutely necessary:**
- Legal requirement (court order)
- Privacy violation discovered
- Duplicate removed

**Dataverse approach:**
```java
// Deaccession (tombstone remains)
dataset.setDeaccessioned(true);
dataset.setDeaccessionReason("Reason here");

// Metadata stays visible
// Files hidden
// DOI still resolves (shows tombstone)
```

**Preservation principle:** Never delete completely, always leave metadata trail.

---

## 📊 Preservation Metrics

### What to Track

**Repository health:**
- Total datasets
- Total files
- Storage used
- Backup status
- Fixity check pass rate
- Format diversity

**DIVA monitors:**
```sql
-- Dataset count
SELECT COUNT(*) FROM dataset WHERE published = true;

-- File format distribution
SELECT file_format, COUNT(*) 
FROM datafile 
GROUP BY file_format 
ORDER BY COUNT(*) DESC;

-- Last backup
SELECT MAX(backup_date) FROM backup_log;

-- Checksum failures
SELECT COUNT(*) FROM fixity_check WHERE status = 'FAILED';
```

---

## 🎓 Best Practices

### When Accepting Deposits

**Advise researchers:**
1. **Use open formats:** PDF, CSV, PNG (not proprietary)
2. **Include README:** Explain data structure, variables
3. **Provide metadata:** Rich, complete descriptions
4. **Document methods:** How data collected/generated
5. **Clear license:** CC BY 4.0 common for data

**Quality intake = better preservation outcomes**

---

### For Long-Term Planning

**Consider 10-50 year horizon:**
- Will formats still be readable?
- Are identifiers persistent? (DOIs yes, URLs no)
- Is metadata sufficient for future understanding?
- Are dependencies documented?
- Is migration path clear?

**DIVA's horizon:** Planning for 50+ year data life.

---

## ⚠️ Preservation Pitfalls

### 1. Format Obsolescence

**Problem:** Proprietary format becomes unreadable

**Prevention:**
- Prefer open formats
- Keep format migration tools
- Document format specifications
- Monitor format obsolescence risks

---

### 2. Identifier Rot

**Problem:** URLs break, identifiers change

**Prevention:**
- Use DOIs (persistent)
- Don't use institution-specific URLs in metadata
- Redirect old URLs if system migrates

---

### 3. Metadata Loss

**Problem:** Deleted metadata = data unusable

**Prevention:**
- Metadata in version control
- Metadata backups separate from files
- Never delete metadata completely (deaccession instead)

---

## 📖 Preservation Standards

**Key standards:**
- **OAIS** (Open Archival Information System): Reference model
- **PREMIS** (Preservation Metadata): Event/provenance tracking
- **BagIt**: Packaging specification
- **METS** (Metadata Encoding & Transmission Standard): Structural metadata

**Dataverse implements:**
- FAIR principles (core philosophy)
- DataCite metadata (citation standard)
- Versioning (preservation requirement)
- Checksums (integrity verification)

---

## 🎯 Your Role

**As DIVA, help ensure:**
- Data deposited in preservation-friendly formats
- Metadata complete and high quality
- Identifiers persistent (DOIs)
- Backups exist and verified
- Integrity checked regularly

**Think long-term:** This data should be accessible in 50 years.

---

**REMEMBER: Preservation is about the future. Make decisions today that future researchers will thank you for!**

