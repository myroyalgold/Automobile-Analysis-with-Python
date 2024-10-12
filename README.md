# Automobile-Analysis

# Data Processing and Preprocessing
## Objectives
- Import a dataset from a CSV file to a Pandas dataframe
- Develop some basic insights about the dataset
- Handle missing data in different ways
- Correct the data type of different data values as per requirement
- Standardize and normalize the appropriate data attributes
- Visualize the data as grouped bar graph using Binning
- Converting a categorical data into numerical indicator variables

## What is the purpose of data wrangling? 
Data wrangling is used to convert data from an initial format to a format that may be better for analysis.

## Data Source: https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DA0101EN-SkillsNetwork/labs/Data%20files/auto.csv

## Set up:
I used the following libraries:
- pandas for managing the data.
- numpy for mathematical operations.
- matplotlib for additional plotting tools
  
## Task 1: Data Cleaning 
Steps for working with missing data:
- Identify missing data
- Deal with missing data
- Correct data format

### Step 1:  Identify missing data
- import python libaries such as pandas, numpy and matplotlib
- download the dataset using the url
- Count missing values in each column
  Based on the summary above, each column has 205 rows of data and seven of the columns containing missing data:
    1. "normalized-losses": 40 missing data
    2. "num-of-doors": 2 missing data
    3. "bore": 4 missing data
    4. "stroke" : 4 missing data
    5. "horsepower": 2 missing data
    6. "peak-rpm": 2 missing data
    7. "price": 4 missing data

### Step 2: Deal with missing data
  How should you deal with missing data?
    Drop data
    a. Drop the whole row
    b. Drop the whole column
    Replace data
    a. Replace it by mean
    b. Replace it by frequency
    c. Replace it based on other functions

- Replace normalized-losses, stroke, bore, horsepower, peak-rpm with mean
- replace num_of_doors by frequency
- Drop the whole row for price

### Step 3: Correct Data Format
- check data types for each column
- Convert data types to proper format
   1. convert bore, stroke, price, peak-rpm as float type
   2. convert normalized-losses as int type
- list the columns after conversion

## Task 2: Data Standardization
Standardization is the process of transforming data into a common format, allowing the researcher to make the meaningful comparison.
such as converting m to km, mpg to L/100km
- Convert mpg to L/100km by mathematical operation (235 divided by mpg)
- transform mpg to L/100km in the column of "highway-mpg" and change the name of column to "highway-L/100km

## Task 3: Data Normalization
Normalization is the process of transforming values of several variables into a similar range. Typical normalizations include
- scaling the variable so the variable average is 0
- scaling the variable so the variance is 1
- scaling the variable so the variable values range from 0 to 1

To demonstrate normalization, say you want to scale the columns "length", "width" and "height".

1. Target: normalize those variables so their value ranges from 0 to 1

2. Approach: replace the original value by (original value)/(maximum value)

## Task 4: Binning
Binning is a process of transforming continuous numerical variables into discrete categorical 'bins' for grouped analysis.
In this data set, "horsepower" is a real valued variable ranging from 48 to 288 and it has 59 unique values. What if you only care about the price difference between cars with high horsepower, medium horsepower, and little horsepower (3 types)? You can rearrange them into three ‘bins' to simplify analysis.

Use the Pandas method 'cut' to segment the 'horsepower' column into 3 bins.
- Convert horsepower column data to correct format i.e as type integer
- Find 3 bins of equal size bandwidth by using Numpy's linspace(start_value, end_value, numbers_generated function
  1. Since you want to include the minimum value of horsepower, set start_value = min(df["horsepower"]).
  2. Since you want to include the maximum value of horsepower, set end_value = max(df["horsepower"]).
  3. Since you are building 3 bins of equal length, you need 4 dividers, so numbers_generated = 4.
- Build a bin array with a minimum value to a maximum value by using the bandwidth calculated above. The values will determine when one bin ends and another begins.
- group_names = ['Low', 'Medium', 'High']
- Apply the function "cut" to determine what each value of df['horsepower'] belongs to.
- See the number of vehicles in each bin
- Plot the distribution of each bin

## Task 5: Indicator Variable
What is an indicator variable?
An indicator variable (or dummy variable) is a numerical variable used to label categories. They are called 'dummies' because the numbers themselves don't have inherent meaning.

Why use indicator variables?
You use indicator variables so you can use categorical variables for regression analysis.

Example
The column "fuel-type" has two unique values: "gas" or "diesel". Regression doesn't understand words, only numbers. To use this attribute in regression analysis, you can convert "fuel-type" to indicator variables.
Use the Panda method 'get_dummies' to assign numerical values to different categories of fuel type.
- Get the indicator variables and assign it to data frame "dummy_variable_1"
- Change the column names for clarity
- merge data frame "df" and "dummy_variable_1"
- drop original column "fuel-type" from "df"
- create an indicator variable for the column "aspiration"
- Merge the new dataframe to the original dataframe, then drop the column 'aspiration'.

