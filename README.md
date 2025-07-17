# Chronic Kidney Disease (CKD) Classification

This project presents a machine learning approach to classify patients with Chronic Kidney Disease (CKD) using clinical data. The primary goal is to develop a high-accuracy model for early detection, which can significantly improve patient outcomes. The analysis was performed on the [Chronic Kidney Disease dataset](https://archive.ics.uci.edu/dataset/336/chronic+kidney+disease) from the UCI Machine Learning Repository.

## Key Achievements

-   Developed a novel **Cluster-Based Decision Tree model** that achieved **99.17% accuracy** and a **99.33% AUC score**.
-   Identified **hemoglobin** as the most significant clinical predictor of CKD, which aligns with existing medical knowledge.
-   Demonstrated that incorporating both numerical and categorical features significantly improves model performance.

## Dataset

-   **Source**: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/336/chronic+kidney+disease)
-   **Instances**: 400 (250 CKD patients, 150 healthy controls)
-   **Features**: 25 clinical variables, including 11 numerical and 14 categorical

## Methodology

The project followed a structured machine learning workflow:

### 1. Data Preprocessing

-   **Data Cleaning**: Standardized categorical values and removed extraneous characters (e.g., tab characters in `class` and `dm` variables).
-   **Missing Value Imputation**: Used median imputation for numerical features and mode (most frequent) imputation for categorical features to handle missing data.
-   **Outlier Handling**: Preserved outliers as they were considered medically significant.

### 2. Exploratory Data Analysis (EDA)

-   Conducted statistical analysis and visualized feature distributions to understand the data's characteristics.
-   Performed correlation analysis, which revealed strong relationships between key variables, such as:
    -   Hemoglobin (`hemo`) and Packed Cell Volume (`pcv`): **r = 0.90**
    -   Blood Urea (`bu`) and Hemoglobin (`hemo`): **r ≈ -0.60**

### 3. Feature Selection

-   Utilized a **Random Forest** classifier to rank features by importance.
-   Selected the top 25 most discriminative features for model training, including both numerical and categorical variables.

### 4. Model Development

Four different models were implemented and evaluated:
1.  **K-Nearest Neighbors (KNN)**: A baseline model using only numerical features.
2.  **Decision Tree**: A model trained on only numerical features.
3.  **Decision Tree (All Features)**: An improved model using both numerical and categorical features.
4.  **Cluster-Based Decision Trees**: A more sophisticated approach where patients were first grouped into three distinct clusters using K-means, and then a separate Decision Tree model was trained for each subgroup.

## Results

The models were evaluated on their accuracy and AUC scores, with the following results:

| Model                        | Accuracy | AUC Score |
| ---------------------------- | :------: | :-------: |
| **Cluster-Based Decision Trees** | **99.17%** | **99.33%** |
| Decision Tree (All Features) |  95.83%  |  95.33%   |
| Decision Tree (Numerical Only) |  95.00%  |  94.67%   |
| K-Nearest Neighbors (KNN)    |  79.17%  |  78.00%   |

## Conclusion

This project successfully demonstrates the potential of machine learning for accurate and early detection of Chronic Kidney Disease. The high performance of the Cluster-Based Decision Tree model suggests that personalized modeling based on patient subgroups can lead to superior results.

### Future Work

-   Validate the models on external datasets to ensure generalizability.
-   Explore other advanced ensemble methods to potentially further improve accuracy.
-   Deploy the best-performing model as a web application for clinical decision support.
