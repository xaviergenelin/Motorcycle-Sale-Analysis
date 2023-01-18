# Motorcycle-Sale-Analysis

## Purpose
This project looks to predict the selling price of a motorcycle by using the Grid Search Method and Gradient Descent Method by using RMSE as the loss function. Both methods will predict the selling price with and without the variable `km_driven` as a predictor variable.

## Dependencies
* pandas
* numpy
* matplotlib
* math

## Dataset Description
The data comes from [Kaggle](https://www.kaggle.com/datasets/nehalbirla/motorcycle-dataset?select=BIKE+DETAILS.csv)'s repository of datasets. 

## Grid Search Algorithm
The grid search algorithm will look through manually selected values and determine which is the best predictor for our data. The selected values will be based on exploratory analysis of `selling_price`. We saw a lot of values less than 100,000, and more specifically between a little under 20,000 and 80,000. We'll first examine it just for our y value, using values between 18,000, and 80,250 in increments of 1. We'll also do this for the variable `km_driven`, to see if our algorithm generalizes. The selected values is also based on the previous exploratory analysis, and we'll use values between 0 and 80,000 in increments of 1. 

When we examine it for a y and x value, we'll find the optimal values of $\beta_0$ and $\beta_1$ that connect the variables selling_price and km_driven in the equation $selling\\_price = \beta_0 + \beta_1 * km\\_driven$. From the graphs we've created, we deduced that the intercept may be between 0 and 80,000. After iterating over (0, 80,000) by 1,000, we concluded that we could reduce our grid size to be between 55,000 and 65,000, using a step size of 100. Also based on the graphs, the relationship between km_driven and selling_price looks mildly negative, so we set the grid values for the slope to be between -1 and 0, using a step size of 0.1.. 

## Gradient Descent Method
The gradient descent method is an iterative optimization algorithm that will find the local minimum of a function. This typically uses calculus to find the minimum based on derivatives, but since we don't have a function to derive, we'll estimate this by using a difference quotient. The difference quotient is the following equation:

$$diff\\_quotient = \frac{RMSE(c + \Delta) - RMSE(c)}{\Delta}$$

This will give us an estimate of the slope of a tangent line. We'll use this slope to calculate our new predicted value and compare the new value to the old value. Once we move a very small distance, we can take a reasonable guess that we're at, or at least close to, the minimum. Our new value will be determined by the equation: $new\\_val = cur\\_val + slope * step\\_size$, where `step_size` is a set value. 


## Results
### Grid Search Algorithm
For just the y value, we found optimal values of 59,638 for `selling_price` and 34,360 for `km_driven`. Adding in a numeric variable x, which is `km_driven`, we get the following optimal values: $\beta_0$ = 61,100 and $\beta_1$ = -0.4.

### Gradient Descent Method

For just the y value, we found optimal values of 59,626.89 for selling price and 34,370.15 for km_driven. Adding in a numeric variable x, which is `km_driven`, we get the following optimal values: $\beta_0$ = 67,734.12 and $\beta_1$ = -0.236.
