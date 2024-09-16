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
we will be using the following libraries:
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

Continuous numerical variables:
- Length
- Width
- Curb-weight
- Engine-size
- Horsepower
- City-mpg
- Highway-mpg
- Wheel-base
- Bore

Categorical variables:
- Drive-wheels







