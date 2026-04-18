# Territory-susceptibility-mapping
Multi-criteria land susceptibility analysis
#Landslide Susceptibility Mapping – Ritsa National Park, Abkhazia region, Georgia

## Overview
Multi-criteria landslide susceptibility analysis for Ritsa National Park 
(Bzyb river basin, Western Caucasus, South Caucasus region), developed using 
Google Earth Engine (GEE) and validated in QGIS.

This project translates field geomorphological observations and academic 
research into a reproducible, automated remote sensing workflow. 
The study area was investigated during field campaigns in the Caucasus, 
where hazardous geomorphological processes — including landslides, 
rockfalls, and debris flows — pose significant risks to infrastructure 
and tourism.

## Study Area
Ritsa National Park is located in the northwestern part of the southern 
macro-slope of the Main Caucasus Ridge, upper Bzyb river basin.

- Area: 390 km²
- Elevation range: 107 m (Blue Lake) to 3,257 m (Mt. Agapsta)
- Main rivers: Lashipse, Avadkhara, Yupsara, Gega
- Key infrastructure: tourist road to Lake Ritsa (digitized and 
  analyzed as priority protection zone)

## Methodology — Step by Step

### Step 1 — Define Study Area
The study area was defined as a bounding rectangle covering the 
Bzyb river basin using FAO GAUL administrative boundaries as reference.

### Step 2 — Terrain Analysis (SRTM DEM)
A 30m resolution Digital Elevation Model (USGS SRTM) was used to 
derive slope and aspect. Slope threshold of 25° was applied as the 
critical angle for landslide initiation in the Caucasus — consistent 
with field observations of active slope processes in the park.

### Step 3 — Rainfall Trigger Factor (CHIRPS)
Daily rainfall data (CHIRPS) was averaged over 2015–2020 to derive 
mean annual precipitation. A threshold of >2000 mm/year was applied 
as the rainfall trigger factor, consistent with the high-precipitation 
climate zone of the park (up to 2500 mm/year at elevation).

### Step 4 — Land Cover Factor (ESA WorldCover 2021)
Forest cover was used as a stabilizing factor — root cohesion 
significantly reduces slope instability. Pixels classified as forest 
(class 10) were assigned low risk; all other land cover types 
(shrubland, bare soil, grassland) were assigned higher risk.

### Step 5 — Multi-Criteria Susceptibility Index
The three binary masks were combined into a composite susceptibility 
index (0–3) by simple addition:
Each pixel receives a score based on how many risk factors coincide 
simultaneously at that location.

### Step 6 — Infrastructure Risk Assessment
The main tourist road to Lake Ritsa was manually digitized in GEE 
using satellite imagery. A 500m buffer was applied along the road 
to identify priority zones for engineering protection measures.

### Step 7 — Export and Validation
The susceptibility raster was exported as GeoTIFF (30m, EPSG:4326) 
and validated in QGIS against satellite imagery and known 
geomorphological features of the area.

## Results

| Class | Score | Description | Area (pixels) |
|-------|-------|-------------|---------------|
| Low | 0 | No risk factors | ~2.87M |
| Moderate | 1 | One factor present | ~4.92M |
| High | 2 | Two factors coincide | ~1.83M |
| Extreme | 3 | All factors present | included above |

High and extreme risk zones are concentrated along river valleys 
(Lashipse, Avadkhara, Yupsara) and steep valley walls — consistent 
with field observations of active landslides, rockfalls and debris 
flows in the area.

The main road to Lake Ritsa crosses multiple high-susceptibility zones, 
confirming the need for engineering protection measures along the 
tourist corridor.

## Key Findings
The spatial pattern of susceptibility shows a clear altitudinal 
zonation: maximum risk occurs at mid-elevations (800–2000m) where 
steep slopes, high rainfall and reduced forest cover coincide. 
At higher elevations risk decreases as slopes become gentler and 
vegetation transitions to alpine meadows. This pattern is consistent 
with the geomorphological structure of the Caucasus ridge.

## Next Steps
- Addition of lithological factor (Macrostrat geology data) — 
  shales and siliciclastics identified as high-risk lithologies 
  in the study area
- Validation against historical landslide inventory
- Extension of analysis to the broader Bzyb river basin

## Tools & Data
- Google Earth Engine (JavaScript API)
- QGIS 3.x
- USGS SRTM GL1 (30m DEM)
- UCSB CHIRPS Daily Rainfall
- ESA WorldCover v200 2021
- Road geometry digitized in GEE

## Author
AR | GIS & Environmental Specialist  
