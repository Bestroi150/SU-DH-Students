# FAIR Data Principles Guide

Implementing FAIR (Findable, Accessible, Interoperable, Reusable) data principles in student projects.

## What are FAIR Data Principles?

FAIR is an international framework for research data management and stewardship, ensuring data is:

- **Findable** — Easy to locate by humans and machines
- **Accessible** — Available through standardized interfaces
- **Interoperable** — Compatible across systems and tools
- **Reusable** — Well-documented for future use

Published in 2016, FAIR principles have become standards in research, education, and digital humanities.

## F - Findable

### What Does Findable Mean?

Data should be easily discovered through:
- Unique identifiers
- Descriptive metadata
- Searchable catalogs
- Clear documentation
- Persistent URLs

### How Student Projects Implement Findable

**✓ Unique Identifiers**
- GitHub URL: Permanent, persistent location
- Project folders with descriptive names
- Individual records with unique IDs (in datasets)

**✓ Descriptive Metadata**
- Clear project titles
- README files with summaries
- Field descriptions and data dictionaries
- Keywords and topic tags

**✓ Clear Documentation**
- README in every project folder
- Data structure explained
- Methodology documented
- Sources cited

**✓ Example - Andrea's Project**
```
Project: Humanities Data Modeling - Student Projects Showcase
Title: Ancient Coins Sample
Student: Andrea
Year: 2026
URL: https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea
Keywords: numismatics, ancient coins, CSV, tidy data, tabular data
```

### Best Practices for Findability

✓ Use descriptive filenames
- Good: `ancient_coins_sample.csv`
- Bad: `data.csv`, `file1.csv`

✓ Include README in every folder
- Summarizes content
- Lists all files
- Explains data structure

✓ Add keywords and tags
- For GitHub repository
- In documentation
- For search engines

✓ Document data relationships
- Explain how datasets connect
- Show primary keys and foreign keys
- Clarify references

### Tools for Improving Findability

- **GitHub README:** Primary discovery mechanism
- **GitHub Topics:** Tags for categorization
- **GitHub Pages:** Create website for projects
- **Zenodo Integration:** Get DOI for persistent identification
- **Data Repositories:** Register in academic catalogs

## A - Accessible

### What Does Accessible Mean?

Data should be:
- Available through standardized protocols
- Downloadable without special permissions
- Machine-readable
- Openly licensed
- Available offline (not behind paywalls)

### How Student Projects Implement Accessible

**✓ Open Data Formats**
- CSV — Readable by any spreadsheet or programming language
- XML — Standard markup format
- JSON — Universal web format
- GeoJSON — Standard geographic format
- No proprietary formats (no Excel-only)

**✓ Open Source Licenses**
- All projects: CC-BY-4.0
- Free to access and download
- Clear terms for reuse
- No restrictions beyond attribution

**✓ No Technical Barriers**
- Free tools required for viewing
- Available via public GitHub (no login required for viewing)
- Downloadable as ZIP archive
- Cloneable via git

**✓ Detailed Access Information**
```
Download options:
- Clone: git clone https://github.com/Bestroi150/student-projects-showcase.git
- Download ZIP: [GitHub provides button]
- Individual files: Click on file → Download button
```

### Best Practices for Accessibility

✓ Use open, non-proprietary formats
- CSV instead of Excel
- XML instead of proprietary markup
- JSON instead of closed APIs
- GeoJSON instead of Shapefile

✓ Avoid paywalls and restrictions
- All work is CC-BY-4.0
- No authentication required
- No geographic restrictions
- No time-limited access

✓ Provide multiple access methods
- Download entire repository
- Download individual files
- Browse online
- Clone via git

✓ Include clear metadata
- What is in each file
- File sizes and formats
- Character encoding (UTF-8)
- Data dictionary

✓ Support multiple platforms
- Works on Windows, Mac, Linux
- Compatible with cloud tools
- Accessible from mobile
- No special hardware requirements

### Tools for Improving Accessibility

- **GitHub:** Free public repository
- **UTF-8 Encoding:** Universal text encoding
- **Standard Formats:** CSV, XML, JSON
- **Creative Commons License:** Clear legal terms
- **Documentation:** README, CITATION.cff, LICENSE

## I - Interoperable

### What Does Interoperable Mean?

Data should be:
- Compatible across different systems
- Convertible between formats
- Usable with common tools
- Following established standards
- Linked to other datasets

### How Student Projects Implement Interoperable

**✓ Standard Formats**
- CSV: Works with spreadsheets, databases, R, Python, etc.
- XML: Compatible with text editors, XSLT transformers, web browsers
- JSON: Parseable by every programming language
- GeoJSON: Works with mapping software (QGIS, Leaflet.js, etc.)

