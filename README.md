# Sofia University Digital Humanities: Student Projects

An exhibition of digital humanities projects created by students in the **Foundations of Humanities Data Modeling and Formats** course at Sofia University. These projects demonstrate practical application of tidy data principles, data format conversion, and spatial methods to real-world humanities research.

## Overview

This repository collects student work showcasing:
- **Data modeling** and format conversion (CSV, XML, JSON, GeoJSON)
- **Domain expertise** in ancient studies, history, and cultural heritage
- **Applied skills** in spreadsheets, markup languages, and GIS visualization
- **FAIR data principles** (Findable, Accessible, Interoperable, Reusable)

## Repository Structure

```
SU-DH-Students/
├── README.md                          # This file
├── LICENSE                            # CC-BY-4.0 License
├── CITATION.cff                       # Citation metadata
├── projects/                          # Student projects organized by name
│   ├── Andrea/
│   │   ├── README.md                 # Project description
│   │   ├── ancient_coins_sample.csv  # Tabular numismatic data
│   │   └── LICENSE.txt
│   ├── Ekaterina/
│   │   ├── README.md
│   │   ├── inscriptions-final.xml    # TEI XML epigraphic data
│   │   ├── sheet_1.csv               # Morphological annotation (primary)
│   │   ├── sheet_2.csv               # Frequency summary
│   │   ├── sheet_3.csv               # Full frequency summary
│   │   ├── sheet_4.csv               # Reference vocabulary
│   │   └── LICENSE.txt
│   ├── Elitsa/
│   │   ├── README.md
│   │   ├── sheet_1.csv               # Multi-sheet relational data
│   │   ├── sheet_2.csv
│   │   ├── sheet_3.csv
│   │   ├── databases/                # 3D model database files
│   │   │   ├── mets_practical.xml
│   │   │   ├── 2/, 6/, 7/, 8/       # 3D model directories
│   │   │   └── Roman_inscription/
│   │   └── LICENSE.txt
│   └── Irina/
│       ├── README.md
│       ├── Greek_colonization_on_the_Black_Sea.csv  # Geographic data
│       ├── TEI_Satirikon_76glava.xml # DH text analysis (Satyricon)
│       └── LICENSE.txt
├── documentation/                     # Shared documentation
│   ├── data-formats.md               # Guide to data formats used
│   ├── citation-guide.md             # How to cite student work
│   └── resources.md                  # Additional learning resources
└── guidelines/                        # Course guidelines
    ├── project-requirements.md       # Project submission standards
    ├── data-quality-checklist.md    # Data validation guidelines
    └── fair-principles.md           # FAIR data implementation guide
```

## Featured Projects

### Andrea: Ancient Coins Sample
**Focus:** Numismatic data in tabular format
- **Format:** CSV (tidy data)
- **Fields:** Coin ID, denomination, metal, mint, date, provenance
- **Learning objectives:** Data normalization, handling categorical data

### Ekaterina: Ancient Inscriptions
**Focus:** Epigraphic data in structured markup
- **Format:** XML (TEI-compliant)
- **Content:** Ancient inscription transcriptions and metadata
- **Learning objectives:** Semantic markup, document structure, metadata encoding

### Elitsa: Multi-sheet Dataset Analysis
**Focus:** Comparative tabular data
- **Format:** Three CSV files
- **Content:** Related datasets for comparative analysis
- **Learning objectives:** Data relationships, referential integrity, linking datasets

### Irina: Greek Colonization on the Black Sea
**Focus:** Historical-geographic data
- **Format:** CSV with geographic data
- **Fields:** Settlement name, coordinates, founding date, colonizing city, material culture
- **Learning objectives:** Spatial data representation, GIS concepts, historical dataset design

### Irina Koleva: Digital Humanities Analysis - Satyricon Chapter 76
**Focus:** Humanities text analysis using multiple DH tools
- **Format:** TEI XML, CSV, Excel analysis
- **Content:** Multi-method analysis of Petronius' Satyricon, Chapter 76
- **Learning objectives:** Markup semantics, quantitative and qualitative analysis, tool integration

### Ekaterina Dimitrova: Multiple Projects
**Focus 1 (Inscriptions):** Epigraphic data in structured markup
- **Format:** XML (TEI-compliant)
- **Content:** Ancient inscription transcriptions and metadata
- **Learning objectives:** Semantic markup, document structure, metadata encoding

**Focus 2 (Morphological Database):** Linguistic annotation and morphological analysis
- **Format:** Relational CSV sheets
- **Content:** 39 sentences from Pliny the Younger's *Epistulae* 6.16 with detailed morphological annotation
- **Learning objectives:** Structured linguistic data, controlled vocabularies, quantitative corpus analysis

### Elitsa: Multiple Projects
**Focus 1:** Comparative tabular data
- **Format:** Three CSV files
- **Content:** Related datasets for comparative analysis
- **Learning objectives:** Data relationships, referential integrity, linking datasets

**Focus 2 (Databases):** 3D modeling and database structures
- **Format:** XML (METS), 3D model files (OBJ/MTL)
- **Content:** Roman inscriptions with 3D models and measurements
- **Learning objectives:** Structured data for complex artifacts, 3D model documentation

## Key Learning Outcomes

By exploring these projects, you will understand:

