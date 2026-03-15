Experiment No. 10

Name: Pranav Menon

PRN No.: 25070123085

Batch: ENTC - B1

Aim: To study the Pandas library in Python and understand Series, DataFrame creation, properties, data access, manipulation, and filtering.

THEORY:

1) Introduction to Pandas

Pandas is a Python library for data manipulation and analysis built on top of NumPy. It provides two primary data structures: Series (1D) and DataFrame (2D).
Key Characteristics:
• Labeled Data – Rows and columns have labels (index/column names)
• Heterogeneous – Columns can have different data types
• Flexible – Supports reading/writing CSV, Excel, SQL, etc.
• Built-in Operations – Sorting, filtering, grouping, aggregation
Import: import pandas as pd

2) Series

A Series is a one-dimensional labeled array that can hold any data type. It has an index (default 0,1,2...) and a dtype.
Syntax: pd.Series([val1, val2, val3])
Example: pd.Series([10,20,30,40]) → index 0–3, dtype int64

3) DataFrame

A DataFrame is a two-dimensional tabular data structure with labeled rows and columns, created from a dictionary where keys become column names and values become column data.
Syntax: pd.DataFrame({"ColName": [values], ...})
Example: pd.DataFrame({"Name":["A","B","C"], "Marks":[85,90,78]})

4) DataFrame Properties

- df.shape – (rows, cols) tuple; e.g. (3,2) for 3 rows and 2 columns
- df.size – Total number of elements (rows × cols)
- df.columns – Index of column names
- df.dtypes – Data type of each column (object, int64, float64, etc.)

5) Accessing Data

- df["ColName"] – Access an entire column as a Series
- df.loc[row, "ColName"] – Access by label (row index and column name)
- df.iloc[row, col] – Access by integer position (zero-based index)
Example: df.loc[0,"Name"] → "A" | df.iloc[2,1] → 78

6) Adding and Modifying Data

- Add column: df["NewCol"] = [val1, val2, ...] → assigns a new column
- Modify by label: df.loc[row,"Col"] = new_value
- Modify by position: df.iloc[row,col] = new_value

7) Deleting Data

- df.drop("ColName", axis=1) – Returns new DataFrame without the column (original unchanged)
- df.drop("ColName", axis=1, inplace=True) – Modifies the original DataFrame directly
Note: axis=1 specifies column; axis=0 specifies row.

8) Mathematical Operations

Pandas supports column-wise aggregation operations:
- df["Col"].mean() – Arithmetic mean of the column
- df["Col"].max() – Maximum value in the column
- df["Col"].min() – Minimum value in the column

9) Filtering Data

Boolean indexing filters rows based on a condition applied to a column.
Syntax: df[df["Col"] condition]
Example: df[df["Marks"]>80] → returns rows where Marks > 80

ALGORITHMS

Algorithm 1: Create and Display a Pandas Series
Step 1: Start
Step 2: Import Pandas
   - Command: import pandas as pd
   - Function: import - imports the Pandas library
   - Source: Pandas library (pip install pandas / pre-installed in Colab)
Step 3: Create a Series
   - Command: s = pd.Series([10,20,30,40])
   - Function: pd.Series() - Creates a 1D labeled array from a list
   - Source: Pandas library function (import pandas as pd)
Step 4: Display the Series
   - Command: print(s)
   - Function: print() - Built-in function for console output
   - Source: Built-in Python function (no import required)
Step 5: Stop

Algorithm 2: Create and Display a DataFrame
Step 1: Start
Step 2: Define data dictionary
   - Command: data = {"Name":["A","B","C"], "Marks":[85,90,78]}
   - Function: {} - Dictionary literal; keys become column names
   - Source: Built-in Python data structure (no import required)
Step 3: Create DataFrame
   - Command: df = pd.DataFrame(data)
   - Function: pd.DataFrame() - Creates 2D tabular structure from dictionary
   - Source: Pandas library function (import pandas as pd)
Step 4: Display DataFrame
   - Command: print(df)
   - Function: print() - Built-in function for console output
   - Source: Built-in Python function (no import required)
Step 5: Stop

Algorithm 3: Determine Shape of DataFrame
Step 1: Start
Step 2: Print shape of DataFrame
   - Command: print(df.shape)
   - Function: .shape - DataFrame attribute returning (rows, cols) tuple
   - Source: Pandas DataFrame attribute (import pandas as pd)
Step 3: Stop

Algorithm 4: Determine Size of DataFrame
Step 1: Start
Step 2: Print total number of elements
   - Command: print(df.size)
   - Function: .size - DataFrame attribute returning total element count
   - Source: Pandas DataFrame attribute (import pandas as pd)
Step 3: Stop

Algorithm 5: Display Column Names of DataFrame
Step 1: Start
Step 2: Print column index
   - Command: print(df.columns)
   - Function: .columns - DataFrame attribute returning Index of column names
   - Source: Pandas DataFrame attribute (import pandas as pd)
