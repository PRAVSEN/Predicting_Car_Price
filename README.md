# Predicting_Car_Price

Objective of this excercse is to build a model that determines the key components that drives the price of the car. This involves identifying and quantifying the most influential variables (features) that impact used car prices using statistical analysis and machine learning techniques.The goal is to extract actionable insights and build a model that can generalize well to unseen (test) data.


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

**Model Evaulation:**

For a Polynomial Transformer value of **Degree 3**, after standardizing the data, Here are some of the scearnios being tested.

**When Alpha =1 **, Linear Ridge and Lasso Model perform very close. You can refer to images/Alpha1.png to review the results. As the hypermeter value is very low, they coefficient standardizations is very low and hence they perform the same as linear regression models. Refer to images/rmse_train_vs_test_alpha1 results

**When Alpha = 20**, We can notice that Ridge and Linear perform very close however the Lasso model performs well on the Test set which is the unseen data.  Refer to images/Alpha20.png and images/ rmse_train_vs_test_alpha20 results.

**When Alpha = 200**, we can see that Lasso Model performs well with car ranges in the 7000 while Ridge performs better in the range of 1000 and 9000.  The RMSE results show that the Ridge model performs better overall in this alpha hyper parameter range.

**Grid Search CV model** for the data set returns 50 as a optimal value for Alpha for Ridge and 200 for Lasso, that was basically also confirmed with the scenarios explained above.

In **Conclusion**, based on the above results, the models perform better at various hyperparameter value range. Finding Optimal value of the Hyperparameter through Grid Search helps us to use them with the relevant models to make it perform better.  It was also identified that the Lasso and Ridge models penalize the features either bringing closer to zero or completely zero to determinate the non-linear relationship deriving from the linear regression model

Extracting the Coefficients that was used by the models, when they are at their optimal alpha ranges, prove that **Condition, Transmission, Fuel, Type, Year and Odometer** drive the price of the car
