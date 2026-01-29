# ICU-LOS-Length-of-Stay-Predictive-Modelling-for-patients-with-Spinal-Injury
Drawing from the MIMIC IV dataset to produce insight on how long a patient with an acute spinal injury would spend in an Intensive Care Unit. 
ICU's are often expensive to operate and require heavy oversight and management from hopsital staff and resources, so these predictions would help control hospital expensive, provide patients with more timely discharges and optimize hospital resource management.

Below details the contents of each uploaded file.

## Project Proposal.pdf:
Provides insight into:
- Research purpose and benefits
- Using a singular, general machine learning model over using multiple for niche patient subgroups, and versus using both.
- Details on the dataset done through EDA such as the size, missing values, data collection, relevant variables to the investigation from each csv file (as MIMIC IV has multiple datasets within itself) and feature engineering that would be useful in the endeavour.
- Discussing the visualizations to use to best capture the insights from EDA and model metrics.
- Potential models and statistical tools to use prior to the start of the investigation such as Causal Inference or Nueral Networks and both the pros & cons of such.
- The final method that was used to carry out the investigation.
- Concerns to keep in mind such as the quality of the dataset as a whole or technical challenges such as using different SQL-based techniques to acquire the data needed and whether these techniques would be optimal or not.

## Shrivar Notebook Clustering.ipynb:
- dataset modifications such as one-hot-encoding on target categorical variables, feature engineering from the existing dataset and melting features into single features if redundant.
- Inverse Transform Sampling to impute missing values based on the distribution of the dataset itself rather than using the mean or mode for a column as the latter approach assumes a normal distribution, which may not yield as accurate results.
- Histograms to observe feature distributions for each feature.
- Normalizing all features to the same scale for more accurate comparisons and to avoid certain features having dominance over others purely due to scale.
- Using Principle Cluster Analysis (PCA) to indentify potential subgroups within the dataset and using a silhouette score to determine the prominence and definition of each identified cluster.
- Studying each cluster by identifying which features influence it the most in either direction.
- Using Kruskal-Wallace testing to determine if the identified PCA clusters do affect LOS.
- Violinplots to depict the effect of said clusters on LOS.
- Trying to find clusters without PCA (due to their distributions for LOS being similar) using the Elbow method.

## Shrivar Naidu ML Complex.ipynb:
- Uses alterations from general model and clustering
- Focus on PCA clusters due to being a better representation of the dataset as a whole:

Cluster 0: Characterized by patients who are primarily referred through physician referrals or other referrals, with a focus on surgical admissions, predominantly married individuals.

Cluster 1: Consists mainly of patients admitted through emergency rooms, with a focus on emergency admissions.

Cluster 2: Primarily transferred from hospitals, with urgent admission types, and higher diagnosis counts.

- Fitted LightGBM, XGBoost and CatBoost for each cluster and performed a comparison of each model's metrics to each other.
- Performed Residual Analysis on each model prior to using a Log transformation and Hubert Loss function.
- Performed the aforementioned treatments to each model to reduce heteroscedacity.
- Redid Residual Analysis on each model to evaluate model performance.
