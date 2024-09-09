# OkCupid Profile Information Analysis

## Overview

This project analyzes data from OkCupid profiles, focusing on demographic information, lifestyle choices, and sentiment analysis of user essay responses. The goal is to extract meaningful insights into user behaviors, profile completion rates, and trends in income and sentiment based on demographic and lifestyle factors. The analysis also identifies potential correlations between specific profile attributes and user-reported income and sentiment.

## Table of Contents

1. [Introduction](#introduction)
2. [Data Source](#data-source)
3. [Data Preprocessing](#data-preprocessing)
4. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis)
   - [Handling Missing Values](#handling-missing-values)
   - [Outlier Detection](#outlier-detection)
   - [Profile Completion Rates](#profile-completion-rates)
5. [Feature Engineering](#feature-engineering)
   - [Body Type Mapping](#body-type-mapping)
   - [Diet Mapping](#diet-mapping)
   - [Job Mapping](#job-mapping)
   - [Sentiment Ratio Calculation](#sentiment-ratio-calculation)
6. [Modeling](#modeling)
   - [Lasso Regression for Income Prediction](#lasso-regression-for-income-prediction)
   - [Decision Tree for Sentiment Prediction](#decision-tree-for-sentiment-prediction)
7. [Findings and Insights](#findings-and-insights)
   - [Key Findings](#key-findings)
   - [Managerial Recommendations](#managerial-recommendations)
8. [Conclusion](#conclusion)

## Introduction

This project analyzes OkCupid profiles to uncover patterns in user preferences, behaviors, and the relationship between various profile attributes such as job type, pet preferences, and income. Additionally, the project aims to understand the sentiment of user essays and how lifestyle choices influence user sentiment and income levels. The [OkCupid dataset](https://www.kaggle.com/datasets/andrewmvd/okcupid-profiles) was taken from kaggle.

## Data Source

The dataset used in this project was sourced from public OkCupid profiles. The key fields in the dataset include:

- **Mandatory Fields**: Age, Status, Sex, Orientation
- **Optional Fields with "Prefer Not to Say" Option**: Body Type, Height, Languages, Ethnicity, Religion, Education, Employment, Sign, Drinks, Smoking, Drugs, Diet, Children, Pets

## Data Preprocessing

To prepare the dataset for analysis, the following steps were taken:

1. **Handling Missing Values**: 
   - Replace missing values in columns with "unknown".
   - Drop rows with missing values in the essay responses, as these are critical for sentiment analysis.

2. **Outlier Detection**:
   - Remove outliers for age (greater than 69).
   - Replace missing values for height with the median value.

3. **Profile Completion Rates**:
   - Calculate profile completion rates by counting the non-null fields for each profile.

## Exploratory Data Analysis

### Handling Missing Values

The dataset had a significant number of missing values across various optional fields, such as income and offspring. The NaN values were replaced or filled as part of the data preprocessing.

### Outlier Detection

Outliers in fields like age were detected and removed, and missing values in critical fields were replaced with appropriate values (e.g., median for height).

### Profile Completion Rates

The dataset was analyzed to identify patterns in profile completion. Most users complete about 80% of their profiles, and key fields like income and offspring were frequently left blank.

## Feature Engineering

### Body Type Mapping

The body type field was simplified into categories like **overweight**, **curvy**, **athletic**, and **skinny** to make analysis more robust.

### Diet Mapping

Dietary preferences were grouped into categories such as **omnivore**, **vegetarian**, **vegan**, and **other** based on the user's response.

### Job Mapping

Job roles were categorized into broader groups such as **Tech**, **Finance**, **Creative**, and **Blue Collar** to reduce dimensionality and enhance interpretability.

### Sentiment Ratio Calculation

The sentiment ratio of user essay responses was calculated using the **Opinion Lexicon** from NLTK. The ratio of positive to negative words in user essays was used to determine overall sentiment.

## Modeling

### Lasso Regression for Income Prediction

A **Lasso Regression model** was used to predict income levels based on features such as job type, drinking habits, pet preferences, and family planning choices. The coefficients from the model indicated that lifestyle choices like drinking habits and drug use were strongly correlated with income.

### Decision Tree for Sentiment Prediction

A **Decision Tree Regressor** was used to predict the sentiment ratio of user essays based on demographic and lifestyle features such as age, job, and drinking habits. The tree highlighted that age and income were strong predictors of sentiment.

## Findings and Insights

### Key Findings

1. **Income Correlates**: Retired individuals, people who dislike dogs, and individuals who want kids tend to have higher income levels. Additionally, drinking and drug use were positively correlated with income.
2. **Sentiment Analysis**: Older users tend to have more positive essays, and men who drink frequently have higher positivity scores in their essays.
3. **Profile Completeness**: Users tend to leave optional fields like diet, offspring, and religion blank, but generally fill in key mandatory fields like age and orientation.

### Managerial Recommendations

1. **Profile Optimization**: Encourage users to fill out more optional fields like offspring and religion, as these are critical for matching algorithms.
2. **Sentiment-Based Matching**: Incorporate sentiment analysis in matching algorithms to pair users with similar sentiment scores, even if they haven’t filled out essay responses.

## Conclusion

This project provides insights into OkCupid user behavior, including correlations between income, sentiment, and lifestyle choices. By leveraging these insights, OkCupid can improve its matching algorithms, enhance user experience, and potentially boost premium subscription sales.
