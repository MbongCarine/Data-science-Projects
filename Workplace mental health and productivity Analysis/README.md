# Workplace Mental Health & Productivity Analysis

## Overview
This project analyzes the relationship between mental health factors and workplace productivity. The focus is on understanding how various mental health-related factors impact an employee's interest in work, with the goal of providing actionable recommendations for employers to enhance workplace mental health policies.

## Objective
- Investigate how mental health factors impact work interest
- Identify significant workplace-related stressors
- Provide data-driven insights for creating supportive workplace environments
- Build interpretable machine learning models to predict work interest

## Dataset
The dataset contains information about:
- **Demographics**: Gender, Country, Occupation, Self-employed status
- **Mental Health History**: Family history, Previous conditions, Access to care
- **Workplace Stressors**: Growing stress, Changes in habits, Coping struggles
- **Social Factors**: Social weakness, Mood swings, Mental health interviews
- **Work Engagement**: Interest in work (`Work_Interest`), Care options availability

## Key Features
Analysis revealed that the most important features affecting work interest are:
1. Days spent indoors (18.16%)
2. Occupation type (18.03%)
3. Changes in habits (10.62%)
4. Mental health history (10.27%)
5. Mood swings (10.06%)

## Models Tested
- Logistic Regression
- Decision Tree
- Random Forest
- Extra Trees
- XGBoost

## Model Explainability
The project uses techniques like SHAP and LIME to provide interpretable results and insights into how different factors affect work interest.

## Key Findings
- Workplace environment and daily habits have the biggest impact on work interest
- Mental and emotional well-being significantly affect work engagement
- Coping mechanisms play an important role in preventing disengagement
- Demographic factors like gender and country have relatively less impact

## Recommendations
- Promote flexible work arrangements
- Implement stress management programs
- Provide mental health resources
- Encourage wellness programs and peer support groups

## Getting Started
1. Install required libraries:
```
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
```

2. Run the Jupyter notebook to:
   - Process and analyze the data
   - Train machine learning models
   - Visualize results and feature importance

## Files Included
- Jupyter notebook with analysis code
- Dataset (not included in repository)
- Documentation of findings