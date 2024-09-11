# Automobile-Analyis : Data Processing and Preprocessing

# Objectives
- Handle missing values
- Correct data formatting
- Standardize and normalize data
- Binning
- Indicator variable

## What is the purpose of data wrangling? 
Data wrangling is used to convert data from an initial format to a format that may be better for analysis.

## Data Source: 

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









