# Data Quality Checklist

A practical guide to validating data quality before submitting projects.

## Introduction

Good data quality is essential for:
- Reliable analysis and conclusions
- Reproducibility and trust
- Reusability by other researchers
- Academic credibility

This checklist helps ensure your data meets professional standards.

## Quick Checklist

### Before You Start

- [ ] Have I documented my data collection process?
- [ ] Do I understand the limitations of my data?
- [ ] Have I created a data dictionary?
- [ ] Is my data in an open format (CSV, XML, JSON)?

### File Quality

- [ ] All files use UTF-8 encoding
- [ ] Filenames are lowercase with hyphens
- [ ] Files are logically organized
- [ ] No temporary or backup files in folder
- [ ] README.md is present and complete

### Structure Quality

- [ ] Column headers are clear and descriptive
- [ ] Column names follow naming convention
- [ ] No empty rows or columns
- [ ] Consistent structure throughout file
- [ ] Data properly aligned in rows/columns

### Content Quality

- [ ] All entries use consistent format
- [ ] No leading/trailing spaces in cells
- [ ] Dates consistent (YYYY-MM-DD format recommended)
- [ ] Numbers consistent (no currency symbols)
- [ ] Text properly capitalized

### Data Completeness

- [ ] No unexpected missing values
- [ ] Missing values consistently marked (NA, NULL, blank)
- [ ] Completeness ratio ≥ 95%
- [ ] Sparse columns documented and justified
- [ ] Required fields populated

### Data Accuracy

- [ ] Spot-checked sample records against sources
- [ ] Geographic data verified
- [ ] Dates verified against historical sources
- [ ] Names spelled correctly
- [ ] No obvious typos or errors

### Data Consistency

- [ ] Values consistent across entire dataset
- [ ] Categorical values from controlled list
- [ ] No mixed data types in single column
- [ ] Duplicate records identified and handled
- [ ] Related datasets properly linked

### Documentation Quality

- [ ] Data dictionary complete
- [ ] Methodology documented
- [ ] Limitations acknowledged
- [ ] Data sources cited
- [ ] Transformations explained

## Detailed Quality Assessment

### 1. File Quality

#### UTF-8 Encoding

**Why:** Ensures compatibility across platforms and languages.

**Check in different tools:**

*Python:*
```python
import chardet
with open('data.csv', 'rb') as f:
    result = chardet.detect(f.read())
print(result['encoding'])  # Should be UTF-8
```

*Command line:*
```bash
file data.csv  # Should indicate UTF-8
```

**Action:** If not UTF-8, convert:
```bash
iconv -f ISO-8859-1 -t UTF-8 old.csv > new.csv
```

#### Filename Quality

**Bad:** `data.csv`, `coins (1).csv`, `file_v2_FINAL.csv`
**Good:** `ancient_coins_sample.csv`, `inscriptions_data.csv`

**Criteria:**
- Descriptive (indicates content)
- Lowercase
- Hyphens for spaces (no underscores)
- Versioning in README, not filename

#### File Organization

```
StudentName/
├── README.md
├── LICENSE.txt
├── primary_data.csv
└── supporting_docs/
    └── methodology.txt
```

Not:
```
StudentName/
├── data_v1.csv
├── data_v2.csv
├── FINAL_data.csv
├── backup.csv
└── random_notes.txt
```

### 2. Structure Quality

#### Column Headers

**Requirements:**
- ✓ Present in first row
- ✓ Descriptive and clear
- ✓ No special characters (except underscore)
- ✓ Consistent naming style (snake_case recommended)

**Bad Headers:**
```
Column1, Col2, Date Created, MATERIAL, name_of_location_where_object_was_found
```

**Good Headers:**
```
ID, Name, Date, Material, Location
```

#### Empty Rows/Columns

**Check:**
```python
import pandas as pd
df = pd.read_csv('data.csv')

# Find empty rows
empty_rows = df.isnull().sum(axis=1)
print(f"Rows with missing data: {(empty_rows > 0).sum()}")

# Find empty columns
empty_cols = df.isnull().sum()
print(f"Completely empty columns: {(empty_cols == len(df)).sum()}")
```

**Action:** Remove or document empty rows/columns.

### 3. Content Quality

#### Leading/Trailing Spaces

**Problem:** Can cause matching and sorting issues.

**Check:**
```python
df.columns = df.columns.str.strip()  # Headers
df = df.applymap(lambda x: x.strip() if isinstance(x, str) else x)  # Data
```

