---
layout: page
title: Endangered Species Suitability Modeling
permalink: /thesis/
---

**Master of Science thesis developed for California State University Long Beach in partnership with the Huntington Library**

This model uses Machine Learning to identify areas of high suitability for endangered species. Everything is written in R and is built to be run in RStudio.

[View full readme](https://gist.github.com/jackjohnson18/fe0d60855d3c2133f2d4883c3fb9a299) · [View thesis manuscript](LINK) · [View Interactive Storymap](https://storymaps.arcgis.com/stories/d660dff3202d40dfa0e34ab9efdcfd9b) · [View our poster for the Esri UC](https://mapgallery.esri.com/event/69209f990d5f072ce16a7d51/submission-detail/43082)

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
|Global Biodiversity Information Facility|[GBIF](https://www.gbif.org/)|Species Occurance Data|
|Shuttle Topography Radar Mission|[SRTM](https://www.earthdata.nasa.gov/data/instruments/srtm)|Elevation and Topography Derivitives|
|WorldClim|[WorldClim](https://www.worldclim.org/)|Monthly meteorological data|
|National Institute of Statistics and Geography|[INEGI](https://en.www.inegi.org.mx/)|Qualitative soil data|
|OpenStreetMap|[OpenStreetMap](https://www.openstreetmap.org)|Human presence data|

---

## Data examples


| Occurance points | Elevation | Climate | Soil |
| :---: | :---: | :---: | :---: |
| <img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/justpoints.png" width="220" alt="points"> | <img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/elevation.png" width="220" alt="elevation"> | <img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/rain.png" width="220" alt="rain"> | <img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/soil.png" width="220" alt="soil"> |


---

## Environmental Predictors

Our literature review found that the most important meteorological data to include are the precipitation of the wettest and driest months as well as the average temperature of the three hottest and coldest months. The three-month periods are averaged out and subtracted for a derived variable called Seasonal Temperature Delta. Elevation is used in the model as a predictor; it is also used to derive slope and aspect. Aspect is further divided into sine and cosine to make them linear. Soil is also used as a qualitative predictor. Any two predictors that have a collinearity score outside of -0.8 to 0.8 are dropped. This helps improve processing time, reduce redundancy, and help stabilize predictor weights.

---

## Modeling Workflow

![Modeling workflow diagram](https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/suitabilityworkflow.png)

---

## Background Point Generation

Randomized background points are spread across the AOI to simulate absence areas. Imagine you surveyed a 30x30 meter area and found none of this plant. That is what these points do: make it so we don't have to physically go there.

![background points](https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/absenceclose.png)

---

## Random Forest Model

The model is initially trained on a 70/30 split. 70 percent of the occurrence and absence points are combined into training data; the remaining 30 percent are testing data. The 70 percent create decision trees based on the data, and then the trees are tested on the training data. After this is run, the model is retrained, where all occurrence and absence data are combined to make new decision trees. Every single tile in our AOI is then given a value between 0 and 1 for how it did on each decision tree. All of the scores are added up for each tile and averaged out to get the final suitability map.

![Random Forest decision tree](https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/random_forest_tree_transparent.png)

---

## Model Evaluation

The first evaluation metric is our confusion matrix. A confusion matrix is a chart depicting how well our training data trees worked on our testing data. Below are the confusion matrices for each of our three case studies. We used a p10 suitability threshold. This means that the bottom 10 percent of points in terms of suitability are cut for the threshold. This helps tighten up our threshold as well as eliminate biases from outliers.

|Observed value|Threshold|True positive|True negative|False positive|False negative|
|---|---|---|---|---|---|
|Species 1 Training|0.544411|60|6549|0|7|
|Species 1 Testing|0.544411|15|2807|0|14|
|Species 2 Training|0.568865|84|6546|1|10|
|Species 2 Testing|0.568865|28|2803|3|13|
|Species 3 Training|0.712693|261|6549|0|29|
|Species 3 Testing|0.712693|102|2793|14|23|

### Evaluation Metrics

|Dataset|Accuracy|Recall|Specificity|Precision|F1 score|Balanced accuracy|Kappa|
|---|---|---|---|---|---|---|---|
|Species 1|99.51|51.72|100|100|68.18|75.86|0.680|
|Species 2|99.44|68.29|99.89|90.32|77.78|84.09|0.775|
|Species 3|98.74|81.60|99.50|87.93|84.65|90.55|0.840|
|Average|99.23|67.21|99.80|92.75|76.87|83.50|0.765|

---

### Results

|Taxa|Current suitability|Future uitability|
|---|---|---|
|Cephalocereus senilis (Haw.) Pfeiff.|<img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/finalcurrent1.png" width="300" alt="finalcurrent1">|<img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/finalfuture1.png" width="300" alt="finalfuture1">|
|Fouquieria burragei rose|<img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/finalcurrent2.png" width="300" alt="finalcurrent2">|<img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/finalfuture2.png" width="300" alt="finalfuture2">|
|Stenocereus martinezii (J.G.Ortega) Buxb.|<img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/Layoutcur.png" width="300" alt="Layoutcur">|<img src="https://raw.githubusercontent.com/jackjohnson18/jackjohnson18/refs/heads/main/Layoutfut.png" width="300" alt="Layoutfut">|

---


## Current and Future Comparison

|Species|Time period|Suitable land area km2|Points inside suitable area|
|---|---|---|---|
|Cephalocereus senilis (Haw.) Pfeiff.|Current|839|86|
|Cephalocereus senilis (Haw.) Pfeiff.|2040-2060|1264|9|
|Fouquieria burragei rose|Current|1004|121|
|Fouquieria burragei rose|2040-2060|530|7|
|Stenocereus martinezii (J.G.Ortega) Buxb.|Current|7876|373|
|Stenocereus martinezii (J.G.Ortega) Buxb.|2040-2060|159|0|

---

## Key Findings

The three species that we covered experienced predicted shifts in their habitats. Some of the habitats' total suitable area expanded, and some shrank. The more important metric is points inside the suitable area. As seen in the maps above, the current ecosystem is expected to go through drastic changes over the next quarter century. Plants are not as mobile as humans, so their only chance at survival would be adaptation. Another thing to note is that these are dry desert plants that are suited for hot arid climates. If the species that thrive in deserts are predicted to die out, the species that require cooler climates are under an even bigger threat.

---

## Uncertainty and Limitations

Uncertainty in a prediction-based science has to be considered. While the areal groupings for these plants are more or less correct, our data source includes a 30km offset radius to protect against poachers. This doesn't change much for climate variables, but things such as soil, slope, aspect, and elevation could be impacted.

Machine learning is also filled with uncertainty. Considering the model we used, we made constraints on how suitability is predicted as a way to mitigate the amount of false negatives. Having small areas of near-perfect suitability is more valuable than a quarter of the country being deemed suitable since the next steps might require fieldwork.

Lastly, climate change is another uncertainty. WorldClim has hundreds of future prediction datasets for multiple climate scenarios. This is just one dataset for one scenario.

---

## Conservation Applications

The Huntington Library is working with the Center for Plant Conservation. The CPC is working towards getting a bunch of botanical gardens together to share taxon locations and create an endangered species database to use for models like this one.
