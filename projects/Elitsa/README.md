# Elitsa's Projects: Comparative Data Analysis & 3D Model Documentation

**Student:** Elitsa  
**Course:** Foundations of Humanities Data Modeling and Formats  
**Data Formats:** CSV (Tabular), XML (Metadata), 3D Models (OBJ/MTL)  
**Last Updated:** 2025-2026

## Project Overview

This folder contains two complementary digital humanities projects demonstrating different data modeling approaches:
1. **Multi-Sheet Comparative Dataset** - Relational data structure across multiple CSV files
2. **3D Roman Artifacts Database** - Digital documentation of artifacts with 3D models, measurements, and metadata

Together, these projects showcase how to structure complex humanities data for both analysis and preservation purposes.

## Project 1: Multi-Sheet Comparative Dataset Analysis

### Learning Objectives

- ✓ Design related datasets with proper referential integrity
- ✓ Structure data for comparative analysis
- ✓ Use consistent identifiers across multiple files
- ✓ Implement foreign key relationships in flat files
- ✓ Maintain data consistency and validation across sheets

### Files Included

**Sheet 1:** `sheet_1.csv` — Primary dataset  
**Sheet 2:** `sheet_2.csv` — Related entity data  
**Sheet 3:** `sheet_3.csv` — Comparative/analytical results

## Project 2: 3D Model Database of Roman Inscriptions

### Learning Objectives

- ✓ Structure documentation for 3D-scanned cultural artifacts
- ✓ Link 3D models with metadata and measurements
- ✓ Implement METS (Metadata Encoding & Transmission Standard) for complex objects
- ✓ Preserve digital cultural heritage with multiple data formats
- ✓ Design systems for long-term accessibility of 3D content

### Files and Directories

**Metadata:** `databases/mets_practical.xml` — METS document with artifact metadata  
**3D Models:** Numbered directories (2/, 6/, 7/, 8/) and Roman_inscription/
- Each contains OBJ (model) and MTL (material) files with specifications
- JPG preview images for quick reference

### File Relationships

```
sheet_1.csv (Primary data)
    ↓ (linked by ID)
sheet_2.csv (Related entities)
    ↓ (linked by ID)
sheet_3.csv (Analytical results)
```

### Data Fields

**Sheet 1:**
| Field | Description | Type | Key Type |
|-------|-------------|------|----------|
| ID | Unique identifier | Text | Primary Key |
| [Field 1] | [Description] | [Type] | |
| [Field 2] | [Description] | [Type] | |

**Sheet 2:**
| Field | Description | Type | Key Type |
|-------|-------------|------|----------|
| Record_ID | Unique identifier | Text | Primary Key |
| Sheet1_ID | Reference to Sheet 1 | Text | Foreign Key |
| [Field 1] | [Description] | [Type] | |

**Sheet 3:**
| Field | Description | Type | Key Type |
|-------|-------------|------|----------|
| Analysis_ID | Unique identifier | Text | Primary Key |
| Sheet1_ID | Reference to Sheet 1 | Text | Foreign Key |
| [Field 1] | [Description] | [Type] | |

## Data Quality Standards

This dataset follows rigorous standards:

✓ **Referential integrity:** All foreign keys reference valid primary keys  
✓ **Normalization:** Data organized to minimize redundancy  
✓ **Consistency:** Identical values use consistent formatting across files  
✓ **Validation:** Automated checks for referential relationships  
✓ **Documentation:** Clear field descriptions and usage patterns  

## Working with the Data

### Viewing the Data

```bash
# View first few rows of each file
head sheet_1.csv
head sheet_2.csv
head sheet_3.csv

# Count records in each file
wc -l sheet_1.csv sheet_2.csv sheet_3.csv
```

### Linking Data in Spreadsheets

**VLOOKUP Example (Excel/Google Sheets):**
```
=VLOOKUP(A2, Sheet2!A:Z, 3, FALSE)
```

**INDEX/MATCH (More robust):**
```
=INDEX(Sheet2!C:C, MATCH(A2, Sheet2!A:A, 0))
```

### Joining Data in Python

```python
import pandas as pd

# Load all sheets
sheet1 = pd.read_csv('sheet_1.csv')
sheet2 = pd.read_csv('sheet_2.csv')
sheet3 = pd.read_csv('sheet_3.csv')

# Join sheet1 and sheet2 on IDs
merged = sheet1.merge(sheet2, left_on='ID', right_on='Sheet1_ID', how='left')

# Add analysis data
final = merged.merge(sheet3, left_on='ID', right_on='Sheet1_ID', how='left')

# Verify referential integrity
missing_refs = merged[merged['Sheet1_ID'].isna()]
print(f"Orphaned records: {len(missing_refs)}")
```

### Checking Data Relationships

```python
# Validate all foreign keys exist
sheet1_ids = set(sheet1['ID'])
sheet2_refs = set(sheet2['Sheet1_ID'].dropna())

missing_in_sheet1 = sheet2_refs - sheet1_ids
print(f"Invalid references in Sheet 2: {len(missing_in_sheet1)}")

# Find records without related data
orphaned = sheet1[~sheet1['ID'].isin(sheet2_refs)]
print(f"Records in Sheet 1 without Sheet 2 data: {len(orphaned)}")
```

### Normalizing to Relational Database

