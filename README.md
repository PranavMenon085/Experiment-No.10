Experiment No. 10

Name: Pranav Menon

PRN No.: 25070123085

Batch: ENTC - B1

Aim: To study the Pandas library in Python and understand Series, DataFrame creation, properties, data access, manipulation, and filtering.


THEORY

1) Introduction to Pandas

Pandas is a powerful open-source Python library built on top of NumPy, designed specifically
for data manipulation and analysis. The name "Pandas" is derived from "Panel Data," a term
used in econometrics for multidimensional structured data sets. It was created by Wes McKinney
in 2008 and has since become one of the most widely used libraries in data science and
analytics workflows.

Pandas provides two primary data structures: Series (one-dimensional) and DataFrame
(two-dimensional). These structures make it easy to work with structured data such as tables,
spreadsheets, and time-series data directly in Python.

Import Statement:
    import pandas as pd

Key Characteristics:

  - Labeled Data: Unlike NumPy arrays which use only integer-based indexing, Pandas structures
    have labeled axes (index for rows, column names for columns). This makes data access more
    intuitive and less error-prone.

  - Heterogeneous: A DataFrame can hold columns of different data types simultaneously — for
    example, one column can contain strings (object), another integers (int64), and another
    floating-point values (float64). This mirrors the structure of a real-world data table.

  - Flexible I/O: Pandas supports reading from and writing to a wide variety of file formats
    including CSV, Excel (.xlsx), SQL databases, JSON, HTML, and HDF5 files. This makes it
    easy to ingest data from virtually any source.

  - Built-in Operations: Pandas includes a rich set of functions for sorting, filtering,
    grouping, merging, pivoting, and aggregating data — operations that would otherwise require
    complex manual code.

  - Missing Data Handling: Pandas has built-in support for representing and handling missing
    values using NaN (Not a Number), which simplifies working with incomplete real-world
    datasets.

  - Time Series Support: Pandas has powerful built-in functionality for working with
    date-time indices, resampling, and rolling windows, making it ideal for financial and
    sensor data analysis.

Pandas serves as the foundation for many data science and machine learning pipelines. It is
commonly used alongside NumPy, Matplotlib, Seaborn, and Scikit-learn.


2) Series

A Series is a one-dimensional labeled array capable of holding any data type, including
integers, floats, strings, Python objects, and more. It can be thought of as a single column
from a spreadsheet or a dictionary with ordered keys.

Syntax:
    pd.Series([val1, val2, val3, ...])

Every Series consists of two components:
  - Values: The actual data stored in the array.
  - Index: Labels associated with each value. By default, the index is a range of integers
    starting from 0 (i.e., 0, 1, 2, ...), but custom labels can also be assigned.

Example:
    s = pd.Series([10, 20, 30, 40])
    Output:
        0    10
        1    20
        2    30
        3    40
        dtype: int64

The dtype (data type) is automatically inferred from the values. If all values are integers,
the dtype is int64. If a mix of integers and floats is provided, Pandas promotes the dtype to
float64. The index and values of a Series can be accessed individually using s.index and
s.values respectively.

A Series can also be created from a Python dictionary, where the dictionary keys become the
index labels and the dictionary values become the Series values. This makes it easy to create
labeled data without a full DataFrame.


3) DataFrame

A DataFrame is a two-dimensional, tabular data structure with labeled rows and columns. It
is the most commonly used Pandas structure and closely resembles a spreadsheet, a SQL table,
or a dictionary of Series objects (where each key maps to a column).

Syntax:
    pd.DataFrame({"ColName1": [values], "ColName2": [values], ...})

In this construction, dictionary keys become column names, and the associated lists become
the column data. All columns must have the same number of elements.

Example:
    data = {"Name": ["Alice", "Bob", "Charlie"], "Marks": [85, 90, 78]}
    df = pd.DataFrame(data)
    Output:
           Name  Marks
        0  Alice     85
        1    Bob     90
        2  Charlie   78

The leftmost column (0, 1, 2) is the row index, automatically assigned as integers starting
from 0. Custom row indices can also be set using the index parameter in pd.DataFrame().

