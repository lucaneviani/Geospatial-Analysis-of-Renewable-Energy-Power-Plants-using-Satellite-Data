Overview

This project investigates the local economic and environmental impact of utility-scale solar and wind power plants across Africa using satellite imagery and causal inference.

Rather than relying on existing datasets, I designed and built an end-to-end geospatial data pipeline that automatically collected, processed, and integrated satellite observations from multiple sources into a longitudinal georeferenced dataset.

The final dataset was then used to estimate the causal effects of renewable energy infrastructure using state-of-the-art econometric methods.

What I Built

The core contribution of this project is the creation of a custom geospatial panel dataset from multiple heterogeneous data sources.

The workflow included:

Accessing satellite products through NASA and ESA APIs
Downloading multi-year Earth observation data
Extracting satellite statistics around thousands of renewable energy plants
Cleaning and validating raw geospatial datasets
Performing spatial joins and geometric operations
Building a longitudinal georeferenced panel dataset
Running causal impact analysis using modern Difference-in-Differences methods
Data Engineering Pipeline
Renewable Power Plant Database
            │
            ▼
     NASA & ESA APIs
            │
            ▼
 Satellite Data Download
            │
            ▼
 Geospatial Data Cleaning
            │
            ▼
 Spatial Buffer Generation
            │
            ▼
 Satellite Feature Extraction
            │
            ▼
 Spatial Joins & Data Integration
            │
            ▼
 Longitudinal Georeferenced Dataset
            │
            ▼
 Causal Inference Analysis
Dataset Construction

One of the main challenges of this project was building the analytical dataset from scratch.

Using Python, I developed an automated workflow to:

retrieve satellite observations from NASA and ESA products;
clean inconsistent spatial geometries and missing values;
generate multiple buffer zones around renewable power plants;
extract satellite statistics for each location and year;
merge heterogeneous geospatial datasets into a single panel dataset ready for econometric analysis.

The resulting dataset contains over 259,000 observations describing economic activity, vegetation dynamics and land cover changes around renewable energy plants between 2012 and 2024.

Technical Highlights
🌍 Built a custom georeferenced dataset from multiple satellite products
🛰 Integrated Earth observation data from NASA and ESA APIs
🐍 Developed the complete geospatial ETL pipeline in Python
🗺 Performed large-scale spatial analysis with GeoPandas
📊 Constructed a longitudinal panel dataset for causal inference
📈 Applied the Callaway & Sant'Anna Difference-in-Differences estimator
🔬 Produced reproducible geospatial and econometric analyses
Technologies
Data Collection
NASA APIs
ESA datasets
Remote Sensing
Earth Observation
Data Engineering
Python
Pandas
GeoPandas
Rasterio
Shapely
GDAL
NumPy
Data Analysis
R
did (Callaway & Sant'Anna)
Panel Econometrics
Difference-in-Differences
Spatial Econometrics
