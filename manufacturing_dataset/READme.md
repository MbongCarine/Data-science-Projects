# Manufacturing Defect Prediction

## Overview
This project uses machine learning to predict defects in manufacturing processes. By analyzing various production metrics, the model can identify conditions likely to result in high defect rates, allowing manufacturers to take preventive action.

## Features
- Data analysis and visualization of manufacturing metrics
- Machine learning pipeline to predict defect status (Low vs. High Defects)
- Handling of class imbalance using SMOTE (Synthetic Minority Over-sampling Technique)
- Comparison of multiple classification algorithms
- Feature importance analysis to identify key factors affecting defect rates

## Requirements
The following Python libraries are required:
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- catboost
- imbalanced-learn (for SMOTE)
- joblib

## Usage

### 1. Data Preparation
The code loads manufacturing data containing metrics like:
- Production Volume
- Production Cost
- Energy Consumption
- Defect Rate
- Safety Incidents
- Additive Process Time

### 2. Exploratory Data Analysis
- Visualizations show relationships between various production metrics and defect status
- Missing values are handled
- Class distribution is analyzed

### 3. Model Training (without oversampling)
Multiple classification models are trained and evaluated:
- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting
- Support Vector Machine (SVM)

### 4. Oversampling with SMOTE
SMOTE is applied to balance the dataset by generating synthetic examples of the minority class (High Defects).

### 5. Model Training (with oversampling)
The same models plus CatBoost are trained on the balanced dataset.

### 6. Feature Importance Analysis
- Random Forest importance scores identify key predictors of defects
- CatBoost importance scores after SMOTE
- Recursive Feature Elimination (RFE) selects the top 10 features

### 7. Model Saving
The best performing model is saved to a file (`best_defect_model.pkl`) for later use in production.

## Results
- Model performance metrics include accuracy, precision, recall, and F1-score
- Confusion matrices visualize classification performance
- ROC curves show the trade-off between true positive rate and false positive rate
- Feature importance charts reveal which manufacturing parameters most affect defect rates
