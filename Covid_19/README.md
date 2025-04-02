# COVID-19 Data Analysis in R

## Project Overview
This project investigates global COVID-19 trends using R by:
- Identifying the **top 10 countries** with the highest number of COVID-19 cases.
- Determining the **top 3 countries** with the highest ratio of positive cases to total tests conducted.
- Storing and organizing data using **vectors, matrices, and lists**.
- Visualizing **daily trends** of positive cases for each country.

## Dataset Used
The dataset contains the following fields:
- **Date**: The reported date.
- **Country_Region**: The country reporting the case.
- **Tested**: The total number of COVID-19 tests conducted.
- **Positive**: The number of confirmed COVID-19 cases.
- **Active**: The number of active cases.
- **Hospitalized**: The number of hospitalizations.

## Technical Implementation
### **Step 1: Identifying the Top 10 Countries**
- Extracted the **top 10 countries** with the highest COVID-19 cases.
- Stored this information in a **dataframe (covid_top_10)**.

### **Step 2: Computing the Test Positivity Ratio**
- Calculated the **ratio of positive cases to total tests** for each country.
- Identified the **top 3 countries** with the highest test positivity ratio:
  - **United Kingdom** (0.11)
  - **United States** (0.10)
  - **Turkey** (0.08)
- Stored these values in the **positive_tested_top_3** variable.

### **Step 3: Storing Data in Vectors and Matrices**
- Created vectors for the **top 3 countries**, storing their ratio and case numbers:
  ```r
  united_kingdom <- c(0.11, 1473672, 166909, 0, 0)
  united_states <- c(0.10, 17282363, 1877179, 0, 0)
  turkey <- c(0.08, 2031192, 163941, 2980960, 0)
  ```
- Combined these vectors into a **matrix (covid_mat)**:
  ```r
  covid_mat <- rbind(united_kingdom, united_states, turkey)
  colnames(covid_mat) <- c("Ratio", "Tested", "Positive", "Active", "Hospitalized")
  ```

### **Step 4: Organizing Data into Lists**
- Created a **list (covid_analysis_list)** containing all our data structures:
  ```r
  question <- "Which countries have had the highest number of positive cases against the number of tests?"
  answer <- c("Positive tested cases" = positive_tested_top_3)

  data_structure_list <- list(
    "Dataframes" = list(covid_df, covid_df_all_states, covid_df_all_states_daily, covid_top_10),
    "Matrices" = list(covid_mat),
    "Vectors" = list(vector_cols, countries)
  )

  covid_analysis_list <- list(question, answer, data_structure_list)
  ```
- Displayed the second element of this list:
  ```r
  covid_analysis_list[[2]]
  ```

### **Step 5: Visualizing COVID-19 Trends**
#### **1. Bar Chart of Top 10 Countries with Most Cases**
```r
library(ggplot2)

ggplot(covid_top_10, aes(x = reorder(Country_Region, Positive), y = Positive)) +
  geom_bar(stat = "identity", fill = "blue") +
  labs(title = "Top 10 Countries with Most COVID-19 Cases", x = "Country", y = "Total Cases") +
  theme_minimal() +
  coord_flip()
```

#### **2. Daily Trend of Positive Cases by Country**
```r
library(dplyr)
library(ggplot2)

# Randomly select 5 countries
set.seed(123) # For reproducibility
selected_countries <- covid_df_all_states_daily %>%
  distinct(Country_Region) %>%
  sample_n(5) %>%
  pull(Country_Region)

# Filter dataset for selected countries
covid_selected <- covid_df_all_states_daily %>%
  filter(Country_Region %in% selected_countries)

# Plot daily positive cases for selected countries
ggplot(covid_selected, aes(x = Date, y = daily_positive, color = Country_Region, group = Country_Region)) +
  geom_line(size = 1) +
  labs(title = "Daily Positive COVID-19 Cases for 5 Randomly Selected Countries",
       x = "Date",
       y = "Daily Positive Cases",
       color = "Country") +
  theme_minimal() +
  theme(legend.position = "bottom") +
  scale_x_date(date_labels = "%b %Y", date_breaks = "1 month") + # Format dates for readability
  scale_y_continuous(labels = scales::comma) # Format y-axis with commas
```

## Project Structure
```
/covid-19-analysis  
│── data/               # Dataset (optional, ignored in .gitignore)  
│── README.md           # Project documentation  
|── covid_analysis.Rmd 
```

## Expected Output
- **A README file** summarizing the project.
- **Well-documented R scripts** for analysis and visualization.
- **Plots showcasing COVID-19 trends** in different countries.

## Conclusion
This project provides an in-depth analysis of COVID-19 trends across various countries. Using R, we extracted insights from the data, stored it efficiently in structured formats, and visualized key patterns to better understand the global COVID-19 situation.

