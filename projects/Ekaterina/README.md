# Ekaterina's Projects: Ancient Inscriptions & Morphological Database

**Student:** Ekaterina Dimitrova  
**Course:** Foundations of Humanities Data Modeling and Formats  
**Data Formats:** XML (TEI), CSV (Relational)  
**Last Updated:** 2025-2026

## Project Overview

This folder contains two complementary digital humanities projects demonstrating different data modeling approaches:
1. **Ancient Inscriptions** - Semantic markup using TEI XML standard
2. **Morphological Database** - Structured linguistic annotation with CSV

Together, these projects showcase how different formats can represent humanities data depending on the research question and analysis needs.

## Project 1: Ancient Inscriptions

### Learning Objectives

-  Understand XML syntax and structure
-  Apply TEI markup standards for epigraphic data
-  Encode textual and metadata elements semantically
-  Create data suitable for digital humanities databases
-  Balance human readability with machine parsing

### File: `inscriptions-final.xml`

A structured XML document containing ancient inscriptions with full TEI encoding, including:
- Inscription text and translations
- Metadata (date, provenance, material)
- Textual apparatus and editorial notes
- Links to related resources

## Project 2: Morphological Database of Pliny's Letters

### Learning Objectives

-  Understand relational data modeling for linguistic annotation
-  Implement controlled vocabularies for morphological tags
-  Structure corpus data for quantitative analysis
-  Create data dictionaries and metadata for linguistic resources
-  Design datasets for interdisciplinary use (corpus linguistics, digital humanities)

### Files: `sheet_1.csv` through `sheet_4.csv`

A corpus of 39 sentences from Pliny the Younger's *Epistulae* 6.16, with detailed morphological annotation at the token level.

## XML Structure Overview

```xml
<?xml version="1.0" encoding="UTF-8"?>
<TEI xmlns="http://www.tei-c.org/ns/1.0">
  <teiHeader>
    <!-- Metadata about the corpus -->
  </teiHeader>
  <text>
    <body>
      <div type="inscriptions">
        <!-- Individual inscription records -->
      </div>
    </body>
  </text>
</TEI>
```

### Key TEI Elements

| Element | Purpose | Example |
|---------|---------|---------|
| `<ab>` | Abstract element for inscription text | `<ab>Εὐθάνορος τὸ παιδί</ab>` |
| `<persName>` | Personal names | `<persName>Athenodorus</persName>` |
| `<placeName>` | Geographic locations | `<placeName>Athens</placeName>` |
| `<date>` | Temporal references | `<date when="0050">1st century CE</date>` |
| `<supplied>` | Editorial restoration | `<supplied reason="lost">[text]</supplied>` |
| `<unclear>` | Uncertain readings | `<unclear>text</unclear>` |
| `<rs>` | Named entities | `<rs type="material">marble</rs>` |

## Data Quality Standards

This dataset follows TEI standards and includes:

- **Valid XML:** Validates against TEI schemas
- **Semantic markup:** Each element type has meaning  
- **Encoding practices:** Follows established TEI conventions  
- **Documentation:** Embedded metadata and comments  
- **Accessibility:** Can be converted to other formats

## Working with the Data

### Viewing XML

**In a text editor:**
- VS Code (with XML extension recommended)
- Notepad++
- Sublime Text

**In a browser:**
- Most modern browsers display XML with syntax highlighting
- Firefox shows XML tree view

**Commands:**
```bash
# Pretty-print XML (macOS/Linux)
xmllint --format inscriptions-final.xml | less

# Validate XML (requires xmllint)
xmllint --schema inscriptions-final.xsd inscriptions-final.xml
```

### Querying XML Data

**Using XPath (Python):**
```python
from lxml import etree

# Load XML
tree = etree.parse('inscriptions-final.xml')
root = tree.getroot()

# Find all inscriptions from Athens
ns = {'tei': 'http://www.tei-c.org/ns/1.0'}
athens = root.xpath('//tei:placeName[text()="Athens"]', namespaces=ns)
print(f"Found {len(athens)} inscriptions from Athens")
```

**Using XPath (command line):**
```bash
xmllint --xpath "//persName" inscriptions-final.xml
```

### Format Conversion

**XML to CSV (Python):**
```python
from lxml import etree
import csv

tree = etree.parse('inscriptions-final.xml')
root = tree.getroot()
ns = {'tei': 'http://www.tei-c.org/ns/1.0'}

rows = []
for inscription in root.xpath('//tei:div[@type="inscription"]', namespaces=ns):
    row = {
        'text': etree.tostring(inscription, encoding='unicode'),
        'place': inscription.xpath('./tei:ab/tei:placeName/text()', namespaces=ns),
        'date': inscription.xpath('./tei:ab/tei:date/@when', namespaces=ns),
    }
    rows.append(row)

with open('inscriptions.csv', 'w', newline='') as f:
    writer = csv.DictWriter(f, fieldnames=['text', 'place', 'date'])
    writer.writeheader()
    writer.writerows(rows)
```

