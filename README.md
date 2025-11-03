# **BrazilianEcommerceRecommendationSystem**

## **Capstone Project**
Recommendation system for Brazilian E-commerce platform
By; Shantanu Kelkar

### **Executive Summary**

This report presents a comprehensive analysis of recommendation systems developed for a Brazilian ecommerce platform. The data comprises 96k unique orders, which include 32k unique products, spanning 93k unique customers

There are 5 distinct recommendation systems implemented: Simple content-based filtering, Context-aware content-based filtering, Collaborative filtering, Popularity-based recommendations and Market basket analysis. Each approach addresses problems. In the real-world, a combination of these approaches will be needed to meet customer satisfaction and business objectives.

### **Exploratory Data Analysis: Key Insights**

Data source link: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

Data files are uploaded at this gdrive location: https://drive.google.com/drive/folders/1eYIplrKW7M-0P1CfJXAjjlXMZwjlGK5W?usp=sharing


The entire dataset comprised 7 different csv files:
- orders.csv: **main** data set comprising all the orders for a Brazilian ecommerce platform
- order items. csv: contains list of items associated with each order
- customers.csv: contains details about the customers who made the orders
- products.csv: contains product descriptions for items contained in the orders
- reviews.csv: customer reviews for orders
- payments.csv: payment details for each order
- product category.csv: translation of product category name into english
  
A master dataset was created by combining all the above .csv files. Following are the key insights drawn by analysing this data

#### Insight #1: The data indicates a very low repeat purchase rate. 
There are 96516 orders from 93k unique customers. That represents roughly 1.03 orders per customers. This implies most customers are first time customers. This data may have been a snapshot during from early days of the platform or suffers from low customer retention

#### Insight #2: Most customers were happy with their experience
The average customer review score per order is 4.03 and 75% of the orders were rated 4 and above. More than half the orders (~56%) were rated 5 stars

#### Insight #3: Household items were the biggest draw
Categories such as bed-bath-table, furniture, and housewares were some of the most popular (based on number of orders) product categories. Besides these, health & beauty, computer accessories were the other popular items

#### Insight #4: The ecommerce platform likely caters to relatively affluent population 
The average item price was 120 (currenncy is not known but probably is Brazilian Real) which is equivalent to US$180 if one applies GDP/capita as the conversion factor. This is a relatively high price point that masses may not be able afford

#### Insight #5: Boleto and credit cards are most popular payment methods
This is not a surprise that credit cards and boleto were the most popular payment methods. Boleto is unique to brazil and is popular due to the prevalence of cash economy

#### Insight #6: Average order size was 1.2 items
Over 86% of the orders had only single item


### Recommendation Algorithms

Five distinct approaches were implemented with each tapping into the unique aspects of product and/or user pattern

##### Model 1: Simple content-filtering

**Approach:** Product features (including review score) are leveraged to determine similarity (cosine similarity) amongst them. Top 10 most similar products, per this criteria, are recommended to the user for a given sample product 

##### Model 2: Context-aware content-filtering

**Approach:** In addition to product features (including review score), freight costs, payments data and state level popularity trends are considered. The final scoring is determined as a weighted average of product similarity, state popularity, review score, freight charges. This approach accounts for geographic variations, which can be significant

##### Model 3: Collaborative filtering

**Approach:** SURPRISE library was leveraged to experiment multiple recommendation algorithms such as SVD, NMF, KNNBasic (user- and item-based). Since most orders were single-item purchases and one-time customers, the efficacy of collaborative filtering will be limited. NMF was the best performer, followed by SVD and KNNbasic respectively.

##### Model 4: Popularity-based recommendations (most purchased + highly rated)

**Approach:** Taking inspiration from Amazon e-commerce experience, I also implemented most purchased and highest rated product features

**Insights:** Each product was purchased 3.6 times on average. And top 10% of products (roughly 3.1k) accounted for 29% of all purchases. This shows the power i.e. impact of popularity based recommendation approach. 


##### Model 5: Market-basket analysis

Approach: Taking inspiration from Amazon's 'Customers who bought this item also bought...' recommendation, I implemented a market-basket analysis. This involved using a library called mlxtrend to unearth causal relationships between products. These relationships are called association rules.

Insights: 
 - Only 64 frequently purchased itemsets were found. Each itemset denotes a collection of items that were observed to be purchased together at a frequency greater than minimum support threshold specified in the code
 - From these frequent itemsets, six association rules were discovered wherein
   - Each rule showed very strong lift. This implies the likelihood 'consequent' purchase increases significantly
   - Average confidence of 63%. This implies the rules are highly reliable
   - But the support for each rule was low. This implies these may be niche combinations that are not purchased as frequently. But whenver it happens, the confidence level of predicting the consequent is high
  

### Conclusions & recommenation

The data set used was highly skewed towards one-time purchases. This situation is a also called as a cold-start problem in the industry since it is hard to glean significant insights from user preferences. Collaborative filtering has limited impact in such situations. Hence, I also implemented content filtering and popularity based approaches. These approaches are shown to recommend the top N (N=10: default) products for a given sample product.

A meaningful, production-ready recommendation system, for such an e-commerce platform, will be a combination of the approaches implemented above. This will allow capturing various patterns of user behavior, product interconnections and even geographical/regional trends. Additionally, a hybrid recommender could also be developed which will be a weighted average of the aforementioned recommendation approaches

### Next steps

I faced challenges in
a) Implementing gridsearch - constantly running into 'kernel dead' error - due to large computational load. Hence, the respective code is commented out
b) Implementing cross-validation: I had to reduce the folds to 3 from 5 to reduce the computational load

The following aspects were not attempted due to time constraints but may be worth considering:
a) Developing an overall hybrid recommender which would be weighted average of all the 5 approaches implemented
b) Optimizing the weights used in approach #2 and approach #4









