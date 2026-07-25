# Data Formats Guide

A comprehensive guide to the data formats used in student projects and how to work with them.

## Overview of Formats

This guide covers the formats used in the student project showcase:

1. **CSV** — Tabular data (comma-separated values)
2. **XML** — Structured markup (eXtensible Markup Language)
3. **JSON** — Modern web format (JavaScript Object Notation)
4. **GeoJSON** — Geographic data format (JSON-based)

## 1. CSV (Comma-Separated Values)

### What is CSV?

CSV is a simple text format for tabular data. Each row represents a record, and columns are separated by commas.

### CSV Structure

```csv
ID,Name,Date,Category
001,Alexander,350 BCE,Ruler
002,Aristotle,384 BCE,Philosopher
003,Cleopatra,69 BCE,Ruler
```

### CSV Characteristics

- **Human-readable:** Can be edited in any text editor
- **Spreadsheet-compatible:** Opens in Excel, Google Sheets, etc.
- **Universal:** Supported by nearly all data tools and programming languages
- **Lightweight:** Small file size relative to data volume
- **Limitations:** Doesn't support nested data or complex hierarchies

### Working with CSV

#### In Spreadsheets

1. Open Excel or Google Sheets
2. File → Open → Select CSV file
3. Choose character encoding (typically UTF-8)
4. Data displays in columns and rows

#### In Python

```python
import pandas as pd

# Read CSV
df = pd.read_csv('data.csv')

# Display info
print(df.head())
print(df.info())

# Filter data
filtered = df[df['Date'] < 2000]

# Save to CSV
df.to_csv('output.csv', index=False)

# Save to other formats
df.to_json('output.json')
df.to_xml('output.xml')
```

#### In Command Line

```bash
# View first 10 lines
head -10 data.csv

# Count rows
wc -l data.csv

# Search for values
grep "keyword" data.csv

# Sort by column (using awk)
awk -F',' '{print $2, $0}' data.csv | sort | cut -d' ' -f2-
```

### CSV Best Practices

✓ Use UTF-8 encoding  
✓ Include header row with column names  
✓ Use consistent delimiter (comma, tab, or semicolon)  
✓ Quote values containing delimiters or newlines  
✓ Avoid leading/trailing spaces in cells  
✓ Use consistent date format (ISO 8601: YYYY-MM-DD)  
✓ Document data dictionary separately  

### CSV Limitations

- No support for hierarchical or nested data
- No standardized type definitions
- Large files can be unwieldy
- Comments require special handling
- No built-in validation

## 2. XML (eXtensible Markup Language)

### What is XML?

XML is a markup language that uses tags to describe data structure and meaning. It's hierarchical and supports complex relationships.

### XML Structure

```xml
<?xml version="1.0" encoding="UTF-8"?>
<root>
  <person>
    <id>001</id>
    <name>Alexander</name>
    <birth_year>356</birth_year>
  </person>
  <person>
    <id>002</id>
    <name>Aristotle</name>
    <birth_year>384</birth_year>
  </person>
</root>
```

### XML Characteristics

- **Self-describing:** Tags indicate meaning
- **Hierarchical:** Supports nested and complex structures
- **Extensible:** You can create custom tags
- **Standardized:** XML standards ensure consistency
- **Verbose:** Larger file sizes than CSV
- **Powerful:** Supports attributes, comments, and namespaces

### Working with XML

#### In Text Editors

1. VS Code (install XML extension)
2. Notepad++
3. Any text editor

**VS Code XML Extension:**
- Syntax highlighting
- Auto-formatting
- Validation against schemas
- XPath queries

#### In Python

```python
from lxml import etree

# Parse XML
tree = etree.parse('data.xml')
root = tree.getroot()

# Access elements
for person in root.findall('person'):
    name = person.find('name').text
    year = person.find('birth_year').text
    print(f"{name}: {year}")

# XPath queries
results = root.xpath("//person[birth_year < 400]")

# Create new XML
new_root = etree.Element('root')
person = etree.SubElement(new_root, 'person')
name = etree.SubElement(person, 'name')
name.text = 'Plato'

# Write to file
tree.write('output.xml', encoding='UTF-8', xml_declaration=True)
```

#### Validation

```python
# Validate against schema
schema_doc = etree.parse('schema.xsd')
schema = etree.XMLSchema(schema_doc)

xml_doc = etree.parse('data.xml')
is_valid = schema.validate(xml_doc)

if not is_valid:
    print(schema.error_log)
```

