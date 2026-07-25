# Irina's Projects: Greek Colonization & Digital Humanities Text Analysis

**Student:** Irina Koleva  
**Course:** Foundations of Humanities Data Modeling and Formats  
**Data Formats:** CSV (Geographic), TEI XML (Text Analysis)  
**Last Updated:** 2025-2026

## Project Overview

This folder contains two complementary digital humanities projects:
1. **Greek Colonization on the Black Sea** - Historical-geographic dataset with spatial coordinates
2. **Digital Humanities Analysis of Satyricon Chapter 76** - Multi-method text analysis using TEI markup and computational tools

Together, these projects demonstrate different methodological approaches in digital humanities: quantitative spatial analysis and qualitative text analysis.

## Project 1: Greek Colonization on the Black Sea

### Learning Objectives

- ✓ Structure geographic data for mapping and analysis
- ✓ Integrate historical information with spatial coordinates
- ✓ Design data for GIS visualization
- ✓ Represent uncertainty and complexity in historical geography
- ✓ Create datasets suitable for both tabular and geospatial analysis

### File: `Greek_colonization_on_the_Black_Sea.csv`

A comprehensive CSV dataset containing:
- Settlement names and alternative names
- Geographic coordinates (latitude/longitude)
- Founding dates and historical periods
- Colonizing city-state (metropolis)
- Cultural and material evidence
- Archaeological information

## Project 2: Digital Humanities Analysis - Satyricon Chapter 76

### Learning Objectives

- ✓ Apply TEI markup standards to literary texts
- ✓ Combine qualitative and quantitative text analysis methods
- ✓ Use digital humanities tools (VoyantTools, DH Text Microscope)
- ✓ Integrate Excel data analysis with XML markup
- ✓ Create reproducible digital scholarship

### File: `TEI_Satirikon_76glava.xml`

TEI-encoded markup of Chapter 76 from Petronius' *Satyricon*, enabling:
- Semantic markup of textual elements
- Named entity recognition
- Linguistic analysis
- Integration with visualization tools

This project combines multiple DH methodologies:
- **Text markup:** TEI XML semantic encoding
- **Quantitative analysis:** VoyantTools word frequency and visualizations
- **Text microscopy:** Detailed structural analysis using DH Text Microscope
- **Data integration:** Excel spreadsheets for comparative analysis

## Dataset Description

### Project 1: CSV Geographic Data
- Historical notes and references

## Data Fields

| Field | Description | Format | Example |
|-------|-------------|--------|---------|
| ID | Unique settlement identifier | Text | BSEA_001 |
| Settlement_Name | Primary name of settlement | Text | Histria |
| Alternative_Names | Other historical names | Text | Istros, Istion |
| Modern_Location | Contemporary geographic name | Text | Romania |
| Region | Black Sea region | Text | Western Shore, Northern Shore |
| Latitude | Geographic coordinate N/S | Float | 44.5500 |
| Longitude | Geographic coordinate E/W | Float | 28.7350 |
| Coord_Source | Source of coordinates | Text | Geopy, Published database |
| Founding_Date | Approximate founding date | Text | 7th century BCE |
| Founding_Date_BCE | Numeric date (BCE) | Integer | -650 |
| Metropolis | Founding city-state | Text | Miletus, Phocaea, Corinth |
| Phyla | Greek tribal affiliations | Text | Ionian, Aeolian |
| Pottery_Evidence | Early pottery types | Text | Milesian, East Greek |
| Coins | Numismatic evidence | Text | Silver staters, Bronze drachmas |
| Material_Culture | Archaeological finds | Text | Terra sigillata, lamps, amphoras |
| Period | Historical-cultural period | Text | Archaic, Classical, Hellenistic |
| Status | Settlement status | Text | Major colony, Minor settlement |
| Duration | Occupation duration | Text | Active 7th-3rd century BCE |
| References | Academic citations | Text | Boardman 1999, Avram 2004 |

## Geographic Data

### Coordinate System
- **Projection:** WGS84 (EPSG:4326) — standard for web mapping
- **Format:** Decimal degrees (DD.DDDD)
- **Precision:** ±0.0001° (approximately ±10 meters)
- **Accuracy:** Based on published archaeological sources and modern identification

### Coverage

**Geographic scope:** Black Sea coast
- **Western Shore:** Modern Romania, Bulgaria
- **Northern Shore:** Modern Russia, Ukraine
- **Eastern Shore:** Modern Georgia, Turkey
- **Southern Shore:** Modern Turkey

**Temporal scope:** 8th century BCE to 1st century CE
- Focus on Greek colonial period (Archaic through Hellenistic)
- Some sites continued under Roman rule

## Working with the Data

### Viewing in Spreadsheets

```bash
# Open in Excel or Google Sheets
open Greek_colonization_on_the_Black_Sea.csv

# Preview in terminal
head -n 10 Greek_colonization_on_the_Black_Sea.csv
```

