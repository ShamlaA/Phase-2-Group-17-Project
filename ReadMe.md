# King County Housing Prices Prediction

**DSF-PT7, Group 17:**
1. Agatha Nyambati
2. Mary Musyoka
3. Phoebe Wawire
4. Shamla Araya
5. Zenah Biwott


### Introduction:

King County, located in the state of Washington, encompasses a diverse range of urban, suburban, and rural communities, including the city of Seattle. The housing market in King County has been characterized by rapid growth, high demand, and escalating prices over the past decade, influenced by factors such as population growth, economic prosperity, and limited housing supply.

The King County Housing Price Prediction Project is an initiative aimed at accurately forecasting housing prices in King County, Washington. This project leverages advanced data analytics and machine learning techniques to provide precise and actionable insights into the factors influencing housing prices in the region. By analyzing historical data and current market trends, we aim to develop a robust predictive model that can assist homebuyers, sellers, real estate agents, and policymakers in making informed decisions.

# Objectives:
We set out to achieve the following three objectives in this project:
1. Determine the key influencing factors for the housing prices in the region.
2. Provide a valuable EDA (Exploratory Data Analysis) for stakeholders such as homebuyers, sellers, real estate professionals, and policymakers to make data-driven decisions regarding property transactions and urban planning.
3. Develop a machine learning model capable of predicting housing prices with high accuracy based on a variety of factors including property features, location, and market conditions.

## Data Understanding

The data set we are using for this project is from Kaggel website. This dataset contains more than 21,000 rows and 21 columns which describe or quantify the different aspects of the housing situation in the region. These features are crucial for achieving the objectives stated above.
We will load the data and check if there are any missing or null values that could impair our analysis. To do this properly we will follow the following steps:

1. Load the dataset.
2. Data cleaning where we will check for missing values and any limitations within the dataset and prepare the dataset.
3. Data exploration where we will clearly identify all the features and select the ones we are willing to work with.
4. Analysis of the data to come up with insights that we can learn about the housing situation in the region
5. Preparing the data for machine learning models to predict the housing prices given different variables.

# Column Names and descriptions for Kings County Data Set
* **id** - unique identified for a house
* **dateDate** - house was sold
* **pricePrice** -  is prediction target
* **bedroomsNumber** -  of Bedrooms/House
* **bathroomsNumber** -  of bathrooms/bedrooms
* **sqft_livingsquare** -  footage of the home
* **sqft_lotsquare** -  footage of the lot
* **floorsTotal** -  floors (levels) in house
* **waterfront** - House which has a view to a waterfront
* **view** - Has been viewed
* **condition** - How good the condition is ( Overall )
* **grade** - overall grade given to the housing unit, based on King County grading system
* **sqft_above** - square footage of house apart from basement
* **sqft_basement** - square footage of the basement
* **yr_built** - Built Year
* **yr_renovated** - Year when house was renovated
* **zipcode** - zip
* **lat** - Latitude coordinate
* **long** - Longitude coordinate
* **sqft_living15** - The square footage of interior housing living space for the nearest 15 neighbors
* **sqft_lot15** - The square footage of the land lots of the nearest 15 neighbors

## 1. Loading the Data

After loading the dataset and observing it we learnt that the dataset contains entries of more that 21,000 rows and 21 columns. This housing data also reveals that the minimum housing price to be $75,000.00 and the highest to be $7.7mill. with the average being around $540,000.00.


## 2. Data Cleaning

Two of the columns had object data type while the rest were float or integer. The dataset also had missing values from the "waterfront", "view" and "yr_renovated" columns which required to be checked  and handled before we could proceed to EDA.

We checked the columns with missing values and non-numeric values and decided to fill the missing values with 0. One entry in the dataset had a house with 33 bedrooms which after a thorough check we decided it was a typo error and dropped the entry.

At this point we also decided to drop the "id", "date", and "zipcode" columns as we didnt find them important for the objectives we set out to meet. We also created another dataframe called "clean_df" which contained data free of outliers and duplicates.

## 3: Data Exploration

At this stage we checked our dataset to learn which of the features had major influence on the target feature which is the house price.

