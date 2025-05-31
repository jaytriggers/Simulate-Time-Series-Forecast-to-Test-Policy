
# Probabilistic Forecast and Simulation To Test Policy 


# <img src="https://private-user-images.githubusercontent.com/142165926/405214659-9f485831-f0af-45c0-9d1e-a9401cb17cfc.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDcyNDEyMTYsIm5iZiI6MTc0NzI0MDkxNiwicGF0aCI6Ii8xNDIxNjU5MjYvNDA1MjE0NjU5LTlmNDg1ODMxLWYwYWYtNDVjMC05ZDFlLWE5NDAxY2IxN2NmYy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwNTE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDUxNFQxNjQxNTZaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT04MzJlZTIxYjY2NTdhZWMzYjI3MGM4OTJkZmU0NTcwYjgwZDdmMjdiN2EzOWZkNjY4OTQxNjJkY2Q4ODZhMzlhJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.xhBxJnelSWg5oU9-uDM5uhOJr-1UHZG-3I992P_-7V8" alt="image" style="max-width: 100%;">
## Overview 
Time Series Sales Forecasting Project. Utilised machine learning techniques to analyse historical sales data, uncover patterns, and forecast future demand. Based on the forecasted values, I conducted a simulation to evaluate the impact of the company’s new Reorder Point (ROP) policy. The simulation estimated key  performance metrics, including stockout costs, holding costs, and the expected number of units held and shorted under various demand and lead time scenarios.
## Project Objective 
- Demand Trend Prediction: Develop robust forecasting models to project future demand across various time horizons.
- Model Evaluation and Optimisation: Compare multiple forecasting techniques to ensure the most accurate predictions.
- Perform a probabilistic forecast and use simulation to test ROP policy.
## Business Problem
- One common challenge in supply chain management is the over-reliance on point forecasts, despite the fact that real-world demand is inherently uncertain. To better reflect this uncertainty, I ran a simulation using the standard deviation of the model’s residuals to generate probabilistic demand forecasts with a 90% confidence interval.- Another challenge is the lack of a controlled environment to test inventory policies before implementation, which can lead to financial losses.
- Another challenge is the inability to test inventory policies in a controlled environment before implementation, which can result in costly mistakes. Accurately modeling demand—accounting for trends and seasonality—is essential for evaluating such policies effectively. To address this, I built a simulation model to assess the performance of a Reorder Point (ROP) policy. The model estimates expected stockout and overstock costs over time under varying demand scenarios, helping to inform better inventory decisions in real-world conditions.
## Dataset Overview 
The dataset consists of historical demand records containing various attributes essential for analysis.
### Key Columns:
<markdown-accessiblity-table data-catalyst=""><table>
<thead>
<tr>
<th>Column Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Order Date</td>
<td>Date and time of the sales transaction</td>
</tr>
<tr>
<td>Product Category</td>
<td>Category of product sold</td>
</tr>
<tr>
<td>Order Demand</td>
<td>Number of units sold</td>
</tr>
<tr>
<td>Unit Price</td>
<td>Price per unit</td>
</tr>
</tbody>
</table></markdown-accessiblity-table>

## Approach and Methodology 
### 1. Data Preprocessing
- Data cleaning: Handling missing values and duplicate records.

### 2. Exploratory Data Analysis (EDA)
- Demand trends analysis.
- Seasonal decomposition to identify underlying patterns.
### 3. Model Development
The project explores multiple time series forecasting models, including:
#### Traditional Models:
- Autoregressive Integrated Moving Average (ARIMA)
- Exponential Smoothing (Holt-Winters)
#### Machine Learning Approaches:
- Facebook Prophet (for weekly and monthly sales forecasting)
- Long Short-Term Memory (LSTM) Networks

### 4. Model Evaluation
Performance metrics used to assess model accuracy:
- Mean Absolute Error (MAE): Measures average error in prediction.
- Root Mean Squared Error (RMSE): Penalizes large errors more than MAE.

