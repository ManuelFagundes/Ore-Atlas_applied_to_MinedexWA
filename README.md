# $\text{Ore-Atlas\_applied\_to\_MinedexWA}$ 

## Overview: $\text{Ore-Atlas\ (Topological\ Mining\ Analysis\ V1.0)}$

This repository houses the **$\text{Ore-Atlas}$ pipeline**, an analytical tool leveraging **Topological Data Analysis ($\text{TDA}$)**, specifically the **Mapper algorithm** (ToposMapper methodology), to discern hidden spatial and operational structures within the **Minedex Western Australia ($\text{WA}$)** dataset.

The primary goal is to transcend conventional $\text{EDA}$ by mathematically modeling the **shape** of the mining data. This reveals non-linear clusters, operational dependencies, and prospective exploration targets based on the data's **topology**, employing a lens function that synthesizes **spatial distance** and **operational complexity**.

---

## Methodology and Mathematical Framework 

The pipeline's foundation rests upon **ToposMapper** ($\text{TDA}$ Mapper algorithm) and **Persistent Homology ($\text{PH}$)** for rigorous structural evaluation.

#### 1. Feature Engineering

The `RobustMiningFeatureEngineer` class calculates essential features for effective $\text{TDA}$:

* **Distance\_To\_Center:** Geospatial position relative to the $\text{WA}$ mining mean.
* **Operational\_Complexity:** A derived score quantifying operation type (e.g., Underground $\gt$ Open Pit $\gt$ Basic).
* **Mineral\_Score:** A weighted metric reflecting the economic importance of contained commodities (e.g., $\text{Au}, \text{Li}, \text{REE}$).

#### 2. Topological Data Analysis Core

| Component | Purpose | TDA Method |
| :--- | :--- | :--- |
| **Mapper Algorithm** | Uncovers non-linear data clusters (nodes) and their relationships (edges) within the mining data manifold. | **Mapper/ToposMapper** ($\text{gtda.mapper}$) |
| **Lens Function** | Projects high-dimensional data onto a 1D filter. It utilizes a **weighted average of scaled Distance and Operational Score**. | **Filter Function** |
| **Persistent Homology** | Quantifies the number of meaningful **loops** ($\text{H1}$) and **connected components** ($\text{H0}$), signifying underlying structural robustness. | **Rips Complex** ($\text{Gudhi}$) |

#### 3. Output Visualizations

The process yields three crucial artifacts for strategic assessment:

1.  **`wa_mining_operations_map.html`**: Interactive $\text{Folium}$ map annotated with **High Potential** indicators.
2.  **`interactive_mining_mapper_graph.html`**: Interactive plot of the topological network; node size reflects **Cluster Size**, and color represents the **Mining Potential Score**.
3.  **`mining_node\_assignments\_map.html`**: $\text{Folium}$ map mapping individual mines to their corresponding **Topological Node/Cluster**.

---

## Prerequisites and Deployment

This analysis necessitates several specialized Python libraries.
## Install core TDA and geospatial dependencies
!pip install giotto-tda gudhi plotly folium geopandas pyvis scikit-learn contextily mapclassify ipywidgets

## Execution Instructions (Using Colab)

The entire pipeline is contained within the primary notebook, Ore_Atlas_Applied_to_Minedex.ipynb. To ensure guaranteed execution and visualization quality without dependency on GitHub's static rendering, use the provided Colab link:

**Execution Link:**
[Open in Colab] https://colab.research.google.com/github/ManuelFagundes/Ore-Atlas_applied_to_MinedexWA/blob/main/Ore_Atlas_Applied_to_Minedex.ipynb

**Data Input:** Upon initial execution, the load_and_preprocess_mining_data function will prompt the user to upload the necessary Minedex $\text{WA}$ $\text{CSV}$ file directly into the Colab session environment.