### Objective 1. Determine the key influencing factors for the housing prices in the region.
To do this, we examined how all the features in our dataset are related to the Price column using the .corr() function and the correlation heatmap.

![Images/Heat Map.png](<Images/Heat Map.png>)

![!\[Images/Pairplot.png\]](Images/Pairplot.png)


Based on the correlation analysis and considering the goal of predicting house prices (price) in King County, here are the most important features we should consider:

**Primary Features:**

**sqft_living:** Square footage of the living area (Correlation: 0.70).

**grade:** Overall grade given to the housing unit (Correlation: 0.67).

**sqft_above:** Square footage of the house above ground level (Correlation: 0.61).

**bathrooms:** Number of bathrooms in the house (Correlation: 0.53).


**Additional Features:**

**bedrooms:** Number of bedrooms in the house (Correlation: 0.31).

# Why These Features?

**Strong Correlation:** These features exhibit the highest correlations with price based on our analysis, indicating a strong linear relationship with house prices in King County.

**Market Relevance:** Features like sqft_living, grade, and bathrooms are fundamental factors influencing property values, reflecting buyer preferences and market dynamics in the region.

**Predictive Power:** Models incorporating these features are likely to yield more accurate predictions of house prices due to their significant impact on property valuations.

## 4: Data Analysis

We started this stage by investigating the price feature of the dataset since it is our target feature.

What we saw from here is that the price ranges from $78k for 2 bedroom house with 780sqft living space, 1 floor, 1 bathroom to $7.7mil for a 6 bedroom, with 8 bathrooms, 2.5 floors and  12050sqft living space. This is a huge gap and maybe the high price could blow our distribution. Let us investigate it.

We run a histogram plot on the price column from the cleaned data to see its distribution.

![alt text](<Images/Price Distribution.png>)

We did scatter plot of three major features on their relationship with the price feature.

![alt text](<Images/Living Space.png>)
![alt text](<Images/House grade.png>)
![alt text](<Images/Number of Bathrooms.png>)

**Observation:**

 The scatter plot shows that sqft_living, grade and bathrooms features are strongly positively correlated with the house price, indicating that houses with larger living areas, above average grade and with multiple bathrooms generally command higher prices.

**Implication:**

 This insight suggests that square footage followed by grade and bathrooms are significant factors in determining property prices in King County, which aligns with common expectations in real estate markets.

 ## Recommendation 1:
Based on the analysis and demonstrations houses with large living spaces, higher grading, and numerous bathrooms cost more than others. Therefore it is advisable to look for houses with such features to invest in and make profit on resale or to consider the features in order to find more affordable houses to buy.

### Objective 2: Provide a valuable EDA (Exploratory Data Analysis) for stakeholders such as homebuyers, sellers, real estate professionals, and policymakers to make data-driven decisions regarding property transactions and urban planning.

After running a joint plot of the highli influential features, 

![alt text](<Images/Joint Plot 2.png>)
![alt text](<Images/Joint Plot 3.png>)
![alt text](<Images/Joint Plot 4.png>)
![alt text](<Images/Joint Plot 5.png>)
![alt text](<Images/Joint Plot.png>)

## Recommendation 2:
This EDA shows that the housing market in King County is highly influenced by the total footage of living space. Even though  the grade a house receives and the number of bathrooms of a house as well influence the price, the power of the total footage of living space is vividly clear. Stakeholders such as homebuyers, sellers, real estate professionals, and policymakers need to pay attention of the total footage of living space to get insights and make data-driven decisions regarding property transactions and urban planning based on this EDA.

# Objective 3 Develop a Multiple Regression Model for Predicting House Prices:

a. Objective: Build a predictive model that accurately estimates housing prices based on various features

b. Feature Selection: Use techniques such as Recursive Feature Elimination (RFE),  to select relevant features.

c. Model Selection: Test various models and select the one that performs with above average accuracy.

d. Linear Models: Linear Regression

e. Finally we will do Model Evaluation: Use metrics like R-squared, Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE) to evaluate model performance. Perform cross-validation to ensure robustness.

Fot this we trained and tested 4 different models with different combination of features.