✓ How humanities scholars structure domain data  
✓ Real-world examples of tidy data principles  
✓ Multiple format representations (CSV, XML, JSON, GeoJSON)  
✓ Data quality and validation practices  
✓ Appropriate documentation for academic datasets  
✓ FAIR data principles in practice  
✓ Format conversion strategies  
✓ Metadata and citation best practices

## Data Formats Overview

| Format | Use Case | Example File |
|--------|----------|--------------|
| **CSV** | Tabular analysis, spreadsheets, databases | Andrea's coins, Irina's colonization data |
| **XML** | Semantic markup, document structure, TEI encoding | Ekaterina's inscriptions |
| **JSON** | Web APIs, modern applications, nested data | (Can be generated from CSV/XML) |
| **GeoJSON** | Geographic visualization, mapping | (Can be created from coordinate data) |

## Quick Start

1. **Explore a project** – Choose a student folder to examine their work
2. **Read the README** – Each project folder contains a README explaining the dataset
3. **Examine the data** – Open CSV files in spreadsheets or XML in text editors
4. **Check documentation** – See `documentation/` for format guides and best practices
5. **Review guidelines** – See `guidelines/` for project standards

## Working with the Data

### Viewing CSV Files
- Open with Excel, Google Sheets, LibreOffice Calc, or any text editor
- Use spreadsheet formulas for analysis and validation
- Export to other formats as needed

### Viewing XML Files
- Use any text editor (VS Code, Notepad++, etc.)
- Validate XML structure with online validators
- Transform to other formats using XSLT or Python scripts

### Format Conversion Workflow
See `documentation/data-formats.md` for detailed instructions on converting between:
- CSV ↔ JSON
- CSV ↔ XML
- XML ↔ JSON
- Any format ↔ GeoJSON (for geographic data)

## FAIR Data Principles

This showcase demonstrates FAIR principles in student work:

**Findable**
- Clear project titles and descriptions
- Structured metadata in each README
- Organized file naming conventions

**Accessible**
- Open file formats (CSV, XML, JSON)
- No proprietary software required
- Free tools for viewing and processing data

**Interoperable**
- Multiple format representations
- Standard markup (XML/TEI)
- Clear data structure documentation

**Reusable**
- Open Creative Commons license (CC-BY-4.0)
- Clear data dictionaries and field descriptions
- Documented methods and data collection procedures

## Citation

If you reference student work from this repository, please use the following format:

```
[Student Name]. [Project Title]. Foundations of Humanities Data Modeling and Formats Course,
[University], 2025-2026. https://github.com/Bestroi150/SU-DH-Students/
```

See `documentation/citation-guide.md` for additional citation formats and tools.

## Course Reference

These projects are created in the **Foundations of Humanities Data Modeling and Formats** course.
The course materials and teaching modules are available at:
[Humanities Data Modeling Samples](https://github.com/Bestroi150/humanities-data-modeling-samples)

## Learning Resources

**Course Materials:**
- Tidy Data Principles
- Spatial Data & GIS Concepts
- Format Conversion Strategies
- Data Quality & Validation

**Recommended Reading:**
- Flanders & Jannidis, *The Shape of Data in the Digital Humanities*
- D'Ignazio & Klein, *Data Feminism*
- Posner, M., "Humanities Data: A Necessary Contradiction?"
- Go, A., "Databases" (in *Debates in the Digital Humanities*)

**Tools & Technologies:**
- Spreadsheets: Excel, Google Sheets, LibreOffice Calc
- Text/Code Editors: VS Code, Notepad++, Sublime Text
- Validation: XML validators, CSV validators
- Conversion: Python (pandas, lxml), OpenRefine, Notepad++

## Project Standards

All student projects follow these standards:
- Consistent file naming (lowercase, hyphens for spaces)
- UTF-8 encoding for all text files
- Clear data dictionaries included in README
- Proper attribution and licensing (CC-BY-4.0)
- README.md in each project folder
- Clear documentation of data sources

See `guidelines/project-requirements.md` for detailed submission standards.

## Contributing

If you are a student and would like to add your project:
1. Create a folder in `projects/` with your name
2. Include your data file(s) and a README.md
3. Add LICENSE.txt (CC-BY-4.0)
4. Submit a pull request or contact course instructors

## License

All student projects are licensed under **Creative Commons Attribution 4.0 International (CC-BY-4.0)**

This means:
- ✓ You are free to share, copy, and redistribute this material
- ✓ You may adapt and create derivative works
- ✓ You must give appropriate credit and indicate changes made

See [LICENSE](LICENSE) for full details.

## Citation Metadata

See `CITATION.cff` for structured citation data in Citation File Format.

## Contact & Questions

For questions about:
- **Student work:** Contact individual students
- **Course materials:** See the main [Humanities Data Modeling Samples](https://github.com/Bestroi150/humanities-data-modeling-samples) repository
- **This showcase:** Open an issue on GitHub

## Acknowledgments

- Student contributors: Andrea, Ekaterina, Elitsa, Irina
- Course instructor: [Your Name]
- Institution: [Your Institution]
- Based on curriculum: Foundations of Humanities Data Modeling and Formats
- Inspiration: Digital Humanities community and FAIR data initiatives

---

**Last Updated:** 2026  
**Course:** Foundations of Humanities Data Modeling and Formats  
**Status:** Active (students continue adding projects)
