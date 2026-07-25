# Project Requirements

Standards and guidelines for student projects in this showcase.

## Overview

This document outlines the requirements and best practices for student projects submitted to the Humanities Data Modeling - Student Projects Showcase.

## General Requirements

All student projects must:

✓ Be student work created during the course  
✓ Relate to humanities data modeling concepts  
✓ Include proper documentation  
✓ Use open data formats  
✓ Follow FAIR data principles  
✓ Include appropriate licensing  
✓ Respect privacy and intellectual property  

## Project Structure

### Required Files

Every student project folder must include:

```
StudentName/
├── README.md              # REQUIRED: Project description
├── LICENSE.txt            # REQUIRED: CC-BY-4.0 license
├── [data files]           # REQUIRED: One or more data files
└── [optional files]       # Optional: additional resources
```

### Project Folder Naming

- Use student's first name or full name
- Use PascalCase (capitalize first letter)
- Examples: `Andrea/`, `Ekaterina/`, `Elitsa/`, `Irina/`
- One folder per student project

## Data Files

### Format Requirements

Data files must be in **open formats**:

**Acceptable:**
- CSV (comma-separated values)
- XML (eXtensible Markup Language)
- JSON (JavaScript Object Notation)
- GeoJSON (for geographic data)
- TSV (tab-separated values)
- Plain text with clear structure

**Not Acceptable:**
- Proprietary Excel formats (.xlsx) — use CSV instead
- Closed binary formats
- Formats requiring special software

### File Naming

- Use lowercase letters
- Use hyphens for word separation (not spaces or underscores)
- Be descriptive
- Examples:
  - `ancient_coins_sample.csv` ✓
  - `Ancient Coins Sample.csv` ✗
  - `coins.csv` ✗
  - `data.csv` ✗

### Encoding

- **All text files:** UTF-8 encoding
- Ensures compatibility across platforms
- Supports special characters and diacritics

### File Size

- Individual data files: preferably < 10 MB
- Total project size: < 50 MB
- GitHub free storage: 100 GB per repository

## README.md Requirements

Every project **must** include a comprehensive README.md file.

### Required Sections

1. **Project Title**
   - Clear, descriptive title
   - Student name and course

2. **Overview/Abstract**
   - 2-3 sentences describing the project
   - What data it contains
   - Why it's interesting

3. **Data Description**
   - List of files included
   - What each file contains
   - Data format and structure

4. **Data Fields/Dictionary**
   - Table with field names and descriptions
   - Data types specified
   - Example values

5. **Working with the Data**
   - How to open/view data
   - Examples in common tools
   - Basic analysis examples

6. **Collection and Methodology**
   - Where data came from
   - How it was collected
   - Time period and scope
   - Any transformations applied

7. **Data Limitations**
   - What data cannot show
   - Known gaps or biases
   - Assumptions made
   - Uncertainties acknowledged

8. **FAIR Data Principles**
   - Statement of FAIR implementation
   - Explain how data is Findable, Accessible, Interoperable, Reusable

9. **Citation**
   - How to cite the project
   - Multiple format examples (APA, BibTeX)
   - In-text and full citation forms

10. **Contact Information**
    - Student name/email (optional)
    - How to report issues

11. **License**
    - Statement of CC-BY-4.0 license
    - Link to full license text

### README Quality Standards

✓ Clear and well-organized  
✓ Written in English (translate if needed)  
✓ Appropriate length (typically 2-4 pages when printed)  
✓ Includes all required sections  
✓ Links are functional  
✓ Examples are accurate and tested  

### README Template

A template is provided in the main repository. Use it as a starting point and customize for your project.

## Data Quality Standards

### Completeness

- No unexplained missing data
- Missing values indicated consistently (NULL, NA, blank)
- Ratio of complete records ≥ 95%

### Accuracy

- Data verified against sources
- Dates consistent with historical record
- Geographic coordinates verified
- Categorical values from controlled list

### Consistency

- Formatting consistent throughout
- Column headers uniform
- Text encoding consistent (UTF-8)
- No mixed data types in columns

### Validation Checklist

Before submission, verify:

- [ ] All rows have unique IDs (if applicable)
- [ ] No leading/trailing whitespace
- [ ] Consistent date formatting
- [ ] Consistent capitalization
- [ ] No duplicate records (unless intentional)
- [ ] Numeric columns contain only numbers
- [ ] Text fields use proper encoding
- [ ] Missing values consistently marked

## Metadata Requirements

### Essential Metadata

Every dataset must include:

1. **Title:** Clear, descriptive project title
2. **Creator:** Student name
3. **Date:** Year created/completed
4. **Subject:** Domain and topics (keywords)
5. **Description:** Overview of contents
6. **Source:** Where data came from
7. **License:** CC-BY-4.0

### Metadata Locations

Metadata appears in:
- Project README.md
- Individual data file headers (comments)
- CITATION.cff (if included)
- GitHub repository metadata

### Example Metadata in CSV

```csv
# Ancient Coins Sample Dataset
# Creator: Andrea
# Date: 2026
# Format: CSV (UTF-8)
# Subject: numismatics, ancient coins, tidy data
# Description: Sample of ancient coins with denomination, material, mint, and provenance
# Source: Published museum catalogs
# License: CC-BY-4.0 (https://creativecommons.org/licenses/by/4.0/)

ID,Denomination,Material,Mint,Date,Museum
```

## Documentation Standards

### Data Dictionary

Required table with:
- **Field Name:** Exact column name
- **Description:** What the field represents
- **Type:** Data type (text, number, date, etc.)
- **Example:** Sample value
- **Notes:** Special information (range, allowed values, etc.)

### Example Data Dictionary

