# Implementing FAIR Principles in Your Project

A guide to making your student project adhere to FAIR (Findable, Accessible, Interoperable, Reusable) data principles.

## FAIR Principles Overview

FAIR principles ensure research data is:
- **Findable** — Easy to locate
- **Accessible** — Available to users
- **Interoperable** — Works with different tools
- **Reusable** — Well-documented for future use

## Practical Implementation Checklist

### F - Findable

#### Your Project is Findable When:

**GitHub Repository**
- [ ] Project folder created with descriptive name
- [ ] Project URL is permanent and shareable
- [ ] GitHub repository is public
- [ ] Repository has clear description

**Metadata**
- [ ] README.md includes descriptive title
- [ ] Keywords listed in README
- [ ] Subject/discipline identified
- [ ] Data types specified

**Documentation**
- [ ] Clear project overview provided
- [ ] File listing with descriptions
- [ ] Data structure explained
- [ ] Access instructions clear

**Searchability**
- [ ] Project title appears in GitHub search
- [ ] Keywords appear in README
- [ ] Topic tags added to repository
- [ ] Related resources linked

#### How to Make Your Project Findable

**1. Add Repository Metadata**

In GitHub:
1. Go to repository Settings
2. Add Description (50 characters)
3. Add Topics (relevant tags)
4. Enable Discussions (if desired)

**2. Create Descriptive README**

```markdown
# Project Title: Ancient Coins Sample

A dataset of ancient coins demonstrating tidy data principles in numismatic research.

**Keywords:** numismatics, ancient coins, CSV, tidy data, humanities data modeling
```

**3. Document Files Clearly**

```
Project Contents:
- ancient_coins_sample.csv — Main data file (150 records)
- README.md — This documentation
- LICENSE.txt — CC-BY-4.0 license
```

**4. Use Consistent Naming**

- Good: `ancient_coins_sample.csv`
- Bad: `data.csv`

### A - Accessible

#### Your Project is Accessible When:

**Open Formats**
- [ ] No proprietary formats (.xlsx, .docx)
- [ ] Using open standards (CSV, XML, JSON)
- [ ] Encoding specified (UTF-8)
- [ ] No special software required

**Open License**
- [ ] CC-BY-4.0 license included
- [ ] License terms clear
- [ ] Attribution requirements stated
- [ ] Derivative works permitted

**No Technical Barriers**
- [ ] Files downloadable without login
- [ ] Data available offline
- [ ] No paywalls or restrictions
- [ ] Free tools can access data

**Machine Readability**
- [ ] Data in structured format
- [ ] Column headers descriptive
- [ ] Encoding specified
- [ ] Data types clear

#### How to Make Your Project Accessible

**1. Use Open Formats**

**Instead of:**
```
ancient_coins.xlsx (Excel)
inscriptions.docx (Word)
```

**Use:**
```
ancient_coins.csv (CSV)
inscriptions.xml (XML)
```

**2. Include CC-BY-4.0 License**

Create `LICENSE.txt`:
```
This work is licensed under the Creative Commons Attribution 4.0 
International License. To view a copy, visit 
http://creativecommons.org/licenses/by/4.0/

You are free to:
- Share — copy and redistribute
- Adapt — remix and create derivatives

You must:
- Attribute the work to the original creator
```

**3. Provide Download Options**

In README:
```markdown
## Access

Download this dataset:

1. **Individual files:** Click "Download" next to each file
2. **Entire project:** Click "Code" → "Download ZIP"
3. **Git clone:** `git clone https://github.com/.../StudentName/`

