# Sephora-Product-Recommender-Analysis
---
Author: Juliana Sahagun

## Table of Contents



## Background Information
Sephora, operating both online and through physical stores worldwide, is a multinational retailer for beauty and personal care products. With an extensive selection of 340 brands and an impressive range of over 45,000 products, the company has emerged as a preferred choice for clients in search of a diverse array of top-notch skincare, makeup, fragrance, and haircare products. Sephora reinforces its dedication to "We Belong to Something Beautiful" by continually striving to provide exceptional customer service, innovative shopping experiences, and staying at the forefront of the ever-evolving beauty industry.
## Problem Statement

**Data:** https://www.kaggle.com/datasets/nadyinky/sephora-products-and-skincare-reviews
### Methods
#### Data Collection
The datasets used in this analysis were sourced from Kaggle which were  collected through a Python Scraper in March 2023, containing information about Sephora

1. The reviews’ datasets were loaded and combined, and then merged with the product information dataset to create the final dataframe.
#### Data Cleaning 
1. A function was created to perform basic cleaning on the dataframe
     - Unnecessary columns were removed
     - Duplicate rows were dropped
     - Columns and rows with more than 50% missing values were eliminated
     - Rows without information in the text column were dropped
     - Null values in the "is_recommended" column were imputed based on the corresponding rating
     - Null values in the "review_title" column were imputed with the value "missing"
     - Remaining null values were imputed with the value "Not specified"
     - Columns were converted to the correct data types
    - Column names were renamed to improve clarity
2. Verified consistency between categorical values and numeric values
3. Saved the cleaned dataframe into a CSV file for further use

#### Exploratory Data Analysis
1. Summary statistics were presented  for the numerical features in the dataset to provide an overview of their distribution and central tendencies
2. Distribution plots were created to visualize the distributions of 'ratings', 'prices', and 'is_recommended'
4. Bar plots were generated to display the top 10 skincare brands, the top 10 most loved products, average prices by category, and the most affordable and most expensive skin care brands
6. A heatmap was constructed to identify any correlations among the numeric features


Preprocessing
Modeling
Conclusions & Recommendations
Further Steps

---
For Further Information:
For any additional questions or concerns in regards to my work, please contact me at julianas4013@gmail.com. Thank you!
