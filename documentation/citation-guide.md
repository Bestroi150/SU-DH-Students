# Citation Guide

Best practices for citing student projects and datasets from this repository.

## Why Cite?

Proper citation:
- ✓ Gives credit to student researchers
- ✓ Allows readers to locate original sources
- ✓ Supports academic integrity
- ✓ Builds verifiable research records
- ✓ Facilitates reproducibility

## Citation Elements

When citing a student project, include:

1. **Student name** — The creator/author
2. **Project title** — Descriptive title
3. **Course information** — Course name and institution
4. **Year** — Publication/completion year
5. **URL** — Link to GitHub repository
6. **License** — How the work can be reused

## Standard Citation Formats

### In-text Citation (APA)

**First mention:**
> Studies of ancient coins demonstrate the application of data normalization principles (Andrea, 2024-2026).

**Subsequent mentions:**
> Further analysis of numismatic data (Andrea, 2024-2026) revealed patterns in minting practices.

### Bibliography Entry (APA Style)

```
Andrea. (2026). Ancient coins sample. Foundations of Humanities Data Modeling 
and Formats Course. 
https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea
```

### Full Citation (MLA Style)

```
Andrea. "Ancient Coins Sample." Foundations of Humanities Data Modeling and 
Formats Course, 2026, 
github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea.
```

### Full Citation (Chicago Style)

```
Andrea. "Ancient Coins Sample." Foundations of Humanities Data Modeling and 
Formats Course. 2026. 
https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea.
```

### BibTeX Format

```bibtex
@dataset{andrea_ancient_coins_2026,
  title={Ancient Coins Sample},
  author={Andrea},
  year={2026},
  url={https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea},
  license={CC-BY-4.0}
}
```

### RIS Format (for reference managers)

```
TY  - DSET
AU  - Andrea
TI  - Ancient Coins Sample
PY  - 2026
PB  - Foundations of Humanities Data Modeling and Formats Course
UR  - https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea
LA  - en
KW  - ancient coins; numismatics; tidy data
LI  - CC-BY-4.0
ER  -
```

## Citation by Use Case

### Citing Specific Data

When citing a specific dataset file:

**In-text:**
> The dataset contains 150 coins documented in tabular format (Andrea, 2026, ancient_coins_sample.csv).

**Bibliography:**
```
Andrea. (2026). ancient_coins_sample.csv. In Ancient Coins Sample. 
Foundations of Humanities Data Modeling and Formats Course. Retrieved from 
https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea
```

### Citing Methodology

When citing project documentation:

**In-text:**
> Data was structured following tidy data principles (Andrea, 2026, README.md).

**Bibliography:**
```
Andrea. (2026). Ancient coins sample [Dataset documentation]. Foundations of 
Humanities Data Modeling and Formats Course. Retrieved from 
https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Andrea/README.md
```

### Citing Specific Findings

When citing analysis results from a project:

**In-text:**
> Analysis of Greek colonies revealed founding patterns by metropolis (Irina, 2026).

**Bibliography:**
```
Irina. (2026). Greek colonization on the Black Sea: A historical-geographic 
dataset. Foundations of Humanities Data Modeling and Formats Course. Retrieved 
from https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Irina
```

## Format-Specific Guidance

### CSV Data Citations

```
Andrea. (2026). ancient_coins_sample.csv [Dataset]. Retrieved from 
https://github.com/Bestroi150/student-projects-showcase/projects/Andrea/ancient_coins_sample.csv
```

### XML Data Citations

```
Ekaterina. (2026). inscriptions-final.xml [Dataset]. Retrieved from 
https://github.com/Bestroi150/student-projects-showcase/projects/Ekaterina/inscriptions-final.xml
```

### Geographic Data Citations

```
Irina. (2026). Greek_colonization_on_the_Black_Sea.csv [Geospatial dataset]. 
Retrieved from 
https://github.com/Bestroi150/student-projects-showcase/projects/Irina/Greek_colonization_on_the_Black_Sea.csv
```

## Citing the Repository

### The Project Showcase as a Whole

**Bibliography:**
```
Bestroi150. (2026). Humanities data modeling: Student projects showcase 
[Dataset collection]. Retrieved from 
https://github.com/Bestroi150/student-projects-showcase
```

**BibTeX:**
```bibtex
@dataset{bestroi_student_showcase_2026,
  title={Humanities Data Modeling: Student Projects Showcase},
  author={Bestroi150},
  year={2026},
  url={https://github.com/Bestroi150/student-projects-showcase},
  license={CC-BY-4.0}
}
```

## How to Find Citation Information

