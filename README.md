**E-Commerce Customer Churn Analysis and Prediction**

Loyal customers are one of the most essential assets of growth in E-commerce. With the increase of competition in the e-commerce sector, companies do not focus on finding new customers, but also need to maintain existing customers, because the success rate of selling products to existing customers is relatively higher (60-70%) than to new customers (2-20%). Furthermore, the acquisition cost for finding new customers can be five times more expensive than maintaining existing customers.

**Problem Statement**

Based on this e-commerce dataset, there are 16.84% of customers who churn, whereas the average churn rate of customers in e-commerce should be 6-7%.

**Goals**

Predict customers who will tend to churn.

**Objective**

Decrease the e-commerce&#39;s churn rate by conveying recommendations based on characteristics of customers who have churn tendencies.

**EDA**

The data used in this analysis is an e-commerce dataset that contains a collection of customer data belonging to a leading e-commerce company. Overall this dataset has 5630 rows and 20 columns in which contains several NaN and duplicated data.

![Data](Capture.JPG)

When looking at the boxplot of each numerical column of the dataset, several outliers can be observed on each column which will later be filtered during the data cleaning process.

![Data](boxplot.png)

Based on the distribution, the majority of the dataset are positively skewed, especially data in WarehouseToHome, OrderCount, NumberOfAddress, DaySinceLastOrder, and CouponUsed column.

![Data](histogram.png)

When looking at the target of this dataset, this dataset has an imbalance class where from 5630 total customer, only 948 (16.84%) chooses to churn.

![Data](imbalance.JPG)

**XGBoost Modelling**

XGBoost (eXtreme Gradient Boosting) is a tree-based machine learning ensemble algorithm. XGBoost works as a boosting method by reducing bias and variance through re-weighting data that were misclassified by previous trees.

By Hyperparameter tuning and early stopping (to reduce the chance of overfitting), this particular XGBoost model has a classification report of:

![Data](classreport.JPG)

**Model Evaluation**

![Data](matrix.JPG)

This XGBoost model with a 94% recall can predict 138 (true positive) customers who choose to churn (actual number of customers who churn: 147). Of a total of 939 customers, XGBoost misclassified 9 customers that choose to churn and 47 customers that supposedly choose to not churn.

**Feature Importance**

![Data](shap.JPG)

The feature importance determination of this model uses the SHAP library due to XGBoost low interpretability nature. Based on SHAP illustration, the five most important features according to this machine learning model in classifying customer churn are:

- Tenure: Churn customers have a relatively low tenure period.

- Complaints: Customer who chooses to churn has filed complaints.

- Number of addresses: Customers who have several home addresses tend to churn (this, however, could not be intervened by the company)

- Day Since Last Order: the customer who churned are customers who have a relatively low number of days since their last order.

- Warehouse to home: Customer who chooses to churn has a relatively larger warehouse to home distance.

**Business Insights**

1. Complain and tenure

![Data](tenure.JPG)

The majority of customers who choose to churn have a tenure period of fewer than 6 months, or relatively speaking, new customers have a higher potential to churn.

New customers who choose to churn can be observed from the complaints they filed. In general, complaints can be the main factor in customer churn, where when a customer filed their complaints, an average customer will generally do specific things that are generally categorized into two actions:

1. Personal Actions: When a customer chooses to not purchase any more products from the company and/or share their negative experiences with those around them (negative word-of-mouth).
2. Public Actions: When customers filed complaints asking for compensations, and/or customers chooses to find other e-commerce (churn).

However, according to Fornell and Wernellfelt, customer complaints that are well-managed and are properly resolved can reduce the number of customer churn.

By this dataset, customers who have complained have a higher churn rate (32%) compared to customers who have never complained (11%)/ Because of the high churn rate of customers who complained, this e-commerce&#39;s complaint management needs to be reviewed and improved.

![Data](complain.JPG)

When the complaint churn rate is grouped according to tenure period, the relationship between tenure period and complaints can be observed, when new customers filed complaints (\&lt;6 months), the risk of churn is greater than customers with a longer tenure period (\&gt;6 months).

![Data](segment.JPG)

2. Warehouse to home

According to Llave Montiel and Lopez (2020), the geographic location of the customer&#39;s address has an important role in customer behaviour. There are three geographical

aspects that can affect churn, namely: 1) Socio-economic characteristics of the

customer&#39;s living environment, 2) The distance between the customer and their preferred

offline supermarkets, and 3) the interaction between customers in their

residential environment.

From this E-commerce dataset, the churn rate increases with the distance between the e-commerce&#39;s warehouse and the customer&#39;s residential address. This can be caused by the increase in shipping costs and the length of delivery time, these two things can make customers find other e-commerce with closer delivery distances or even make customers prefer to shop at an offline store

![Data](warehouse.JPG)

3. Day Since Last Order

From the graph of days since last order with churn rate, the highest churn rate is owned by customers who have just placed an order, there are possibilities that the customer who has just ordered had an unsatisfactory shopping experience and resulted in their choice churn.

![Data](daysince.JPG)

When observed in more detail of average order count of customers who churned, it turns out that customers who decided to churn have only ordered 1-2 times, this may support the claim that customers who churned are new customers and/or customers who rarely shop at this e-commerce.

![Data](totalorder.JPG)

The main cause of customer churn may be because of their complaint amount. From the graph of complaints and day since last order, the majority of customers who just ordered have filed for complaints. There is a possibility that the customer is not satisfied with the e-commerce service and decided to churn after only ordering 1-2 times.

![Data](totalcomplaints.JPG)

**Recommendations**

1. Create customer rewards &amp; loyalty programs to increase the tenure period. From the analysis above, it can be seen that tenure is a factor that is closely related to churn. Churn tends to occur more frequently in customers with lower tenure periods. One of the methods that can be recommended is gamification. With this more enjoyable loyalty program, it is hoped that it can foster customer motivation to use the specific e-commerce applications regularly.

2. Improve customer service performance to reduce complaints. From the results of the analysis, it can be concluded that high churn rates are related to the high level of complaints. Improving customer service performance can be done by using a chatbot that can help customers 24 hours and can respond to customers more quickly. In addition, it is also necessary to conduct complaint handling training on customer service so that they can provide better services to customers.

3. After obtaining data on customers who are predicted to churn, it is compulsory to follow up on these customers to prevent churn from happening. Follow up can be done with email marketing, by sending promos, asking for feedback, or doing a &#39;we miss you&#39; campaign. The promos given can be in the form of postage promos, considering the results of the analysis show that the farther the distance from the warehouse to the customer, the higher the churn rate. In addition, follow up can be done by sending personalized push notifications by mentioning the customer&#39;s name and providing specific or relevant promos for each customer.