A DataFrame can be created from multiple sources including:
  - A dictionary of lists (as shown above)
  - A list of dictionaries (each dictionary becomes a row)
  - A NumPy 2D array
  - An existing CSV or Excel file using pd.read_csv() or pd.read_excel()


4) DataFrame Properties

Every Pandas DataFrame exposes a set of built-in attributes that describe its structure,
dimensions, and content. These properties are accessed using dot notation and do not require
parentheses, as they are attributes rather than methods.

  - df.shape:
    Returns a tuple (rows, cols) representing the dimensions of the DataFrame.
    For a DataFrame with 3 rows and 2 columns, df.shape returns (3, 2).
    This is useful for quickly checking the size of a dataset after loading it.

  - df.size:
    Returns an integer equal to the total number of elements in the DataFrame,
    calculated as rows × columns. For a 3×2 DataFrame, df.size returns 6.

  - df.columns:
    Returns a Pandas Index object containing all column names. This can be iterated
    over, converted to a list, or used to check if a specific column exists in the
    DataFrame. Example: df.columns → Index(['Name', 'Marks'], dtype='object')

  - df.dtypes:
    Returns a Series where each entry corresponds to a column name and its associated
    data type. Text and mixed data appear as dtype object, integers as int64, and
    decimal numbers as float64. This is useful for data type validation before
    performing numerical operations.

  - df.index:
    Returns the row index of the DataFrame. By default, this is a RangeIndex starting
    from 0. Custom string or datetime indices can also be set to enable label-based
    row access.

  - df.head(n) / df.tail(n):
    Returns the first or last n rows of the DataFrame respectively. Useful for
    quickly previewing large datasets without printing all rows. Default n is 5.


5) Accessing Data

Pandas provides multiple ways to access individual elements, rows, columns, or subsets of
a DataFrame. The two primary accessor methods are .loc[] for label-based access and
.iloc[] for integer position-based access.

  a) Column Access using []:
     A single column can be retrieved by passing the column name in square brackets.
     The result is a Pandas Series.
     Example: df["Name"] → returns the Name column as a Series.
     Multiple columns can be accessed by passing a list of names:
     df[["Name", "Marks"]] → returns a DataFrame with only those two columns.

  b) Label-based Access using .loc[]:
     .loc[] accesses rows and columns by their labels (index values and column names).
     Syntax: df.loc[row_label, "ColumnName"]
     Example: df.loc[0, "Name"] → returns "Alice" (value at row 0, column Name).
     Slicing is also supported: df.loc[0:1, "Name"] returns rows 0 and 1 of Name.
     Note: Unlike Python slicing, .loc[] includes both endpoints.

  c) Position-based Access using .iloc[]:
     .iloc[] accesses data purely by integer positions (zero-based indexing), regardless
     of the actual index labels or column names.
     Syntax: df.iloc[row_position, col_position]
     Example: df.iloc[2, 1] → returns 78 (row index 2, column index 1, i.e., Charlie's Marks).
     This is especially useful when the row index is not a standard integer range.


6) Adding and Modifying Data

Pandas allows new columns to be added to an existing DataFrame and existing values to be
updated using label-based or position-based assignment.

  a) Adding a New Column:
     A new column is added by assigning a list of values to a new column name using the
     bracket operator. The list must have the same length as the number of rows.
     Example: df["Grade"] = ["First Class", "Distinction", "Second Class"]
     This creates a new column named Grade and appends it to the right of the DataFrame.

  b) Modifying Data Using .loc[]:
     An existing value can be updated using label-based assignment with .loc[].
     Example: df.loc[0, "Marks"] = 88 → changes Alice's Marks from 85 to 88.
     This directly modifies the original DataFrame in place.

  c) Modifying Data Using .iloc[]:
     Values can also be updated using integer position-based assignment with .iloc[].
     Example: df.iloc[0, 1] = 88 → changes the value at row 0, column 1 to 88.
     This achieves the same result as the .loc[] example above, but using positions
     instead of labels.

