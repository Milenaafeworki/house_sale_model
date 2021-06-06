# King's County House Sale Prediction

In this project I'm going to analyze the King's County housing data set listing various data points for property sales in the King's County area of Washington (centered around Seattle). I will be using Linear Regression to identify the most influential variables controlling sale price. For the purposes of this exercise, I will be working from the position as a consultant to a hypothetical Real Estate Agency interested in single falmily homes in the Seattle area. I will be using the OSEMN (Obtain, Scrub, Explore, Model, Interpret) Data Science process in this project.

## The Business Problem

The King's County data shows various figures of features for house sold in 2014 and 2015. As a consultant, I will try and identify the significant factors affecting the sale price of homes, so the agency could have a finest structure of how much a house entering the market would cost according to these specific factors. These factors will include location of the house, living area, number of bedrooms, grade/condition of the house etc. Such conceptual information could increase the agency's ability to provide valuable knowledge and information at each step for the clients while also coming up with an unbiased valuation of their home and help set a listing/buying price.

## The OSMEN Process

For this project, I will follow the OSEMN process of data science inquiry. It is split into five stages which include:

- Obtain
- Scrub
- Explore
- Model
- Interpret


## The Data

The raw housing data contains the following columns:

- Id - The index of house in the data set
- Date - The date of the house's sale
- Price - The final price of the home at the time of sale
- Bedrooms - The number of bedrooms in the house
- Bathrooms - The number of bathrooms in the house (a decimal to account for toilet-only bathrooms etc.)
- sqft_living - The square footage of the living area
- sqft_lot - The size of building's plot of land
- Floors - The number of floors in the house (half counts for an attic)
- Waterfront - A binary value indicating if the house has a waterfront view.
- View - How many times the home was viewed before it sold
- Condition - The overall condition grade of the home
- Grade - The overall quality grade of the home
- sqft_above - The square footage of the home above ground
- sqft_basement - The square footage of the basement
- yr_built - The year the home was built
- yr_renovated - The year the home was renovated
- zipcode - The zipcode of the home
- lat - The house's latitude
- long - The house's longitude
- sqft_living15 - The average square footage of the interiors of the nearest 15 neighbors
- sqft_lot15 - The avergae square footage of the lots of the nearest 15 neighbors.

Here is a map of the data around the Seattle area:



# IMAGE

## Baseline model

For my baseline model, after I cleaned the columns for null and outlier values, I divided my data into continuous, categorical and outcome data, but for the purpose of this first model, categorical and continuous variables will both be treated as continuous. My outcome, price, is the success metric. Predictably, this model was poorly fit to the data. Below you can see the residuals show strong heteroscedasticity and the residuals do not follow a normal distribution:

# IMAGE

## Process

Using my baseline model as a guide, I reiterated this process with the following steps:

- Log Transformation
- One-Hot-Encoding Categoricals
- Bining Categoricals
- Handled Correlation
- Sorted Zipcodes by city name


My final model used a combination of every one of these alterations listed. The final model has the following residuals and R2 score:

# IMAGE

Our final R2 score came to 0.806, meaning that it can account for 80.6% of the data's variance. Our Mean Absolute Error is around $100,000, so the model won't be able to effectively predict the final dollar amount of a property sale, but we can infer the most important factors involved in calculating the price.

## Conclusions and Interpretation

As we have seen, in our final model, we could account for about 77.9% of the variance in the housing price data. Our mean absolute error for the model is around $91,600, which is not ideal for accurately predicting a sale price. That said, based on this model, we know that the five most influential factors in property sale price with their coefficients are:

- Latitude - How far North the property is (1.25)
- Built in Medina (0.865)
- Built in Mercer (0.599)
- Square Footage of Living Space (0.57)
- Waterfront View (0.47)


- Adding square footage to a property can add significant value to a house.
- Properties built in the Cities Medina and Mercer neighbourhoods do have a higher sale price.
- And the more North we travel the higher the housing market price of the properties.

The model can be used to predict house price although the model is not amazingly accurate. Still the results can be used for understanding the features of a property's relationship to the market. The models here focus on isolating factors for accurate coefficients rather than on precise prediction.

## Areas of Further Study

This model has a lot of room for improvement. Other areas to explore in this data for the Real Estate agency are:

- Discover how sqft_basement for a given Lot area would play a role
  in the sales price.
- Determine the value of different types of expansions (Bedroom,
  Bathroom) and investigate how that affects the value of a house.
- Identify areas of Seattle where housing prices are increasing and possibly predict which neighborhoods will be ideal for     settlement in the future.
- Improve the model With more data over the years after 2015 and observe if there is any change in the trend of the major  factors.


```python

```
