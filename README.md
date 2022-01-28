![walmart 2](https://user-images.githubusercontent.com/97288194/151464581-e98d27a2-1649-4f7e-8c45-df3e6ee02910.jpg)

# Walmart-Sales-Store

# 1.0 Business Context (Ficticious)

Here it is historical sales data for 45 Walmart stores located in different regions. Each store contains many departments, and you have project the sales for each department in each store. To add to the challenge, selected holiday markdown events are included in the dataset. 

# 2.0 Business Problem

1. What is the context?

At a meeting with the leads of each department, the Walmart CEO made a proposal to renovate all of their store.

2. What is the cause?

The Walmart CEO want to predict how much each store will sell. He need to know if the budget will be enough to make a renovate each store.

3. Who will lead the project?

We need someone who really know what is the business problem, because he will lead the solution. Therefore, he's our stakeholder.

4. How will be our solution?

Project the sales for each department in each store using Machine Learning Model - Regression.

# 3.0 Business Assumptions

stores.csv: This file contains anonymized information about the 45 stores, indicating the type and size of store.

train.csv: This is the historical training data, which covers to 2010-02-05 to 2012-11-01. Within this file you will find the following fields:

Store - the store number
Dept - the department number
Date - the week
Weekly_Sales -  sales for the given department in the given store
IsHoliday - whether the week is a special holiday week
test.csv

This file is identical to train.csv, except we have withheld the weekly sales. You must predict the sales for each triplet of store, department, and date in this file.

features.csv: This file contains additional data related to the store, department, and regional activity for the given dates. It contains the following fields:

Store - the store number
Date - the week
Temperature - average temperature in the region
Fuel_Price - cost of fuel in the region
MarkDown1-5 - anonymized data related to promotional markdowns that Walmart is running. MarkDown data is only available after Nov 2011, and is not available for all stores all the time. Any missing value is marked with an NA.
CPI - the consumer price index
Unemployment - the unemployment rate
IsHoliday - whether the week is a special holiday week
For convenience, the four holidays fall within the following weeks in the dataset (not all holidays are in the data):

Super Bowl: 12-Feb-10, 11-Feb-11, 10-Feb-12, 8-Feb-13
Labor Day: 10-Sep-10, 9-Sep-11, 7-Sep-12, 6-Sep-13
Thanksgiving: 26-Nov-10, 25-Nov-11, 23-Nov-12, 29-Nov-13
Christmas: 31-Dec-10, 30-Dec-11, 28-Dec-12, 27-Dec-13

# 4.0 Solution Strategy

**Step 01:** Data Collection: I collected data files from https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting/overview

**Step 02:** Data Description: Here I checked number of rows, number os columns and apllied techniques to fill missing values, i've choosen to filling missing values with mean of each column.

**Step 03:** Feature Engineering: Here I created some new features like day, day_of_week, hour and month from date and created state_holiday feature.

**Step 04:** Exploratory Data Analysis: Here I created a hypothesis map, there were 7 hipothesis, where I found 2 relevancy findings.

**Step 05:** Data Preparation: Here I chose to use the rescaling features with MinMaxScaler method and applied OneHotEncoding for holiday features and LabelEncoder method for feature type

**Step 06:** Feature Selection: The results were very different, I decided to go with the random forest results variables

**Step 07:** ML Modeling: Here I chose the Average Model as Baseline, then I implemented 2) Linear Regression, 3) Linear Regression - Lasso and finally 4) Random Forest Regressor, to be more assertive about error model, I implemented cross-validation in all models, and after comparing them, Random Forest Regressor was the one that presented the best result in the MAP, MAPE and RMSE metric and that's why I selected it to proceed with the project.

**Step 08:** Hyperparameters Fine Tuning: 

**Step 09:** Interpretação e Tradução do Erro:  The model presents about 8% MAPE and 2200 MSE in , that means the projection error for each department is 2200 plus or minus.

# 4.0 Future Works

**Step 10:** Deploy Model to Production