Each project includes:

1. **README.md** — Contains full citation examples in multiple formats
2. **LICENSE.txt or LICENSE** — Shows CC-BY-4.0 terms
3. **GitHub metadata** — Student name, date, repository URL

To cite a project:
1. Open the project folder
2. Read the README section titled "Citation"
3. Choose the format that matches your style guide

## Quick Reference Table

| Style | Format | Example |
|-------|--------|---------|
| APA | Author (Year). Title. Institution. URL | Andrea (2026). Ancient Coins Sample. Foundations... |
| MLA | Author. "Title." Institution, Year, URL | Andrea. "Ancient Coins Sample." Foundations..., 2026 |
| Chicago | Author. "Title." Institution. Year. URL | Andrea. "Ancient Coins Sample." Foundations... 2026 |
| BibTeX | @dataset{key, fields...} | @dataset{andrea_2026,...} |

## Reference Manager Integration

### Zotero

1. Install Zotero
2. Copy RIS format information
3. Right-click in Zotero → Import from Clipboard

### Mendeley

1. Install Mendeley Desktop
2. File → Import → Paste BibTeX
3. Or manually create entry with information

### Google Scholar

1. Search for project name
2. If available, use Google Scholar citation
3. Or manually create citation

## DOI and Persistent Identifiers

Some repositories support Digital Object Identifiers (DOIs) for permanent citing:

- Check GitHub repository for Zenodo badge
- If present, use DOI instead of GitHub URL
- Example: https://doi.org/10.5281/zenodo.XXXXX

## Attribution Requirements

When reusing student data or projects, you must:

✓ **Provide clear attribution**
- Include student name
- Include project title
- Include publication year
- Include original source URL

✓ **Indicate modifications**
- State that you modified the data/work
- Describe nature of modifications
- Date of modification

✓ **Include license information**
- State that work is CC-BY-4.0
- Link to full license text
- Maintain license in derivative works

### Attribution Example

```
This data is derived from "Ancient Coins Sample" by Andrea 
(2024-2026, https://github.com/Bestroi150/student-projects-showcase).

Modifications: Filtered to coins minted in Athens, added modern equivalents 
of monetary value.

Original work licensed under CC-BY-4.0 
(https://creativecommons.org/licenses/by/4.0/)
```

## Common Citation Mistakes to Avoid

❌ **Don't:**
- Omit the student's name
- Use only GitHub URL without title/author
- Forget the year
- Misattribute work to course instructor
- Ignore license requirements

✓ **Do:**
- Include complete author name
- Provide descriptive project title
- Include year of publication
- Mention "Student Project" or course name
- Follow CC-BY-4.0 attribution requirements

## Tips for Different Contexts

### In Academic Papers

Use formal citation in body and bibliography:
```
As demonstrated by Irina (2026), geographic data can be effectively 
structured for historical analysis.
```

### In Blog Posts or Articles

Use a more conversational style:
```
Andrea's dataset on ancient coins shows how to organize numismatic 
data properly (2026).
```

### In Code/Technical Documentation

Include as comments:
```python
# Data source: Andrea. Ancient Coins Sample (2026)
# URL: https://github.com/Bestroi150/student-projects-showcase
# License: CC-BY-4.0
data = pd.read_csv('ancient_coins_sample.csv')
```

### In Presentations

Include source slide:
```
Data source: Irina, "Greek Colonization on the Black Sea" (2026)
https://github.com/Bestroi150/student-projects-showcase
```

## Using Citation Tools Online

### EasyBib
- Supports multiple formats
- Generate bibliography automatically
- https://www.easybib.com

### BibMe
- Citation guide and generator
- Convert between formats
- https://www.bibme.org

### CitationMachine
- Comprehensive citation tool
- Educational resources
- https://www.citationmachine.net

### Zotero Standalone
- Open-source reference manager
- Free and feature-rich
- https://www.zotero.org

## Getting Help

- **Citation questions:** Open GitHub issue with "Citation" tag
- **Format questions:** Consult your discipline's style guide
- **Tool questions:** Check tool documentation
- **License questions:** See LICENSE file in repository

## Further Resources

- [APA Style Guide](https://apastyle.apa.org/)
- [MLA Handbook](https://www.mla.org/)
- [Chicago Manual of Style](https://www.chicagomanualofstyle.org/)
- [Creative Commons Attribution Guide](https://creativecommons.org/licenses/by/4.0/)
- [Citing Digital Objects](https://www.library.virginia.edu/research/data-management/citing-digital-objects/)

---

**Last Updated:** 2026

**Remember:** Proper citation honors student work and supports the broader academic community!
