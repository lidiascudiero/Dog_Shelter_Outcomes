# Shelter Intelligence: Predictive Analytics for Adoption Optimization

##  Project Overview
This project implements an end-to-end Data Science pipeline to optimize animal shelter operations. By analyzing a complex dataset of shelter animals, the goal is to predict adoption outcomes and identify the key behavioral and demographic factors that influence an animal's "adoptability."

The project follows the **CRISP-DM** methodology, moving from raw data exploration to advanced predictive modeling (Clustering, Classification, and Regression).

---

## The "Behavioral" Angle 
> **Author's Note:** Leveraging my background in **Cognitive Neuroscience**, I approached this dataset not just as rows of data, but as "behavioral profiles." My expertise in analyzing biological neural signals allows me to treat machine and animal data as dynamic systems. In this project, I focused on how qualitative traits—such as energy levels, sociability, and temperament—translate into quantitative predictors of real-world outcomes.

---

##  Dataset Architecture & Sources
To achieve a holistic view of the shelter ecosystem, I integrated and pre-processed two distinct data sources, creating a unified dataset for analysis:

1. **Austin Animal Center (AAC) Outcomes**: 
   - Source: [City of Austin Open Data Initiative](https://www.kaggle.com/datasets/aaronschlegel/austin-dog-center-shelter-intakes-and-outcomes)
   - Scope: Real-world intake and outcome records from the largest no-kill shelter in the US (18,000+ dogs annually).

2. **Dog Breeds Intelligence**: 
   - Source: [Dog Breeds Details Dataset](https://www.kaggle.com/datasets/warcoder/dog-breeds-details)
   - Scope: Standardized breed-specific metadata including **lifespan, weight, and height ranges**. This allowed for "Feature Augmentation," moving beyond simple IDs to physical and biological predictors.

---

##  Data Dictionary & Feature Engineering
Beyond the raw data, I engineered specific features to capture the "Behavioral State" of the animals at the time of the outcome:

| Feature | Description | Engineering Applied |
| :--- | :--- | :--- |
| `log_dog_age` | Age of the dog at outcome | Log-transformed to handle skewed distribution. |
| `sex_upon_outcome` | Biological sex and neuter status | Categorical encoding for model compatibility. |
| `outcome_type` | Target variable (Adoption, Transfer, etc.) | Grouped into risk-based classes for classification. |
| `breed_avg_weight` | Physical size metric | Merged from Breed Details to assess size-bias in adoption. |
| `time_in_shelter` | Duration of stay | Derived from `intake_datetime` vs `outcome_datetime`. |


##  Technical Depth & Methodology

### 1. Data Understanding & Preparation
* **Feature Engineering:** Implemented log transformations to normalize skewed distributions (e.g., Age and Weight). 
* **Data Cleaning:** Managed missing values and inconsistent categorical labels, ensuring a robust foundation for modeling.
* **Scaling:** Applied standard scaling to ensure feature parity for distance-based algorithms.

### 2. Unsupervised Learning (Clustering)
* **Goal:** Identify latent segments within the shelter population.
* **Models:** Evaluated **K-Means**, **Hierarchical Clustering (Ward)**, and **DBSCAN**.
* **Result:** Successfully segmented the population into two primary clusters ($k=2$, Silhouette Score: 0.31). Analysis revealed that physical size and weight are the primary drivers of variance, helping shelters categorize space and resource allocation.

### 3. Predictive Classification
* **Goal:** Predict the final outcome of the animal (Adoption, Transfer, etc.).
* **Algorithms:** Compared **Random Forest**, **Decision Trees**, **KNN**, and **SVM** against a **Dummy Classifier** baseline.
* **Performance:** The **Random Forest** model emerged as the leader with an **Accuracy of 0.73**.
* **Imbalance Handling:** Critically analyzed the "Class 0" (negative outcomes) difficulty. Used **Precision-Recall** and **F1-Score** to ensure the model provides a realistic view of shelter challenges beyond simple accuracy.

### 4. Regression Analysis
* **Goal:** Predict the "Length of Stay" (LoS).
* **Finding:** Identified a weak linear correlation ($R^2 \approx 0.06$), indicating that adoption time is influenced by non-linear external factors or missing variables. 
* **Insight:** This honest analysis suggests that shelters should focus on categorical "risk bands" rather than precise day-counts, a crucial finding for operational planning.

---

## Actionable Insights for Shelters
1. **Behavioral Impact:** Traits like `good_with_other_dogs` and `energy_level` are stronger predictors of outcome than many physical attributes.
2. **Resource Allocation:** Early identification of "low-probability" adoption profiles allows for early behavioral intervention or targeted marketing.
3. **Strategic Transfer:** The model identifies which animals are prime candidates for transfers between facilities to maximize adoption speed.

---

##  Tech Stack
- **Language:** Python
- **Libraries:** Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn
- **Environment:** Jupyter Notebook / Google Colab
- **Models:** K-Means, DBSCAN, Hierarchical Clustering,Decision Tree, Random Forest (Classifier/Regressor), SVM, KNN, Linear Regression

---

## How to Use
1. Clone the repository: `git clone https://github.com/yourusername/shelter-intelligence.git`
2. Install dependencies: `pip install -r requirements.txt`
3. Explore the notebooks in order: `01_preparation`, `02_clustering`, `03_classification`, `04_regression`.

---
*Disclaimer: This project was developed as part of the Master in Big Data Analytics and AI for Society at the University of Pisa.*


