### Converting to GeoJSON for Web Mapping

```python
import csv
import json
from decimal import Decimal

# Read CSV
features = []
with open('Greek_colonization_on_the_Black_Sea.csv', 'r', encoding='utf-8') as f:
    reader = csv.DictReader(f)
    for row in reader:
        feature = {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [float(row['Longitude']), float(row['Latitude'])]
            },
            "properties": {
                "id": row['ID'],
                "name": row['Settlement_Name'],
                "metropolis": row['Metropolis'],
                "founding_date": row['Founding_Date'],
                "period": row['Period']
            }
        }
        features.append(feature)

# Create FeatureCollection
geojson = {
    "type": "FeatureCollection",
    "features": features
}

# Save
with open('Greek_colonization_on_the_Black_Sea.geojson', 'w', encoding='utf-8') as f:
    json.dump(geojson, f, indent=2, ensure_ascii=False)
```

### Using Leaflet.js for Interactive Maps

```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    <style>
        #map { height: 500px; }
    </style>
</head>
<body>
    <div id="map"></div>
    <script>
        // Initialize map centered on Black Sea
        const map = L.map('map').setView([43, 35], 6);
        
        // Add basemap
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map);
        
        // Load colonies
        fetch('Greek_colonization_on_the_Black_Sea.geojson')
            .then(res => res.json())
            .then(data => {
                L.geoJSON(data, {
                    pointToLayer: (feature, latlng) => {
                        return L.circleMarker(latlng, {
                            radius: 6,
                            fillColor: '#FF6B6B',
                            color: '#000',
                            weight: 1,
                            opacity: 1,
                            fillOpacity: 0.7
                        });
                    },
                    onEachFeature: (feature, layer) => {
                        layer.bindPopup(
                            `<b>${feature.properties.name}</b><br/>
                             Founded by: ${feature.properties.metropolis}<br/>
                             Date: ${feature.properties.founding_date}`
                        );
                    }
                }).addTo(map);
            });
    </script>
</body>
</html>
```

### Spatial Analysis in Python

```python
import pandas as pd
from geopy.distance import geodesic

df = pd.read_csv('Greek_colonization_on_the_Black_Sea.csv')

# Calculate distances between colonies
def distance_to_metropolis(row):
    """Calculate distance from colony to nearest known metropolis"""
    # This would require additional metropolis coordinates
    pass

# Identify clusters of colonies
from sklearn.cluster import DBSCAN
coords = df[['Latitude', 'Longitude']].values
clustering = DBSCAN(eps=1, min_samples=2).fit(coords)
df['cluster'] = clustering.labels_

# Count colonies by metropolis
metropolis_counts = df['Metropolis'].value_counts()
print("Colonies by founding city:")
print(metropolis_counts)

# Analyze temporal patterns
df['Founding_Century'] = df['Founding_Date_BCE'].apply(
    lambda x: f"{(-x // 100) + 1}th century BCE"
)
print("\nFoundations by century:")
print(df['Founding_Century'].value_counts().sort_index())
```

## Data Dictionary

### Categorical Variables

**Region values:**
- Western Shore, Northern Shore, Eastern Shore, Southern Shore

**Period values:**
- Archaic (8th-6th century BCE)
- Classical (5th-4th century BCE)
- Hellenistic (4th-1st century BCE)

**Status values:**
- Major colony, Minor settlement, Trading post, Unknown

**Metropolis values:**
- Miletus, Phocaea, Corinth, Megara, Thrace, Aeolia, [others]

## Collection and Methodology

- **Primary Sources:**
  - Strabo, *Geography* (ancient geographical descriptions)
  - Pliny, *Natural History*
  - Pausanias, *Description of Greece*
  - Archaeological excavation reports

- **Secondary Sources:**
  - Boardman, *The Greeks Overseas* (comprehensive Greek colonization)
  - Braund, *Scythia and the Black Sea*
  - Avram et al., *The Black Sea Region*
  - Ancient Coins journal articles

- **Coordinate Sources:**
  - Published archaeological surveys
  - Modern geographic databases
  - Historic maps and historical-geographic studies

- **Archaeological Evidence:**
  - Early Greek pottery types
  - Numismatic finds
  - Inscriptions and dedications
  - Architectural remains

- **Data Quality Assurance:**
  - Cross-referenced with multiple scholarly sources
  - Coordinates verified against site locations
  - Founding dates based on archaeological consensus
  - Uncertain information marked appropriately

## Data Limitations

- **Dating uncertainty:** Ancient dates approximate ±25-50 years
- **Location precision:** Some sites exactly located, others ~10km uncertainty
- **Missing settlements:** May not include all minor or undiscovered colonies
- **Incomplete data:** Some fields sparse for poorly-documented sites
- **Modern geography:** Uses contemporary borders (not ancient political boundaries)
- **Material culture:** Representative examples only, not exhaustive inventories

