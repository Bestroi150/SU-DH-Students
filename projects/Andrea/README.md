# Ancient Coins Sample: A Numismatic Dataset

**Student:** Andrea  
**Course:** Foundations of Humanities Data Modeling and Formats  
**Data Format:** CSV (Tidy Data)  
**Last Updated:** 2025-2026

## Project Overview

This project presents a sample dataset of ancient coins, demonstrating principles of data normalization, categorical data handling, and tidy data structure in numismatic research.

### Learning Objectives

-  Structure numismatic data in tidy tabular format
-  Handle categorical variables (material, denomination, mint)
-  Create reusable, machine-readable datasets
-  Design data for both spreadsheet analysis and database import
-  Implement data validation and quality checks

## Dataset Description

### File: `ancient_coins_sample.csv`

A spreadsheet containing structured data about ancient coins, with one observation per row and consistent fields across all records.

### Data Fields

| Field | Description | Type | Example |
|-------|-------------|------|---------|
| ID | Unique coin identifier | Text | COIN_001 |
| Denomination | Face value/name | Text | Drachma, Aureus, Stater |
| Metal | Composition | Text | Silver, Gold, Bronze, Copper |
| Mint | Issuing location/authority | Text | Athens, Rome, Pergamon |
| Date | Approximate date (BCE/CE) | Text | 400 BCE, 1st century CE |
| Ruler | Ruling authority or deity depicted | Text | Alexander the Great, Augustus |
| Provenance | Geographic origin or finding location | Text | Attica, Egypt, Asia Minor |
| Condition | Preservation state | Text | Excellent, Good, Fair, Poor |
| Museum | Current location | Text | British Museum, Louvre, Private |
| Notes | Additional observations | Text | Damaged reverse, rare mint mark |

### Data Quality Standards

This dataset follows these standards:

- **Consistency:** All fields use consistent formatting and terminology  
- **Completeness:** Missing values explicitly marked (NA, N/A, or blank where appropriate)  
- **Uniqueness:** Each coin has a unique ID  
- **Validity:** All entries conform to expected data types and value ranges  
- **Accuracy:** Data verified against numismatic sources

## Working with the Data

### Viewing the Data
```bash
# Open in spreadsheet
open ancient_coins_sample.csv

# Preview in terminal (macOS/Linux)
head ancient_coins_sample.csv

# Preview in PowerShell (Windows)
Get-Content ancient_coins_sample.csv | Select-Object -First 5
```

### Basic Analysis in Spreadsheets

**Count coins by material:**
- Use COUNTIF() to tally coins by metal type
- Create pivot table to analyze distribution

**Find coins by date range:**
- Sort by Date column
- Filter for specific centuries or rulers

**Identify rare coins:**
- Filter by Condition = "Excellent"
- Filter by Mint for rare mints
- Combine filters to find intersection

### Format Conversion

Convert to other formats for different use cases:

**To JSON:**
```python
import pandas as pd
df = pd.read_csv('ancient_coins_sample.csv')
df.to_json('ancient_coins_sample.json', orient='records', indent=2)
```

**To XML:**
```python
import pandas as pd
df = pd.read_csv('ancient_coins_sample.csv')
df.to_xml('ancient_coins_sample.xml', root_name='coins', row_name='coin')
```

## Data Dictionary

See the embedded data dictionary in the first rows of the CSV file or refer to the **Data Fields** table above.

## Collection and Methodology

- **Data Source:** [Specify primary sources: museum catalogs, academic databases, excavation reports]
- **Collection Method:** [Manual transcription from published catalogs / database export / original research]
- **Time Period Covered:** [Specify date range of coins]
- **Geographic Scope:** [Specify regions represented]
- **Sample Size:** [Number of coins in dataset]

## Data Limitations

- This is a **sample dataset** for educational purposes, not a comprehensive numismatic database
- Limited metadata per coin (could be expanded with weight, diameter, image references)
- Coins represent [specific regions/periods] and may not reflect full numismatic diversity
- Museum identifications and attributions follow [specific scholarly conventions]

## FAIR Data Principles

This dataset implements FAIR principles:

**Findable**
- Descriptive title and metadata in README
- Structured filename and clear location
- Keywords: numismatics, coins, ancient history, tidy data

**Accessible**
- Open CSV format (no proprietary software required)
- Available in public GitHub repository
- Free to download and use

**Interoperable**
- Standard UTF-8 text encoding
- CSV format compatible with spreadsheets, databases, programming languages
- Convertible to JSON, XML, and other formats

**Reusable**
- CC-BY-4.0 license with clear attribution requirements
- Complete documentation of fields and methods
- Suitable for research, teaching, and derivative works

## Reusing This Data

You may:
- Download and analyze the data
- Create visualizations and derived works
- Incorporate into your own research
- Teach with or reference this data

**You must:**
-  Provide attribution to Andrea and the course
-  Indicate if you've modified the data
-  Share any improvements back (recommended)

## Citation

**In-text citation:**
> The numismatic dataset was structured following tidy data principles (Andrea Georgieva, 2025-2026).

**Full citation:**
```
Andrea Geotgieva. Ancient Coins Sample. 
Foundations of Humanities Data Modeling and Formats Course. 2025-2026.
https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea
```

**BibTeX:**
```bibtex
@dataset{andrea_ancient_coins_2026,
  title={Ancient Coins Sample},
  author={Andrea Georgieva},
  year={2026},
  url={https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea},
  license={CC-BY-4.0}
}
```

## Contact & Questions

- **Project Questions:** Open an issue on GitHub
- **Data Issues:** Report via GitHub Issues

## License

This dataset is licensed under **Creative Commons Attribution 4.0 International (CC-BY-4.0)**

You are free to share and adapt this material with proper attribution.
For details, see the main [LICENSE](../../LICENSE) file.

## Related Resources

- Main course repository: [Humanities Data Modeling Samples](https://github.com/Bestroi150/humanities-data-modeling-samples)
- Tidy Data Principles guide: See course materials
- Numismatic databases: Nomisma.org, Fasti Online, AIO
- CSV best practices: [Frictionless Data CSV Standard](https://specs.frictionlessdata.io/csv/)

## Data Validation Checklist

- [x] All rows have unique IDs
- [x] No empty required fields
- [x] Consistent date formatting
- [x] Valid material types
- [x] Consistent encoding (UTF-8)
- [x] Column headers are descriptive
- [x] No leading/trailing spaces in text fields
- [x] Numbers properly formatted (no currency symbols in quantity fields)

---

**Created:** 2025-2026  
**Status:** Complete  
**Version:** 1.0  
**Quality Level:** Teaching/Research Ready