### TEI XML Specifics

TEI (Text Encoding Initiative) is a standard for humanities text encoding:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<TEI xmlns="http://www.tei-c.org/ns/1.0">
  <teiHeader>
    <fileDesc>
      <titleStmt>
        <title>Inscription Title</title>
      </titleStmt>
    </fileDesc>
  </teiHeader>
  <text>
    <body>
      <div type="inscription">
        <ab>
          <persName>Alexander</persName> dedicated this to 
          <placeName>Athens</placeName>
        </ab>
      </div>
    </body>
  </text>
</TEI>
```

**Key TEI Elements:**
- `<persName>` — Person names
- `<placeName>` — Geographic locations
- `<date>` — Dates and temporal references
- `<supplied>` — Editorial additions
- `<unclear>` — Uncertain readings

### XML Best Practices

✓ Use UTF-8 encoding  
✓ Include XML declaration  
✓ Use meaningful tag names  
✓ Maintain consistent indentation  
✓ Use attributes for simple values  
✓ Use elements for complex values  
✓ Document schema or DTD  
✓ Validate against schema  
✓ Use namespaces for clarity  

## 3. JSON (JavaScript Object Notation)

### What is JSON?

JSON is a lightweight format based on JavaScript object notation. It's widely used for web APIs and modern applications.

### JSON Structure

```json
{
  "people": [
    {
      "id": "001",
      "name": "Alexander",
      "birth_year": 356,
      "accomplishments": ["Conquered Persia", "Founded Alexandria"]
    },
    {
      "id": "002",
      "name": "Aristotle",
      "birth_year": 384,
      "fields": ["Philosophy", "Biology", "Logic"]
    }
  ]
}
```

### JSON Characteristics

- **Lightweight:** Compact syntax
- **Web-friendly:** Native to JavaScript and web APIs
- **Nested:** Supports complex hierarchies
- **Typed:** Supports strings, numbers, booleans, nulls, arrays, objects
- **Human-readable:** Relatively easy to read and edit
- **Wide support:** Parseable in all modern programming languages

### Working with JSON

#### In Python

```python
import json

# Read JSON
with open('data.json', 'r') as f:
    data = json.load(f)

# Access data
for person in data['people']:
    print(f"{person['name']}: {person['birth_year']}")

# Filter data
philosophers = [p for p in data['people'] if 'Philosophy' in p.get('fields', [])]

# Create JSON
output = {
    "people": philosophers,
    "count": len(philosophers)
}

# Write JSON
with open('output.json', 'w') as f:
    json.dump(output, f, indent=2, ensure_ascii=False)
```

#### Using Web Browser

```javascript
// Fetch and parse JSON from URL
fetch('data.json')
  .then(response => response.json())
  .then(data => {
    console.log(data);
    // Use data...
  });
```

### JSON Best Practices

✓ Use UTF-8 encoding  
✓ Use consistent indentation (2 or 4 spaces)  
✓ Use meaningful key names  
✓ Quote all keys (required in valid JSON)  
✓ Use lowercase keys with underscores (snake_case)  
✓ Use null for missing values  
✓ Avoid deeply nested structures  
✓ Include metadata at top level  

### JSON Schema (Optional Validation)

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "people": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "id": {"type": "string"},
          "name": {"type": "string"},
          "birth_year": {"type": "number"}
        },
        "required": ["id", "name"]
      }
    }
  }
}
```

## 4. GeoJSON (Geographic JSON)

### What is GeoJSON?

GeoJSON is a JSON-based format for representing geographic features and coordinates. It's ideal for mapping and spatial data.

### GeoJSON Structure

```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [28.7349, 44.5500]
      },
      "properties": {
        "name": "Histria",
        "founded": "7th century BCE",
        "metropolis": "Miletus"
      }
    }
  ]
}
```

### GeoJSON Geometry Types

- **Point:** Single location
- **LineString:** Connected points (paths, routes)
- **Polygon:** Enclosed areas (regions, territories)
- **MultiPoint:** Multiple locations
- **MultiLineString:** Multiple paths
- **MultiPolygon:** Multiple regions

### Converting to GeoJSON

#### From CSV with Coordinates

```python
import csv
import json

features = []
with open('data.csv', 'r') as f:
    reader = csv.DictReader(f)
    for row in reader:
        feature = {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [float(row['Longitude']), float(row['Latitude'])]
            },
            "properties": {row['Name']: row['Value']}
        }
        features.append(feature)

geojson = {
    "type": "FeatureCollection",
    "features": features
}

with open('data.geojson', 'w') as f:
    json.dump(geojson, f, indent=2)
```

