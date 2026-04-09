# Seagrass Vegetation and Turbidity Analysis
---
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ssullivan9661/seagrass-analysis/main)

## Authors
[Sara Sullivan](https://github.com/ssullivan9661), [Daniel Smith](https://github.com/ianraymondsmith), and [Omar Alazmi](https://github.com/engomarm03-commits)

Workflow for the Python-based-pipeline analysis of Sentinel-2 and turbidity data with correlation to coastal seagrass dynamics in Upper Keys, FL.
# Features
---
- Python code for automated conversion, cloud-masking, and clipping of satiellite raster data files using libraries such as Xarray, Rasterio and Rioxarray.
- Automated water quality data processing with GeoPandas, NumPy, Matplotlib, and clipping to the study area using Rasterio, and Rioxarray.
- Calculation of spectral and turbidity indexes using extracted band information of sentinel-2 scenes.
- Spatial mapping of NDVI, NDWI, EVI and Turbidity overlayed with water quality parameters.
- Time series analysis and correlation heat mapping of Sentinel-2 data and water quality data.
- Automated export and save of results.
  
  Ultimately, the goal is a reproducible workflow for integrating satellite imagery with environmental data to analyze coastal ecosystem health.
