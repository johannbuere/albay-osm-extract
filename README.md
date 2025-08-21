# Albay OSM Extract

This repository contains OpenStreetMap (OSM) data for **Albay Province, Philippines**.  
It includes both the polygon boundary file and a pre-extracted `.osm.pbf` dataset, ready for use in routing, rendering, or geospatial analysis.

---

## 📂 Contents

- `Albay.poly` — Polygon file defining the administrative boundary of Albay.  
- `albay.osm.pbf` — OSM extract (PBF format) clipped to the Albay boundary.  

---

## 🔧 Usage

You can use these files for:

- 🚗 Routing engines (e.g. [Valhalla](https://valhalla.readthedocs.io), [OSRM](http://project-osrm.org/), [GraphHopper](https://www.graphhopper.com/))  
- 🗺️ Map rendering with tools like [Mapnik](https://mapnik.org/) or [QGIS](https://qgis.org/)  
- 📊 Geospatial analysis or research projects  

---

## 🔄 Regenerating the Albay Extract

This guide explains how to reproduce or update the **Albay OSM extract**
for use with Valhalla or other tools.

------------------------------------------------------------------------

## Step 1 --- Download the source dataset

Get the latest Philippines OSM extract from Geofabrik:

``` bash
wget https://download.geofabrik.de/asia/philippines-latest.osm.pbf
```

-   File: `philippines-latest.osm.pbf`\
-   Updated daily (as of 2025-08-18, \~579 MB)\
-   More info: [Geofabrik Philippines Download
    Page](https://download.geofabrik.de/asia/philippines.html)

------------------------------------------------------------------------

## Step 2 --- Ensure you have the boundary file

Place `Albay.poly` (included in this repo) in the same directory.\

------------------------------------------------------------------------

## Step 3 --- Extract Albay data using the boundary file

With the full Philippines dataset (`philippines-latest.osm.pbf`) and the
`Albay.poly` boundary file, run:

``` bash
osmium extract -p Albay.poly philippines-latest.osm.pbf -o albay-latest.osm.pbf
```

-   `-p Albay.poly` → specifies the polygon boundary for Albay\
-   `philippines-latest.osm.pbf` → the source dataset\
-   `-o albay-latest.osm.pbf` → output file containing only Albay

Result:\
- `albay-latest.osm.pbf` (\~6--7 MB) with only Albay's OSM data

------------------------------------------------------------------------

## Step 4 --- Verify the extract

Check the metadata of the new file:

``` bash
osmium fileinfo albay-latest.osm.pbf
```

Look for:\
- `Bounding box` → should match Albay's approximate lat/lon range\
- `Size` → much smaller than the full Philippines extract

------------------------------------------------------------------------

## Step 5 --- Use with Valhalla (or other tools)

Copy `albay-latest.osm.pbf` into your Valhalla data directory, e.g.:

``` bash
cp albay-latest.osm.pbf /path/to/custom_files/
```

Then restart your Valhalla container:

``` bash
docker restart valhalla
```

Valhalla will rebuild tiles based on the new Albay extract.

---

## 📜 Source & License

- **OSM Data**: Extracted from [OpenStreetMap](https://www.openstreetmap.org).  
- **License**: © OpenStreetMap contributors, available under the [Open Database License (ODbL)](https://www.openstreetmap.org/copyright).  
- This repository republishes a processed extract for convenience.  

---


