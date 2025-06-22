# EV Indian Customer Segmentation

## Project Overview

This project aims to identify and segment potential electric vehicle (EV) customers in India by leveraging two distinct datasets: a general customer dataset and a credit data dataset. The objective is to understand the diverse customer base and recommend strategic target segments for the Indian EV industry, facilitating more effective marketing, product development, and market entry strategies.

> 👤 **Role Contribution**:
> I specifically worked on the **age and income-based segmentation analysis** — core demographic parameters critical to understanding consumer readiness and affordability for EV adoption. This analysis formed the foundation of our customer segmentation and strategic targeting decisions.

## Problem Statement (EV Market)

You are a team working under an Electric Vehicle Startup. The Startup is still deciding in which vehicle/customer space it will develop its EVs.

You have to analyse the Electric Vehicle market in India using segmentation analysis and come up with a feasible strategy to enter the market, targeting the segments most likely to use Electric vehicles.

Customer segmentation was expected across multiple dimensions including **Geographic, Demographic, Psychographic**, and **Behavioral** categories depending on the data available. A specific focus was placed on understanding market feasibility through the **Innovation Adoption Life Cycle**.

## Data Sources

The analysis integrates data from two sources, both located in the Datasets/ directory:

1. **`Customers.csv`**: Contains general customer demographic and behavioral information.
2. **`credit_data.csv`**: Provides credit-related information which also includes demographic details like age and income.

> For computational efficiency, the `credit_data.csv` was sampled down to 10,000 records if its original size exceeded this threshold.

## Methodology

The customer segmentation was performed using K-Means clustering, following these key steps:

1. **Data Loading and Sampling**
2. **Feature Selection and Combination**: Selected features included `Age`, `Income`, `Family Size`, `Profession`, `City`, `Employment Profile`.
3. **Data Preprocessing**: Missing value handling and one-hot encoding for categorical data.
4. **Feature Scaling**: StandardScaler was used to normalize numerical features.
5. **Optimal Cluster Selection**:

   * **Elbow Method** (for inertia minimization).
   * **Silhouette Score** (for measuring cluster cohesion/separation).
6. **K-Means Clustering**
7. **Cluster Profiling**: Profiling was heavily influenced by the age and income distribution in each cluster.
8. **Visualization**: Scatter plot showing Age vs. Income clustering (`indian_ev_segments_scatter_enhanced_sampled.jpg`).

---

## 🔍 Key Findings: Age & Income Segmentation (My Focus Area)

Age and income emerged as the **most influential demographic factors** for determining readiness and feasibility of EV adoption in India. From our segmentation analysis:

* 🔹 **Prime EV Adoption Group**:
  Customers aged **30–60 years** with **income between ₹6–₹15 Lakhs per annum**, found predominantly in **Cluster 0** and **Cluster 4**, represent a **financially stable and EV-ready audience**.

* 🔸 **Emerging Potential Segment**:
  **Young professionals (25–35 years)** with moderate income (**₹4–₹8 Lakhs annually**) form a high-interest group for **affordable EVs with financing support**.

* ⚠️ **Low Adoption Probability Segment**:
  Customers below **25 years** or earning **less than ₹3 Lakhs annually** showed **limited EV feasibility** due to affordability constraints and lower financial maturity.

This segmentation is critical to aligning EV models and marketing with early adopters per the [Innovation Adoption Life Cycle](https://en.wikipedia.org/wiki/Technology_adoption_life_cycle).

---

## ✅ Strategic Recommendations

Based on the age-income cluster profiles, we propose the following:

* **Target customers aged 30–60 years with ₹6–15L income**: These individuals represent the strongest early adopters for urban-oriented EVs.
* **Design city-targeted campaigns** in metros like **Bangalore, Pune, Delhi**, where higher income professionals with environmental consciousness reside.
* **Enable financing schemes** and **mid-range EV models** for younger professionals (25–35) to tap into the emerging EV interest.
* **Avoid over-targeting low-income youth segments**, as their adoption likelihood remains constrained under current pricing and infrastructure.

---

## How to Use the Notebook

To run this analysis:

1. **Install Python dependencies**:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```
2. **Place Files**: Ensure the notebook file is in the root directory, and that the datasets (Customers.csv, credit_data.csv) are located inside the Datasets/ folder.
3. **Run**:

   ```bash
   jupyter notebook
   ```
4. **Open and Execute**: Run all cells in `EV_Indian_Customer_Segmentation_Sampled_Fixed.ipynb`.

---

## Repository Contents

* `EV_Indian_Customer_Segmentation_Sampled_Fixed.ipynb`
* `Datasets/Customers.csv`
* `Datasets/credit_data.csv`
* `Images/elbow_method_enhanced_sampled.png`
* `Images/silhouette_score_enhanced_sampled.png`
* `Images/indian_ev_segments_scatter_enhanced_sampled.jpg`
* `README.md`