**Example:**
```
Bad:  " Athens ", "Athens", " Athens"
Good: "Athens", "Athens", "Athens"
```

#### Date Formatting

**Standard:** YYYY-MM-DD (ISO 8601)

**Examples:**
- Good: `2026-03-15`, `1850-06-12 BCE`
- Bad: `03/15/2026`, `15 March 2026`, `2026/03/15`

**Check:**
```python
# Validate ISO date format
import re
date_pattern = r'^\d{4}-\d{2}-\d{2}$'
valid_dates = df['date'].str.match(date_pattern)
print(f"Invalid dates: {(~valid_dates).sum()}")
```

#### Number Formatting

**Issues to avoid:**
```
Bad:  "1,000", "$1000", "1.000,00", "~1000"
Good: "1000", "1000.5", "-500"
```

**Check:**
```python
# Numeric columns should contain only numbers
df['amount'].apply(lambda x: isinstance(x, (int, float)))
```

### 4. Data Completeness

#### Missing Value Patterns

**Consistent indication:**
```
Good:   NA, NULL, "", (blank)
Bad:    "?", "unknown", "-", "N/A", "na", "n/a"
```

**Check:**
```python
# Check for different missing value representations
missing_patterns = [np.nan, 'NA', 'N/A', 'na', '?', 'unknown', 'null', '']
for pattern in missing_patterns:
    count = (df == pattern).sum().sum()
    if count > 0:
        print(f"Found '{pattern}': {count} times")
```

#### Completeness Ratio

**Target:** ≥95% of data present

**Calculate:**
```python
total_cells = df.size
missing_cells = df.isnull().sum().sum()
completeness = (total_cells - missing_cells) / total_cells * 100
print(f"Completeness: {completeness:.1f}%")
```

#### Required Fields

**Action:**
```python
required_fields = ['ID', 'Name', 'Date']
for field in required_fields:
    missing = df[field].isnull().sum()
    if missing > 0:
        print(f"WARNING: {missing} missing values in required field: {field}")
```

### 5. Data Accuracy

#### Spot Checking

**Method:**
1. Select 10-20% of records randomly
2. Verify against original sources
3. Check for transcription errors
4. Verify computations if any

**In Python:**
```python
import random
sample_size = max(10, len(df) // 10)  # At least 10 records
sample = df.sample(n=sample_size)
# Manually verify these records
```

#### Geographic Validation

**For latitude/longitude:**
```python
# Check coordinate ranges
valid_lat = (-90 <= df['latitude']) & (df['latitude'] <= 90)
valid_lon = (-180 <= df['longitude']) & (df['longitude'] <= 180)

invalid = ~(valid_lat & valid_lon)
if invalid.sum() > 0:
    print(f"Invalid coordinates: {invalid.sum()}")
    print(df[invalid][['latitude', 'longitude']])
```

#### Date Validation

**Check date ranges make sense:**
```python
# Convert to datetime
df['date'] = pd.to_datetime(df['date'])

# Find outliers
too_old = df['date'] < pd.Timestamp('0001-01-01')
too_new = df['date'] > pd.Timestamp.now()

if too_old.sum() + too_new.sum() > 0:
    print("Questionable dates found")
```

### 6. Data Consistency

#### Categorical Variables

**Define allowed values:**
```python
allowed_materials = ['Silver', 'Gold', 'Bronze', 'Copper']

invalid = ~df['material'].isin(allowed_materials)
if invalid.sum() > 0:
    print(f"Invalid materials: {df[invalid]['material'].unique()}")
```

**Action:** Standardize or create controlled vocabulary.

#### Case Consistency

**Problem:** "Athens", "athens", "ATHENS"

**Solution:**
```python
# Standardize capitalization
df['location'] = df['location'].str.title()
```

#### Data Type Consistency

**Check:**
```python
# Ensure numeric columns are numeric
df['amount'] = pd.to_numeric(df['amount'], errors='coerce')

if df['amount'].isnull().sum() > 0:
    print("Some values couldn't be converted to numbers")
```

#### Duplicate Records

**Identify:**
```python
# Check for exact duplicates
duplicates = df.duplicated()
print(f"Exact duplicates: {duplicates.sum()}")

# Check for near-duplicates (useful for names)
from difflib import SequenceMatcher
# [comparison logic]
```

**Decide:** Keep (with justification), merge, or remove.

### 7. Referential Integrity (if multiple files)

#### Foreign Key Validation

