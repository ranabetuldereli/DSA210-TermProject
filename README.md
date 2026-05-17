# DSA210 Term Project  
## Socioeconomic and Demographic Factors in Cardiovascular Mortality Across U.S. Counties

This repository contains my term project for **DSA 210 – Introduction to Data Science** in the **Spring 2025–2026** semester.

The project investigates how county-level poverty and demographic composition are associated with cardiovascular mortality rates across the United States.

---

## Motivation

My motivation for this project comes partly from my personal observations during the approximately six months I spent in the United States. During that time, I noticed that living conditions, lifestyle patterns, access to resources, and regional environments could differ significantly across communities and locations. These differences made me more curious about how social, economic, demographic, and regional factors might be connected to health outcomes.

Cardiovascular mortality is not only a medical issue, but also a social and economic issue. Health outcomes can be influenced by poverty, access to healthcare, neighborhood conditions, regional inequalities, and demographic composition. Because of this, I wanted to turn my observations into a data-driven research project and examine whether county-level poverty and demographic variables are associated with cardiovascular mortality rates.

Instead of focusing only on national-level averages, this project analyzes county-level data to better observe local differences. The main goal is to understand whether counties with different socioeconomic and demographic characteristics also show different cardiovascular mortality patterns.

The main research question is:

**How are poverty levels and demographic composition associated with cardiovascular mortality rates across U.S. counties?**

---

## Overview

This project follows the main stages of the data science pipeline:

1. Data collection and preparation  
2. Exploratory data analysis  
3. Hypothesis testing  
4. Machine learning modeling  
5. Model comparison and interpretation  
6. Final report and limitations  

The project combines poverty, demographic, and cardiovascular mortality data at the county level. The goal is to understand whether socioeconomic and demographic variables are statistically associated with cardiovascular mortality and whether they can be used to predict mortality rates.

The results are interpreted as **county-level associations**, not as causal relationships.

---

## Data to be Used

This project uses three county-level datasets:

- **Poverty data** from the U.S. Census Bureau  
- **Demographic data** from the U.S. Census Bureau  
- **Cardiovascular mortality data** from a Kaggle dataset  

The datasets were merged at the county level. The main variables used in the analysis are:

- `poverty_rate`
- `black`
- `white`
- `hispanic`
- `mortality_rate`

The mortality dataset was enriched with poverty and demographic variables in order to analyze the relationship between socioeconomic conditions and cardiovascular mortality outcomes.

---

## Methodology

The methodology consists of four main parts: data preparation, exploratory data analysis, hypothesis testing, and machine learning.

### Data Preparation

The datasets were loaded, cleaned, and merged into a single county-level dataset. Since the datasets came from different sources, county and state information had to be aligned before merging.

Main preparation steps included:

- Loading the poverty, demographic, and mortality datasets
- Cleaning county and state information
- Merging datasets at the county level
- Selecting relevant variables
- Handling missing or incompatible values
- Preparing the final dataset for analysis and modeling

### Exploratory Data Analysis

Exploratory data analysis was used to understand the structure of the dataset and observe initial patterns.

The EDA focused on:

- Summary statistics
- Distribution of poverty rates
- Distribution of cardiovascular mortality rates
- Relationship between poverty and mortality
- Relationship between demographic variables and mortality

The EDA suggested that counties with higher poverty rates generally tend to have higher cardiovascular mortality rates. However, the relationship is not perfect, which suggests that other factors also influence mortality outcomes.

---

## Hypothesis Test

Hypothesis testing was used to evaluate whether the relationships observed during EDA were statistically significant.

The main hypothesis tests were:

### 1. Poverty Rate and Cardiovascular Mortality

The Pearson correlation between poverty rate and cardiovascular mortality rate was:

- Correlation coefficient: `0.553`
- p-value: `3.018e-250`

This indicates a moderate positive and statistically significant association. Counties with higher poverty rates tend to have higher cardiovascular mortality rates.

### 2. High-Poverty vs. Low-Poverty Counties

A Welch two-sample t-test was used to compare mortality rates between high-poverty and low-poverty counties.

The result was:

- t-statistic: `31.164`
- p-value: `2.403e-184`

The result was statistically significant, showing that high-poverty and low-poverty counties differ significantly in cardiovascular mortality rates.

### 3. Black Population Share and Cardiovascular Mortality

