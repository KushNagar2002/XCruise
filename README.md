# Used to import library
import pandas as pd 

# Used to create DataFrame 
df = pd.DataFrame([[1,2,3], [4,5,6], [7,8,9]], columns = ["X","Y","Z"], index=["a","b","c"]) 

# Methods for accessing Data --> .head(), .tail(), .sample()   
# Example:
    df.head(2)  # To display top 5 rows of Dataframe (2) for first 2 rows

    df.tail(2)  # To display bottom 5 rows of Dataframe (2) for last 2 rows

    df.sample(4)  # Random 4 rows from the Dataframe

    df.index.to_list()  # to_list() is used to convert dataframe to list  //

# Methods to load different files into the project

    # Add CSV file into the project
    coffee = pd.read_csv('https://raw.githubusercontent.com/KeithGalli/complete-pandas-tutorial/refs/heads/master/warmup-data/coffee.csv')

    # Add parquet file into the project
    coffee = pd.read_parquet('RAW FILE LOCATION') 

    # Add excel file into the project
    coffee = pd.excel('RAW FILE LOCATION' , sheet_name="SPECIFIC SHEET NAME")

# Accessing Data
    # (Uses location) .loc[#ROWS, #COLUMNS] =>

        1. coffee.loc[0]  # Give the first row of coffee dataframe 
        2. coffee.loc[[2,4,6]]  # Give the selected row of coffee dataframe
        3. coffee.loc[2:4]  # Gives the result from 2 row till 4th row of coffee dataframe
        4. coffee.loc[2:]  # Gives the result from onwards 2 row of coffee dataframe
        5. coffee.loc[5:8]  # Gives the result from onwards 2 and till 8th row of coffee dataframe
        6. coffee.loc[5:8, ["Day","Units Sold"]]  # We can get specific columns as well as rows
        7. coffee.loc[:, ["Day","Units Sold"]]  # We can get all rows and specific columns
    
    # (Uses index location) .iloc[#ROWS, #COLUMNS] =>
        1. coffee.iloc[0]  # Give the first row of coffee dataframe 
        2. coffee.iloc[[2,4,6]]  # Give the selected row of coffee dataframe
        3. coffee.iloc[2:4]  # Gives the result from 2 row till 3th row of coffee dataframe
        4. coffee.iloc[2:]  # Gives the result from onwards 2 row of coffee dataframe
        5. coffee.iloc[5:8]  # Gives the result from onwards 5 and till 7th row of coffee dataframe
        6. coffee.iloc[5:8, [0,2]]  # We can get specific columns as well as rows
        7. coffee.iloc[:, [0,2]]  # We can get all rows and specific columns

    # Difference between loc and iloc:
        - loc uses inclusive values.
        - loc uses names of the columns.

        - iloc uses exclusive values.
        - iloc uses indexes for displaying the columns

# Setting values with .loc() and .iloc()
    - coffee.index = orders["Day"]  # This will replace index of coffee with Day column
    - coffee.loc["Monday":"Wednesday", "Units Sold"]  # Now we can filter data without using indexes
    - coffee.loc[1, "Units Sold"] = 10  # This will update 1st row of Units Sold to 10

    # There are 2 more methods that can be used to access values from a file
        - coffee.at[0, "Units Sold"]
        - coffee.iat[0:3, "Units Sold"]
        (These are another way like .loc() and .iloc())

# Performing operations on Data
    - Sort Values = coffee.sort_values(["Units Sold", "Coffee Type"], ascending = False)
    - Sort Values = coffee.sort_values(["Units Sold", "Coffee Type"], ascending = [0,1])  (0 is False for "Units Sold")
    
