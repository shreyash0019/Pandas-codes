# Python Pandas Code Repository

This repository contains Python code examples demonstrating the usage of Pandas for data manipulation and analysis. Pandas is a powerful library for data analysis in Python, providing data structures and functions needed to manipulate structured data seamlessly.

## Getting Started with Pandas

### Importing Pandas and Creating a DataFrame

To begin using Pandas, you need to import the library. The most common alias for Pandas is `pd`. You can create a DataFrame, which is a two-dimensional, size-mutable, potentially heterogeneous tabular data structure with labeled axes (rows and columns).

Here’s an example:

```python
import pandas as pd

# Sample data for creating a DataFrame
data = {
    'Name': ['John', 'Anna', 'Peter', 'Linda'],
    'Age': [28, 24, 35, 32],
    'City': ['New York', 'Paris', 'Berlin', 'London']
}

# Creating a DataFrame
df = pd.DataFrame(data)
print(df)
```

**Output:**
```
    Name  Age       City
0   John   28   New York
1   Anna   24      Paris
2  Peter   35     Berlin
3  Linda   32     London
```

In the example above, we create a dictionary with sample data and then convert it into a DataFrame using `pd.DataFrame(data)`.

### DataFrame Operations

Pandas provides numerous functions for data manipulation. Below are some common operations:

#### Sorting Data

Sorting is an essential operation to organize data. You can sort a DataFrame by one or more columns using the `sort_values` method:

```python
# Sorting by 'Age'
df_sorted = df.sort_values(by='Age')
print(df_sorted)
```

**Output:**
```
    Name  Age       City
1   Anna   24      Paris
0   John   28   New York
3  Linda   32     London
2  Peter   35     Berlin
```

You can also sort by multiple columns. For instance, to sort by `City` and then by `Age`:

```python
# Sorting by 'City' and then by 'Age'
df_sorted_multi = df.sort_values(by=['City', 'Age'])
print(df_sorted_multi)
```

**Output:**
```
    Name  Age       City
2  Peter   35     Berlin
3  Linda   32     London
1   Anna   24      Paris
0   John   28   New York
```

#### Filtering Data

Filtering allows you to select rows that meet certain conditions. For example, to filter all people over the age of 30:

```python
# Filtering rows where 'Age' > 30
filtered_df = df[df['Age'] > 30]
print(filtered_df)
```

**Output:**
```
    Name  Age     City
2  Peter   35   Berlin
3  Linda   32   London
```

You can also filter using multiple conditions. For instance, to filter people who are older than 30 and live in London:

```python
# Filtering rows where 'Age' > 30 and 'City' is 'London'
filtered_df_multi = df[(df['Age'] > 30) & (df['City'] == 'London')]
print(filtered_df_multi)
```

**Output:**
```
    Name  Age    City
3  Linda   32  London
```

### Adding and Removing Columns

You can easily add new columns to a DataFrame. Here’s how to add a new column called `Salary`:

```python
# Adding a new column
df['Salary'] = [70000, 80000, 120000, 110000]
print(df)
```

**Output:**
```
    Name  Age     City  Salary
0   John   28  New York   70000
1   Anna   24     Paris   80000
2  Peter   35    Berlin  120000
3  Linda   32    London  110000
```

To remove a column, use the `drop` method:

```python
# Removing the 'Salary' column
df = df.drop('Salary', axis=1)
print(df)
```

**Output:**
```
    Name  Age     City
0   John   28  New York
1   Anna   24     Paris
2  Peter   35    Berlin
3  Linda   32    London
```

### Data Aggregation and Grouping

Pandas provides powerful group-by functionality to perform complex data analysis and aggregation. For example, to group by the `City` column and calculate the mean age:

```python
# Grouping by 'City' and calculating mean age
grouped_df = df.groupby('City').mean()
print(grouped_df)
```

**Output:**
```
         Age
City         
Berlin   35.0
London   32.0
New York 28.0
Paris    24.0
```

You can apply multiple aggregation functions using the `agg` method:

```python
# Applying multiple aggregation functions
agg_df = df.groupby('City').agg({'Age': ['mean', 'max', 'min']})
print(agg_df)
```

**Output:**
```
            Age          
           mean max min
City                     
Berlin     35.0  35  35
London     32.0  32  32
New York   28.0  28  28
Paris      24.0  24  24
```

### Handling Missing Data

Pandas provides methods to handle missing data. For example, to fill missing values with a specific value:

```python
# Creating a DataFrame with missing values
data_with_nan = {
    'Name': ['John', 'Anna', 'Peter', 'Linda'],
    'Age': [28, None, 35, 32],
    'City': ['New York', 'Paris', 'Berlin', None]
}

df_nan = pd.DataFrame(data_with_nan)
print(df_nan)

# Filling missing values
df_filled = df_nan.fillna({'Age': 30, 'City': 'Unknown'})
print(df_filled)
```

**Output:**
```
    Name   Age     City
0   John  28.0  New York
1   Anna   NaN     Paris
2  Peter  35.0    Berlin
3  Linda  32.0      NaN

    Name   Age      City
0   John  28.0  New York
1   Anna  30.0     Paris
2  Peter  35.0    Berlin
3  Linda  32.0   Unknown
```

You can also drop rows with missing values:

```python
# Dropping rows with missing values
df_dropped = df_nan.dropna()
print(df_dropped)
```

**Output:**
```
    Name   Age     City
0   John  28.0  New York
2  Peter  35.0    Berlin
```

### Merging and Joining DataFrames

Pandas allows you to combine DataFrames using various methods, such as `merge`, `join`, and `concat`. Here’s an example of merging two DataFrames:

```python
# Creating another DataFrame
data2 = {
    'Name': ['John', 'Anna', 'Peter', 'Linda'],
    'Salary': [70000, 80000, 120000, 110000]
}

df2 = pd.DataFrame(data2)

# Merging DataFrames on 'Name'
merged_df = pd.merge(df, df2, on='Name')
print(merged_df)
```

**Output:**
```
    Name  Age     City  Salary
0   John   28  New York   70000
1   Anna   24     Paris   80000
2  Peter   35    Berlin  120000
3  Linda   32    London  110000
```

### Conclusion

This repository demonstrates how to perform various data manipulation and analysis tasks using the Pandas library in Python. Pandas provides a comprehensive set of tools that make data analysis efficient and straightforward. The examples provided cover the basics, but Pandas has many more functionalities that can be explored for more advanced data analysis tasks.
