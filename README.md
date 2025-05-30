# Chronic Kidney Disease Classification

## Project Overview

This project develops and compares multiple machine learning models to accurately classify patients with Chronic Kidney Disease based on their clinical features. The analysis includes 400 patients (250 CKD cases and 150 healthy controls) with 25 clinical variables including blood tests, urine tests, and other medical measurements.

### Key Achievements
- **99.17% accuracy** using cluster-based decision trees
- **99.33% AUC score** demonstrating excellent diagnostic performance
- Identification of key clinical predictors (hemoglobin and blood urea)
- Implementation of patient subgroup-based modeling approach

## Dataset Information

- **Source**: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/336/chronic+kidney+disease)
- **Size**: 400 patients, 25 clinical features
- **Target Distribution**: 
  - CKD patients: 250 (62.5%)
  - Healthy controls: 150 (37.5%)
- **Feature Types**: 
  - Numerical variables: 11 (age, blood pressure, blood glucose, etc.)
  - Categorical variables: 14 (including target variable)

### Clinical Features
- **Blood Tests**: Hemoglobin, packed cell volume, white/red blood cell counts
- **Kidney Function**: Blood urea, serum creatinine, blood glucose
- **Urine Tests**: Specific gravity, albumin, sugar levels
- **Medical History**: Hypertension, diabetes, coronary artery disease
- **Physical Symptoms**: Appetite, pedal edema, anemia

## Methodology

### 1. Data Preprocessing
- **Missing Value Treatment**: Median imputation for numerical variables, mode imputation for categorical variables
- **Data Cleaning**: Removal of tab characters and standardization of categorical values
- **Feature Engineering**: Creation of dummy variables for categorical features
- **Outlier Handling**: Preserved outliers due to medical significance

### 2. Exploratory Data Analysis
- Statistical summary and distribution analysis
- Correlation analysis revealing key relationships:
  - Hemoglobin & Packed Cell Volume: r = 0.90
  - Blood Urea with hemo/rbcc/pcv: r ≈ -0.60
- Missing value pattern analysis (up to 38% missing in some variables)

### 3. Feature Selection
- Random Forest-based feature importance ranking
- Selection of top 25 most discriminative features
- Inclusion of both numerical and categorical variables

### 4. Model Development

#### Models Implemented:
1. **K-Nearest Neighbors (KNN)** - Numerical features only
2. **Decision Tree** - Numerical features only  
3. **Decision Tree** - All features (numerical + categorical)
4. **Cluster-Based Decision Trees** - Patient subgroup-specific models

#### Hyperparameter Optimization:
- KNN: Optimal k = 2
- Decision Trees: Optimal depth = 4 (determined via cost complexity pruning)
- Clustering: k = 3 clusters for patient subgrouping

## Results

### Model Performance Comparison

| Model | Accuracy | AUC Score |
|-------|----------|-----------|
| **Cluster-Based Decision Trees** | **99.17%** | **99.33%** |
| Decision Tree (All Features) | 95.83% | 95.33% |
| Decision Tree (Numerical Only) | 95.00% | 94.67% |
| K-Nearest Neighbors | 79.17% | 78.00% |

### Key Features
- **Primary Predictor**: Hemoglobin levels (root node in decision tree)
- **Secondary Predictor**: Blood urea levels
- **Feature Impact**: Categorical variables improve model performance significantly
- **Patient Subgroups**: Three distinct patient clusters identified for personalized modeling

### Clinical Relevance
1. **Hemoglobin** emerges as the most discriminative feature, aligning with medical knowledge about anemia in CKD patients
2. **Multi-feature approach** outperforms single-feature models, emphasizing comprehensive clinical assessment

## Clinical Applications

### Immediate Implementation
- **Screening Tool**: Deploy in primary care settings using standard lab values
- **Risk Stratification**: Identify high-risk patients for nephrology referral
- **Early Detection**: Integrate into routine health checkups

### Operational Benefits
- **Resource Optimization**: Prioritize patient care based on risk scores
- **Cost Reduction**: Enable early intervention to prevent disease progression
- **Workflow Integration**: Clear decision rules facilitate clinical adoption
