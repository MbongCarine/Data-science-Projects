# Mental Health Prediction Model

## Overview

This project uses machine learning to predict mental health struggles based on various psychological, behavioral, and demographic features. Multiple classification algorithms are compared to find the most effective model for early detection and intervention. The project incorporates explainable AI techniques (SHAP and LIME) to ensure that predictions are transparent and interpretable.

## Features

- **Data cleaning and preprocessing** of mental health dataset
- **Exploratory data analysis** with informative visualizations
- **Feature engineering** for categorical variables
- **Model training and comparison** across multiple algorithms
- **Hyperparameter tuning** using GridSearchCV
- **Model explainability** using SHAP and LIME

## Dataset

The dataset contains information about individuals' mental health status including:

- Demographic information (Gender, Country)
- Employment status (Self-employed)
- Psychological indicators (Mood Swings, Growing Stress)
- Behavioral patterns (Days Indoors, Changes in Habits)
- Mental health history (Family history, Previous treatment)
- Social factors (Work Interest, Social Weakness)

## Data Preprocessing

1. **Handling duplicates**
   - Removed duplicate records, reducing the dataset significantly

2. **Handling missing values**
   - Used Random Forest to predict missing values in the 'self_employed' column

3. **Feature encoding**
   - Binary variables (Yes/No): Converted to 1/0
   - Ordinal variables: Mapped to ordered integers
   - Categorical variables: Applied label encoding
   - Days Indoors: Custom mapping to numerical values

## Models Evaluated

The project tests multiple machine learning models:

- Logistic Regression
- Decision Tree
- Random Forest
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVC)
- Gaussian Naive Bayes
- Gradient Boosting
- XGBoost

## Model Tuning

GridSearchCV was used to optimize hyperparameters for:
- Random Forest
- Gradient Boosting
- XGBoost

## Results

Gradient Boosting emerged as the best-performing model for predicting mental health struggles. 

## Explainability Analysis

Two explainability techniques were used to interpret model predictions:

1. **SHAP (SHapley Additive exPlanations)**
   - Identifies the most influential features globally
   - Key factors: Growing Stress, Mood Swings, and Changes in Habits

2. **LIME (Local Interpretable Model-agnostic Explanations)**
   - Provides case-by-case explanations for individual predictions
   - Helps understand why specific predictions were made

## Key Insights

- **Growing Stress, Mood Swings, and Changes in Habits** are the most significant predictors of mental health struggles
- **Work Interest and Occupation** may have protective effects on mental health
- The **Gradient Boosting** algorithm provides the most accurate predictions for this problem

## Requirements

The project requires the following Python libraries:
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- xgboost
- catboost
- shap
- lime

## Usage

1. **Data preprocessing**
   ```python
   # Load and clean data
   mental.drop_duplicates(inplace=True)
   
   # Handle missing values
   # (Using Random Forest to predict missing self_employed values)
   ```

2. **Feature encoding**
   ```python
   # Example: Binary encoding
   for col in binary_columns:
       mental_cat[col] = mental_cat[col].map({'Yes': 1, 'No': 0})
   ```

3. **Model training and evaluation**
   ```python
   # Split data into training and testing sets
   X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.30, random_state=101)
   
   # Standardize features
   scaler = StandardScaler()
   X_train = scaler.fit_transform(X_train)
   X_test = scaler.transform(X_test)
   
   # Train models with GridSearchCV
   # Compare model performances
   ```

4. **Model explainability**
   ```python
   # SHAP analysis
   explainer = shap.Explainer(best_model, X_test_df)
   shap_values = explainer(X_test_df)
   
   # LIME explanation for individual predictions
   explainer = lime.lime_tabular.LimeTabularExplainer(
       training_data=X_train_array,  
       feature_names=X_train_df.columns.tolist(),
       class_names=['No Struggle', 'Struggle'],  
       mode='classification'
   )
   ```

## Future Work

Potential improvements include:
- Temporal analysis to track mental health trends over time
- Integration of causal inference methods
- Expanding the dataset for better generalization across diverse populations