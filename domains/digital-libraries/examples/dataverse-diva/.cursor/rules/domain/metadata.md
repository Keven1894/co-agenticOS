# Metadata Standards for Digital Libraries
**Domain Knowledge - Tier 1 (Context: metadata work)**

---

## 📚 Metadata Standards Overview

### Why Metadata Matters

**In digital libraries:**
- Metadata makes data findable
- Standards enable interoperability
- Quality metadata = data reusability
- Compliance requirement (funders, institutions)

---

## 🎯 Primary Standards

### 1. DataCite Metadata Schema

**Used for:** DOI registration, citation metadata

**Required fields:**
```xml
<resource>
  <identifier identifierType="DOI">10.5064/F6-EXAMPLE</identifier>
  <creators>
    <creator>
      <creatorName nameType="Personal">Smith, John</creatorName>
      <nameIdentifier schemeURI="https://orcid.org/" 
                      nameIdentifierScheme="ORCID">
        0000-0002-1825-0097
      </nameIdentifier>
    </creator>
  </creators>
  <titles>
    <title>Research Data from Study X</title>
  </titles>
  <publisher>Florida International University</publisher>
  <publicationYear>2025</publicationYear>
  <resourceType resourceTypeGeneral="Dataset">Research Data</resourceType>
</resource>
```

**Critical elements:**
- **Identifier**: DOI (10.xxxxx/yyyyy)
- **Creators**: Authors with ORCID if available
- **Title**: Clear, descriptive
- **Publisher**: Institution
- **PublicationYear**: YYYY format
- **ResourceType**: Dataset, Software, etc.

**Validation:**
```java
public void validateDataCiteMetadata(Metadata metadata) {
    String[] required = {"identifier", "creator", "title", 
                        "publisher", "publicationYear", "resourceType"};
    
    for (String field : required) {
        if (!metadata.hasField(field)) {
            throw new ValidationException("Missing required field: " + field);
        }
    }
    
    // Validate ORCID format if present
    if (metadata.hasORCID()) {
        validateORCID(metadata.getORCID());
    }
}
```

---

### 2. Dublin Core

**Used for:** General metadata, OAI-PMH harvesting

**15 core elements:**
1. dc.title
2. dc.creator
3. dc.subject
4. dc.description
5. dc.publisher
6. dc.contributor
7. dc.date
8. dc.type
9. dc.format
10. dc.identifier
11. dc.source
12. dc.language
13. dc.relation
14. dc.coverage
15. dc.rights

**Example:**
```xml
<dc:title>Ocean Temperature Data 2024</dc:title>
<dc:creator>Smith, John</dc:creator>
<dc:subject>Oceanography</dc:subject>
<dc:description>Monthly ocean temperature readings from...</dc:description>
<dc:publisher>FIU Libraries</dc:publisher>
<dc:date>2024-12-01</dc:date>
<dc:type>Dataset</dc:type>
<dc:format>CSV</dc:format>
<dc:identifier>https://doi.org/10.5064/F6-EXAMPLE</dc:identifier>
<dc:language>en</dc:language>
<dc:rights>CC BY 4.0</dc:rights>
```

---

### 3. ORCID Identifiers

**Purpose:** Persistent identifier for researchers

**Format:** 0000-0002-1825-0097 (16 digits with dashes)

**Structure:**
- 4 groups of 4 digits
- Last digit is checksum
- Must resolve at https://orcid.org/

**Validation:**
```javascript
function validateORCID(orcid) {
    // Format: 0000-0002-1825-0097
    const orcidPattern = /^\d{4}-\d{4}-\d{4}-\d{3}[0-9X]$/;
    
    if (!orcidPattern.test(orcid)) {
        throw new Error('Invalid ORCID format');
    }
    
    // Verify checksum (last digit)
    const checksum = calculateORCIDChecksum(orcid);
    if (checksum !== orcid.slice(-1)) {
        throw new Error('Invalid ORCID checksum');
    }
    
    // Verify resolvable
    const url = `https://orcid.org/${orcid}`;
    // Check if URL resolves...
}
```

**Common mistakes:**
- Missing dashes
- Wrong number of digits
- Invalid checksum
- Fake/non-existent ORCID

---

### 4. DOI (Digital Object Identifier)

**Purpose:** Persistent identifier for research outputs

**Format:** 10.5064/F6-EXAMPLE
- Prefix: 10.5064 (assigned to institution)
- Suffix: F6-EXAMPLE (locally assigned)

**Registration:**
```java
// Dataverse auto-generates DOI on publication
dataset.setIdentifier("doi:10.5064/F6-" + generateUniqueSuffix());

