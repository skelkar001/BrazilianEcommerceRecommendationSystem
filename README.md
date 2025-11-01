# BrazilianEcommerceRecommendationSystem

## Capstone Project
Recommendation system for Brazilian E-commerce platform
By; Shantanu Kelkar

###Executive Summary

This report presents a comprehensive analysis of recommendation systems developed for a Brazilian ecommerce platform. The data comprises 96k unique orders, which include 32k unique products, spanning 93k unique customers

There are 5 distinct recommendation systems implemented: Simple content-based filtering, Context-aware content-based filtering, Collaborative filtering, Popularity-based recommendations and Market basket analysis. Each approach addresses problems. In the real-world, a combination of these approaches will be needed to meet customer satisfaction and business objectives.

### Exploratory Data Analysis: Key Insights

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




