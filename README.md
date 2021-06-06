{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# King's County House Sale Prediction"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "In this project I'm going to analyze the King's County housing data set listing various data points for property sales in the King's County area of Washington (centered around Seattle). I will be using Linear Regression to identify the most influential variables controlling sale price. For the purposes of this exercise, I will be working from the position as a consultant to a hypothetical Real Estate Agency interested in single falmily homes in the Seattle area. I will be using the OSEMN (Obtain, Scrub, Explore, Model, Interpret) Data Science process in this project."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## The Business Problem"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The King's County data shows various figures of features for house sold in 2014 and 2015. As a consultant, I will try and identify the significant factors affecting the sale price of homes, so the agency could have a finest structure of how much a house entering the market would cost according to these specific factors. These factors will include location of the house, living area, number of bedrooms, grade/condition of the house etc. Such conceptual information could increase the agency's ability to provide valuable knowledge and information at each step for the clients while also coming up with an unbiased valuation of their home and help set a listing/buying price."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## The OSMEN Process"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "For this project, I will follow the OSEMN process of data science inquiry. It is split into five stages which include:\n",
    "\n",
    "- Obtain\n",
    "- Scrub\n",
    "- Explore\n",
    "- Model\n",
    "- Interpret\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## The Data"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The raw housing data contains the following columns:\n",
    "\n",
    "- Id - The index of house in the data set\n",
    "- Date - The date of the house's sale\n",
    "- Price - The final price of the home at the time of sale\n",
    "- Bedrooms - The number of bedrooms in the house\n",
    "- Bathrooms - The number of bathrooms in the house (a decimal to account for toilet-only bathrooms etc.)\n",
    "- sqft_living - The square footage of the living area\n",
    "- sqft_lot - The size of building's plot of land\n",
    "- Floors - The number of floors in the house (half counts for an attic)\n",
    "- Waterfront - A binary value indicating if the house has a waterfront view.\n",
    "- View - How many times the home was viewed before it sold\n",
    "- Condition - The overall condition grade of the home\n",
    "- Grade - The overall quality grade of the home\n",
    "- sqft_above - The square footage of the home above ground\n",
    "- sqft_basement - The square footage of the basement\n",
    "- yr_built - The year the home was built\n",
    "- yr_renovated - The year the home was renovated\n",
    "- zipcode - The zipcode of the home\n",
    "- lat - The house's latitude\n",
    "- long - The house's longitude\n",
    "- sqft_living15 - The average square footage of the interiors of the nearest 15 neighbors\n",
    "- sqft_lot15 - The avergae square footage of the lots of the nearest 15 neighbors."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Here is a map of the data around the Seattle area:\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# IMAGE"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Baseline model"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "For my baseline model, after I cleaned the columns for null and outlier values, I divided my data into continuous, categorical and outcome data, but for the purpose of this first model, categorical and continuous variables will both be treated as continuous. My outcome, price, is the success metric. Predictably, this model was poorly fit to the data. Below you can see the residuals show strong heteroscedasticity and the residuals do not follow a normal distribution:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# IMAGE"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Process"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Using my baseline model as a guide, I reiterated this process with the following steps:\n",
    "\n",
    "- Log Transformation\n",
    "- One-Hot-Encoding Categoricals\n",
    "- Bining Categoricals\n",
    "- Handled Correlation\n",
    "- Sorted Zipcodes by city name\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "My final model used a combination of every one of these alterations listed. The final model has the following residuals and R2 score:"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# IMAGE"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Our final R2 score came to 0.806, meaning that it can account for 80.6% of the data's variance. Our Mean Absolute Error is around $100,000, so the model won't be able to effectively predict the final dollar amount of a property sale, but we can infer the most important factors involved in calculating the price."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Conclusions and Interpretation"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "As we have seen, in our final model, we could account for about 77.9% of the variance in the housing price data. Our mean absolute error for the model is around $91,600, which is not ideal for accurately predicting a sale price. That said, based on this model, we know that the five most influential factors in property sale price with their coefficients are:\n",
    "\n",
    "- Latitude - How far North the property is (1.25)\n",
    "- Built in Medina (0.865)\n",
    "- Built in Mercer (0.599)\n",
    "- Square Footage of Living Space (0.57)\n",
    "- Waterfront View (0.47)\n",
    "\n",
    "\n",
    "- Adding square footage to a property can add significant value to a house.\n",
    "- Properties built in the Cities Medina and Mercer neighbourhoods do have a higher sale price.\n",
    "- And the more North we travel the higher the housing market price of the properties.\n",
    "\n",
    "The model can be used to predict house price although the model is not amazingly accurate. Still the results can be used for understanding the features of a property's relationship to the market. The models here focus on isolating factors for accurate coefficients rather than on precise prediction."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Areas of Further Study"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "This model has a lot of room for improvement. Other areas to explore in this data for the Real Estate agency are:\n",
    "\n",
    "- Discover how sqft_basement for a given Lot area would play a role\n",
    "  in the sales price.\n",
    "- Determine the value of different types of expansions (Bedroom,\n",
    "  Bathroom) and investigate how that affects the value of a house.\n",
    "- Identify areas of Seattle where housing prices are increasing and possibly predict which neighborhoods will be ideal for     settlement in the future.\n",
    "- Improve the model With more data over the years after 2015 and observe if there is any change in the trend of the major  factors."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.5"
  },
  "toc": {
   "base_numbering": 1,
   "nav_menu": {},
   "number_sections": true,
   "sideBar": true,
   "skip_h1_title": false,
   "title_cell": "Table of Contents",
   "title_sidebar": "Contents",
   "toc_cell": false,
   "toc_position": {},
   "toc_section_display": true,
   "toc_window_display": false
  },
  "varInspector": {
   "cols": {
    "lenName": 16,
    "lenType": 16,
    "lenVar": 40
   },
   "kernels_config": {
    "python": {
     "delete_cmd_postfix": "",
     "delete_cmd_prefix": "del ",
     "library": "var_list.py",
     "varRefreshCmd": "print(var_dic_list())"
    },
    "r": {
     "delete_cmd_postfix": ") ",
     "delete_cmd_prefix": "rm(",
     "library": "var_list.r",
     "varRefreshCmd": "cat(var_dic_list()) "
    }
   },
   "types_to_exclude": [
    "module",
    "function",
    "builtin_function_or_method",
    "instance",
    "_Feature"
   ],
   "window_display": false
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
