Experiment No. 10

Name: Pranav Menon

PRN No.: 25070123085

Batch: ENTC - B1

Aim:

To study the Pandas library in Python and understand Series, DataFrame creation,
attributes, data access, manipulation, and their practical applications.

THEORY

1) Introduction to Pandas

Pandas is an open-source Python library built on top of NumPy, designed
specifically for data manipulation and analysis. It provides two primary data
structures — Series and DataFrame — that make it easy to work with structured,
labelled, and tabular data.

Pandas is widely used in data science, machine learning, and analytics for
tasks such as cleaning, filtering, transforming, aggregating, and summarising
datasets. It handles both numerical and non-numerical data, supports missing
values (NaN), and integrates seamlessly with other libraries like NumPy and
Matplotlib for end-to-end data workflows.

Pandas must be imported before use and is conventionally aliased as pd,
which is the widely accepted standard convention in the data science community.

Why use Pandas?

Working with raw NumPy arrays is efficient for numerical data but becomes
cumbersome when data has labels, mixed types, or missing values. Pandas solves
this by providing labelled axes (named rows and columns), flexible data types
per column, and a rich set of methods for data manipulation — all in a concise,
readable syntax similar to SQL and spreadsheet operations.

Key Characteristics:
• Tabular Structure – Data is organised in rows and columns like a spreadsheet.
• Labelled Axes – Both rows (index) and columns have meaningful labels.
• Flexible Data Types – Different columns in a DataFrame can hold different types.
• Missing Value Support – Handles NaN values gracefully without errors.
• Powerful Filtering – Supports boolean indexing for conditional row selection.
• Built on NumPy – Inherits speed and efficiency of NumPy for numeric operations.
• Imported as: import pandas as pd

2) Pandas Series

A Series is a one-dimensional labelled array capable of holding data of any
single type — integers, floats, strings, or Python objects. It is the simplest
Pandas data structure and is similar to a Python list, but with an associated
index label for every element.

The index defaults to 0, 1, 2, 3... (integer-based) unless explicitly
specified by the user. A Series also has an associated dtype that is
automatically inferred from the input data. Each element can be accessed using
its index label, similar to how a dictionary value is accessed by its key.

A Series can be created from:
- A Python list
- A Python dictionary (keys become index labels)
- A scalar value
- A NumPy array

Syntax:
s = pd.Series([10, 20, 30, 40])

Example Output:
0    10
1    20
2    30
3    40
dtype: int64

Custom Index Example:
s = pd.Series([10, 20, 30], index=["a", "b", "c"])
s["b"] → 20

Series from Dictionary:
data = {"Math": 90, "Science": 85, "English": 78}
s = pd.Series(data)
Output:
Math       90
Science    85
English    78
dtype: int64

In this case the dictionary keys become the index labels.
Individual values are accessed the same way: s["Math"] → 90

Series Attributes:
s.dtype  → data type of values
s.index  → the index labels
s.values → the underlying NumPy array of values

3) Pandas DataFrame

A DataFrame is a two-dimensional labelled data structure where each column can
hold a different data type. It is the most commonly used Pandas object and is
the central tool for data analysis in Pandas.

A DataFrame can be thought of as:
- A table in a relational database
- An Excel spreadsheet with named columns
- A dictionary of Series objects (each column is a Series)

DataFrames are typically created from dictionaries where keys become column
names and the associated lists become the column data. Each row is assigned an
integer index starting from 0 by default. DataFrames support a wide range of
operations including selection, filtering, aggregation, sorting, and merging.

Syntax:
data = {"Name": ["A","B","C"], "Marks": [85,90,78]}
df = pd.DataFrame(data)

Example Output:
  Name  Marks
0    A     85
1    B     90
2    C     78

The first unnamed column (0, 1, 2) is the row index.
Column names (Name, Marks) are the labels derived from dictionary keys.

DataFrames can also be created from:
- A list of dictionaries (each dictionary becomes a row)
- A 2D NumPy array with column names specified separately
- Reading external files such as CSV or Excel using pd.read_csv()

DataFrame vs Series:
- Series: 1D, single column of data with an index.
- DataFrame: 2D, multiple columns each of which is a Series.
  Every column in a DataFrame is internally stored as a Series.

4) DataFrame Attributes

Pandas DataFrames provide built-in attributes to quickly inspect the structure
and content of the data. These attributes do not modify the DataFrame — they
simply return information about it. They are accessed using dot notation.

a) df.shape
Returns a tuple (rows, columns) representing the dimensions of the DataFrame.
Useful for quickly understanding dataset size without printing the full data.

Example: df.shape → (3, 2)   [3 rows, 2 columns]

