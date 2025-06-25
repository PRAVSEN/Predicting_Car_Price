# Predicting_Car_Price

_**Objective of this excercse is to build a model that determines the key components that drives the price of the car. This involves identifying and quantifying the most influential variables (features) that impact used car prices using statistical analysis and machine learning techniques.The goal is to extract actionable insights and build a model that can generalize well to unseen (test) data.
**_

**Data Understanding:**

**First Step is to Analyze the data (Cleansing Data):**

Remove Duplicates. 
  NOTE: I did not remove duplicates based on VIN, if i did, that takes away 60% of the data. Infact i dropped the VIN column considering it has incorrect values with duplicate entries.
Drop Size columns as it does not have values more than 30%
Convert Year to Age
Identify Outliers, using Percentile and considering 99% Percentile

**Steps for understanding the data (EDA Techniques Used):**

Univariate Anlaysis - Price Column - Understand its range
Analysis on the Other Numerical - Understand their relationship with Price
Bivariate Analysis - Perform Histograms and Pairplot Analysis on Numerical Columns - Visual Represenation of the relationship between the features with Price
Detailed analysis on Categorical Columns and their relationship with the Price Column
Correlation Analysis on numerical Columns

**Data Preparation:**

Perform Feature Selection using PCA 
Convert Year to Age
Categorical Columns to numerical using One Hot Encoding
Using Percentile methods to filter out Outliers

**Modelling**

Performing Linear Regression, Lasso and Ridge models
Provide Density Plot on the features
Scale the data using Standard Scaler

**Evaluation**

**Scenario 1:** Use Alpha value 1 as Hyper Parameter with Odometer and Age against the price

Evaluate the Linear Regression by comparing its performance against Lasso and Ridge models show the Optimal Value for 

![image](https://github.com/user-attachments/assets/871258fb-1570-4240-8452-762690666a7e)

![image](https://github.com/user-attachments/assets/fc54c311-c210-41cc-9bf0-cfe4d4cbc97d)


The Results show that if the car price range is near 20k the Predictions are near the same. Whereas if the price of the car is at the range of 40k, the prediction came down to 22k. Overall both the Linear, Ridge and Lasso model performs the same as the optimal alpha value is 0.001 which means that it is closer to 0 leaning towards Linear Regression. 

**Scenario 2:** Use Alpha value 200 as Hyper Parameter with Odometer and Age against the price, We see that Ridge and Linear models perform better than the Lasso. 

![image](https://github.com/user-attachments/assets/780d70a6-cf06-4804-9a5a-5625663334bb)



![image](https://github.com/user-attachments/assets/dc761886-dc3f-4bd1-96bf-122fc3f8106b)

**Scenario 3:** Use Alpha value 1 as Hyper Parameter adding around 20 features, We see that Ridge and Linear models perform better than the Lasso. We see that all 3 models perform better with predictions close to price range at 20k levels. However the deviation is still true on the 40k range and the below 10k range

![image](https://github.com/user-attachments/assets/a227f926-d4f6-4c56-96be-b2857072de31)

We see that the Testing RMSE is lower than Training to our surprise

![image](https://github.com/user-attachments/assets/5b59d1c0-093d-4ece-9cd4-340e87811142)