## Model Selection and Performance
### Weekly Forecasting: Hot-Winters Exponential Smoothing
 Our analysis shows that LSTM Weekly Metrics provides optimal performance for short-term forecasting. 
 The model achieved lower MAE (Mean Absolute Error) values on average compared to the 
 other models.
 - Exponential Smoothing - 7.781178e+05
 - Prophet - 1.209010e+06
 - ARIMA - 7.919662e+05
 - LSTM - 7.889473e+05
### Monthly Forecasting: LSTM  
 For long-term predictions, LSTM demonstrated superior performance with low MAE values on average compared to 
 other models.
 - Exponential Smoothing - 3.748631e+06	
 - Prophet - 6.961000e+06
 - ARIMA - 2.601691e+06
 - LSTM - 2.428455e+06

## Probabilistic Forecasting for category_019
### Why Probabilistic Forecasting? 
Traditional forecasts provide a single number. But in real life, demand varies.
- Point Forecast: ”We expect 315000 demand for category_019”
- Reality: Demand could be 320000 or 550000.
- Probabilistic Forecast: ”There’s a 90% chance demand is between 235000 and 330000.”

## Process:
### - Establishing the Distribution of Demand Uncertainty
To run an effective simulation, it's essential to base the simulated data on the underlying distribution of demand uncertainty. This means understanding how actual demand deviates from the forecasted values. By analyzing the residuals (forecast errors) from our forecasting model, we can estimate the variability in demand. If the residuals are approximately normally distributed, we can use the standard deviation of these residuals to simulate future demand scenarios. This allows us to incorporate randomness into our simulation and reflect the uncertainty that naturally occurs in real-world demand.
#### Result
A normal distribution.
### - Upper Lower Bound and Expected Value 
Next, we calculate the expected value and the upper and lower bounds for each forecast period using the simulated data.
#### Result 
For Week_1:

  🔹 Expected demand: 15819101.92
  
  🔹 90% Confidence Interval: [9852704.06, 21670317.47]


## Testing ROP policy for category_019
### Goal
The goal here estimate the Units held, Units shorted as well as their costs for the ROP of 3150000 for each demand and lead time scenario. 
### Process:
### - Establishing the Distribution of Variables to be Simulated
We are simulating demand and lead time.
We have established that our demand follows a normal distribution; now we will validate for lead time.
#### Visualising and Testing the Distribution of Lead Time

An initial visualisation of the lead time data suggests that it does not clearly follow any well-known theoretical distribution. However, to validate this observation statistically, I will conduct a Chi-squared goodness-of-fit test.

The test will be performed against theoretical distributions that are commonly associated with event-driven or time-between-event data, specifically:

- Poisson (for count-based processes)

- Exponential (for modeling time between events)

- Normal (as a general-purpose benchmark)

This will help determine which, if any, of these distributions provides a reasonable fit for the lead time data.\
#### Result
We can confirm that our data does not follow a theoretical distribution. I will process to use the peice-wise distribution to fit the data.
### - Define the formula for variables to be estimated 
- Units held = max(ROP - D, 0)
- Units Short = max(D - ROP, 0)
- Hodling cost per unit = (Item_purchasing_cost x Ann_hold_rate) x (lead_time / 365)
- Stock out cost per unit  = (Item_selling_cost - Item_purchasing_cost)
- Holding Cost = Holding Cost per Unit × Overstock
- Stockout cost = Stockout Cost per Unit × Stockout
- Total Cost = Holding Cost + Stockout Cost
### - Run simulation 
#### Result
In practice, simulation is a powerful tool used to model the performance of inventory policies under uncertainty. For example, given a scenario where demand is 3,500,000 units and lead time is 4 days, we can estimate the expected stockouts, overstock, and associated costs.
More realistically, demand and lead time vary. To reflect this, we run simulations across a range — say, demand between 3,150,000 and 3,500,000 units and lead time between 1 and 3 days. By averaging results over many iterations, we get probabilistic estimates of key metrics like average stockouts, holding costs, and total cost. This allows us to evaluate inventory strategies more robustly before implementing them in the real world.







   











