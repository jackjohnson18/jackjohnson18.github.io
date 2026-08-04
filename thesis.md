---
layout: page
title: Endangered Species Suitability Modeling
permalink: /thesis/
---

# Endangered Species Suitability Modeling

**Master of Science thesis project developed for The Huntington Library, Art Museum, and Botanical Gardens**

This project developed a reproducible spatial modeling workflow to predict endangered plant habitat suitability across Mexico. The model used known species-occurrence locations and environmental predictor variables to identify areas with conditions similar to the taxon’s known habitat.

## Project Purpose

The purpose of this research was to create a repeatable habitat-suitability modeling workflow that could be used to examine current suitable habitat and explore how that suitability may change under future climate conditions.

## Data

The project combined biological, climate, terrain, soil, and anthropogenic datasets.

- Species occurrence records from GBIF
- Elevation data from SRTM
- Slope and aspect derived from elevation
- Temperature and precipitation data from WorldClim
- Soil data from INEGI
- Anthropogenic and landscape data from OpenStreetMap

Because these datasets came from different sources, a major part of the project involved checking and correcting coordinate systems, resolution, extent, raster alignment, NoData values, and variable consistency.

## Modeling Workflow

The workflow included:

1. Cleaning and preparing occurrence records
2. Processing environmental predictor layers
3. Aligning all rasters to a common grid
4. Deriving terrain and seasonal climate variables
5. Extracting predictor values at known occurrence points
6. Generating background points
7. Training and evaluating a Random Forest model
8. Creating a continuous suitability probability raster
9. Applying a threshold to create a binary suitability map
10. Comparing current and future suitability conditions

## Tools

- R and RStudio
- Python
- Google Colab
- Google Earth Engine
- Random Forest
- MaxEnt
- ArcGIS Pro
- Raster and vector processing
- Cartographic design

## Outputs

The project produced:

- A 30-meter suitability probability raster
- A binary suitability map
- Model evaluation metrics
- Variable-importance results
- An environmental predictor stack
- Current and future suitability comparisons
- Final maps and research documentation

## Key Result

The model identified areas with environmental conditions similar to those found at the known occurrence locations. These predicted areas do not prove that the species is present, but they can help identify locations for further field investigation, conservation planning, or habitat monitoring.

## Skills Demonstrated

Machine learning, species distribution modeling, habitat suitability analysis, raster alignment, environmental predictor development, Random Forest, MaxEnt, climate-data processing, terrain analysis, cartographic design, and reproducible research.

## Project Links

Links to the thesis documentation, literature review, Esri User Conference poster, and StoryMap will be added here.