b) df.size
Returns the total number of elements in the DataFrame.
Calculated as: rows × columns.

Example: df.size → 6   [3 rows × 2 columns = 6 elements]

c) df.columns
Returns a Pandas Index object containing all column labels.
Useful for confirming column names before performing operations.

Example: df.columns → Index(['Name', 'Marks'], dtype='object')

d) df.dtypes
Returns the data type of each column in the DataFrame.
Columns containing text data show dtype as object.
Numeric columns show int64 or float64 depending on the values.

Example:
df.dtypes →
Name     object
Marks     int64
dtype: object

5) Accessing Data — Columns, loc, and iloc

Pandas provides multiple ways to access specific rows, columns, or individual
cells within a DataFrame. Choosing the right accessor depends on whether you
are working with labels or integer positions.

a) Column Access using [ ]
The simplest way to access an entire column is by using square brackets with
the column name as a string. This returns the column as a Pandas Series.

Syntax: df["column_name"]
Example: df["Name"] → returns all values in the Name column as a Series

b) df.loc[ ] — Label-Based Indexing
loc is used to access rows and columns by their label (name).
The first argument is the row label (index), the second is the column name.
If the DataFrame uses the default integer index, labels and positions coincide.

Syntax: df.loc[row_label, "column_name"]
Example:
df.loc[0, "Name"]   → "A"
df.loc[0, "Marks"]  → 85

c) df.iloc[ ] — Integer-Position-Based Indexing
iloc is used to access rows and columns strictly by their integer position
(0-based). It works regardless of what the actual index labels are.

Syntax: df.iloc[row_position, column_position]
Example:
df.iloc[0, 0]  → "A"    (row 0, column 0)
df.iloc[2, 1]  → 78     (row 2, column 1)

Key Difference:
loc  → uses labels  (what the index/column is named)
iloc → uses positions (0, 1, 2... counting from the left/top)


6) Adding, Modifying, and Deleting Columns

DataFrames are mutable data structures — their contents can be changed after
creation by adding new columns, updating existing values, or removing columns.

a) Adding a New Column
A new column is added by assigning a list of values to a new key name.
The list must have the same length as the number of existing rows.

Syntax: df["NewColumn"] = [val1, val2, val3]
Example:
df["Grade"] = ["First Class", "Distinction", "Second Class"]

b) Modifying an Existing Value
A specific cell can be updated using loc (label-based) or iloc (position-based).

Syntax: df.loc[row, "column"] = new_value
Example:
df.loc[0, "Marks"] = 88     # Updates row 0, Marks column to 88
df.iloc[0, 1] = 88           # Same operation using integer positions

c) Deleting a Column — Non-Destructive (drop)
df.drop("column", axis=1) returns a new DataFrame with the column removed.
The original DataFrame remains unchanged. axis=1 specifies column-wise operation.
axis=0 would remove a row instead.

Syntax: df1 = df.drop("Grade", axis=1)
Example:
df1 = df.drop("Grade", axis=1)
print(df)    # Original — still has Grade column
print(df1)   # New — Grade column removed

d) Deleting a Column — In-Place
Adding inplace=True permanently removes the column from the original DataFrame
without creating a new one. This is useful when the original variable should
reflect the change directly.

Syntax: df.drop("column", axis=1, inplace=True)
Example:
df.drop("Grade", axis=1, inplace=True)
print(df)    # Grade column is now permanently removed

7) Statistical and Filtering Operations

Pandas supports column-level statistical methods applied directly to a Series
(individual column), making descriptive analysis simple and readable.

a) Statistical Methods
- df["col"].mean() – Arithmetic mean of all values in the column.
- df["col"].max()  – Largest value in the column.
- df["col"].min()  – Smallest value in the column.

Example:
df["Marks"].mean() → 85.33
df["Marks"].max()  → 90
df["Marks"].min()  → 78

b) Boolean Filtering
Filtering uses boolean indexing to select specific rows based on a condition.
When a condition is applied to a column (e.g., df["Marks"] > 80), Pandas
produces a True/False Series of the same length. Passing this back into the
DataFrame returns only the rows where the condition is True.
This is more concise and efficient than using loops or if statements.

Syntax: df[df["column"] > value]
Example:
df[df["Marks"] > 80]
Output:
  Name  Marks
0    A     88
1    B     90
(Only rows where Marks > 80 are returned)


These operations make Pandas a concise and powerful tool for performing
data analysis directly on structured tabular datasets.

ALGORITHMS

Algorithm 1: Create and Display a Pandas Series

Step 1: Start
   - Begin Series creation and display

