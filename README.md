# --- EV_sales_analysis --- 

## Project Overview

This project aims to identify and segment potential electric vehicle (EV) customers in India by leveraging two distinct datasets: a general customer dataset and a credit data dataset. The objective is to understand the diverse customer base and recommend strategic target segments for the Indian EV industry, facilitating more effective marketing, product development, and market entry strategies.

## Data Sources

The analysis integrates data from two sources:
1.  **`Customers.csv`**: Contains general customer demographic and behavioral information.
2.  **`credit_data.csv`**: Provides credit-related information which also includes demographic details.

*Note: For computational efficiency, the `credit_data.csv` was sampled down to 10,000 records if its original size exceeded this threshold, to enable quicker prototyping and analysis within the notebook.*

## Methodology

The customer segmentation was performed using K-Means clustering, following these key steps:

1.  **Data Loading and Sampling**:
    * Both `Customers.csv` and `credit_data.csv` are loaded.
    * `credit_data.csv` is sampled to 10,000 rows if it's a large file.
2.  **Feature Selection and Combination**:
    * Relevant features (`Age`, `Income`, `Family Size`, `Profession`, `City`, `Employment Profile`) are extracted from both datasets.
    * A 'Source' column is added to distinguish between the original datasets.
    * The selected features are concatenated into a single DataFrame.
3.  **Data Preprocessing**:
    * **Missing Value Imputation**: `Family Size` (numerical) is imputed with its mean. Categorical features (`Profession`, `City`, `Employment Profile`) are imputed with 'Unknown'.
    * **One-Hot Encoding**: Categorical features are converted into numerical format using one-hot encoding for compatibility with K-Means.
4.  **Feature Scaling**: All numerical features (including the one-hot encoded ones, excluding the 'Source' column) are scaled using `StandardScaler` to ensure that no single feature dominates the clustering process due to its magnitude.
5.  **Determining Optimal Number of Clusters (K)**:
    * **Elbow Method**: The Sum of Squared Distances (Inertia) is plotted against the number of clusters (`K`) to identify the "elbow point" where the decrease in inertia substantially slows down. (Refer to `elbow_method_enhanced_sampled.png`)
    * **Silhouette Score**: This metric measures how similar an object is to its own cluster (cohesion) compared to other clusters (separation). A higher silhouette score (closer to +1) indicates better-defined clusters. (Refer to `silhouette_score_enhanced_sampled.png`)
6.  **K-Means Clustering**: K-Means is applied with the chosen optimal `K` (e.g., 5 in the notebook example) to segment the customers.
7.  **Cluster Profiling and Recommendation**: Each identified cluster is profiled based on the mean/mode of its original (unscaled) features. Strategic recommendations for the Indian EV market are then derived from these profiles. A scatter plot visualizes the clusters based on Age and Income. (Refer to `indian_ev_segments_scatter_enhanced_sampled.jpg`)

## Key Findings and Recommendations

### 📊 Key Findings (Age & Income Focused)

The clustering analysis reveals distinct customer segments in the Indian EV market when projected onto **Age vs. Income**:

- 🔹 **Prime EV Adoption Group**:  
  **Age 30–60 years** with **income between ₹6L–₹15L annually** — concentrated in Cluster 0 and Cluster 4. This segment shows stable income and higher adoption readiness.

- 🔸 **Emerging Potential Group**:  
  **Young professionals (Age 25–35)** with **income ₹4L–₹8L annually** — motivated by affordable EVs and financing options.

- ⚠️ **Lower Adoption Likelihood**:  
  Customers below **25 years** or with **income < ₹3L annually** are less suitable due to affordability constraints.

### ✅ Strategic Recommendations 

- **Target Age 30–60 & Income ₹6–15L** with affordable EV models, financing options, and city-oriented features.
- **Focus Metro Cities** like Bangalore, Pune, and Delhi with campaigns aimed at urban professionals and families.
- **Build Charging Infrastructure & Partner with Employers** to enhance convenience and boost EV adoption.

## How to Use the Notebook

To run this analysis:

1.  **Prerequisites**: Ensure you have Python installed, preferably via Anaconda or Miniconda.
2.  **Dependencies**: Install the required libraries:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn jupyter
    ```
3.  **Data Files**: Place `Customers.csv` and `credit_data.csv` in the same directory as the Jupyter notebook file (`EV_Indian_Customer_Segmentation_Sampled_Fixed.ipynb`).
4.  **Run Jupyter**: Open a terminal or command prompt, navigate to the directory containing the files, and run:
    ```bash
    jupyter notebook
    ```
5.  **Execute Cells**: Open `EV_Indian_Customer_Segmentation_Sampled_Fixed.ipynb` and run all cells sequentially.

## Files in this Repository

* `EV_Indian_Customer_Segmentation_Sampled_Fixed.ipynb`: The main Jupyter notebook for segmentation analysis.
* `Customers.csv`: Input dataset containing customer information.
* `credit_data.csv`: Input dataset containing credit-related data.
* `elbow_method_enhanced_sampled.png`: Elbow plot for optimal K.
* `silhouette_score_enhanced_sampled.png`: Silhouette score plot.
* `indian_ev_segments_scatter_enhanced_sampled.jpg`: Age vs Income scatter plot of clusters.
* `README.md`: This file, providing an overview of the project.