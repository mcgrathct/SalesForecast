# HNIFinancial
Fall 2020-- Analytics Experience

# Introduction
Countless factors play into influencing the overall sales of products in a given industry. From unemployment numbers, to imposed tariffs, isolating which factors are "impactful" when looking at sales numbers is no simple task. The furniture industry is not exempt from fluctuations in sales, and the purpose of this project is to determine which economic factors are most impactful/account for the most varaince in furniture industry sales. 

This project utilizes both Python and R code, Python for the consolidation and import of data, and R for the purpose of forecasting and 


# Python (Jupyter Notebook)

### Libraries to install 
Not many libraries are required, but install both fredapi, pandas, and urllib

### Data import and cleaning
The Python notebook is largely self explanatory, with the only file import required coming in the form of the industry sales data. 

Create a csv file containing a table of sales values. The format should follow the file named "Example Sales Data.csv" contained in this repository. Follow the template by adding future years into columns to the right of the existing columns. 

### FRED API section 
- Contains all code used for importing the values for capacity utilization, advance retail sales, SAHM recession indicator, and industrial production. 

### Combine FRED DFs section
- Consolidate the imported FRED data into a single dataframe

### Import provided files section
#### Sales
- Import the sales data file using the provided template. Clean the files into a longer format and adjust the date column. These values are stored df_fis before being consolidated with the primary dataframe (df_full)

#### Create lag df
- This dataframe stores all lag12 sales (sales for the same month in the prior year) into a single dataframe for use in R. 

#### Percent change column
- Stores the percent change in sales by month. 

#### Create dataframe for months with known variables for unknown sales
- Finds the difference between dataframe records with sales values and without. It takes the difference in records and stores records without sales values into a dataframe for predicting using the R regression models. 

### Write csv
- Write the dataframes to csv files. The file locations will depend on the location you are using as a folder for data storage. Maintain the csv file names, as they are used in R


# R (R Studio)

### Libraries to install
Install the following libraries
- urca, vars, mFilter, tseries, forecast, tidyverse, dplyr, randomForest, glmnet, Metrics
These libraries are loaded in the first code chunk

## Code Chunks

### 2 
- This chunk loads the dataframes created in Jupyter. It also corrects a few columns to further prepare the data for processing.

### 3 
- This chunk creates time series objects for a number of imported values. 

### 4
- Each piece of this chunk creates and stores an arima forecast fore future variable values

### 5
- Each individual forecast is stored in a dataframe. 

### 6
- The dataframes created using forecasting are combined into a single dataframe (df_m). Df_m is cleaned to ensure readability and continuity. Most temporary dataframes/objects are cleared from the environment.

### 7 
- A train and test set is created. The linear model is trained and a summary statistics output is given along with a graph charting sales figures for this portion of the data

### 8 
- The test data portion of the data set is run through the linear model. Outputs are bound to a dataframe titled ltpred

### 9 
- The predicted records with unknown sales values are run through the linear model with the outputted predicted values stored in a dataframe titled pred

### 10
- Predicted values are charted against actual sales using the linear model outputs. The residuals are also output to a histogram

### 11
- The random forest model is created using the training data. The test data is then plotted with its output shown in the graph. 

### 12
- The forecasted values are run through the random forest model here and the predicted values are stored into the pred dataframe.

### 13
- GLMnet model is trained here

## 14 (output)
- Create a consolidated dataframe with forecasted values for given periods.
- The dataframe containing the output for forecasted values is called fisoutlook. The date columns is self-explanatory, the linear column contains predicted values from the df_m input into the linear model, the rf columns contains predicted values from the df_m input into the random forest, and the opt column contains values values created by an average of the output from the linear model and the ARIMA outputs from the monthly sales percent change over prior years numbers. 