**Check:**
```python
# For related datasets
primary_ids = set(sheet1['ID'])
foreign_ids = set(sheet2['Sheet1_ID'].dropna())

# Find orphaned records
orphaned = foreign_ids - primary_ids
if orphaned:
    print(f"Orphaned foreign keys: {orphaned}")

# Find unlinked primary records
unlinked = primary_ids - foreign_ids
if unlinked:
    print(f"Primary records without related data: {unlinked}")
```

## Validation Script Template

```python
import pandas as pd
import numpy as np

def validate_data(filepath):
    """Comprehensive data quality check"""
    df = pd.read_csv(filepath)
    
    print(f"=== Validating: {filepath} ===\n")
    
    # 1. Structure
    print("STRUCTURE VALIDATION:")
    print(f"  Rows: {len(df)}")
    print(f"  Columns: {len(df.columns)}")
    print(f"  Memory: {df.memory_usage(deep=True).sum() / 1024**2:.2f} MB")
    
    # 2. Missing Values
    print("\nMISSING VALUES:")
    missing = df.isnull().sum()
    if missing.sum() > 0:
        print(missing[missing > 0])
    else:
        print("  No missing values")
    
    # 3. Duplicates
    print("\nDUPLICATES:")
    dups = df.duplicated().sum()
    print(f"  Exact duplicates: {dups}")
    
    # 4. Data Types
    print("\nDATA TYPES:")
    print(df.dtypes)
    
    # 5. Column-specific checks
    print("\nCOLUMN ANALYSIS:")
    for col in df.columns:
        print(f"  {col}: {df[col].dtype}, {df[col].nunique()} unique values")
    
    return df

# Usage
validate_data('data.csv')
```

## Before/After Checklist

### Before Data Entry

- [ ] Plan data structure
- [ ] Define fields and data types
- [ ] Create data dictionary
- [ ] Establish validation rules
- [ ] Prepare standardized formats

### During Data Entry

- [ ] Validate entries as entered
- [ ] Check against source documents
- [ ] Use dropdown lists for categories
- [ ] Flag uncertain values
- [ ] Record any deviations

### After Data Entry

- [ ] Run automated validation
- [ ] Spot-check sample records
- [ ] Check for completeness
- [ ] Verify accuracy
- [ ] Check for consistency
- [ ] Document any issues
- [ ] Create final clean version

## Common Data Quality Issues and Fixes

| Issue | Detection | Fix |
|-------|-----------|-----|
| Whitespace | `df['col'].str.len()` varies | `df['col'].str.strip()` |
| Mixed case | Sorting issues | Use `.str.title()` or `.str.lower()` |
| Date format | Inconsistent | Standardize to ISO 8601 |
| Missing indicator | Multiple representations | Choose one: NA, NULL, blank |
| Duplicates | `df.duplicated()` | Review and merge or remove |
| Type mismatch | `df.dtypes` | Convert with `pd.to_numeric()` |
| Outliers | `df.describe()` | Investigate and document |

## Quality Tiers

**Tier 1: Minimum (Acceptable)**
- UTF-8 encoded
- Open format
- No empty rows/columns
- Documented

**Tier 2: Good (Recommended)**
- Tier 1 requirements
- ≥95% complete
- Spot-checked accuracy
- Data dictionary included

**Tier 3: Excellent (Best Practice)**
- Tier 2 requirements
- Validated against sources
- Comprehensive documentation
- Automated validation scripts provided

## Tools for Validation

- **OpenRefine:** Interactive data cleaning
- **Pandas (Python):** Programmatic validation
- **Google Sheets:** Built-in validation rules
- **Excel:** Data validation feature
- **Online CSV Validators:** Format checking

## Documentation of Data Quality

Document in README:

```markdown
## Data Quality

This dataset has been validated according to professional standards:

- **Completeness:** 98.5% of expected data present
- **Accuracy:** Spot-checked against 15 original sources
- **Consistency:** All categorical values verified against controlled vocabulary
- **Format:** UTF-8 encoding, ISO 8601 dates
- **Validation:** Automated checks performed using pandas

Known quality issues:
- 2 records (0.5%) have estimated dates ±5 years
- Location data for 3 records based on approximate descriptions
- 1 field (Material) incomplete for 20 records
```

## Getting Help

- Check this guide
- See [project-requirements.md](project-requirements.md)
- Consult tool documentation
- Ask instructor
- Post to course forum

---

**Last Updated:** 2026

**Remember:** Good data quality is an investment in your research's credibility and reusability!