Model 1:
R-squared: 0.32444782772387404
Mean Absolute Error: 0.3463239556238238
Coefficients: [0.04354581 0.3559081  0.87554247 0.08357308]
Intercept: 11.858860373149204

# Interpretation of Results

**R-squared**

**R-squared:** 0.3244: This indicates that approximately 32.44% of the variance in the logarithmically transformed house prices (price_log) can be explained by the model. This is a moderate level of explanatory power and suggests that while the selected features ('bedrooms', 'bathrooms', 'waterfront', 'condition') are relevant, there are other important factors influencing house prices not captured by this model.

**Mean Absolute Error (MAE)**

**MAE: 0.3452:** This represents the average magnitude of errors in predicting the logarithmically transformed prices. In this case, the MAE is 0.3452 units on the log scale, which is a typical prediction error magnitude for this transformed variable.

Model 2:
R-squared: 0.551175224211654
Mean Absolute Error: 0.2832943470967524
Coefficients: [ 0.00022653  0.18971437 -0.01728759]
Intercept: 11.161694871756431

# Interpretation of Results

**R-squared**

**R-squared:** 0.5511: This indicates that approximately 55.11% of the variance in the logarithmically transformed house prices (price_log) can be explained by the model. This is a moderate level of explanatory power and suggests that while the selected features (sqft_living, grade, bathrooms) are relevant, there could be other important factors influencing house prices not captured by this model.

**Mean Absolute Error (MAE)**

**MAE: 0.2832:** This represents the average magnitude of errors in predicting the logarithmically transformed prices. In this case, the MAE is 0.2832 units on the log scale, which is a typical prediction error magnitude for this transformed variable.

Model 3:
R-squared: 0.5573214108677681
Mean Absolute Error: 0.28003622865725314
Coefficients: [ 0.00028895  0.20126344 -0.18594717 -0.00326576 -0.01669707]
Intercept: 12.34536944779032

# Interpretation of Results
**R-squared**

**R-squared: 0.5573:** This indicates that approximately 55.73% of the variance in the logarithmically transformed house prices (price_log) can be explained by the model. This is a moderate level of explanatory power, suggesting that the selected features explain a significant portion of the variation in house prices.

**Mean Absolute Error (MAE)**

**MAE: 0.2802:** This represents the average magnitude of the errors in predicting the logarithmically transformed prices. An MAE of 0.2800 units on the log scale indicates a reasonably good prediction accuracy, better than the previous model with fewer features.

**Coefficients**

**sqft_living (0.6514):** For each additional unit increase in square footage of living space, the logarithm of the price is expected to increase by approximately 0.6514 units, holding other factors constant. This shows a substantial positive impact of living space on house prices.

Model 4:
R-squared: 0.7063608450810133
Mean Absolute Error: 0.21953428946767334
Coefficients: [ 2.43805906e-04  1.59188965e-01  1.43172655e+00 -2.70519235e-01]
Intercept: -89.83181608893119


# Interpretation of Results

**R-squared**

**R-squared:** 0.7063: This indicates that approximately 70.63% of the variance in the logarithmically transformed house prices (price_log) can be explained by the model. 

**Mean Absolute Error (MAE)**

**MAE: 0.2195:** This represents the average magnitude of the errors in predicting the logarithmically transformed prices. In this case, the MAE is 0.2195 units on the log scale.
A lower MAE indicates better prediction accuracy. This idicaates that our model which have an MAE of 0.2195 is more accurate in predicting the log-transformed house prices than our Previous model with an MAE of 0.2789.


**Coefficients**

**sqft_living (0.0002439):** For each additional unit increase in square footage of living space, the logarithm of the price is expected to increase by approximately 0.0002439 units, holding other factors constant.

**grade (0.1591):** Each one-unit increase in the grade of the house is associated with an increase in the logarithm of the price by about 0.1591 units, holding other factors constant.

**lat (1.4346):** Each one-degree increase in latitude is associated with an increase in the logarithm of the price by approximately 1.4346 units, holding other factors constant. This indicates that latitude has a significant impact on house prices in the logarithmic scale.

**long (-0.2694):** Each one-degree increase in longitude is associated with a decrease in the logarithm of the price by approximately 0.2694 units, holding other factors constant.