# Explanatory Data Analysis (EDA)
## Objectives
- Explore features or characteristics to predict price of car
- Analyze patterns and run descriptive statistical analysis
- Group data based on identified parameters and create pivot tables
- Identify the effect of independent attributes on price of cars

## Task
- What is the data type of the column "peak-rpm"?
- Find the correlation between the following columns: bore, stroke, compression-ratio, and horsepower.
- Examine the correlation between 'engine-size' and 'price'
- Examine the correlation between 'highway-mpg' and 'price'
- Examine the correlation between 'peak-rpm' and 'price'
- Find the correlation between x="stroke" and y="price".
- Examine the relationship between "body-style" and "price".
- Examine "drive-wheels" and "price"
- Examine "enginelocation" and " price"
- Find the average "price" of each car based on "body-style".
- Calculate the Pearson Correlation Coefficient and P-value of 'wheel-base' and 'price'.
- Calculate the Pearson Correlation Coefficient and P-value of 'horsepower' and 'price'.
- Calculate the Pearson Correlation Coefficient and P-value of 'length' and 'price'.
- Calculate the Pearson Correlation Coefficient and P-value of 'width' and 'price'
- Calculate the Pearson Correlation Coefficient and P-value of 'curb-weight' and 'price'
- Calculate the Pearson Correlation Coefficient and P-value of 'engine-size' and 'price'
- Calculate the Pearson Correlation Coefficient and P-value of 'bore' and 'price'
- Calculate the Pearson Correlation Coefficient and P-value of'city-mpg' and 'highway-mpg'
- Calculate the Pearson Correlation Coefficient and P-value of Highway-mpg vs. Price

## Conclusion: Important Variables
We now have a better idea of what our data looks like and which variables are important to take into account when predicting the car price. We have narrowed it down to the following variables:

**Continuous numerical variables**:Continuous numerical variables are variables that may contain any value within some range. They can be of type "int64" or "float64".A great way to visualize these variables is by using scatterplots with fitted lines.
- Length
- Width
- Curb-weight
- Engine-size
- Horsepower
- City-mpg
- Highway-mpg
- Wheel-base
- Bore

**Categorical variables**:These are variables that describe a 'characteristic' of a data unit, and are selected from a small group of categories. The categorical variables can have the type "object" or "int64". A good way to visualize categorical variables is by using boxplots.
- Drive-wheels

## Correlation and Causation
**Correlation**: a measure of the extent of interdependence between variables.
**Causation:** the relationship between cause and effect between two variables.
**The Pearson Correlation** measures the linear dependence between two variables X and Y.
**The P-value** is the probability value that the correlation between these two variables is statistically significant. Normally, we choose a significance level of 0.05, which means that we are 95% confident that the correlation between the variables is significant.


# Model Development
In data analytics, we often use Model Development to help us predict future observations from the data we have.
A model will help us understand the exact relationship between different variables and how these variables are used to predict the result.

## Objective: 
Develop prediction models

##  Task 1:  Linear Regression and Multiple Linear Regression
### Simple Linear Regression
Simple Linear Regression is a method to help us understand the relationship between two variables:
- The predictor/independent variable (X)
- The response/dependent variable (that we want to predict)(Y)
- The result of Linear Regression is a linear function that predicts the response (dependent) variable as a function of the predictor (independent) variable.

#### Setup
- load the modules for linear regression
- Create the linear regression object

#### Task on Simple Linear Regression
- How could "highway-mpg" help us predict car price?
- How could "engine-size" help us predict car price?
  
### Multiple Linear Regression
If we want to use more variables in our model to predict car price, we can use Multiple Linear Regression. Multiple Linear Regression is very similar to Simple Linear Regression, but this method is used to explain the relationship between one continuous response (dependent) variable and two or more predictor (independent) variables. Most of the real-world regression models involve multiple predictors.

#### Task on Multiple Linear Regression
- Develop a model using Horsepower, Curb-weight, Engine-size and Highway-mpg as the predictors
- Create and train a Multiple Linear Regression model where the response variable is "price", and the predictor variable is "normalized-losses" and "highway-mpg"

## Task 2: Model Evaluation Using Visualization
Now that we've developed some models, how do we evaluate our models and choose the best one? One way to do this is by using a visualization.
First thing to do is to Import the visualization package, seaborn.
we will discuss on:
- Regression Plot
- Residual Plot
- Distribution plot

### Regression Plot
When it comes to simple linear regression, an excellent way to visualize the fit of our model is by using regression plots.
This plot will show a combination of a scattered data points (a scatterplot), as well as the fitted linear regression line going through the data. This will give us a reasonable estimate of the relationship between the two variables, the strength of the correlation, as well as the direction (positive or negative correlation).

#### What to do using regression plot
-  visualize highway-mpg as potential predictor variable of price
-  visualize peak-rpm as potential predictor variable of price
-  compare this plot to the regression plot of highway with peak-rpm
-  Given the regression plots above, check if "peak-rpm" or "highway-mpg" is more strongly correlated with "price"?

### Residual Plot
A good way to visualize the variance of the data is to use a residual plot.

What is a residual?
The difference between the observed value (y) and the predicted value (Yhat) is called the residual (e). When we look at a regression plot, the residual is the distance from the data point to the fitted regression line.

