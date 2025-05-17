# CASIA_CapstoneProject_EmergingTechnologies
TEECE 2 Capstone Project Lifestyle and Learning – Predicting Student Performance
# Student Lifestyle Analysis and Exam Performance Prediction

This project explores the relationship between student lifestyle habits and their academic performance using a dataset of 1,000 simulated student records. The notebook applies a combination of data preprocessing, feature engineering, exploratory analysis, clustering, regression, and classification to uncover insights and develop predictive models.

## Project Goals

- Analyze how lifestyle habits such as study time, sleep, diet, and screen time affect academic performance.
- Cluster students based on lifestyle attributes to identify distinct behavioral profiles.
- Build regression models to predict final exam scores.
- Classify students into performance groups (Low, Average, High) based on predicted scores.
- Compare multiple machine learning models and visualize their performance.

## Dataset Description

Each record includes:
- Demographic info (age, gender, parental education)
- Lifestyle metrics (study hours, screen time, diet quality, sleep)
- Activity indicators (extracurricular participation, part-time job)
- Mental health and well-being indicators
- Final exam score (target variable)

## Workflow Summary

### 1. Data Preprocessing
- Missing values patched (e.g., treating 'None' as a valid class)
- Encoding: One-hot, binary mapping, and ordinal encoding
- Features scaled using `StandardScaler`

### 2. Feature Engineering
Created composite features to better capture behavioral patterns:
- `overall_wellness`: average of sleep, diet, exercise, and mental health
- `distractors`: average screen time from social media and Netflix
- `productive_hours`: average of study time and attendance

### 3. Exploratory Data Analysis
- Histograms, scatter plots, box plots, and correlation heatmaps
- Insight: `study_hours_per_day`, `mental_health_rating`, and `productive_hours` had strong correlation with exam score

### 4. Clustering (K-Means)
- Optimal K = 3 (based on silhouette and elbow methods)
- Cluster profiles:
  - **Distracted Low Achievers**: high distractor use, low study, lowest exam scores
  - **Balanced & Health-Focused**: high study and wellness, highest scores
  - **Highly Involved**: moderate metrics, high extracurricular participation

### 5. Regression Modeling
Models used to predict scaled `exam_score`:
- **Linear Regression**
  - Mean R² (CV): 0.896
  - Mean MAE: 0.254
- **Decision Tree Regressor**
  - Mean R² (CV): 0.686
  - GridSearchCV Test R²: 0.908
- **Random Forest Regressor (Best)**
  - Mean R² (CV): 0.862
  - GridSearchCV Test R²: 0.977
  - GridSearchCV Test MAE: 0.115
  - GridSearchCV Test RMSE: 0.150

### 6. Classification Modeling
Students were grouped into `Low`, `Average`, and `High` performers using quantile thresholds of exam score. Models used:
- **Decision Tree Classifier**
  - CV Accuracy: 0.684
  - CV F1 (macro): 0.696
- **Logistic Regression (Best Classifier)**
  - CV Accuracy: 0.817
  - CV F1 (macro): 0.819
  - Best params from GridSearchCV: `C=100`, `penalty='l2'`

---

## Table of Contents

### I. Project Introduction

### II. Project Goals

### III. Project Components

1. **Problem Definition**

2. **Data Understanding and Preprocessing**
   - Loading Data  
   - Data Information Summary  
   - Patching Missing Data  
     - Null Checker  
   - Categorical Values  
   - Scaling  
   - Feature Engineering  

3. **Exploratory Data Analysis**
   - Feature Histogram  
   - Feature vs Exam Score Scatter Plot  
   - Feature vs Exam Score Box Plot  
   - Feature Correlation Heatmap  

4. **Clustering (Unsupervised Learning)**
   - Apply K-Means clustering using lifestyle features (excluding exam score)  
   - Determine optimal K using:  
     - Elbow method (Inertia Plot)  
     - Silhouette Score  
   - K-Means clustering labeling and description  

5. **Regression Analysis (Supervised Learning)**

   **Using Linear Regression**  
   - Train/Test Split 70/30  
   - Model Evaluation  
   - Cross-Validation  
   - Result Visualization  

   **Decision Tree Regressor**  
   - Model Evaluation (70/30 Split and GridSearchCV)  
   - Model Visualization  

   **Random Forest Regressor**  
   - Model Evaluation (70/30 Split, Cross-Validation, GridSearchCV)  
   - Model Visualization  

6. **Optional Classification Task**
   - Classification of Data into `performance_group`  
   - Decision Tree Classification (70/30 Split, CV, GridSearchCV, Confusion Matrix)  
   - Logistic Regression Classification (CV, GridSearchCV, Confusion Matrix)  

### IV. Interpretation and Insights

A. Feature Importance  
B. Cluster Profiling  
C. Model Performance  
   - Model Evaluation Summary (Regression)  
   - Trade-Off: Interpretability vs Accuracy  
D. Real-World Implications  
   - Actionable Advice Based on Findings  
   - Surprising or Counter-Intuitive Results  

---

## Summary of Results

### Regression Models (Target: `exam_score`)

| Model                              | Mean R² | Mean MAE | Mean RMSE |
|-----------------------------------|---------|----------|-----------|
| Linear Regression (CV)            | 0.896   | 0.254    | 0.319     |
| Decision Tree Regressor (CV)      | 0.686   | 0.431    | 0.554     |
| Decision Tree (GridSearchCV)      | 0.908   | 0.228    | 0.299     |
| Random Forest Regressor (CV)      | 0.862   | 0.295    | 0.368     |
| **Random Forest (GridSearchCV, Test Set)** | **0.977** | **0.115** | **0.150** |

### Classification Models (Target: `performance_group`)

| Model                             | CV Accuracy | CV F1 (Macro) |
|----------------------------------|-------------|---------------|
| Decision Tree Classifier         | 0.684       | 0.696         |
| Logistic Regression Classifier   | 0.817       | 0.819         |

---

## Key Insights

- `study_hours_per_day`, `mental_health_rating`, and `productive_hours` consistently ranked as the top predictors across all models.
- The best-performing cluster was the **Balanced & Health-Focused** group, which combined strong study habits and moderate wellness behaviors.
- Random Forest Regressor, after tuning, proved to be the most accurate and generalizable predictor of academic performance.

## Requirements

- Python 3.7+
- pandas, numpy, matplotlib, seaborn
- scikit-learn

## How to Run

1. Upload the notebook to Google Colab or run it in Jupyter.
2. Ensure the dataset (`student_habits_performance.xlsx`) is accessible.
3. Follow the notebook sequentially from preprocessing to modeling.

## License

This project is for academic and demonstration purposes.

---
