# Intrusion Detection System
## About the dataset 
- URL: https://archive.ics.uci.edu/dataset/942/rt-iot2022 
- Source: UCI Machine Learning Repository 
- Domain: IoT Network Security 
- Size: 123,117 records with 85 features 
- Target Variable: Attack_type (12 classes)
## Problem Statement 
The primary objective is to develop a robust and automated intrusion detection system (IDS) tailored for IoT network environments, capable of both supervised and unsupervised threat analysis. 
## Methodology 
### Data Preprocessing 
The RT-IOT2022 dataset, consisting of 123,117 rows and 85 columns, was first explored to confirm the absence of missing values and to understand the distribution of numerical and categorical features. To reduce dimensionality and improve model efficiency, 25 redundant or derived features were removed. These included aggregated totals already captured by min/max/average statistics, duplicate index columns, and rarely-used flag counters. The refined dataset retained 60 informative features. Categorical columns such as proto, service, and Attack_type were encoded using label encoding, and all numerical features were standardized using StandardScaler to ensure compatibility with algorithms sensitive to feature magnitude. Visual exploration included plotting the class distribution to assess imbalance and generating a feature correlation heatmap to identify multicollinearity and feature relationships. 
### Classification Algorithms 
Two classification models were implemented to detect and categorize network intrusions. **Logistic Regression** was selected as a baseline due to its simplicity, interpretability, and efficiency in multi-class classification. It was configured with the lbfgs (Limited-memory Broyden–Fletcher–Goldfarb–Shanno) solver, multinomial strategy, and a maximum of 1000 iterations. **XGBoost** was chosen for its ability to model complex non-linear relationships and its robustness against class imbalance. It was configured with the softmax as objective function for multiclass classification and categorical cross entropy (mlogloss) as evaluation metric. Both models were trained on an 80/20 stratified split and evaluated using accuracy, precision, recall, and F1-score. To validate generalization, 5-fold cross-validation was performed for each model, confirming consistent performance across folds. 
### Clustering Algorithm 
To complement supervised classification, **KMeans** clustering was applied for unsupervised analysis of network traffic. The target label Attack_type was excluded to allow natural groupings to emerge. **Principal Component Analysis (PCA)** was used to reduce the feature space to two dimensions for visualization. An initial cluster count of four was selected, and clustering quality was assessed using silhouette scores and the elbow method across k-values ranging from 2 to 10. Cluster profiling was conducted by computing mean feature values per cluster and mapping clusters to attack types using cross-tabulation. This enabled deeper insights into behavioural groupings and supported the identification of potential anomalies or unknown attack patterns. 
## Result
This project successfully demonstrates the use of machine learning for securing IoT networks within the web security domain. Through efficient preprocessing, the feature set was reduced from 85 to 60 without compromising accuracy, enabling faster and scalable intrusion detection. XGBoost achieved a classification accuracy of **99.83%**, outperforming Logistic Regression and effectively distinguishing between 12 attack types. KMeans clustering revealed meaningful behavioural patterns with a **Silhouette Score of 0.7958**, supporting anomaly detection and profiling of unknown threats. 
- XGBoost is production-ready and has a high accuracy of 99.83%.
- The cluster formed revealed natural groupings in attack behaviour.
- We have reduced dimensionality and optimised features for real-time efficiency. 