The Pearson correlation between Black population share and cardiovascular mortality rate was:

- Correlation coefficient: `0.387`
- p-value: `2.236e-112`

This shows a statistically significant positive association. However, this result should be interpreted carefully because demographic composition may reflect broader socioeconomic, regional, and structural inequalities.

### 4. White Population Share and Cardiovascular Mortality

The Pearson correlation between White population share and cardiovascular mortality rate was:

- Correlation coefficient: `-0.294`
- p-value: `2.101e-63`

This shows a statistically significant negative association. This result should also be interpreted as a county-level association rather than a causal relationship.

Overall, the hypothesis tests supported the patterns observed during EDA. Poverty showed the strongest association with cardiovascular mortality among the tested variables.

---

## Machine Learning (ML)

The machine learning part of the project tested whether poverty and demographic variables could be used to predict cardiovascular mortality rates.

Since the target variable, `mortality_rate`, is continuous, this is a **regression problem**.

The models compared were:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor

Random Forest was selected as the main model because it combines the predictions of multiple decision trees and can capture more complex, non-linear patterns than a simple linear model.

### Model Comparison Results

| Model | MAE | RMSE | R-squared |
|---|---:|---:|---:|
| Linear Regression | 34.568 | 45.914 | 0.402 |
| Decision Tree Regressor | 35.917 | 47.183 | 0.368 |
| Random Forest Regressor | 33.130 | 43.917 | 0.453 |

The Random Forest Regressor performed best among the tested models. It had the lowest MAE and RMSE values and the highest R-squared score.

However, the model performance was still moderate. The R-squared value of `0.453` means that the model explained about 45.3% of the variation in cardiovascular mortality rates. This suggests that poverty and demographic variables contain meaningful predictive information, but they are not enough to fully explain cardiovascular mortality differences across counties.

### Feature Importance

The Random Forest feature importance results showed that `poverty_rate` was the most important predictor.

| Feature | Importance |
|---|---:|
| poverty_rate | 0.575 |
| hispanic | 0.173 |
| black | 0.158 |
| white | 0.093 |

This result supports the EDA and hypothesis testing findings, where poverty also showed the strongest association with cardiovascular mortality.

Feature importance should not be interpreted as causality. It only shows which variables were most useful for prediction in the model.

---

## Limitations & Future Work

This project has several limitations.

First, the analysis is based on county-level data. Therefore, the results describe patterns across counties, not individual-level outcomes.

Second, the results are correlational, not causal. The analysis can show associations between poverty, demographic composition, and cardiovascular mortality, but it cannot prove that one variable directly causes another.

Third, the machine learning model uses a limited number of variables. Cardiovascular mortality is affected by many other factors that were not fully included in this project, such as:

- Healthcare access
- Insurance coverage
- Age distribution
- Smoking rates
- Obesity rates
- Diet and physical activity
- Urban-rural differences
- Regional health policies

Future work could improve the analysis by adding more health, behavioral, economic, and regional variables. More advanced models or regional subgroup analyses could also be used to better understand why some counties experience higher cardiovascular mortality rates than others.

---


## AI Usage Disclaimer

AI tools were used as supporting tools during this project, including both the coding and writing stages. They were used to help with code organization, debugging, explaining statistical and machine learning concepts, interpreting model evaluation results, and structuring the final report.

Specifically, AI assistance was used for:

- Organizing and improving Python notebook code
- Debugging errors and clarifying code logic
- Explaining statistical concepts such as p-values, correlation, and hypothesis testing
- Explaining machine learning concepts such as regression, Random Forest, baseline models, MAE, RMSE, and R-squared
- Interpreting model outputs and feature importance results
- Structuring and improving the final report and README
- Planning the GitHub submission workflow

The datasets, code execution, analysis results, model outputs, and final project decisions were reviewed by the student. AI assistance was used as guidance and support, not as a replacement for the student's own work.

## Project Structure


DSA210-TermProject/
│
├── datasets/
│   ├── demographics.csv
│   ├── mortality.csv
│   └── poverty2010.csv
│
├── DSA 210 Project Proposal.pdf
├── DSA210_Milestone1_EDA.ipynb
├── DSA210_Milestone2_ML.ipynb
├── 2026-05-18_Milestone2_ML_Final_Version.ipynb
├── final_report.md
├── requirements.txt
└── README.md