---
layout: page
title: Endangered Species Suitability Modeling
permalink: /thesis/
---

# Endangered Species Suitability Modeling

**Master of Science thesis developed for California State University Long Beach in partnership with the Huntington Library**

This model uses Machine Learning to identify areas of high suitability for endangered species. Everything is written in R and is built to be run in RStudio.

[View full readme](https://gist.github.com/jackjohnson18/fe0d60855d3c2133f2d4883c3fb9a299) · [View thesis manuscript](LINK) · [View Interactive Storymap](https://storymaps.arcgis.com/stories/d660dff3202d40dfa0e34ab9efdcfd9b) · [View our poster submission for the Esri UC](https://mapgallery.esri.com/event/69209f990d5f072ce16a7d51/submission-detail/43082)

---

## Featured Map



![Featured suitability map](https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/finalcurrent1.png)

The final suitability map of our case study species

---

## Project Overview

This R script takes raw ecological data and uses it to train a Random Forest model. The Random Forest creates decision trees based on occurrence and pseudo-absence data. Each cell throughout the country is then given a score from 0-1 based on predicted suitability. The trained model can be rerun on future climate prediction data to examine how the suitable area might shift in the following years to come.

---

## Research Objective

This code is being handed over to the Huntington Library, where they will partner with the Center for Plant Conservation. These two organizations will cross-reference occurrence data to determine the locations of many more species throughout the globe.

---

## Study Area

All three of our case studies took place in Mexico, particularly Hidalgo, Baja California, and Sinaloa. 15 of the 18 species on the list we were given were in Mexico.

![Study area map](https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/Screenshot%202026-08-06%20013649.png)

---

## Data Sources

|Source|Link|Usage|
|---|---|---|
|Global Biodiversity Information Facility|![GBIF](https://www.gbif.org/)|Species Occurance Data|
|Shuttle Topography Radar Mission|![SRTM](https://www.earthdata.nasa.gov/data/instruments/srtm)|Elevation and Topography Derivitives|

---

## Data Preparation

[Explain how the datasets were projected, aligned, resampled, clipped, checked, and standardized.]

![Environmental predictor examples](/assets/images/thesis/predictor-layers.png)

---

## Environmental Predictors

[List and explain the final predictor variables used in the model.]

---

## Modeling Workflow

[Describe the complete workflow from occurrence records to the final suitability maps.]

![Modeling workflow diagram](/assets/images/thesis/modeling-workflow.png)

---

## Background Point Generation

[Explain how background points were created and why they were needed.]

---

## Random Forest Model

[Explain how the model was trained, how the data were split, and how the model produced suitability probabilities.]

![Random Forest decision tree](/assets/images/thesis/random-forest-tree.png)

---

## Model Evaluation

[Explain how the model was evaluated.]

### Evaluation Metrics

[Add accuracy, recall, specificity, Kappa, confusion-matrix results, or other metrics.]

![Confusion matrix](/assets/images/thesis/confusion-matrix.png)

---

## Suitability Threshold

[Explain how the threshold was selected and how it converted probability values into suitable and unsuitable areas.]

---

## Variable Importance

[Explain which variables were most influential and what that means.]

![Variable importance chart](/assets/images/thesis/variable-importance.png)

---

## Current Habitat Suitability

[Describe the current-condition model results.]

![Current suitability map](/assets/images/thesis/current-suitability.png)

### Current Results

[Add suitable area, occurrence points captured, major geographic patterns, and other key values.]

---

## Future Habitat Suitability

[Describe how future climate data were used.]

![Future suitability map](/assets/images/thesis/future-suitability.png)

### Future Results

[Add future suitable area, occurrence points captured, and major geographic patterns.]

---

## Current and Future Comparison

[Explain the major differences between current and future suitability.]

![Current and future comparison map](/assets/images/thesis/current-future-comparison.png)

### Change in Suitable Area

[Add the total area change and percent change.]

### Geographic Patterns of Change

[Describe where suitability increased, decreased, remained stable, or shifted.]

---

## Key Findings

[Summarize the most important findings in a few short paragraphs.]

---

## Uncertainty and Limitations

[Discuss occurrence-data uncertainty, sampling bias, future climate uncertainty, model limitations, and the difference between suitability and confirmed presence.]

---

## Conservation Applications

[Explain how the results could support field surveys, monitoring, conservation planning, botanical collections, or future research.]

---

## Final Deliverables

### Thesis and Documentation

- [Full Thesis PDF](LINK)
- [Thesis Presentation](LINK)
- [Research Poster](LINK)

### Code

- [Project Repository](LINK)
- [Data Preparation Code](LINK)
- [Random Forest Code](LINK)
- [Future Projection Code](LINK)

### Maps and Results

- [Current Suitability Map](LINK)
- [Future Suitability Map](LINK)
- [Comparison Map](LINK)
- [Model Evaluation Results](LINK)
- [Variable Importance Results](LINK)

### Interactive Products

- [Interactive Map](LINK)
- [ArcGIS Application](LINK)

---

## Skills Demonstrated

[Add the main technical, analytical, research, and cartographic skills demonstrated by the project.]

---

## Software and Technologies

[Add the software, programming languages, packages, and platforms used.]

---

[Return to Portfolio Home](/)
