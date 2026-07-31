<div align="center">

<img src="renewable_energy_banner.jpg" alt="Renewable Energy Geospatial Analysis Banner" width="100%"/>

# Geospatial Analysis of Renewable Energy Power Plants in Africa

**Satellite-Based Evaluation of Environmental and Economic Impacts of Solar and Wind Infrastructure**

<br>

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Google Earth Engine](https://img.shields.io/badge/Google%20Earth%20Engine-Cloud%20GIS-34A853?style=for-the-badge&logo=google&logoColor=white)](https://earthengine.google.com/)
[![GeoPandas](https://img.shields.io/badge/GeoPandas-Spatial%20Analysis-139C5A?style=for-the-badge&logo=pandas&logoColor=white)](https://geopandas.org/)
[![R](https://img.shields.io/badge/R-Econometrics-276DC3?style=for-the-badge&logo=r&logoColor=white)](https://www.r-project.org/)


</div>


## Overview
Research project developed in collaboration with the University of Padua, investigates the local economic and environmental impact of utility-scale solar and wind power plants across Africa using satellite imagery and causal inference.

Rather than relying on existing datasets, I designed and built an end-to-end geospatial data pipeline that collected, processed, and integrated satellite observations from multiple sources into a longitudinal georeferenced dataset. 

The final dataset was then used to estimate the causal effects of renewable energy infrastructure using state-of-the-art econometric methods.

## Academic Thesis

This project was developed as part of my Master's thesis in **Economic Data Analytics**.

The complete methodology, datasets, econometric framework, and empirical results are described in the full thesis document:

📄 **[Read the full thesis](Thesis.pdf)**

---

---

## What I Built
The core contribution of this project is the creation of a custom geospatial panel dataset from multiple heterogeneous data sources.

The workflow included:
- **Accessing satellite products** through NASA and ESA APIs
- **Downloading multi-year Earth observation data** (2012–2024)
- **Extracting satellite statistics** around thousands of renewable energy plants
- **Cleaning and validating** raw geospatial datasets and geometries
- **Performing spatial joins** and geometric buffer operations (500m to 20km)
- **Building a longitudinal georeferenced panel dataset** with over 259,000 observations
- **Running causal impact analysis** using modern Difference-in-Differences methods

---

## Data Engineering Pipeline
To process satellite imagery at scale, I built an automated ETL workflow combining Python and Google Earth Engine:

```mermaid
flowchart TD
    A["⚡ Renewable Power Plant Database (RePP Africa: 1,128 Solar, 276 Wind)"] --> B["🛰️ NASA & ESA APIs (VIIRS Nighttime Lights, MODIS NDVI, MCD12Q1)"]
    B --> C["🐍 Satellite Data Download & GEE Processing"]
    C --> D["🗺️ Geospatial Data Cleaning & Geometry Fixes"]
    D --> E["🎯 Spatial Buffer Generation (Concentric rings from 500m to 20km)"]
    E --> F["📐 Counterfactual Donut Sampling (25km–150km control annuli)"]
    F --> G["📊 Satellite Feature Extraction & Zonal Statistics"]
    G --> H["🔗 Spatial Joins & Data Integration (NASADEM terrain & ERA5 climate baselines)"]
    H --> I["📁 Longitudinal Georeferenced Dataset (259,480 panel observations across 3,992 spatial units)"]
    I --> J["📈 Causal Inference Analysis (Doubly Robust Staggered DiD in R)"]
```

---

## Dataset Construction
One of the main challenges of this project was building the analytical dataset from scratch. 

Using Python and Google Earth Engine, I developed an automated workflow to:
- retrieve satellite observations from NASA and ESA products;
- clean inconsistent spatial geometries and missing values;
- generate multiple concentric buffer zones around renewable power plants (500m, 2km, 5km, 10km, 20km);
- extract satellite statistics for each location and year;
- merge heterogeneous geospatial datasets into a single panel dataset ready for econometric analysis.

The resulting dataset contains **over 259,000 observations** describing economic activity, vegetation dynamics, and land cover changes around renewable energy plants between **2012 and 2024**.

---

## Key Empirical Findings
By comparing treated power plant buffers against matched regional control areas, the causal analysis revealed that **solar and wind energy generate completely different environmental and economic footprints**:

```mermaid
graph LR
    subgraph Solar ["☀️ Solar PV Plants"]
        direction TB
        S1["📍 500m Footprint: Vegetation Loss (-86.4 NDVI)"]
        S2["📈 20km Regional Scale: Economic Growth (+0.27 NTL)"]
        S3["⚠️ 20km Regional Scale: Barren Land Increase (+0.90 pp)"]
    end

    subgraph Wind ["💨 Wind Power Plants"]
        direction TB
        W1["💡 All Buffer Scales: No Lighting Spillovers (Zero NTL change)"]
        W2["🌱 20km Regional Scale: Barren Land Reduction (-1.00 pp)"]
        W3["🌿 2km Local Buffer: Vegetation Greening (+1.53 pp)"]
    end
```

### Summary of Results
| Satellite Metric | What It Measures | ☀️ Solar PV Plants | 💨 Wind Power Plants | Simple Takeaway for Recruiters |
| :--- | :--- | :---: | :---: | :--- |
| **VIIRS Nighttime Lights (NTL)** | Local economic activity and electrification | 🟢 **+0.27** <br>*(20km buffer)* | ⚪ **No Effect** <br>*(All scales)* | Solar drives regional commercial and grid growth; Wind benefits likely flow via public revenues rather than local lighting. |
| **MODIS NDVI** | Vegetation health and density | 🔴 **-86.41** <br>*(500m footprint)* | 🟢 **+1.53 pp** <br>*(2km buffer)* | Solar arrays require initial land clearing; Wind farms act as a greening catalyst by restricting overgrazing. |
| **MODIS Land Cover (Barren %)** | Bare soil and land degradation | 🔴 **+0.90 pp** <br>*(20km buffer)* | 🟢 **-1.00 to -1.45 pp** <br>*(All scales)* | **Key Contrast:** Wind acts as a powerful landscape stabilizer in semi-arid areas, while solar requires careful spatial planning. |

---

## Technical Highlights
- 🌍 **Built a custom georeferenced dataset** from multiple satellite products
- 🛰 **Integrated Earth observation data** from NASA and ESA APIs
- 🐍 **Developed the complete geospatial ETL pipeline** in Python
- 🗺 **Performed large-scale spatial analysis** with GeoPandas and Google Earth Engine
- 📊 **Constructed a longitudinal panel dataset** (259,480 observations) for causal inference
- 📈 **Applied the Callaway & Sant'Anna Difference-in-Differences estimator** for staggered adoption
- 🔬 **Produced reproducible geospatial and econometric analyses**

---

## Technologies
- **Data Collection:** NASA APIs, ESA datasets, Remote Sensing, Earth Observation
- **Data Engineering:** Python, Pandas, GeoPandas, Rasterio, Shapely, GDAL, NumPy, Google Earth Engine
- **Data Analysis:** R, did (Callaway & Sant'Anna), Panel Econometrics, Difference-in-Differences, Spatial Econometrics