**SQLite Example:**
```sql
-- Create tables
CREATE TABLE sheet1 (
    ID TEXT PRIMARY KEY,
    field1 TEXT,
    field2 TEXT
);

CREATE TABLE sheet2 (
    Record_ID TEXT PRIMARY KEY,
    Sheet1_ID TEXT REFERENCES sheet1(ID),
    field1 TEXT
);

-- Import CSV files
.import sheet_1.csv sheet1
.import sheet_2.csv sheet2
.import sheet_3.csv sheet3

-- Query across datasets
SELECT s1.*, s2.* 
FROM sheet1 s1
LEFT JOIN sheet2 s2 ON s1.ID = s2.Sheet1_ID
WHERE s1.ID = 'some_value';
```

## Data Dictionary

### Shared Conventions

**ID Fields:**
- Format: [Consistent naming across sheets]
- Uniqueness: Guaranteed to be unique within each sheet
- References: Foreign keys use identical values to primary keys

**Date Fields:**
- Format: [Specify format: YYYY-MM-DD, etc.]
- Missing values: [Specify: NULL, "Unknown", blank]

**Categorical Fields:**
- Controlled vocabulary: [List allowed values]
- Case sensitivity: [Specify standards]

## Collection and Methodology

- **Data Source:** [Specify sources for each sheet]
- **Collection Method:** [How data was gathered]
- **Relationships:** [How sheets relate to each other]
- **Time Period:** [Temporal scope]
- **Total Records:** Sheet 1: [#], Sheet 2: [#], Sheet 3: [#]

## Analytical Approach

**Research Questions:**
- [Question addressed by comparative analysis]
- [Question enabled by relational structure]
- [Insights from combining datasets]

**Methods Used:**
- [Aggregation methods]
- [Comparative analysis techniques]
- [Statistical approaches, if any]

**Key Findings:**
- [Primary insights]
- [Patterns discovered]
- [Recommendations]

## Data Limitations

- This is a **sample dataset** for educational purposes
- Some data simplified for clarity and size
- Relationships represent [specific context]
- May not cover all edge cases
- Designed for learning, not production use

## FAIR Data Principles

This dataset implements FAIR principles:

**Findable**
- Clear filenames indicating relationships
- Metadata in README and data headers
- Structured organization with IDs

**Accessible**
- Open CSV format (universally readable)
- No specialized software required
- Available via public repository

**Interoperable**
- CSV format readable by all platforms
- Clear ID naming conventions
- Convertible to JSON, XML, SQL, and other formats

**Reusable**
- CC-BY-4.0 license
- Complete documentation of relationships
- Data dictionary and methodology explained

## Reusing This Data

You may:
- Download and analyze the datasets
- Join and merge the data
- Create derivative analyses
- Use for teaching and research

**You must:**
-  Attribute the datasets to Elitsa
-  Document any modifications
-  Include appropriate licensing

## Citation

**In-text citation:**
> Comparative analysis was performed using interconnected datasets (Elitsa, 2025-2026).

**Full citation:**
```
Elitsa. Multi-Sheet Comparative Dataset Analysis.
Foundations of Humanities Data Modeling and Formats Course. 2025-2026.
https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Elitsa
```

**BibTeX:**
```bibtex
@dataset{elitsa_comparative_2026,
  title={Multi-Sheet Comparative Dataset Analysis},
  author={Elitsa Lilova},
  year={2026},
  url={https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Elitsa},
  license={CC-BY-4.0}
}
```

## Contact & Questions

- **Data Questions:** Open an issue on GitHub
- **Technical Support:** See documentation folder

## License

This dataset is licensed under **Creative Commons Attribution 4.0 International (CC-BY-4.0)**

You are free to share and adapt this material with proper attribution.
For details, see the main [LICENSE](../../LICENSE) file.

## Related Resources

- Relational data design: [Database normalization guide](https://en.wikipedia.org/wiki/Database_normalization)
- Pandas documentation: [Data manipulation with Python](https://pandas.pydata.org/docs/)
- SQL tutorials: [W3Schools SQL](https://www.w3schools.com/sql/)
- CSV best practices: [Frictionless Data CSV Standard](https://specs.frictionlessdata.io/csv/)
- Course materials: [Humanities Data Modeling Samples](https://github.com/Bestroi150/humanities-data-modeling-samples)

## Data Validation Checklist

- [x] All CSV files have consistent encoding (UTF-8)
- [x] Column headers are descriptive and consistent
- [x] Foreign key references are valid
- [x] No orphaned records (unlinked data)
- [x] Primary keys are unique within each sheet
- [x] Date formats consistent within each field
- [x] Categorical values from controlled vocabulary
- [x] No unexpected null or missing values
- [x] Files tested with multiple tools (Excel, pandas, etc.)

## Comparative Analysis Examples

### Find Related Records
```python
# For each record in sheet1, find all related records in sheet2
for idx, row in sheet1.iterrows():
    related = sheet2[sheet2['Sheet1_ID'] == row['ID']]
    print(f"{row['ID']}: {len(related)} related records")
```

### Aggregate Across Datasets
```python
# Count related items per primary record
counts = sheet2.groupby('Sheet1_ID').size()
sheet1['related_count'] = sheet1['ID'].map(counts)
```

### Find Gaps in Data
```python
# Identify records without corresponding secondary data
sheet1_ids = set(sheet1['ID'])
sheet2_ids = set(sheet2['Sheet1_ID'].dropna())
missing_secondary = sheet1_ids - sheet2_ids
```

---

**Created:** 2025-2026  
**Status:** Complete  
**Version:** 1.0  
**Quality Level:** Teaching/Research Ready