So what is a residual plot?
A residual plot is a graph that shows the residuals on the vertical y-axis and the independent variable on the horizontal x-axis.

What do we pay attention to when looking at a residual plot?
We look at the spread of the residuals:
- If the points in a residual plot are randomly spread out around the x-axis, then a linear model is appropriate for the data.

Why is that?
Randomly spread out residuals means that the variance is constant, and thus the linear model is a good fit for this data.

#### What to do using residual plot
-  visualize highway-mpg as potential predictor variable of price

### Multiple Linear Regression
How do we visualize a model for Multiple Linear Regression?
This gets a bit more complicated because you can't visualize it with regression or residual plot.
One way to look at the fit of the model is by looking at the distribution plot. We can look at the distribution of the fitted values that result from the model and compare it to the distribution of the actual values.

## Task 3: Polynomial Regression and Pipelines
### Polynomial Regression
Polynomial regression is a particular case of the general linear regression model or multiple linear regression models.
- create a function for plot
- define the x and y variables
- define the order of the polynomial
- plot the function

### Pipeline
Data Pipelines simplify the steps of processing the data. We use the module Pipeline to create a pipeline. We also use StandardScaler as a step in our pipeline.
- Import standardscaler, pipeline and polynomial feature
- create the pipeline by creating a list of tuples including the name of the model or estimator and its corresponding constructor.
- input the list as an argument to the pipeline constructor
- convert the data type Z to type float to avoid conversion warnings that may appear as a result of StandardScaler taking float inputs.
- normalize the data, perform a transform and produce a prediction simultaneously.

## Task 4: Measures for In-Sample Evaluation
When evaluating our models, not only do we want to visualize the results, but we also want a quantitative measure to determine how accurate the model is.
Two very important measures that are often used in Statistics to determine the accuracy of a model are:
- R^2 / R-squared
- Mean Squared Error (MSE)

R squared:  also known as the coefficient of determination, is a measure to indicate how close the data is to the fitted regression line.
The value of the R-squared is the percentage of variation of the response variable (y) that is explained by a linear model.

Mean Squared Error (MSE) :The Mean Squared Error measures the average of the squares of errors. That is, the difference between actual value (y) and the estimated value (ŷ).

### Simple Linear Regression Fit
- R2score =lm.score(X, Y)
- MSE = mean_squared_error(Y, Yhat)

### Multiple Linear Regression Fit 
- R2score =lm.score(Z, Y)
- MSE = mean_squared_error(Y, Yhat)

### Polynomial Fit
import r2_score
- r_squared = r2_score(y, p(x))
- MSE = mean_squared_error(df['price'], p(x))


## Prediction and Decision Making
### Prediction
In the previous section, we trained the model using the method fit. Now we will use the method predict to produce a prediction. Lets import pyplot for plotting; we will also be using some functions from numpy.
- Create a new input: new_input=np.arange(1, 100, 1).reshape(-1, 1)
- Fit the model: lm.fit(X, Y)
- Produce a prediction: yhat=lm.predict(new_input), yhat[0:5]
- plot the data: plt.plot(new_input, yhat), plt.show()

### Decision Making: Determining a Good Model Fit
Now that we have visualized the different models, and generated the R-squared and MSE values for the fits, how do we determine a good model fit?

What is a good R-squared value?
When comparing models, the model with the higher R-squared value is a better fit for the data.

What is a good MSE?
When comparing models, the model with the smallest MSE value is a better fit for the data.

Let's take a look at the values for the different models.
#### Simple Linear Regression: Using Highway-mpg as a Predictor Variable of Price.
- R-squared: 0.49659118843391759
- MSE: 3.16 x10^7

#### Multiple Linear Regression: Using Horsepower, Curb-weight, Engine-size, and Highway-mpg as Predictor Variables of Price.
- R-squared: 0.80896354913783497
- MSE: 1.2 x10^7

#### Polynomial Fit: Using Highway-mpg as a Predictor Variable of Price.
- R-squared: 0.6741946663906514
- MSE: 2.05 x 10^7

#### Simple Linear Model (SLR) vs. Polynomial Fit
- MSE: We can see that Polynomial Fit brought down the MSE, since this MSE is smaller than the one from the SLR.
- R-squared: The R-squared for the Polynomial Fit is larger than the R-squared for the SLR, so the Polynomial Fit also brought up the R-squared quite a bit.

Since the Polynomial Fit resulted in a lower MSE and a higher R-squared, we can conclude that this was a better fit model than the simple linear regression for predicting "price" with "highway-mpg" as a predictor variable.

#### Multiple Linear Regression (MLR) vs. Polynomial Fit
- MSE: The MSE for the MLR is smaller than the MSE for the Polynomial Fit.
- R-squared: The R-squared for the MLR is also much larger than for the Polynomial Fit.

#### Conclusion
Comparing these three models, we conclude that the MLR model is the best model to be able to predict price from our dataset. This result makes sense since we have 27 variables in total and we know that more than one of those variables are potential predictors of the final car price.




