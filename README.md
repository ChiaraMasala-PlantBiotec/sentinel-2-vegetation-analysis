# Sentinel-2 Vegetation Analysis

## Overview
This project analyzes multispectral satellite imagery from Sentinel-2 in raster format using Python. The objective of the analysis is to calculate and visualize the Normalized Difference Vegetation Index (NDVI) to explore the spatial distribution of the index values.
The project was developed as a practical exercise to apply Python to basic remote sensing and geospatial data analysis.

## Objectives
- Inspect raster properties and metadata.
- Visualize a natural-color composite.
- Visualize the near-infrared (NIR) band.
- Calculate the Normalized Difference Vegetation Index (NDVI).
- Visualize the NDVI map.
- Analyze the distribution of NDVI values using a histogram.
- Calculate the summary statistics: minimum, maximum, and mean.
- Export the NDVI map and the summary statistics table.

## Dataset
The analysis uses a small Sentinel-2 raster dataset stored in GeoTIFF format (https://zenodo.org/records/21917533). 
The raster contains multispectral bands used for visualization and vegetation index calculations.
- Raster band 1: blue band
- Raster band 2: green band
- Raster band 3: red band
- Raster band 4: near-infrared (NIR) band

The input file is expected at data/sentinel-2_small.tif

## Methodology
1. **Raster Data Inspection**
The raster is opened with Rasterio to inspect its dimensions, number of bands, Coordinate Reference System (CRS), spatial resolution, and data types.
2. **Band Descriptions and Metadata**
The raster's band descriptions, tags and profile are examined to better understand its structure and properties.
3. **Natural-Color Composite**
The blue, green, and red bands are combined to create a natural-color visualization. A percentile stretch (2nd-98th percentiles) is applied to improve image contrast.
4. **Near-Infrared Visualization**
The near-infrared band is displayed in grayscale to explore its spatial variation.
5. **NDVI Calculation**
The Normalized Difference Vegetation Index is calculated using the red and near-infrared bands:
`NDVI = (NIR - RED) / (NIR + RED)`
Division by zero is handled by assigning NaN to pixels where the denominator is zero.
6. **NDVI Visualization**
The calculated NDVI values are displayed as a thematic map using a red-yellow-green color scale, with the visualization range set from -1 to 1.
7. **NDVI Distribution**
A histogram is generated to examine the distribution of valid NDVI values across the raster.
8. **Summary Statistics**
The minimum, maximum, and mean NDVI values are calculated and organized into a summary table.
9. **Export Results**
The analysis produces two output files:
- ndvi_map.png - an exported NDVI map.
- ndvi_summary.csv - a CSV table containing the minimum, maximum, and mean NDVI values.

## Technologies Used
- Python
- **Rasterio** — raster data access and metadata inspection.
- **NumPy** — numerical calculations and array manipulation.
- **Matplotlib** — raster visualization and histogram generation.
- **Pandas** — tabular data organization and CSV export.

## Project Structure
```text
sentinel-2-vegetation-analysis/
├── data/
│   └── sentinel-2_small.tif
├── outputs/
│   ├── ndvi_map.png
│   └── ndvi_summary.csv
├── Zenodo.ipynb
└── README.md
```

The notebook saves the exported files in the `outputs/` directory.

## How to Run
1. Clone or download the repository.
2. Ensure that Python and the required libraries are installed.
3. Place the input raster at data/sentinel-2_small.tif.
4. Open Zenodo.ipynb in Jupyter Notebook or JupyterLab.
5. Run the notebook cells in order.
6. Install the required libraries with:
```bash
pip install rasterio numpy matplotlib pandas
```

## Scope and Limitations
This project focuses on introductory remote sensing workflows and raster analysis. The visualizations and statistics describe the NDVI values in the selected raster and are intended for learning and exploration.

The analysis does not include atmospheric correction, time-series analysis, or a comprehensive agronomic interpretation of vegetation conditions.

## Author
Developed as a personal learning project in remote sensing, Python, and geospatial data analysis.