# Predicting_Car_Price

_**Objective of this excercse is to build a model that determines the key components that drives the price of the car. This involves identifying and quantifying the most influential variables (features) that impact used car prices using statistical analysis and machine learning techniques.The goal is to extract actionable insights and build a model that can generalize well to unseen (test) data.
**_

**Data Understanding:**

**First Step is to Analyze the data (Cleansing Data):**

1. Remove Duplicates. 
  NOTE: I did not remove duplicates based on VIN, if i did, that takes away 60% of the data. Infact i dropped the VIN column considering it has incorrect values with duplicate entries.
2. Drop Size columns as it does not have values more than 30%
3. Convert Year to Age
4. Identify Outliers, using Percentile and considering 99% Percentile

**Steps for understanding the data (EDA Techniques Used):**

1. Univariate Anlaysis - Price Column - Understand its range
2. Analysis on the Other Numerical - Understand their relationship with Price
3. Bivariate Analysis - Perform Histograms and Pairplot Analysis on Numerical Columns - Visual Represenation of the relationship between the features with Price
4. Detailed analysis on Categorical Columns and their relationship with the Price Column
5. Correlation Analysis on numerical Columns

**Data Preparation:**

1. Perform Feature Selection using PCA 
2. Convert Year to Age
3. Categorical Columns to numerical using One Hot Encoding
4. Using Percentile methods to filter out Outliers
5. Removing High Cardinality categorical features such as Manufacturer, Model and state

**Modelling**

1. Performing Linear Regression, Lasso and Ridge models
2. Provide Density Plot on the features
3. Scale the data using Standard Scaler

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

**HyperParameters**

GridSearch CV in combination with Lasso or Ridge helps us to point to the Optimal Value of Alpha. It recommends 20 for Ridge and 5 on Lasso.

Overall Conclusion is that the more features we fit, the models perform better, however it can lead to OverFitting scenarios that one needs to be cautious. Based on the PCA analysis we see that fitting 6 features would be ideal. Anthing beyond that would not make much impact on the Car Price Prediction

![image](https://github.com/user-attachments/assets/ea485c19-bb60-4249-ab28-c4f9409e99d4)

When we increase the alpha to fine tune, we see that the Lasso or Ridge, identifies the features that are important, and reduces the cooefficient for other colums. Ridge reduces towards zero, while the Lasso complete reduces them to zero removing the features from being considered to improve the mode performance.

The Advantages of using Gridsearch is that it identifies the optimum alpha (hyperparameter value) for the model.  Based on the running GridSearch CV and Ridge and Lasso. It suggests that the Optimal Value for the Alpha that is the hyperparameter value as **5** for **Ridge** and **20** for **Lasso**. 

This means that Ridge uses 5 as a standardization value and drive other features or coefficients towards zero, while Lasso optimal model is aggressive in terms of feature selection.  


**Conclusion**

In Conclusion, the Ridge and Lasso Model perform very close in both Training and Test Model when compared to Liner regression with 200k data set. However, If we further clean the data and reduce it to 50k rows, removing all VIN duplicates, nulls and other values. We can see that Lasso performs better in the alpha range of 100 when compared to Ridge. 


Finally Extractig the non zero coefficients from the Lasso Model reveal that, **Condition, Tranmission, Fuel, Type, Year and Odometer drive the price of the car**