All formats: Open (no login required)
All tools: Works with spreadsheets, databases, programming languages
```

**4. Ensure UTF-8 Encoding**

When exporting CSV from Excel:
1. File → Export As → Change file type to CSV
2. Look for encoding option
3. Select UTF-8
4. Save

### I - Interoperable

#### Your Project is Interoperable When:

**Standard Formats**
- [ ] Uses established standards (CSV, XML, JSON)
- [ ] Compatible with common tools
- [ ] Can be converted to other formats
- [ ] Follows format specifications

**Standard Metadata**
- [ ] Dublin Core elements included
- [ ] FAIR citation information provided
- [ ] Controlled vocabularies used
- [ ] Data structure documented

**Standard Data Representation**
- [ ] Dates: ISO 8601 (YYYY-MM-DD)
- [ ] Coordinates: WGS84 (lat/lon decimal)
- [ ] Encoding: UTF-8 (text)
- [ ] Numbers: No currency symbols

**Related Data**
- [ ] Foreign key relationships clear
- [ ] References documented
- [ ] Cross-references working
- [ ] Linked data explained

#### How to Make Your Project Interoperable

**1. Follow Data Standards**

**Dates:**
```
Bad:  03/15/2026, March 15, 2026, 15.03.2026
Good: 2026-03-15
```

**Coordinates (for geographic data):**
```
Bad:  44°33'N 28°44'E, N44 E28
Good: 44.5500, 28.7333 (WGS84)
```

**Numbers:**
```
Bad:  1,000.50 (if it's supposed to be numeric)
Good: 1000.50
```

**2. Use Standard Metadata**

Include in README:
```markdown
## Metadata

- **Creator:** [Student Name]
- **Created:** 2026
- **Subject:** Numismatics, ancient coins
- **Format:** CSV (UTF-8)
- **Records:** 150
- **Coverage:** Coins from 500 BCE to 50 CE
- **Rights:** CC-BY-4.0
```

**3. Document Data Conversions**

In README, show how to convert:

```markdown
## Format Conversion

Convert CSV to JSON:
    
import pandas as pd
df = pd.read_csv('data.csv')
df.to_json('data.json', orient='records', indent=2)
```

**4. Provide Data Dictionary**

| Field | Description | Type | Standard Format |
|-------|-------------|------|-----------------|
| ID | Unique identifier | Text | COIN_### |
| Date | Dating of coin | Date | YYYY-MM-DD |
| Mint | Place of minting | Text | City name (English) |
| Material | Metal composition | Text | See controlled list below |

**Controlled Vocabulary:**
- Material: Silver, Gold, Bronze, Copper
- Region: Attica, Boeotia, Ionia, ...

### R - Reusable

#### Your Project is Reusable When:

**Documentation**
- [ ] Comprehensive README
- [ ] Data dictionary provided
- [ ] Methodology documented
- [ ] Limitations acknowledged

**Context**
- [ ] Data collection explained
- [ ] Assumptions documented
- [ ] Uncertainty indicated
- [ ] Transformations recorded

**License & Attribution**
- [ ] License clearly stated
- [ ] Attribution requirements explicit
- [ ] Citation format provided
- [ ] Multiple format examples

**Quality Information**
- [ ] Data accuracy described
- [ ] Completeness noted
- [ ] Known issues listed
- [ ] Validation procedures explained

#### How to Make Your Project Reusable

**1. Write Comprehensive Documentation**

In README, include:

```markdown
## Collection and Methodology

### Data Sources
Coins catalogued from: [Museum names, publications]

### Collection Process
- Records extracted from museum databases
- Verified against published catalogs
- Cross-referenced for consistency

### Time Period
Coins dated 500-50 BCE (approximately ±25 years)

### Geographic Scope
Ancient Mediterranean regions: Greece, Asia Minor, Egypt

### Transformations
- Standardized material names
- Converted dates to ISO format
- Corrected spelling inconsistencies
```

**2. Document Limitations**

```markdown
## Data Limitations

- Dates are approximate (±25-50 years uncertainty)
- Not all coins from all mints represented
- Incomplete inscription records for 15% of coins
- Primarily Greek and Roman coins (limited Near Eastern coverage)
- Museum identifications follow specific scholarly conventions

## What This Data Does NOT Show

- Complete inventory of all ancient coins
- Archaeological contexts of discoveries
- Wear patterns or physical condition (except basic grade)
- Detailed paleographic analysis
```

**3. Provide Multiple Citation Formats**

```markdown
## How to Cite

### APA Format
Andrea. (2026). Ancient coins sample. Foundations of Humanities Data 
Modeling and Formats Course, [Institution]. 
https://github.com/Bestroi150/student-projects-showcase

### BibTeX Format
@dataset{andrea_coins_2026,
  title={Ancient Coins Sample},
  author={Andrea},
  year={2026},
  url={https://github.com/Bestroi150/student-projects-showcase}
}

### In-text
(Andrea, 2026)
```

**4. Include Quality Information**

```markdown
## Data Quality

- **Completeness:** 98.2% of records have all expected fields
- **Accuracy:** Spot-checked 20 records against original sources
- **Consistency:** All categorical values verified against controlled vocabulary
- **Encoding:** UTF-8 (supports special characters)
- **Validation:** Automated format checks performed

### Known Issues
- 3 records have uncertain material identification
- 2 records missing mint information
- Dates for 5 records approximated (±50 years)
```

## FAIR Self-Assessment

### Minimal FAIR (Score: 5/10)
- ✓ GitHub repository
- ✓ CC-BY-4.0 license
- ✓ README present
- ~ Some documentation
- ~ Open formats (partially)

**Improvements needed:** Better documentation, consistent formats

### Good FAIR (Score: 8/10)
- ✓ Public GitHub repository with clear description
- ✓ CC-BY-4.0 license with attribution guidelines
- ✓ Comprehensive README with all sections
- ✓ Data dictionary included
- ✓ Open formats (CSV, XML, JSON)
- ✓ UTF-8 encoding
- ✓ Citation instructions provided
- ~ Conversion examples provided
- ~ Some metadata

**Improvements needed:** More conversion examples, fuller metadata

### Excellent FAIR (Score: 10/10)
- ✓ Well-organized GitHub repository
- ✓ Persistent identifier (DOI via Zenodo)
- ✓ Comprehensive metadata
- ✓ Multiple format representations
- ✓ Complete documentation
- ✓ Data quality assessment
- ✓ Conversion tools provided
- ✓ Linked to related resources
- ✓ Automated validation available
- ✓ Example analyses provided

## Implementation Steps

### Week 1: Setup
- [ ] Create project folder
- [ ] Choose data format (CSV, XML, JSON)
- [ ] Prepare data files
- [ ] Draft README outline

### Week 2: Documentation
- [ ] Write README sections
- [ ] Create data dictionary
- [ ] Document methodology
- [ ] List limitations

### Week 3: Formatting & Encoding
- [ ] Verify UTF-8 encoding
- [ ] Check file naming
- [ ] Validate data structure
- [ ] Test in multiple tools

### Week 4: Quality & Licensing
- [ ] Spot-check data accuracy
- [ ] Add LICENSE.txt
- [ ] Add citation information
- [ ] Create CITATION.cff (optional)

### Week 5: Review & Polish
- [ ] Self-assess FAIR compliance
- [ ] Get peer feedback
- [ ] Make final revisions
- [ ] Submit for review

## FAIR vs. Other Standards

| Aspect | FAIR | OPEN | Archival | Research |
|--------|------|------|----------|----------|
| Discoverable | ✓✓ | ✓ | ✓✓ | ✓ |
| Accessible | ✓✓ | ✓✓ | ~ | ✓ |
| Standard Format | ✓✓ | ~ | ~ | ✓ |
| Documented | ✓ | ~ | ✓✓ | ✓ |
| Licensed | ~ | ✓✓ | ✓ | ~ |

## Common FAIR Implementation Mistakes

❌ **Not Findable**
- Vague project names
- No README
- Missing keywords
- Poor documentation

❌ **Not Accessible**
- Proprietary formats (Excel, Word)
- Behind paywalls
- Unclear license
- Login required

❌ **Not Interoperable**
- Inconsistent date formats
- Mixed data types in columns
- Non-standard encoding
- Poor metadata

❌ **Not Reusable**
- Sparse documentation
- Unexplained data
- No methodology
- Missing limitations

## Tools That Help with FAIR

- **GitHub:** Hosting and discovery
- **Zenodo:** DOI assignment (persistent ID)
- **FAIR Data Checklist Tools:** Online assessment
- **CSV Validator:** Format checking
- **XML Validator:** Structure verification

## Templates and Examples

### README Template
Use the template provided in the main repository repository and customize for your project.

### Data Dictionary Template
```
| Field | Description | Type | Example | Notes |
|-------|-------------|------|---------|-------|
| [name] | [what it is] | [type] | [example] | [special info] |
```

### CITATION.cff Template
```yaml
cff-version: 1.2.0
title: Project Title
authors:
  - family-names: StudentName
    given-names: First
creators:
  - family-names: StudentName
    given-names: First
date-released: 2026-01-01
license: CC-BY-4.0
repository: https://github.com/...
```

## Assessment Rubric

Your project will be evaluated on FAIR implementation:

| Criterion | Excellent | Good | Fair | Poor |
|-----------|-----------|------|------|------|
| Findable | Clear metadata, discoverable | Documented, searchable | Basic info present | Hard to find |
| Accessible | Open format, no barriers | Open format, licensed | Mostly accessible | Barriers present |
| Interoperable | Standard formats, convertible | Standard formats | Some standards | Non-standard |
| Reusable | Fully documented | Well documented | Some documentation | Sparse docs |

## Getting Help

- Review this guide
- Check [documentation/fair-principles.md](../documentation/fair-principles.md)
- See [project-requirements.md](project-requirements.md)
- Examine example projects
- Ask instructor
- Post to course forum

---

**Last Updated:** 2026

**Remember:** FAIR principles make your research more valuable and impactful!