**✓ Format Conversions**
Each project can be converted to other formats:
```python
import pandas as pd

# CSV → JSON
df = pd.read_csv('data.csv')
df.to_json('data.json')

# CSV → XML
df.to_xml('data.xml')

# XML → CSV
# [conversion code]
```

**✓ Standardized Metadata**
- Dublin Core metadata elements
- FAIR data citation principles
- CITATION.cff for structured citation
- README.md in standard format

**✓ Linked Data Elements**
- Foreign keys connect related datasets
- Geographic coordinates in WGS84 (standard)
- Dates in ISO 8601 format (YYYY-MM-DD)
- URLs point to external resources

**✓ Data Dictionary Standards**
Each project includes field documentation:
```
| Field | Description | Type | Format |
|-------|-------------|------|--------|
| ID | Unique identifier | Text | XXXX_###|
| Name | Entity name | Text | Text string |
| Date | Event date | Date | YYYY-MM-DD |
```

### Best Practices for Interoperability

✓ Follow established standards
- ISO 8601 for dates (YYYY-MM-DD)
- WGS84 (EPSG:4326) for coordinates
- UTF-8 encoding for text
- Use controlled vocabularies

✓ Use semantic markup
- Element/field names indicate meaning
- Data types clearly specified
- Relationships documented
- References linked

✓ Provide conversion guides
- How to convert CSV to JSON
- How to convert XML to CSV
- How to create GeoJSON from coordinates
- Examples in documentation

✓ Include technical metadata
- File format and version
- Encoding information
- Schema or structure documentation
- Software requirements (if any)

✓ Link to external resources
- References to source materials
- URLs for related datasets
- DOIs for academic papers
- Links to geographic databases

### Tools for Improving Interoperability

- **Data Conversion:** pandas, OpenRefine, XSLT
- **Standardized Formats:** CSV, XML, JSON, GeoJSON
- **Controlled Vocabularies:** Established term lists
- **Metadata Standards:** Dublin Core, MIAOW
- **Validation:** Schema validators

### Example: Converting Andrea's CSV to Multiple Formats

**Original (CSV):**
```csv
ID,Name,Material,Mint
COIN_001,Drachma,Silver,Athens
```

**Converted to JSON:**
```json
[
  {
    "ID": "COIN_001",
    "Name": "Drachma",
    "Material": "Silver",
    "Mint": "Athens"
  }
]
```

**Converted to XML:**
```xml
<coins>
  <coin>
    <ID>COIN_001</ID>
    <Name>Drachma</Name>
    <Material>Silver</Material>
    <Mint>Athens</Mint>
  </coin>
</coins>
```

**Converted to RDF (Semantic Web):**
```xml
<rdf:RDF>
  <rdf:Description rdf:about="http://example.org/COIN_001">
    <ex:Name>Drachma</ex:Name>
    <ex:Material>Silver</ex:Material>
    <ex:Mint>Athens</ex:Mint>
  </rdf:Description>
</rdf:RDF>
```

## R - Reusable

### What Does Reusable Mean?

Data should be:
- Well-documented for future use
- Clearly licensed for reuse
- Suitable for research and teaching
- Accompanied by metadata about collection
- Suitable for derivative works

### How Student Projects Implement Reusable

**✓ Comprehensive Documentation**
- **README.md:** Project overview and guide
- **Data Dictionary:** Field definitions
- **Methodology:** Collection and analysis methods
- **Limitations:** What data cannot show
- **References:** Sources and citations

**✓ Clear Licensing**
- All projects: CC-BY-4.0
- Permits sharing and adaptation
- Requires attribution only
- Available in multiple formats

**✓ Reproducibility Support**
- Clear data collection procedures
- Reproducible data transformations
- Version control (GitHub)
- Historical record of changes

**✓ Quality Assurance**
- Data validation documentation
- Quality checks performed
- Known limitations noted
- Error handling documented

**✓ Context and Provenance**
- Data sources cited
- Collection methodology explained
- Uncertainty acknowledged
- Time period documented

### Best Practices for Reusability

✓ Document thoroughly
- What data represents
- How data was collected
- What conclusions can/cannot be drawn
- Known limitations and biases

✓ Include data dictionary
- Define all fields
- Specify data types
- Note missing value conventions
- Explain categorical values

✓ Provide usage examples
- Code samples for common tasks
- Analysis workflows
- Visualization examples
- Transformation scripts

✓ Use clear, consistent naming
- Field names self-explanatory
- File names descriptive
- Variable names consistent
- Consistent capitalization

✓ Document quality measures
- Validation performed
- Accuracy assessment
- Completeness checks
- Known issues

✓ Include methodology
- Data collection procedures
- Selection criteria
- Processing steps
- Analysis decisions

