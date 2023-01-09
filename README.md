# Predictive Model - Churn Rate

![image](https://user-images.githubusercontent.com/95591600/211230472-66baf2c5-2bea-4d7f-a62a-de0aa43c20e1.png)


SyriaTel Communications is a telecommunications company that aims to predict and prevent customer churn. Customer churn is when a customer cancels their service with the company. This is a significant issue for service-based companies as it is costly. The company not only loses the customer's monthly or yearly payment, but it also incurs a cost to acquire a new customer to replace the one who has left.

To address the problem of customer churn, I conducted an Exploratory Data Analysis (EDA) and built a machine learning classifier that predicts which customers are likely to churn. This allows SyriaTel to implement a more effective strategy to retain its customers.

In the EDA phase, I analyzed the following questions:

- Is calling customer service a sign of customer dissatisfaction and potential churn?
- How does the international plan and the voicemail plan impact on whether a customer will churn in the near future or not?

This project used the churn in telecoms dataset, which can be found in the data folder and on Kaggle. The dataset includes 21 columns and 3333 unique values. It was already relatively clean with no large outliers or null values.

## EDA

---

### Customer service calls

For this part, I splitted the data frame into 2 groups, people who churned and people who stayed and see how their metrics differed.

As you guys can see customers who churned have on average 2.2 customers service calls compared to the 1.4 average customer service calls from customers who stayed. This is an great indicator to look at

![customer_service_calls](https://user-images.githubusercontent.com/95591600/211230938-761c46f5-a8a7-4294-94ba-ceb62a1cc37c.png)

recommendation:

To follow up with customers who've called customer service 2x or more 

### International plan

For this graph we are going to look at the same 2 groups, but this time proportionally.

As you guys can see, a much bigger proportion of people who churn are in the international plan, this could be for a number of different reasons. The first one is that customers are dissatisfied with the service or the second one could be that a competitor has a much better service that customers are willing to drop their current plan and change providers.

![international_plan](https://user-images.githubusercontent.com/95591600/211231685-8aceb2f8-3c9b-4042-8bb5-be86b4f2e615.png)

recommendation:

The company needs to address the problem, this is a clear indicator that the international plan has a negative effect on customer retention.


### Voicemail plan

Same as the international plan, we are looking at the 2 groups proportionally, and we se that voicemail plan tends to have a positive impact on customer retention.

![voicemail_plan](https://user-images.githubusercontent.com/95591600/211232326-bc2b545c-ccf2-463d-9021-6ccb6f80f44c.png)

recommendation:

Promote the voicemail plan since it has a positive impact on customer retention.

---

## Predictive Model

The baseline model: 85.5% accuracy for the majority group FALSE (Customers who stayed)

Since the target we are trying to predict is a binary outcome, originally I thought the log regression was going to perform best, but since the features in the data provided didn't really have a linear correlation, a non-parametric model worked best.

First Step:

Built a pipeline that separates the numerical data from the objects, then I used a column transformer and made the numerical values Standard Scaler and the object values OneHotEncoder.

Then I split the data into Training and Testing data, and fitted my pipeline.

Second Step:

Once the pipelines were in place I tested multiple Machine learning models with their respective accuracy:

- Logistic Regression:  0.8545727136431784
- Random Forest:  0.8860569715142429
- Decision Tree:  0.8140929535232384
- K-Nearest Neighbors:  0.8650674662668666

Third Step:

GridSearch for Random forest since it was the most accurate model out of all the rest. Hypertuned the parameters and came up with a more accurate model.

Random Forest: 0.8905547226386806

Here is a look at the confusion matrix:

![image](https://user-images.githubusercontent.com/95591600/211236978-89557dbf-a228-4c3f-9381-b8a5771b5653.png)