| Field | Description | Type | Example | Notes |
|-------|-------------|------|---------|-------|
| ID | Unique identifier | Text | COIN_001 | Format: COIN_### |
| Denomination | Face value | Text | Drachma | From controlled list |
| Material | Metal composition | Text | Silver | Silver, Gold, Bronze, Copper |
| Mint | Issuing location | Text | Athens | Greek city-state names |

### Methodology Documentation

Document:
- Data sources (URLs, publications, databases)
- Collection procedures
- Inclusion/exclusion criteria
- Date range of data
- Geographic scope
- Data transformations performed
- Quality assurance measures

### Limitations Documentation

Acknowledge:
- Data gaps or incompleteness
- Known biases or limitations
- Uncertainty in measurements/dates
- Scope boundaries
- Assumptions made
- What cannot be concluded from data

## Licensing Requirements

### License Requirement

**All student projects must use CC-BY-4.0 license**

This license:
- ✓ Permits sharing and remixing
- ✓ Allows commercial use
- ✓ Requires attribution only
- ✓ Is widely recognized and supported

### License Implementation

Include LICENSE or LICENSE.txt file with:

```
Creative Commons Attribution 4.0 International

This work is licensed under the Creative Commons Attribution 4.0 
International License. To view a copy of this license, visit 
http://creativecommons.org/licenses/by/4.0/

You are free to:
- Share — copy and redistribute the material in any medium or format
- Adapt — remix, transform, and build upon the material for any purpose

Under the following terms:
- Attribution — You must give appropriate credit, provide a link to 
  the license, and indicate if changes were made.
```

## Submission Checklist

Before submitting your project, verify:

### Structure
- [ ] Project folder created with your name
- [ ] All files organized logically
- [ ] Naming conventions followed

### Files
- [ ] Data file(s) in open format (CSV, XML, JSON)
- [ ] README.md with all required sections
- [ ] LICENSE.txt with CC-BY-4.0

### Documentation
- [ ] Data dictionary included
- [ ] Methodology explained
- [ ] Limitations acknowledged
- [ ] Examples provided

### Quality
- [ ] Data validated and accurate
- [ ] UTF-8 encoding verified
- [ ] No proprietary formats
- [ ] Consistent formatting

### Metadata
- [ ] Title clear and descriptive
- [ ] Creator (your name) listed
- [ ] Date included
- [ ] License specified

### Citation
- [ ] Citation instructions provided
- [ ] Multiple format examples included
- [ ] URLs functional

## Review Process

### Submission

1. Create pull request or submit to instructor
2. Include description of project
3. Note any special considerations
4. Reference this guidelines document

### Review

Projects will be evaluated on:
- ✓ Adherence to format requirements
- ✓ Documentation quality
- ✓ Data quality and accuracy
- ✓ Relevance to course material
- ✓ Originality and effort
- ✓ FAIR principles implementation

### Feedback

Students will receive:
- Approval or suggestions for revision
- Constructive feedback on data and documentation
- Guidance for improvement

### Revision

If revisions requested:
1. Address feedback
2. Update files
3. Resubmit for approval

## Common Mistakes to Avoid

❌ **Data Format Issues**
- Submitting Excel files instead of CSV
- Mixing data types in columns
- Inconsistent encoding

❌ **Documentation Issues**
- Missing or incomplete README
- Vague project descriptions
- Missing data dictionary
- No methodology documentation

❌ **Data Quality Issues**
- Unverified or inaccurate data
- Unexplained missing values
- Inconsistent formatting
- Duplicate records not documented

❌ **Licensing Issues**
- No license file included
- Unclear attribution
- Proprietary license instead of CC-BY-4.0

❌ **File Management Issues**
- Poor file naming
- Large binary files
- Disorganized folder structure
- Too many temporary files

## Excellent Examples

Reference these projects as models:

- **Andrea:** Ancient Coins Sample
  - Well-structured CSV
  - Comprehensive data dictionary
  - Clear methodology

- **Ekaterina:** Ancient Inscriptions (XML)
  - Proper TEI markup
  - Complete metadata
  - Good documentation

- **Elitsa:** Multi-Sheet Dataset
  - Related datasets properly linked
  - Foreign key relationships clear
  - Referential integrity verified

- **Irina:** Greek Colonization (GeoJSON)
  - Geographic data well-documented
  - Coordinates properly formatted
  - Historical context included

## Special Cases

### Large Datasets

If your dataset exceeds 10 MB:
- Discuss with instructor first
- Consider sampled version for showcase
- Full dataset available separately
- Document the relationship

### Sensitive Data

If your data includes sensitive information:
- Anonymize personal information
- Get appropriate permissions
- Document any redactions
- Ensure privacy compliance

### Collaborative Projects

If working with multiple students:
- Create one project folder per student
- Include all contributors in README
- Reference collaborators' work
- Clarify individual contributions

### Multiple Data Files

If submitting multiple related files:
- Document relationships clearly
- Explain how files connect
- Provide examples of joining
- Include metadata for each file

## Getting Help

**Questions about requirements?**

1. Review this document
2. Check example projects
3. Ask instructor
4. Post to course forum
5. Email course contact

**Technical help?**

- See documentation folder
- Check data-formats.md guide
- Review example projects
- Consult tools' documentation

## Resources

- See [documentation/resources.md](../documentation/resources.md) for learning materials
- See [documentation/data-formats.md](../documentation/data-formats.md) for format help
- See [documentation/fair-principles.md](../documentation/fair-principles.md) for FAIR guidance
- See [documentation/citation-guide.md](../documentation/citation-guide.md) for citation help

---

**Last Updated:** 2026

**Questions?** Contact the course instructor or open an issue on GitHub.