## Historical Context

### Greek Colonization and the Black Sea

The Greek colonization of the Black Sea (8th-6th centuries BCE) represented:
- **Economic expansion:** Trade networks for grain, fish, timber
- **Defensive strategy:** Expanding sphere of Greek cultural influence
- **Population outlet:** Relief from land scarcity in Greece
- **Cultural dissemination:** Spread of Greek language, religion, practices
- **Strategic importance:** Control of important sea routes

### The Colonies

Greek colonies on the Black Sea included:
- **Major centers:** Histria, Callatis, Tomis, Dioscurias
- **Trading posts:** Phasis, Sarmatia
- **Settlement types:** Full city-states, trading posts, military outposts

### Historical Significance

- Maintained Greek cultural identity under Scythian, Persian, and later Roman rule
- Centers of trade connecting Mediterranean to Central Asian networks
- Evidence of cross-cultural interaction between Greeks and local populations
- Archaeological sites providing evidence of daily life in colonial environments

## FAIR Data Principles

This dataset implements FAIR principles:

**Findable**
- Descriptive title and metadata
- Unique identifiers for each settlement
- Keywords for geographic and historical searches

**Accessible**
- Open CSV format readable on all platforms
- No special software required
- Available via public repository
- Coordinates in standard WGS84 format

**Interoperable**
- CSV convertible to GeoJSON, JSON, XML
- Geographic coordinates in standard format (EPSG:4326)
- Compatible with GIS software (QGIS, ArcGIS, etc.)
- Links to academic sources and references

**Reusable**
- CC-BY-4.0 open license
- Complete metadata and data dictionary
- Documented methodology and sources
- Suitable for research, teaching, and visualization

## Reusing This Data

You may:
- ✓ Download and analyze the geographic data
- ✓ Create maps and visualizations
- ✓ Incorporate into GIS projects
- ✓ Use for teaching and research
- ✓ Perform spatial analysis

**You must:**
- ✓ Attribute the dataset to Irina
- ✓ Document any modifications
- ✓ Include appropriate attribution

## Citation

**In-text citation:**
> Greek colonies on the Black Sea coast were analyzed using geographic data (Irina, 2025-2026).

**Full citation:**
```
Irina. Greek Colonization on the Black Sea: A Historical-Geographic Dataset.
Foundations of Humanities Data Modeling and Formats Course. 2025-2026.
https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Irina
```

**BibTeX:**
```bibtex
@dataset{irina_greek_colonization_2026,
  title={Greek Colonization on the Black Sea: A Historical-Geographic Dataset},
  author={Irina Koleva},
  year={2026},
  url={https://github.com/Bestroi150/student-projects-showcase/tree/main/projects/Irina},
  license={CC-BY-4.0}
}
```

## Contact & Questions

- **Data Questions:** Open an issue on GitHub
- **Geographic Questions:** See related resources

## License

This dataset is licensed under **Creative Commons Attribution 4.0 International (CC-BY-4.0)**

You are free to share and adapt this material with proper attribution.
For details, see the main [LICENSE](../../LICENSE) file.

## Related Resources

- **GIS Tools:**
  - QGIS (Free, open-source GIS software)
  - Leaflet.js (Interactive web mapping library)
  - Folium (Python GIS mapping)

- **Data Sources:**
  - Pleiades (Ancient geographic data): https://pleiades.stoa.org/
  - Nomisma (Numismatic data): https://nomisma.org/
  - ToposText (Ancient geography): https://topostext.org/

- **Academic Resources:**
  - Boardman, J. *The Greeks Overseas* (4th ed., 2006)
  - Braund, D. *Scythia and the Black Sea* (2005)
  - Tsetskhladze, G. *Phoceans Abroad* (edited collection)

- **Course Materials:**
  - Spatial Data & GIS module
  - Format conversion tutorial
  - Main [Humanities Data Modeling Samples](https://github.com/Bestroi150/humanities-data-modeling-samples) repository

## Interactive Visualization Examples

See the `/visualizations/` folder for pre-built interactive maps showing:
- Colony founding periods (color-coded by century)
- Metropolis relationships (arrows showing founding colonies)
- Material culture distribution
- Trade network representations

## Data Validation Checklist

- [x] All coordinates within valid ranges (Lat: ±90°, Lon: ±180°)
- [x] UTF-8 encoding for all text
- [x] Consistent date formatting
- [x] No duplicate settlement IDs
- [x] Geographic coordinates verified against published sources
- [x] Metropolis names match known Greek city-states
- [x] Historical periods align with scholarly consensus
- [x] Column headers descriptive and consistent
- [x] Compatible with QGIS, ArcGIS, web mapping libraries

---

**Created:** 2025-2026  
**Status:** Complete  
**Version:** 1.0  
**Quality Level:** Research-ready  
**Last Verification:** [Date coordinates and data last verified]
