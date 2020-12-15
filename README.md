# HNIFinancial
Fall 2020-- Analytics Experience

# Introduction
Countless factors play into influencing the overall sales of products in a given industry. From unemployment numbers, to imposed tariffs, isolating which factors are "impactful" when looking at sales numbers is no simple task. The furniture industry is not exempt from fluctuations in sales, and the purpose of this project is to determine which economic factors are most impactful/account for the most varaince in furniture industry sales. 

This project utilizes both Python and R code, Python for the consolidation and import of data, and R for the purpose of forecasting and 


# Python

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