#### From XML

```python
from lxml import etree
import json

tree = etree.parse('data.xml')
root = tree.getroot()
ns = {'geo': 'http://www.example.org/geo'}

features = []
for location in root.xpath('//geo:location', namespaces=ns):
    lat = float(location.xpath('./geo:latitude/text()', namespaces=ns)[0])
    lon = float(location.xpath('./geo:longitude/text()', namespaces=ns)[0])
    name = location.xpath('./geo:name/text()', namespaces=ns)[0]
    
    feature = {
        "type": "Feature",
        "geometry": {"type": "Point", "coordinates": [lon, lat]},
        "properties": {"name": name}
    }
    features.append(feature)

geojson = {"type": "FeatureCollection", "features": features}
with open('output.geojson', 'w') as f:
    json.dump(geojson, f)
```

### Mapping with GeoJSON

#### Using Leaflet.js

```html
<script>
  L.geoJSON('data.geojson').addTo(map);
</script>
```

#### Using Folium (Python)

```python
import folium
import json

# Load GeoJSON
with open('data.geojson', 'r') as f:
    geojson_data = json.load(f)

# Create map
m = folium.Map(location=[45, 28], zoom_start=7)

# Add GeoJSON layer
folium.GeoJson(geojson_data).add_to(m)

# Save
m.save('map.html')
```

### GeoJSON Best Practices

✓ Use WGS84 coordinates (EPSG:4326)  
✓ Order coordinates as [longitude, latitude]  
✓ Use consistent property keys across features  
✓ Include descriptive properties  
✓ Validate against GeoJSON specification  
✓ Use Feature properties for metadata  
✓ Consider file size for large datasets  

## Format Comparison

| Aspect | CSV | XML | JSON | GeoJSON |
|--------|-----|-----|------|---------|
| **Human readable** | ✓ | ✓ | ✓ | ✓ |
| **Hierarchical** | ✗ | ✓ | ✓ | ✓ |
| **Web-friendly** | ~ | ✓ | ✓✓ | ✓✓ |
| **Compact** | ✓✓ | ~ | ✓ | ✓ |
| **Standardized** | ✓ | ✓✓ | ✓ | ✓ |
| **Typed data** | ~ | ✓ | ✓ | ✓ |
| **Geographic** | ~ | ~ | ~ | ✓✓ |
| **Database-ready** | ✓ | ✓ | ✓ | ✓ |

## Conversion Workflows

### CSV → JSON
```python
import pandas as pd
df = pd.read_csv('data.csv')
df.to_json('data.json', orient='records', indent=2)
```

### CSV → XML
```python
import pandas as pd
df = pd.read_csv('data.csv')
df.to_xml('data.xml', root_name='root', row_name='record')
```

### XML → CSV
```python
import pandas as pd
from lxml import etree

tree = etree.parse('data.xml')
root = tree.getroot()

# Extract to list of dicts
data = []
for element in root:
    row = {}
    for child in element:
        row[child.tag] = child.text
    data.append(row)

df = pd.DataFrame(data)
df.to_csv('data.csv', index=False)
```

### JSON → CSV
```python
import pandas as pd
df = pd.read_json('data.json')
df.to_csv('data.csv', index=False)
```

### CSV → GeoJSON (with coordinates)
```python
import csv
import json

features = []
with open('data.csv') as f:
    for row in csv.DictReader(f):
        feature = {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [float(row['lon']), float(row['lat'])]
            },
            "properties": {k: v for k, v in row.items() if k not in ['lat', 'lon']}
        }
        features.append(feature)

with open('data.geojson', 'w') as f:
    json.dump({"type": "FeatureCollection", "features": features}, f)
```

## Validation Tools

- **CSV:** OpenRefine, Frictionless Validator
- **XML:** XMLLint, Oxygen XML, VS Code with XML extension
- **JSON:** JSONLint, JSON Schema validators
- **GeoJSON:** GeoJSON Validator, QGIS

## Further Reading

- [RFC 4180 - CSV Standard](https://tools.ietf.org/html/rfc4180)
- [W3C XML Standards](https://www.w3.org/XML/)
- [JSON.org](https://www.json.org/)
- [GeoJSON Specification](https://tools.ietf.org/html/rfc7946)
- [Frictionless Data Standards](https://frictionlessdata.io/)

---

**Last Updated:** 2026