**Intercept**

**Intercept (-89.8274):** The intercept represents the expected value of the logarithm of the house price when all predictors are zero. Since we're dealing with logarithmic transformation, this **interpretation is in terms of logarithmic units.

# Summary of Overall Models Performance:

**Model 1:** shows a relatively low R-squared value (0.3244), indicating that it explains only 32.44% of the variance in the data. Its MAE is 0.3452, suggesting a moderate level of prediction error.

**Model 2:** shows an improved R-squared value 0f 0.5511 explaining 55.11% of the variance and a 0.28 MAE value. However this is not satisfactory level of prediction given the significance of the model.

**Model 3:** has a lower R-squared value (0.5485), explaining 54.85% of the variance. Its MAE is 0.278, indicating a weaker predictive performance than Model 2.

**Model 4:** has the highest R-squared value (0.7063), explaining 70.63% of the variance. It also has the lowest MAE (0.21), suggesting it provides the most accurate predictions.

## Recommendation 3:

The best model for predicting housing prices in King County, based on the provided dataset and transformation techniques, is Model 4. This model has a high R-squared value of 0.7063, indicating it explains 70.63% of the variance in the logarithmically transformed house prices. It also has a low MAE of 0.2194, indicating it has the lowest prediction error. This model effectively captures the mean and standard deviation of the logarithmically transformed house prices.

With the highest R-squared value of 0.7063, and lowest MAE of 0.2194, this Model is the most accurate and reliable model for predicting housing prices.

# Moderate Fit:

An R-squared value of 0.7 indicates a moderate level of explanatory power. This suggests that our model is capturing some, but not all, of the important factors influencing house prices. In real estate data, it is common for multiple factors to influence the house prices.

Error Magnitude:
The MAE of 0.2 provides a clear understanding of the average prediction error. Given that MAE is in the same units as our target variable (log-transformed house prices), we can interpret this as the average deviation of our predictions from the actual values.

 **Visualize Predicted vs. Actual Prices**

The predicted vs. actual prices plot helps us see how well the model's predictions match the actual values. Ideally, points should lie along the 45-degree line, indicating perfect predictions.

![alt text](<Images/Presicted vs Actual Price.png>)

**Perform Residual Analysis**

Residual analysis involves examining the residuals (differences between actual and predicted values). Residual plots and histograms can help identify systematic errors or biases.

**Residuals vs. Predicted Prices**
A residuals vs. predicted prices plot helps check for patterns. Ideally, residuals should be randomly distributed around zero.

**Histogram of Residuals**

A histogram of residuals will  help us check if they are normally distributed around zero.

![alt text](<Images/Residuals vs Predicted.png>)
![alt text](<Images/Frequency vs Residuals.png>)
![alt text](<Images/Fitted value vs Residuals.png>)
![alt text](<Images/Ordered Value vs Theoretical Value.png>)

***

## Conclusion:

The project aimed to:

**1:** Identify key features influencing housing prices in the region.

**2:** Provide a valuable Exploratory Data Analysis (EDA) for stakeholders such as homebuyers, sellers, real estate professionals, and policymakers to make informed decisions regarding property transactions and urban planning.

**3:** Develop a machine learning model to accurately predict housing prices based on property features, location, and market conditions.

Using the King County housing dataset, we examined the data, cleaned it of missing and NaN values, performed an analysis, and developed a model that predicts housing prices with 70% accuracy based on various factors.

## Recommendations
**Investment Strategy:** Houses with larger living spaces, higher grades, and more bathrooms tend to be more expensive. Investors should focus on these features to maximize resale profits or find affordable options by considering these factors.

**Market Insights:** The EDA reveals that the King County housing market is significantly influenced by the total footage of living space. Stakeholders can use these insights for data-driven decisions in property transactions and urban planning.

**Model Selection:** The best model for predicting housing prices in King County is Model 4, which has an R-squared value of 0.7063 and a low Mean Absolute Error (MAE) of 0.2194. This model explains 70.63% of the variance in logarithmically transformed house prices and has the lowest prediction error, effectively capturing the mean and standard deviation of the transformed prices.


THE END