✓ Provide attribution requirements
- How to cite the work
- What attribution is needed
- Where to place attribution
- Example citations

### Tools for Improving Reusability

- **Documentation:** README.md, data dictionaries
- **Version Control:** GitHub history
- **Code Comments:** Explain data transformations
- **Metadata:** CITATION.cff, embedded descriptions
- **Examples:** Scripts, notebooks, analysis guides

## Assessing FAIR Implementation

### Self-Assessment Checklist

**Findable:**
- [ ] Project has unique URL (GitHub)
- [ ] README file included
- [ ] Data dictionary provided
- [ ] Keywords/topics documented
- [ ] Data can be searched online

**Accessible:**
- [ ] Uses open, non-proprietary formats
- [ ] Publicly available (no paywall)
- [ ] Available in multiple ways (download, clone, browse)
- [ ] Clear access instructions
- [ ] UTF-8 encoding used

**Interoperable:**
- [ ] Follows established standards (ISO 8601, WGS84)
- [ ] Can be converted to other formats
- [ ] Compatible with common tools
- [ ] Metadata follows standards
- [ ] Related data properly linked

**Reusable:**
- [ ] Comprehensive documentation
- [ ] Clear license (CC-BY-4.0)
- [ ] Methodology documented
- [ ] Data quality described
- [ ] Attribution guidelines provided

### FAIR Maturity Levels

**Level 1 - Aware:** Project acknowledges FAIR principles

**Level 2 - Implemented:** Project follows most FAIR practices
- ✓ Good documentation
- ✓ Open license
- ✓ Standard formats
- ~ Some gaps in metadata

**Level 3 - Advanced:** Project exemplifies FAIR principles
- ✓ Comprehensive documentation
- ✓ Multiple format options
- ✓ Persistent identifiers
- ✓ Semantic linking
- ✓ Full reproducibility

## Real-World Examples

### Andrea's Ancient Coins - FAIR Implementation

**Findable:**
✓ GitHub URL is persistent
✓ Descriptive title: "Ancient Coins Sample"
✓ CSV format standard and discoverable
✓ README explains content

**Accessible:**
✓ CSV format (open standard)
✓ CC-BY-4.0 license
✓ No paywall or login
✓ Works with spreadsheets and programming languages

**Interoperable:**
✓ CSV convertible to JSON, XML
✓ Consistent field names
✓ Data types specified
✓ Can import into databases

**Reusable:**
✓ Detailed methodology
✓ Data dictionary included
✓ Quality standards documented
✓ Citation guidelines provided

## Improving FAIR Implementation

### Recommended Enhancements

1. **Add DOI:** Register with Zenodo for persistent identifier
   ```
   https://zenodo.org/record/XXXXX
   ```

2. **Add RDF/Semantic Data:** Enable linked data
   ```xml
   <rdf:Description rdf:about="http://example.org/coins">
     <dc:title>Ancient Coins Sample</dc:title>
   </rdf:Description>
   ```

3. **Enable Machine Tagging:** Add JSON-LD
   ```json
   {
     "@context": "https://schema.org/",
     "@type": "Dataset",
     "name": "Ancient Coins Sample"
   }
   ```

4. **Version Control:** Use semantic versioning (1.0, 1.1, 2.0)

5. **Data Repository Registration:** Submit to academic data catalogs
   - Zenodo
   - Dataverse
   - Figshare
   - OSF

## FAIR vs. Open

**FAIR principles ≠ Open Access**

- **FAIR** = Organized, findable, standardized data
- **Open** = Freely available, no restrictions

FAIR data should be open, but open data isn't necessarily FAIR.
All student projects here are both FAIR and open.

## Further Reading

- [FAIR Guiding Principles (Original Publication)](https://www.nature.com/articles/sdata201618)
- [GO FAIR Implementation Network](https://www.go-fair.org/)
- [FAIR Data Maturity Model](https://www.fairsfair.eu/resources/fair-data-maturity-model)
- [RDA FAIR Data Toolkit](https://www.rd-alliance.org/groups/fair-data-maturity-model-wg)
- [Digital Humanities and FAIR Data](https://dh.royalhistoricalsociety.org/fair-data-humanities/)

## Quick Reference

| Principle | Implementation | Tools |
|-----------|------------------|-------|
| **Findable** | GitHub + README + Keywords | GitHub, Documentation |
| **Accessible** | Open formats + CC-BY-4.0 | CSV, XML, JSON, License |
| **Interoperable** | Standards (ISO 8601, WGS84) | Conversion scripts |
| **Reusable** | Documentation + Methodology | README, Data dictionary |

---

**Last Updated:** 2026

**Remember:** FAIR principles support better science, better teaching, and better reuse of research data!
