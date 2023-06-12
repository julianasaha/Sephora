# Sephora Skincare Product Recommender/Analysis
---
**Author:** Juliana Sahagun

## Table of Contents

<!--ts-->
   * [Prerequisites](#prerequisites)
   * [Background Information](#background-information)
   * [Problem Statement](#problem-statement)
   * [Methods](#methods)
        * [Data Collection](#data-collection)
        * [Data Cleaning](#data-cleaning)
        * [Exploratory Data Analysis](#exploratory-data-analysis)
        * [Text Analysis](#text-analysis)
        * [Modeling](#modeling)
   * [Conclusion](#conclusions)
        * [Recommendations](#recommendations)
        * [Further Steps](#further-steps)
   
   
## Prerequisites 
To successfully run this notebook, ensure the following requirements are met:
1. Download the "product_info.csv" file and the "reviews.csv" files. These files can be found at the following URL: https://www.kaggle.com/datasets/nadyinky/sephora-products-and-skincare-reviews
2. Make sure the downloaded files are saved in the same directory as this notebook or provide the correct file paths when loading the data


## Background Information
Sephora, operating both online and through physical stores worldwide, is a multinational retailer for beauty and personal care products. With an extensive selection of 340 brands and an impressive range of over 45,000 products, the company has emerged as a preferred choice for clients in search of a diverse array of top-notch skincare, makeup, fragrance, and haircare products. Sephora reinforces its dedication to "We Belong to Something Beautiful" by continually striving to provide exceptional customer service, innovative shopping experiences, and staying at the forefront of the ever-evolving beauty industry.

## Problem Statement

In the extensive selection of skincare brands offered at Sephora, promoting user exploration and engagement with diverse products and brands is key. This project aims to create a recommendation system that offers users highly rated product suggestions tailored to their specific skincare product searches. This recommendation system can be implemented as a weekly discovery feature. Additionally , by conducting text analysis on product reviews and utilizing  K-means clustering, we seek to extract valuable insights and group similar products together. Through these methodologies, we can enhance exposure to the wide range of skincare options available at Sephora, elevate user satisfaction, and ultimately drive sales growth.

## Methods

### Data Collection
The datasets used in this analysis were sourced from Kaggle which were  collected through a Python Scraper in March 2023, containing information about Sephora's products and product reviews.

**Data:** https://www.kaggle.com/datasets/nadyinky/sephora-products-and-skincare-reviews

1. The reviews’ datasets were loaded and combined, and then merged with the product information dataset to create the final dataframe.

### Data Cleaning 
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

### Exploratory Data Analysis
1. Summary statistics were presented  for the numerical features in the dataset to provide an overview of their distribution and central tendencies
2. Distribution plots were created to visualize the distributions of 'ratings', 'prices', and 'is_recommended'
4. Bar plots were generated to display the top 10 skincare brands, the top 10 most loved products, average prices by category, and the most affordable and most expensive skin care brands
6. A heatmap was constructed to identify any correlations among the numeric features

### Text Analysis
 The objective for text analysis is to uncover insights regarding the reasons behind people's product recommendations as well as the reasons why they do not recommend certain products.
1. Load a subset of clean data (n=100,000) including only 'review_text', 'is_recommended', 'brand_name','product_name',and 'rating’ columns for NLP analysis
2. Balanced the classes of reviews (recommended and not recommended products) to ensure equal representation
3. Performed initial exploratory data analysis by examining word count and length distributions in the review text for each class
4. Preprocess the data the data using regex to remove special characters and applied stemming and lemmatization to the text data to reduce words to their base forms and maintain the base meaning
5. Utilize count vectorizer to explore the most frequent bigrams for each class to help identify common occurrences of  two-word combinations in each review class.
6. Conducted sentiment analysis on all reviews and separately for each class.

### Modeling
#### KMeans Clustering

The main objective of using k-means clustering on skincare products at Sephora is to identify similarities and patterns within products found in these dataset.
1. To reduce running time, a subset of the data with a sample size of 50,000 was used
2. Preprocessing of the data included scaling numeric features and one-hot encoding categorical features
3. Optimal number of clusters was determined by evaluating the silhouette score as a metric
4. Final K-means model was built based on the number of clusters that achieved the highest silhouette score.
5. Exploratory data analysis was conducted on the resulting clusters, including 3D scatter plots, pair plots, top 10 products/brands and analysis of the mean values within each cluster
#### Recommender System
 The primary goal of this recommender system is to offer users product recommendations based on their search queries. For example, if a user is seeking a new sunscreen, the system will present 2-3 appropriate options for them to explore, similar to a weekly discovery feature but focused on their exact product of interest.
1. Load data about product and rating information only
2. A new column was created through feature engineering to combine both the product and brand name 
3. A function was implemented to clean the product names by removing special characters and converting them to lowercase. This was done to simplify the search process for product names.
4. TF-IDF(Term Frequency-Inverse Document Frequency) was utilized to convert the product names into numerical representations
5. A search function was developed to calculate the similarity between the search term and product names using cosine similarity. The function returns the results based on the similarity scores
6. An interactive recommendation widget was created by constructing a function that identifies similar products/brands based on users who have tried and recommended the same product. IPYwidgets was utilized to display the results.

### Observations

##### Text analysis revealed the following insights:

Recommended Products:

- Users appreciate products that go a long way, address specific skin concerns, leave a positive feeling, and have long-term usage.
- Positive experiences were reported by long-time users and those trying the products for the first time.
- Consistency in nightly use was mentioned.

Not Recommended Products:

- Users were disappointed when not seeing expected differences or felt the products didn't justify their price.
- The value for money and availability of better alternatives were mentioned.
- Honest feedback expressed dissatisfaction or disappointment.

##### Application of Kmeans

By applying the k-means clustering algorithm, the products were divided into three distinct clusters.

- Cluster 0: High-rated, recommended, affordable products with high review counts. 

- Cluster 1: Low-rated, not recommended, expensive products with low review counts.

- Cluster 2: Highest-rated, highly recommended, higher-priced products with low review counts. 

#### Recommendations

Based on these findings, I recommend moving forward with implementing the insights gained from the analysis. They provide valuable information for promoting the exploration of different brands at Sephora and understanding user preferences and dislikes. Knowing that there are typically three types of products at Sephora can help guide marketing strategies and product placement. Additionally, implementing the recommendation model would not only be fun but also beneficial for Sephora, enhancing the customer experience and driving sales.

#### Further Steps

*Optimization*: This could be done by going back and looking into alternative recommendations algorithms which  could involve considering collaborative filtering, content-based filtering, or hybrid approaches to improve the accuracy and diversity of recommendations. Also, looking into what features can help personalized recommendations further can be useful.

*Data Enrichment*: As the system currently does not include all the brands and products carried by Sephora, it's important to continuously update the dataset with new products that have been recently launched. This ensures that the recommendation system stays up to date and can provide recommendations for the latest offerings. To further expand on our system's limits, we can inlcude makeup,frangance and haircare products as well.

---
For Further Information:
For any additional questions or concerns in regards to my work, please contact me at julianas4013@gmail.com. Thank you!