Both .loc[] and .iloc[] support conditional assignment and bulk updates, making them
versatile tools for data cleaning and transformation workflows.


7) Deleting Data

Pandas provides the .drop() method to remove rows or columns from a DataFrame. The method
can operate in two modes: returning a new DataFrame (non-destructive) or modifying the
original DataFrame directly (destructive).

  - Removing a Column (Without inplace):
    df.drop("ColName", axis=1) returns a new DataFrame with the specified column removed.
    The original DataFrame df remains unchanged.
    Example:
        df1 = df.drop("Grade", axis=1)
        print(df)   → still has Grade column
        print(df1)  → does not have Grade column

  - Removing a Column (With inplace=True):
    df.drop("ColName", axis=1, inplace=True) modifies the original DataFrame directly
    and returns None. The column is permanently removed from df.
    Example: df.drop("Grade", axis=1, inplace=True)

  - Axis Parameter:
    axis=1 specifies that a column is being removed.
    axis=0 specifies that a row is being removed.
    Example: df.drop(0, axis=0) removes the row with index label 0.

It is generally recommended to use the non-inplace version during exploratory analysis
to preserve the original data, and the inplace version only when the deletion is final.


8) Mathematical Operations

Pandas Series and DataFrame objects support a variety of built-in aggregation and
mathematical methods that operate on column data directly. These are especially useful for
quick statistical summaries without needing to write custom functions.

  - df["Col"].mean():
    Computes and returns the arithmetic mean (average) of all values in the specified column.
    Example: df["Marks"].mean() → returns 85.33 (average of 88, 90, 78 after modification).

  - df["Col"].max():
    Returns the maximum value present in the specified column.
    Example: df["Marks"].max() → returns 90.

  - df["Col"].min():
    Returns the minimum value present in the specified column.
    Example: df["Marks"].min() → returns 78.

  - df["Col"].sum():
    Returns the sum of all values in the column.

  - df["Col"].std():
    Returns the standard deviation of the column values, measuring how spread out the
    values are from the mean.

  - df["Col"].count():
    Returns the number of non-null (non-NaN) values in the column. This is useful for
    identifying missing data.

  - df.describe():
    Generates a comprehensive statistical summary of all numerical columns, including
    count, mean, standard deviation, minimum, 25th percentile, median, 75th percentile,
    and maximum values.

These operations work on any numeric column and can also be applied across an entire
DataFrame by calling them directly on df (e.g., df.mean() returns the mean of all columns).


9) Filtering Data

Filtering in Pandas is performed using Boolean indexing, where a condition is applied to a
column and the resulting Boolean Series (True/False for each row) is used to select only
the rows that satisfy the condition. This is one of the most powerful and frequently used
features of Pandas for data analysis.

Syntax:
    df[df["Col"] condition]

The inner expression df["Col"] condition evaluates to a Boolean Series of True/False values.
Passing this Boolean Series back into df[] as an index returns only the rows where the
condition evaluates to True.

Example:
    df[df["Marks"] > 80]
    → Returns all rows where the Marks column contains a value greater than 80.
    Output:
           Name  Marks
        0  Alice     88
        1    Bob     90

Supported Comparison Operators:
  - df["Col"] > value     → Greater than
  - df["Col"] < value     → Less than
  - df["Col"] >= value    → Greater than or equal to
  - df["Col"] <= value    → Less than or equal to
  - df["Col"] == value    → Equal to
  - df["Col"] != value    → Not equal to

Multiple conditions can be combined using:
  - & (AND):  df[(df["Marks"] > 75) & (df["Marks"] < 95)]
  - | (OR):   df[(df["Marks"] < 80) | (df["Marks"] > 88)]
  - ~ (NOT):  df[~(df["Marks"] == 90)]

Note: When combining multiple conditions, each individual condition must be enclosed in
parentheses due to Python's operator precedence rules.

String-based filtering can also be done using .str accessor methods such as
df["Name"].str.startswith("A") or df["Name"].str.contains("li"), which return Boolean
Series suitable for indexing.


CONCLUSION

The study of the Pandas library in Python was successfully completed.
