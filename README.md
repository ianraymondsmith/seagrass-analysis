# Seagrass Vegetation and Turbidity Analysis
---
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ssullivan9661/seagrass-analysis/main)

### Authors
[Sara Sullivan](https://github.com/ssullivan9661), [Daniel Smith](https://github.com/ianraymondsmith), and [Omar Alazmi](https://github.com/engomarm03-commits)

## Introduction

Workflow for the Python-based-pipeline analysis of Sentinel-2 and turbidity data with correlation to coastal seagrass dynamics in Upper Keys, FL. The goal is a reproducible workflow for integrating satellite imagery with environmental data to analyze coastal ecosystem health.

## Structure

This cookbook is initially divided into two sections Sentinel-2 imagery and water quality data processing for notebooks 00-03, and then joined for the main analysis in the final 04-06 notebooks. 

### Sentinel-2 Imagery Data Processing

Python code for automated processing of Sentinel-2 raster data, includes the download, access, preprocessing, and calculation of spectral indices using libraries such as Pandas, Xarray, Rioxarray, and Rasterio, contained in notebooks 00a, 01a, 02a, and 03a. Manifest `.csv` files are saved throughout, which are metadata summaries of processed data, with the goal of memory effeciency. 
- `00_Copernicus_Downloading` - contains instructions for downloading Sentinel-2 data for a range of years, and code for converting shapefile polygon dimensions to preferred JSON format for defining an AOI in the [!Copernicus Data Space Ecosystem]() search engine.
- `01_access_data` - contains a working code to unzip, convert file type jp2 -> tif, and save scene by scene as netCDF, and delete from memory to prevent memory or RAM issues on any device. A manifest records of each scenes `.nc` is also saved as CSV.
- `02a_preprocess_imagery` - Clips scenes to the area of interest shapefile and masks cloud cover for L2A scenes to save as `.nc` per scene and manifest record of clipped/masked scenes.
- `03a_calculate_indices` - Calculate spectral vegetation indices - NDVI, NDWI, NDAVI, EVI, SSSII, and NDTI - and also incorporates a correction for water column depth calculating DII or the Depth Invariant Index.

### Water Quality Data Processing

Automated water quality data processing with GeoPandas, NumPy, Matplotlib, and clipping to the study area using Rasterio, and Rioxarray.

# Combined Analysis Features

The main analysis workflow integrates and joins the spectral vegetation indices and water quality data, to spatially map the processed data together for visualization of patterns and relationships, analysis of seagrass dynamics with varying water quality overtime to discover any trend relationships, and correlataion heat mapping of NDTI and water turbidity data. With automated save and export and notable figures in the `figures` folder. 
- `04_spatial_mapping` - Spatial mapping of spectral indices with water quality parameters to detect patterns and relationships.
- `05_time_series_analysis` - Time series analysis and correlation heat mapping of Sentinel-2 data and water quality data.
- `06_turbidity_correlation_analysis` - Heat mapping and correlation analysis of NDTI and water turbidity data.


# Binder Setup
Follow this workflow to run binder locally:

1. Clone the `https://github.com/ssullivan9661/seagrass-analysis` repository:

   ```bash
    git clone https://github.com/ssullivan9661/seagrass-analysis.git
   ```

2. Move into the `seagrass-analysis` directory
   ```bash
   cd seagrass-analysis
   ```
3. Create and activate your conda environment from the `environment.yml` file
   ```bash
   conda env create -f environment.yml
   conda activate seagrass-analysis
   ```
4. Move into the `notebooks` directory and start up Jupyterlab
   ```bash
   cd notebooks/
   jupyter lab
   ```
