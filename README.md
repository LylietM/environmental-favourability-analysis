# Environmental Favourability analysis in protected areas

## Overview

This project uses Python and geospatial data to calculate the percentage of the total surface of protected-area datasets occupied by different environmental favourability classes.

The workflow applies spatial overlay operations to intersect protected-area polygons with an environmental favourability layer, calculates the area associated with each class, and estimates its percentage relative to the total area of each protected-area dataset.

The analysis is designed for environmental applications involving protected areas and spatial favourability data.

## Objectives

- Quantify the surface area associated with each environmental favourability class within protected-area datasets.
- Calculate the percentage of total protected-area surface represented by each class.
- Apply a reusable workflow to two different protected-area datasets.

## Methodology

The workflow consists of the following steps:

1. Load the environmental favourability and protected-area vector layers.
2. Select the four environmental favourability classes included in the analysis.
3. Intersect each protected-area dataset with the selected favourability polygons.
4. Calculate the area of the resulting intersection geometries.
5. Sum the intersected area associated with each favourability class.
6. Calculate the percentage of total protected-area surface represented by each class.
7. Display the results for each protected-area dataset.

## Input Data

The script requires three polygon shapefiles:

- An environmental favourability layer containing a `Fav_clas` attribute.
- A Natura 2000 protected-area dataset.
- A second protected-area dataset.

The favourability attribute must contain the following categories:

- High
- Upper-intermediate
- Lower-intermediate
- Low

The input filenames and paths are defined in the Python script.

**Data availability:** Input datasets are not included in this repository. Users must provide their own datasets and ensure they have the necessary rights to use and process them.

## Requirements

- Python
- GeoPandas
- pandas

## Data Validation and Preparation

Before performing the spatial analysis, the script checks that the input files exist and loads the three vector layers. It then inspects their attribute fields and coordinate reference systems (CRS), and displays sample records to facilitate an initial review of the data structure.

All three layers use EPSG:25830, so no coordinate reprojection is required before calculating areas. The favourability layer is subsequently filtered to retain the four classes included in the analysis.

## Results

The script prints the percentage of total area associated with each of the four favourability classes for both protected-area datasets.

Percentages are rounded to two decimal places.

The calculations use the sum of polygon areas in each protected-area dataset as the denominator. They therefore represent dataset-level percentages, not separate percentages for each individual protected area.


## Limitations

The results depend on the spatial accuracy, coverage and classification of the input data.

The analysis assumes that the favourability classes provide an appropriate spatial representation for calculating area proportions. Gaps in the favourability layer may leave portions of the protected-area surface unclassified. Overlapping geometries may lead to duplicated area calculations.

## Reproducibility

To run the analysis:

1. Install the required Python packages.
2. Place the three input shapefiles in the project directory, or update the paths in the script.
3. Ensure that the favourability layer contains the required `Fav_clas` attribute.
4. Run the Python script.
5. Review the percentages printed for both protected-area datasets.

## Efficiency and Practical Value

This workflow automates a geospatial analysis that would otherwise require several manual operations in a GIS environment. In a real application, the script completed the calculation in 11 minutes and 46 seconds, compared with an estimated 40 minutes or more for a manual workflow.

Using the 40-minute estimate as a conservative baseline, automation reduces processing time by at least 70.6%, saving approximately 28 minutes per execution. Beyond time savings, the script provides a reusable and consistent workflow for calculating the distribution of environmental favourability classes across protected-area datasets.

## Author

Lidia Sánchez
