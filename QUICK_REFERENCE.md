# Quick Reference Guide

A one-page guide to navigate this repository.

## What is This?

A showcase of student projects from the **Foundations of Humanities Data Modeling and Formats** course, demonstrating practical application of data principles in humanities research.

## Quick Navigation

### For Students (Submitting Projects)

**Step 1:** Read project requirements
- [guidelines/project-requirements.md](guidelines/project-requirements.md)

**Step 2:** Check data quality
- [guidelines/data-quality-checklist.md](guidelines/data-quality-checklist.md)

**Step 3:** Ensure FAIR compliance
- [guidelines/fair-implementation.md](guidelines/fair-implementation.md)

**Step 4:** Document your project
- Use README template from example projects
- Include citation information
- Add LICENSE.txt (CC-BY-4.0)

**Step 5:** Submit
- Create folder in `projects/YourName/`
- Include data files and README.md
- Submit pull request or send to instructor

### For Educators (Teaching with These Projects)

**Teaching Resources:**
- [documentation/data-formats.md](documentation/data-formats.md) — Guide to CSV, XML, JSON
- [documentation/resources.md](documentation/resources.md) — Learning materials and tools
- [documentation/fair-principles.md](documentation/fair-principles.md) — FAIR principles explained

**Example Projects:**
- [projects/Andrea/](projects/Andrea/) — CSV/tabular data example
- [projects/Ekaterina/](projects/Ekaterina/) — XML markup example
- [projects/Elitsa/](projects/Elitsa/) — Multi-dataset relationships
- [projects/Irina/](projects/Irina/) — Geographic/spatial data example

### For Researchers (Using These Datasets)

**How to Access:**
- Browse project folders
- Download individual files or entire project (Code → Download ZIP)
- Clone repository: `git clone https://github.com/Bestroi150/student-projects-showcase.git`

**How to Cite:**
- See project README for citation instructions
- Use [documentation/citation-guide.md](documentation/citation-guide.md) for multiple formats
- Include CC-BY-4.0 attribution

**Data Format Help:**
- [documentation/data-formats.md](documentation/data-formats.md) — Format specifications
- Each project README includes conversion examples

## Directory Structure

```
student-projects-showcase/
├── README.md                           # Main overview (start here)
├── LICENSE                             # CC-BY-4.0 for all projects
├── CITATION.cff                        # Citation metadata
│
├── projects/                           # Student projects
│   ├── Andrea/                         # Coins dataset (CSV)
│   │   ├── README.md
│   │   ├── LICENSE.txt
│   │   └── ancient_coins_sample.csv
│   ├── Ekaterina/                      # Inscriptions (XML)
│   ├── Elitsa/                         # Multi-sheet datasets
│   └── Irina/                          # Geographic data (CSV + GeoJSON)
│
├── documentation/                      # Learning guides
│   ├── data-formats.md                 # CSV, XML, JSON, GeoJSON guide
│   ├── citation-guide.md               # How to cite datasets
│   ├── fair-principles.md              # FAIR data explanation
│   └── resources.md                    # Learning materials
│
└── guidelines/                         # For project contributors
    ├── project-requirements.md         # Submission standards
    ├── data-quality-checklist.md       # Quality validation
    └── fair-implementation.md          # FAIR compliance guide
```

## Frequently Asked Questions

**Q: Can I use these datasets?**
A: Yes! All projects are CC-BY-4.0 licensed. You must give attribution.

**Q: How do I cite a project?**
A: See the README in each project folder. Multiple citation formats provided.

**Q: How do I submit my project?**
A: Follow [guidelines/project-requirements.md](guidelines/project-requirements.md). Create a folder and submit pull request or contact instructor.

**Q: What format should my data be in?**
A: Open formats: CSV, XML, JSON, or GeoJSON. No proprietary formats.

**Q: Do I need a data dictionary?**
A: Yes. Required in README with field descriptions.

**Q: What if I need help?**
A: See documentation folder or example projects for reference.

**Q: Can I modify these datasets?**
A: Yes, but you must indicate modifications and maintain CC-BY-4.0 license.

**Q: How are projects organized?**
A: By student name in `projects/` folder. One folder per student project.

