Watershed Delineation

A Python package for automatic watershed delineation from a Digital Elevation Model (DEM) and a pour point (longitude & latitude).
The tool uses WhiteboxTools and GeoPandas to perform hydrologic analysis and export watershed shapefiles with attributes.

Installation

Clone or download this repository, then from the parent folder run:

pip install -e ./watershed-delineation


The "-e" flag installs the package in editable mode, so any code changes update immediately without reinstalling.

Dependencies

The package requires the following libraries (installed automatically):

geopandas

rasterio

whitebox-tools

pyproj

numpy

shapely

You’ll also need a DEM raster (GeoTIFF) for your study area.

Usage

From Python

from watershed_delineation.core import delineate_watershed

# Input parameters
dem_path = r"F:\data\dem.tif"
pour_lon = 32.561170
pour_lat = 39.835840
output_dir = r"C:\results"
watershed_name = "my_basin"

# Run delineation
result_path = delineate_watershed(
    dem_path=dem_path,
    pour_lon=pour_lon,
    pour_lat=pour_lat,
    output_dir=output_dir,
    name=watershed_name,
    export_lfp=True   # also export Longest Flow Path
)

print("Watershed shapefile saved at:", result_path)


This creates a shapefile (and optionally a flow path shapefile) in the output folder.

From Command Line

Once installed, you can run:

delineate_watershed "F:\data\dem.tif" 32.561170 39.835840 -o "C:\results" -n "my_basin" --export-lfp


Arguments:

dem_file → Path to DEM raster (.tif)

pour_lon → Longitude of pour point

pour_lat → Latitude of pour point

-o, --output → Output directory (default: current dir)

-n, --name → Base name of shapefile (default: watershed_lon_lat)

--export-lfp → Export Longest Flow Path as shapefile

Output

my_basin.shp → Watershed polygon shapefile with attributes:

Area, perimeter

Longest flow path

Form factor, circularity ratio

Elevation stats

Slope stats

Drainage density

Pour point coordinates

my_basin_lfp.shp → (optional) Longest flow path shapefile

Development

Folder structure:

watershed-delineation/
├── setup.py
├── README.md
└── watershed_delineation/
    ├── __init__.py
    ├── core.py   (core hydrology + delineation functions)
    └── cli.py    (command line interface)


Reinstall after changes:

pip install -e ./watershed-delineation

Author

Developed by FYEC_SKasa
Date: August 2025