Step 2: Import Pandas library
   - Command: import pandas as pd
   - Function: import - Python keyword to load external module
   - Source: pandas library (import required)

Step 3: Create a Series
   - Command: s = pd.Series([10,20,30,40])
   - Function: pd.Series() - Creates a one-dimensional labelled array
   - Source: pandas library (import required)

Step 4: Display the Series
   - Command: print(s)
   - Function: print() - Built-in function for console output
   - Source: Built-in Python function (no import required)

Step 5: Stop
   - End the algorithm

Algorithm 2: Create and Display a DataFrame

Step 1: Start
   - Begin DataFrame creation and display

Step 2: Define data as a dictionary
   - Command: data = {"Name":["A","B","C"], "Marks":[85,90,78]}
   - Function: {} - Dictionary literal; [] - List literal
   - Source: Built-in Python data structures (no import required)

Step 3: Create DataFrame from dictionary
   - Command: df = pd.DataFrame(data)
   - Function: pd.DataFrame() - Creates a 2D tabular data structure
   - Source: pandas library (import required)

Step 4: Display the DataFrame
   - Command: print(df)
   - Function: print() - Built-in function for console output
   - Source: Built-in Python function (no import required)

Step 5: Stop
   - End the algorithm

Algorithm 3: Inspect DataFrame Attributes

Step 1: Start
   - Begin DataFrame attribute inspection

Step 2: Display shape of DataFrame
   - Command: print(df.shape)
   - Function: .shape - Attribute returning (rows, columns) tuple
   - Source: pandas DataFrame attribute (import required)

Step 3: Display total number of elements
   - Command: print(df.size)
   - Function: .size - Attribute returning total element count
   - Source: pandas DataFrame attribute (import required)

Step 4: Display column names
   - Command: print(df.columns)
   - Function: .columns - Attribute returning column labels
   - Source: pandas DataFrame attribute (import required)

Step 5: Display data types of columns
   - Command: print(df.dtypes)
   - Function: .dtypes - Attribute returning data type of each column
   - Source: pandas DataFrame attribute (import required)

Step 6: Stop
   - End the algorithm

Algorithm 4: Access, Modify, and Delete DataFrame Data

Step 1: Start
   - Begin data access and manipulation

Step 2: Access individual columns
   - Command: print(df["Name"]) ; print(df["Marks"])
   - Function: [] - Column access by name
   - Source: pandas DataFrame operation (import required)

Step 3: Access specific cell using loc and iloc
   - Command: print(df.loc[0,"Name"]) ; print(df.iloc[2,1])
   - Function: .loc[] - Label-based access; .iloc[] - Integer-based access
   - Source: pandas DataFrame indexers (import required)

Step 4: Add a new column
   - Command: df["Grade"] = ["First Class","Distinction","Second Class"]
   - Function: [] - Column assignment operator
   - Source: pandas DataFrame operation (import required)

Step 5: Modify an existing value
   - Command: df.loc[0,"Marks"] = 88
   - Function: .loc[] - Label-based assignment
   - Source: pandas DataFrame operation (import required)

Step 6: Delete a column without modifying original
   - Command: df1 = df.drop("Grade", axis=1)
   - Function: .drop() - Returns new DataFrame with specified column removed
   - Source: pandas DataFrame method (import required)

Step 7: Delete a column in-place
   - Command: df.drop("Grade", axis=1, inplace=True)
   - Function: .drop() with inplace=True - Modifies original DataFrame directly
   - Source: pandas DataFrame method (import required)

Step 8: Stop
   - End the algorithm

Algorithm 5: Statistical Operations and Filtering

Step 1: Start
   - Begin statistical analysis and data filtering

Step 2: Calculate mean of Marks column
   - Command: mean1 = df["Marks"].mean()
   - Function: .mean() - Returns arithmetic mean of column values
   - Source: pandas Series method (import required)

Step 3: Find maximum marks
   - Command: max1 = df["Marks"].max()
   - Function: .max() - Returns maximum value in column
   - Source: pandas Series method (import required)

Step 4: Find minimum marks
   - Command: min = df["Marks"].min()
   - Function: .min() - Returns minimum value in column
   - Source: pandas Series method (import required)

Step 5: Display results
   - Command: print(mean1) ; print(max1) ; print(min)
   - Function: print() - Built-in function for console output
   - Source: Built-in Python function (no import required)

Step 6: Filter rows where Marks > 80
   - Command: print(df[df["Marks"]>80])
   - Function: [] with condition - Boolean indexing for row filtering
   - Source: pandas DataFrame operation (import required)

Step 7: Stop
   - End the algorithm

Conclusion:

The study of the Pandas library in Python was successfully completed.