**XML to JSON (XSLT or Python):**
```python
import json
from lxml import etree

# Parse and convert
tree = etree.parse('inscriptions-final.xml')
data = etree.tostring(tree, encoding='unicode')
# [conversion logic here]

with open('inscriptions.json', 'w') as f:
    json.dump(data, f, indent=2)
```

## TEI Customization

This project uses a subset of TEI P5 elements suitable for epigraphic data:

**Used Elements:**
- Header elements: `<teiHeader>`, `<fileDesc>`, `<titleStmt>`
- Text elements: `<text>`, `<body>`, `<div>`, `<ab>`
- Inline elements: `<persName>`, `<placeName>`, `<date>`, `<rs>`
- Editorial elements: `<supplied>`, `<unclear>`, `<gap>`
- Reference elements: `<ref>`, `<ptr>`

**NOT used (by design):**
- Drama-specific elements (`<stage>`, `<sp>`)
- Verse-specific elements (`<l>`, `<lg>`)
- Apparatus elements (for simplified encoding)

## Collection and Methodology

- **Data Source:** [Specify databases: Inscriptions of Aphrodisias, PHI Greek Inscriptions, etc.]
- **Encoding Method:** Manual markup from transcriptions
- **Collection Period:** [Specify date range of inscriptions]
- **Geographic Scope:** [Specify regions: Attica, Asia Minor, Egypt, etc.]
- **Sample Size:** [Number of inscriptions encoded]
- **Quality Assurance:** [Specify validation methods]

## Data Limitations

- This is a **sample dataset** for educational purposes
- Simplified encoding compared to comprehensive epigraphic databases
- Does not include full diplomatic or critical apparatus
- Photographs and detailed paleographic analysis not included
- Relies on published texts (original materials not examined)

## FAIR Data Principles

This dataset implements FAIR principles:

**Findable**
- Clear TEI document structure
- Metadata in `<teiHeader>` section
- Descriptive keywords in README

**Accessible**
- Open XML format (industry standard)
- No proprietary software required
- Available via public repository

**Interoperable**
- TEI XML follows international standards
- Convertible to multiple formats (CSV, JSON, RDF)
- Usable with TEI tools and databases

**Reusable**
- CC-BY-4.0 license with clear attribution
- Complete documentation of encoding practices
- Suitable for research, teaching, and linked data

## Reusing This Data

You may:
- Download and analyze the XML
- Convert to other formats
- Incorporate into digital humanities projects
- Use for teaching and research

**You must:**
-  Provide attribution to Ekaterina
-  Indicate modifications made
-  Include license information

## Citation

**In-text citation:**
> Inscriptions were encoded using TEI XML following international standards (Ekaterina Dimitrova, 2025-2026).

**Full citation:**
```
Ekaterina Dimitrova. Ancient Inscriptions: A TEI-XML Dataset.
Foundations of Humanities Data Modeling and Formats Course. 2025-2026.
https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Ekaterina
```

**BibTeX:**
```bibtex
@dataset{ekaterina_inscriptions_2026,
  title={Ancient Inscriptions: A TEI-XML Dataset},
  author={Ekaterina Dimitrova},
  year={2026},
  url={https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Ekaterina},
  license={CC-BY-4.0}
}
```

## Contact & Questions

- **Project Questions:** Open an issue on GitHub
- **TEI Questions:** See TEI Guidelines at tei-c.org

## License

This dataset is licensed under **Creative Commons Attribution 4.0 International (CC-BY-4.0)**

You are free to share and adapt this material with proper attribution.
For details, see the main [LICENSE](../../LICENSE) file.

## Related Resources

- TEI Guidelines: [tei-c.org](https://www.tei-c.org/)
- TEI by Example: [Interactive TEI tutorials](http://www.tei-c.org/release/doc/tei-p5-examples/html/)
- Epidoc guidelines: [Epigraphy resources](https://epidoc.stoa.org/)
- XML Tools: VS Code with XML extensions, Oxygen XML
- Course materials: Main [Humanities Data Modeling Samples](https://github.com/Bestroi150/humanities-data-modeling-samples) repository

## XML Validation Checklist

- [x] Well-formed XML (no parsing errors)
- [x] Valid against TEI schema
- [x] Proper namespace declarations
- [x] Consistent encoding (UTF-8)
- [x] All elements properly closed
- [x] Attributes properly quoted
- [x] Special characters properly escaped
- [x] Header contains essential metadata

---

**Created:** 2025-2026  
**Status:** Complete  
**Version:** 1.0  
**Quality Level:** Teaching/Research Ready