// Register with DataCite
dataCiteService.registerDOI(dataset.getIdentifier(), metadata);
```

**Validation:**
```javascript
function validateDOI(doi) {
    // Format: 10.xxxxx/yyyyy
    const doiPattern = /^10\.\d{4,}\/[-._;()/:A-Za-z0-9]+$/;
    
    if (!doiPattern.test(doi)) {
        throw new Error('Invalid DOI format');
    }
    
    // Check if resolves
    const url = `https://doi.org/${doi}`;
    // Verify HTTP 200...
}
```

---

## 🔧 Metadata Workflows

### Creating Dataset Metadata

```java
public DatasetMetadata createMetadata() {
    DatasetMetadata metadata = new DatasetMetadata();
    
    // Required fields
    metadata.setTitle("Clear, descriptive title");
    metadata.setAuthor("Smith, John", "0000-0002-1825-0097"); // Name + ORCID
    metadata.setDescription("Complete description of research data...");
    metadata.setSubject("Oceanography"); // From controlled vocabulary
    metadata.setPublisher("Florida International University");
    metadata.setProductionDate("2024");
    
    // Optional but recommended
    metadata.setKeyword("ocean", "temperature", "climate");
    metadata.setGeographicCoverage("Miami, FL, USA");
    metadata.setTimePeriod("2024-01-01", "2024-12-31");
    metadata.setLanguage("en");
    metadata.setRights("CC BY 4.0");
    
    // Validate
    validateMetadata(metadata);
    
    return metadata;
}
```

---

### Metadata Validation

```java
public void validateMetadata(DatasetMetadata metadata) {
    // Required fields
    if (metadata.getTitle() == null || metadata.getTitle().trim().isEmpty()) {
        throw new ValidationException("Title is required");
    }
    
    if (metadata.getAuthors().isEmpty()) {
        throw new ValidationException("At least one author required");
    }
    
    // ORCID validation
    for (Author author : metadata.getAuthors()) {
        if (author.hasORCID()) {
            validateORCID(author.getORCID());
        }
    }
    
    // Title length
    if (metadata.getTitle().length() > 255) {
        throw new ValidationException("Title too long (max 255 characters)");
    }
    
    // Date format
    if (metadata.getProductionDate() != null) {
        validateDateFormat(metadata.getProductionDate()); // YYYY or YYYY-MM-DD
    }
}
```

---

## 📖 Controlled Vocabularies

### Subject Terms

**Use controlled vocabularies when available:**

**NASA GCMD Science Keywords:**
- EARTH SCIENCE > OCEANS > OCEAN TEMPERATURE

**Library of Congress Subject Headings (LCSH):**
- Oceanography--Florida

**DDC (Dewey Decimal Classification):**
- 551.46 (Oceanography)

**In Dataverse:**
```java
// Use controlled vocabulary
metadata.setSubject("Oceanography");  // From CVoc Subjects

// Or custom
metadata.setKeyword("ocean temperature", "climate data");
```

---

### Resource Types

**DataCite Resource Types:**
- Dataset (most common for Dataverse)
- Software
- Text
- Image
- Collection

**In Dataverse:**
```java
metadata.setResourceType("Dataset");  // Match DataCite general type
metadata.setResourceSubType("Observational Data");  // Specific type
```

---

## 🌍 Metadata Crosswalks

### Mapping Between Standards

**DataCite → Dublin Core:**
```
datacite:creator      → dc:creator
datacite:title        → dc:title
datacite:publisher    → dc:publisher
datacite:date         → dc:date
datacite:resourceType → dc:type
datacite:description  → dc:description
```

**Implementation:**
```java
public DublinCoreMetadata convertToDublinCore(DataCiteMetadata datacite) {
    DublinCoreMetadata dc = new DublinCoreMetadata();
    
    dc.setTitle(datacite.getTitle());
    dc.setCreator(datacite.getCreators());
    dc.setPublisher(datacite.getPublisher());
    dc.setDate(datacite.getPublicationYear());
    dc.setType(datacite.getResourceType());
    dc.setDescription(datacite.getDescription());
    // ... more mappings
    
    return dc;
}
```

---

## 🎯 Metadata Quality

### Quality Indicators

**Minimal (acceptable):**
- Required fields present
- Identifiers valid
- Names formatted correctly

**Good:**
- + Controlled vocabularies used
- + ORCIDs for authors
- + Rich description
- + Keywords provided

**Excellent:**
- + All optional fields populated
- + Relationships documented
- + Funding information
- + Geographic/temporal coverage

**DIVA's role:** Suggest quality improvements, not just validate minimum.

---

## 🔍 Metadata Queries

### Common Questions

**For datasets:**
```sql
-- Find by title
SELECT * FROM dataset WHERE title LIKE '%ocean%';

-- Find by author ORCID
SELECT d.* FROM dataset d
JOIN author a ON d.id = a.dataset_id
WHERE a.orcid = '0000-0002-1825-0097';

-- Find by subject
SELECT d.* FROM dataset d
JOIN subject s ON d.id = s.dataset_id
WHERE s.value = 'Oceanography';
```

---

## 📊 DIVA's Metadata Work

**Metadata handled:**
- Datasets: 50+ curated
- Authors: 100+ with ORCID resolution
- Subjects: Validated against controlled vocabularies
- DOIs: All valid and resolvable

**Quality improvements suggested:**
- Missing ORCID: 15 suggestions
- Better subjects: 20 improvements
- Description quality: 10 enhancements

---

## 📖 Further Reading

**Dataverse Metadata:**
- https://guides.dataverse.org/en/latest/user/dataset-management.html

**DataCite Schema:**
- https://schema.datacite.org/

**ORCID:**
- https://orcid.org/

**Dublin Core:**
- https://www.dublincore.org/specifications/dublin-core/

---

**REMEMBER: Metadata is what makes research data FAIR (Findable, Accessible, Interoperable, Reusable). Quality metadata = quality repository!**

