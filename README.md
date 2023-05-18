# Product Personalization Engine (Recommendation-System)

## Data Collection
Data for this project was collected from open source amazon review dataset. The data deals with sports and outdoor equipment. The dataset contains 435924 rows and 12 columns. Originally, the dataset was contained as a .json file.

## Techniques Used
### 1. Collaborative Filtering using Alternating Least Squares(ALS) 

Collaborative Filtering:  A filtering technique which analyses information about users with similar tastes to assess the probability of what a target individual will enjoy (a similar product, movie, book etc.). It depends on past interactions recorded between users and items in order to produce new recommendations. The more users interact with products, the more new recommendations become accurate. But because it only considers past interactions to make recommendations, this method of filtering suffers from the “cold start problem” - it is impossible to recommend anything to new users or recommend a new item to any users and many users or items have too few interactions to be efficiently handled. However, there are ways to address the cold-start problem.

Alternating Least Squares (ALS): In this method we have a large matrix and we factor it into smaller matrices through alternating least squares. We end up with two or more lower dimensional matrices whose product equals the original one. ALS comes inbuilt in Apache Spark.
To pre-process the data, the productID and reviewerID columns had to be converted from string to integer using a string indexer in order to prepare them for the ALS regression. While building the recommendation model using ALS on the training data, the ‘cold-start-strategy’ was dropped to avoid getting NaN value in evaluation metrics. Cold starts occur when it is attempted to predict a rating for a user-item pair but there were no ratings for this user/item in the training set. Dropping the cold-start-strategy simply removes those rows/columns from the predictions and from the test set. The result will therefore only contain valid numbers that can be used for evaluation.  