**Q: What is FAIR?**
A: Findable, Accessible, Interoperable, Reusable data principles. See [documentation/fair-principles.md](documentation/fair-principles.md).

## Key Files to Know

| File | Purpose | Who Uses It |
|------|---------|------------|
| README.md | Project overview | Everyone (start here!) |
| LICENSE | CC-BY-4.0 terms | All users |
| CITATION.cff | Citation metadata | Researchers |
| projects/ | Student work | Learners & researchers |
| guidelines/ | Submission requirements | Students submitting |
| documentation/ | Learning resources | Educators & learners |

## Useful Commands

### Clone the Repository
```bash
git clone https://github.com/Bestroi150/student-projects-showcase.git
```

### Download Specific Project
```bash
# Download just Andrea's project
git clone --depth 1 --filter=blob:none --sparse \
  https://github.com/Bestroi150/student-projects-showcase.git
cd student-projects-showcase
git sparse-checkout set projects/Andrea
```

### Convert CSV to Other Formats
```python
import pandas as pd

df = pd.read_csv('data.csv')
df.to_json('data.json')    # → JSON
df.to_xml('data.xml')      # → XML
```

## Learning Path

**For Beginners:**
1. Read main [README.md](README.md)
2. Explore one project (e.g., Andrea's)
3. Read project README
4. Try opening data in spreadsheet
5. See [documentation/data-formats.md](documentation/data-formats.md)

**For Intermediate:**
1. Review multiple projects
2. Study data dictionaries
3. Try format conversions
4. Learn about FAIR principles
5. See [documentation/fair-principles.md](documentation/fair-principles.md)

**For Advanced:**
1. Analyze datasets with Python
2. Create geographic visualizations
3. Perform comparative analysis
4. Contribute improvements
5. Cite work in publications

## Course Connection

These student projects are created in the **Foundations of Humanities Data Modeling and Formats** course, which uses materials from:

[Humanities Data Modeling Samples](https://github.com/Bestroi150/humanities-data-modeling-samples)

Main course modules cover:
- Tidy data principles
- Spatial data & GIS concepts
- Format conversion strategies
- FAIR data implementation

## Tools You'll Need

**To View Data:**
- Spreadsheet: Excel, Google Sheets, LibreOffice Calc
- Text Editor: VS Code, Notepad++, Sublime Text
- Web Browser: Any modern browser

**For Analysis (Optional):**
- Python (pandas, matplotlib)
- R (tidyverse)
- QGIS (for mapping)

All free and open-source options available!

## Quick Links

**Documentation:**
- [Data Formats Guide](documentation/data-formats.md)
- [Citation Guide](documentation/citation-guide.md)
- [FAIR Principles](documentation/fair-principles.md)
- [Learning Resources](documentation/resources.md)

**Guidelines:**
- [Project Requirements](guidelines/project-requirements.md)
- [Data Quality Checklist](guidelines/data-quality-checklist.md)
- [FAIR Implementation](guidelines/fair-implementation.md)

**Example Projects:**
- [Andrea's Coins](projects/Andrea/)
- [Ekaterina's Inscriptions](projects/Ekaterina/)
- [Elitsa's Multi-sheet Data](projects/Elitsa/)
- [Irina's Geographic Data](projects/Irina/)

## Contributing

Have improvements? Found an error? Want to add your project?

1. Open an issue to discuss
2. Fork repository
3. Make changes
4. Submit pull request
5. Or contact course instructor

## License & Attribution

**All student projects:** CC-BY-4.0
- Free to share and adapt
- Must provide attribution
- No restrictions beyond that

**When using:** Include project title, student name, year, and URL.

## Getting Help

1. **Project submission:** See [guidelines/project-requirements.md](guidelines/project-requirements.md)
2. **Data questions:** See relevant project README
3. **Format help:** See [documentation/data-formats.md](documentation/data-formats.md)
4. **Citation help:** See [documentation/citation-guide.md](documentation/citation-guide.md)
5. **Still stuck:** Open GitHub issue or email instructor

## Status

- **Repository:** Active
- **Projects:** Growing (add your own!)
- **Maintenance:** Updated regularly
- **Version:** 1.0+

---

**Last Updated:** 2026

**Ready to explore?** Start with [README.md](README.md) or pick a [project](projects/)!
