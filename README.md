# Albay OSM Extract

This repository contains OpenStreetMap (OSM) data for **Albay Province, Philippines**.  
It includes both the polygon boundary file and a pre-extracted `.osm.pbf` dataset, ready for use in routing, rendering, or geospatial analysis.

---

## 📂 Contents

- `Albay.poly` — Polygon file defining the administrative boundary of Albay.  
- `albay.osm.pbf` — OSM extract (PBF format) clipped to the Albay boundary.  
- `scripts/extract_albay.sh` — Shell script to regenerate the extract from the full Philippines dataset.  

---

## 🔧 Usage

You can use these files for:

- 🚗 Routing engines (e.g. [Valhalla](https://valhalla.readthedocs.io), [OSRM](http://project-osrm.org/), [GraphHopper](https://www.graphhopper.com/))  
- 🗺️ Map rendering with tools like [Mapnik](https://mapnik.org/) or [QGIS](https://qgis.org/)  
- 📊 Geospatial analysis or research projects  

---

## 🔄 Regenerating the Albay Extract

If you’d like to reproduce or update the extract yourself, follow these steps:

### Requirements
- [`osmium-tool`](https://osmcode.org/osmium-tool/) installed  
  - Linux: `sudo apt install osmium-tool`  
  - macOS: `brew install osmium-tool`  

### Step 1 — Download the source dataset
Get the latest Philippines OSM extract from Geofabrik:  

```bash
wget https://download.geofabrik.de/asia/philippines-latest.osm.pbf
```

- File: `philippines-latest.osm.pbf`  
- Updated daily (as of 2025-08-18, ~579 MB)  
- More info: [Geofabrik Philippines Download Page](https://download.geofabrik.de/asia/philippines.html)  

### Step 2 — Ensure you have the boundary file
Place `Albay.poly` (included in this repo) in the same directory.  

### Step 3 — Run the extraction script
```bash
bash scripts/extract_albay.sh
```

This will generate `albay.osm.pbf` clipped to the Albay province boundary.  

---

## 📁 Repository Structure

```
albay-osm-extract/
├── Albay.poly
├── albay.osm.pbf
├── README.md
└── scripts/
    └── extract_albay.sh
```

---

## 📜 Source & License

- **OSM Data**: Extracted from [OpenStreetMap](https://www.openstreetmap.org).  
- **License**: © OpenStreetMap contributors, available under the [Open Database License (ODbL)](https://www.openstreetmap.org/copyright).  
- This repository republishes a processed extract for convenience.  

---

## 🏷️ Releases

Each dataset snapshot is tagged and released for reproducibility.  
For example:  
- `v2025-08-18` — Initial release containing Albay boundary and OSM extract.  

You can find releases under the **[Releases section](../../releases)** of this repository.  

---