Step 3: Stop

Algorithm 6: Identify Data Types of DataFrame Columns
Step 1: Start
Step 2: Print data type of each column
   - Command: print(df.dtypes)
   - Function: .dtypes - DataFrame attribute returning data type per column
   - Source: Pandas DataFrame attribute (import pandas as pd)
Step 3: Stop

Algorithm 7: Access Individual Columns
Step 1: Start
Step 2: Access and print Name column
   - Command: print(df["Name"])
   - Function: [] - Column accessor; returns column as a Pandas Series
   - Source: Pandas DataFrame indexing (import pandas as pd)
Step 3: Access and print Marks column
   - Command: print(df["Marks"])
   - Function: [] - Column accessor; returns column as a Pandas Series
   - Source: Pandas DataFrame indexing (import pandas as pd)
Step 4: Stop

Algorithm 8: Access Specific Rows Using loc and iloc
Step 1: Start
Step 2: Access by label using loc
   - Command: print(df.loc[0,"Name"]) ; print(df.loc[0,"Marks"])
   - Function: .loc[row,col] - Label-based row and column access
   - Source: Pandas DataFrame accessor (import pandas as pd)
Step 3: Access by position using iloc
   - Command: print(df.iloc[0,0]) ; print(df.iloc[2,1])
   - Function: .iloc[row,col] - Integer position-based access (zero-indexed)
   - Source: Pandas DataFrame accessor (import pandas as pd)
Step 4: Stop

Algorithm 9: Add a New Column to DataFrame
Step 1: Start
Step 2: Assign new column with values
   - Command: df["Grade"] = ["First Class","Distinction","Second Class"]
   - Function: [] - Column assignment; creates new column in DataFrame
   - Source: Pandas DataFrame operation (import pandas as pd)
Step 3: Display updated DataFrame
   - Command: print(df)
   - Function: print() - Built-in function for console output
   - Source: Built-in Python function (no import required)
Step 4: Stop

Algorithm 10: Modify Data Using loc and iloc
Step 1: Start
Step 2: Modify value using loc
   - Command: df.loc[0,"Marks"] = 88
   - Function: .loc[row,col] = value - Label-based assignment
   - Source: Pandas DataFrame accessor (import pandas as pd)
Step 3: Display updated DataFrame
   - Command: print(df)
   - Function: print() - Built-in function for console output
   - Source: Built-in Python function (no import required)
Step 4: Modify value using iloc
   - Command: df.iloc[0,1] = 88
   - Function: .iloc[row,col] = value - Position-based assignment
   - Source: Pandas DataFrame accessor (import pandas as pd)
Step 5: Display updated DataFrame
   - Command: print(df)
   - Function: print() - Built-in function for console output
   - Source: Built-in Python function (no import required)
Step 6: Stop

Algorithm 11: Delete a Column (Without inplace)
Step 1: Start
Step 2: Drop column without modifying original
   - Command: df1 = df.drop("Grade",axis=1)
   - Function: .drop(col,axis=1) - Returns new DataFrame with column removed
   - Source: Pandas DataFrame method (import pandas as pd)
Step 3: Display original and new DataFrame
   - Command: print(df) ; print(df1)
   - Function: print() - Shows original unchanged and new DataFrame without column
   - Source: Built-in Python function (no import required)
Step 4: Stop

Algorithm 12: Delete a Column (With inplace=True)
Step 1: Start
Step 2: Drop column modifying original DataFrame
   - Command: df.drop("Grade",axis=1,inplace=True)
   - Function: .drop() with inplace=True - Permanently removes column from df
   - Source: Pandas DataFrame method (import pandas as pd)
Step 3: Display updated DataFrame
   - Command: print(df)
   - Function: print() - Built-in function for console output
   - Source: Built-in Python function (no import required)
Step 4: Stop

Algorithm 13: Mathematical Operations on DataFrame Column
Step 1: Start
Step 2: Calculate mean of Marks column
   - Command: mean1 = df["Marks"].mean() ; print(mean1)
   - Function: .mean() - Returns arithmetic mean of column values
   - Source: Pandas Series method (import pandas as pd)
Step 3: Calculate maximum of Marks column
   - Command: max1 = df["Marks"].max() ; print(max1)
   - Function: .max() - Returns maximum value in column
   - Source: Pandas Series method (import pandas as pd)
Step 4: Calculate minimum of Marks column
   - Command: min = df["Marks"].min() ; print(min)
   - Function: .min() - Returns minimum value in column
   - Source: Pandas Series method (import pandas as pd)
Step 5: Stop

Algorithm 14: Filter Data Using Boolean Indexing
Step 1: Start
Step 2: Apply filter condition on Marks column
   - Command: print(df[df["Marks"]>80])
   - Function: df[condition] - Boolean indexing; returns rows where condition is True
   - Source: Pandas DataFrame filtering (import pandas as pd)
Step 3: Stop

CONCLUSION

The study of the Pandas library in Python was successfully completed.
