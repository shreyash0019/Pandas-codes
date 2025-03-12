
# Python Pandas Code Repository

This repository contains Python code examples demonstrating the usage of Pandas for data manipulation and analysis.

## Examples

### Importing Pandas and Creating a DataFrame

To begin using Pandas, you need to import it and create a DataFrame:

```python
import pandas as pd

data = {
    'Name': ['John', 'Anna', 'Peter', 'Linda'],
    'Age': [28, 24, 35, 32],
    'City': ['New York', 'Paris', 'Berlin', 'London']
}

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

### DataFrame Operations: Sorting

You can sort the DataFrame by one or more columns. Here's how to sort by Age:

```python
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

### Filtering Data

You can filter data based on conditions, for example, selecting all people over the age of 30:

```python
filtered_df = df[df['Age'] > 30]
print(filtered_df)
```

**Output:**
```
    Name  Age     City
2  Peter   35   Berlin
3  Linda   32   London
```

///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////


