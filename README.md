# Seagrass Vegetation and Turbidity Analysis
---
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ssullivan9661/seagrass-analysis/main)

### Authors
[Sara Sullivan](https://github.com/ssullivan9661), [Daniel Smith](https://github.com/ianraymondsmith), and [Omar Alazmi](https://github.com/engomarm03-commits)

## Introduction

Workflow for the Python-based-pipeline analysis of Sentinel-2 and turbidity data with correlation to coastal seagrass dynamics in Upper Keys, FL. The goal is a reproducible workflow for integrating satellite imagery with environmental data to analyze coastal ecosystem health.

### Spectral Indices

| Name | Abbreviation | 
| --- | --- | 
| NDVI | Normalized Difference Vegetation Index | 
| EVI | Enhanced Vegetation Index | 
| NDWI | Normalized Difference Water Index | 
| NDAVI | Normalized Difference Aquatic Index |
| SSI-II | Submerged Seagrass Index |
| NDTI | Normalized Difference Turbidity Index |
| DII | Depth Invariant Index |

## Structure

This cookbook is initially divided into two sections Sentinel-2 imagery and water quality data processing for notebooks 00-03, and then joined for the main analysis in the final 04-06 notebooks. 

### Sentinel-2 Imagery Data Processing

Python code for automated processing of Sentinel-2 raster data, includes the download, access, preprocessing, and calculation of spectral indices using libraries such as Pandas, Xarray, Rioxarray, and Rasterio, contained in notebooks 00-03. Manifest `.csv` files are saved throughout, which are metadata summaries of processed data, with the goal of memory effeciency. 
- `00_Copernicus_Downloading` - contains instructions for downloading Sentinel-2 data for a range of years, and code for converting shapefile polygon dimensions to preferred JSON format for defining an AOI in the [Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu/) search engine.
- `01_access_data` - contains a working code to unzip, convert file type jp2 -> tif, and save scene by scene as netCDF, and delete from memory to prevent memory or RAM issues on any device. Outputs a manifest records of each scenes `.nc` is also saved as CSV.
- `02_preprocess_imagery` - Clips scenes to the area of interest shapefile and masks cloud cover for L2A scenes to save as `.nc` per scene and manifest record of clipped/masked scenes.
- `03_calculate_indices` - Calculate spectral vegetation indices - NDVI, NDWI, NDAVI, EVI, SSSII, NDTI, and DII - and also incorporates a correction for water column depth calculating DII or the Depth Invariant Index. Outputs a `indice_summary.csv` of calculated indices.

### Water Quality Data Processing

Automated water quality data pipeline to prepare, analyze, and relate parameters to Sentinel-2 satellite imagery for better understanding of seagrass dynamics over the study period 2015-2024, contained in the 04 notebooks.
- `04_water_quality_data_preparation.ipynb` - Queries and cleans water quality data to focus on the parameters of interest; Turbidity, Temperature, Secchi Depth and Chlorophyll-a within the bounding box of the study area, the Upper Keys, Fl. Pivots the raw data into a usable format to then build as GeoDataFrame and outputs a paraquet file of valid historical water quality records.


### Combined Analysis Features

The main analysis workflow integrates and joins the spectral vegetation indices and water quality data, in notebooks `05` - `07`. Using various Python modules and libraries for data statistics, visualization, time-series, and spatial mapping to uncover patterns and trends of seagrass, from sentinel-2 data and water quality data, or measures of ecosystem viability. With automated save and outputs of notable figures in the `figures` folder.

- `05_water_quality` - Main water quality Python based statistical analysis includes both spatial and seasonal distributions of water quality parameters using statistical Python based modules and `matplotlib`. Methods of plotting include correlation matrices, seasonal boxplots, and spatial mean maps.
- `06_time_series_analysis` - Time series analysis and correlation heat mapping of Sentinel-2 data and water quality data ussing the Mann-Kendall test for long term trends of seagrass trends. Incorporates a dual time series and cross correlation heatmap of both water quality data and spectral indices.
- `07_spatial_analysis` - Statistical spatial analysis of spectral indices includes, model validating correlataion heat map of spectral indices and an annuall seasonal comparison of NDVI vs. NDAVI vs. SSSII. Followed by the visual spatial analysis of spectral indices with turbidity to detect patterns and confirm relationships, through a 9-map-subplot and base-map function using modules `Rasterio` and  `Cartopy`. Followed by an animation analysis of seagrass dynamics with NDAVI overtime to discover any trend relationships. 

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
