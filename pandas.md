## Day 4: Pandas Cheet Codes

### Key Learnings
- Pandas

### Code Snippet
```python

import pandas as pd

# --- Pandas DataFrame and Series Creation ---

# Create a Series from a list
s = pd.Series([1, 2, 3, 4, 5])

# Create a Series with a custom index
s_indexed = pd.Series([10, 20, 30], index=['a', 'b', 'c'])

# Create a DataFrame from a dictionary of lists (common)
data = {
    'col1': [1, 2, 3, 4],
    'col2': ['A', 'B', 'C', 'D'],
    'col3': [True, False, True, False]
}
df = pd.DataFrame(data)

# Create a DataFrame from a list of dictionaries (each dict is a row)
data_rows = [
    {'name': 'Alice', 'age': 25},
    {'name': 'Bob', 'age': 30},
    {'name': 'Charlie', 'age': 35}
]
df_from_rows = pd.DataFrame(data_rows)

# Create an empty DataFrame
empty_df = pd.DataFrame()

# --- Viewing Data ---

# Display the first 5 rows
print(df.head())

# Display the last 5 rows
print(df.tail())

# Display a specific number of rows
print(df.head(2))

# Get a concise summary of the DataFrame
print(df.info())

# Get descriptive statistics for numerical columns
print(df.describe())

# Get the shape (number of rows, number of columns)
print(df.shape)

# Get the column names
print(df.columns)

# Get the index
print(df.index)

# Get the data types of each column
print(df.dtypes)

# --- Selection ---

# Select a single column (returns a Series)
print(df['col1'])

# Select multiple columns (returns a DataFrame)
print(df[['col1', 'col2']])

# Select rows by label (loc) - single row
print(df.loc[0])

# Select rows by label (loc) - multiple rows
print(df.loc[0:2])  # Inclusive of end label

# Select rows and columns by label (loc)
print(df.loc[0:1, ['col1', 'col3']])

# Select rows by integer position (iloc) - single row
print(df.iloc[0])

# Select rows by integer position (iloc) - multiple rows
print(df.iloc[0:2]) # Exclusive of end integer

# Select rows and columns by integer position (iloc)
print(df.iloc[0:1, 0:2])

# Conditional selection (Boolean indexing)
print(df[df['col1'] > 2])

# Multiple conditions
print(df[(df['col1'] > 2) & (df['col3'] == True)])

# Using .isin() for multiple values
print(df[df['col2'].isin(['A', 'C'])])

# --- Adding/Modifying/Deleting Columns ---

# Add a new column
df['new_col'] = df['col1'] * 10
print(df)

# Modify an existing column
df['col1'] = df['col1'] + 100
print(df)

# Delete a column (returns a new DataFrame)
df_no_col3 = df.drop('col3', axis=1)
print(df_no_col3)

# Delete a column in-place
del df['new_col']
print(df)

# --- Handling Missing Data ---

# Create a DataFrame with missing values
df_missing = pd.DataFrame({'A': [1, 2, pd.NA], 'B': [4, pd.NA, 6]})
print(df_missing)

# Check for missing values (returns a DataFrame of Booleans)
print(df_missing.isna())

# Count missing values per column
print(df_missing.isna().sum())

# Drop rows with any missing values
df_dropna_rows = df_missing.dropna()
print(df_dropna_rows)

# Drop columns with any missing values
df_dropna_cols = df_missing.dropna(axis=1)
print(df_dropna_cols)

# Fill missing values with a specific value
df_fillna_value = df_missing.fillna(0)
print(df_fillna_value)

# Fill missing values with the mean of the column
# For numerical columns, you would typically convert to a numeric type first
df_missing_num = pd.DataFrame({'A': [1, 2, 3, float('nan')], 'B': [4, 5, float('nan'), 7]})
df_fillna_mean = df_missing_num.fillna(df_missing_num['A'].mean())
print(df_fillna_mean)

# Forward fill missing values
df_ffill = df_missing.ffill()
print(df_ffill)

# Backward fill missing values
df_bfill = df_missing.bfill()
print(df_bfill)

# --- Operations ---

# Basic arithmetic operations on columns
df['col_sum'] = df['col1'] + df['col2'].astype(str) # Example, ensure compatible types
print(df)

# Applying a function to a Series
df['col1_squared'] = df['col1'].apply(lambda x: x**2)
print(df)

# Applying a function to a DataFrame row-wise or column-wise
def custom_func(row):
    return row['col1'] + 5

df['custom_calc'] = df.apply(custom_func, axis=1)
print(df)

# Unique values in a Series
print(df['col2'].unique())

# Count unique values
print(df['col2'].nunique())

# Value counts
print(df['col2'].value_counts())

# Sorting by values
print(df.sort_values(by='col1', ascending=False))

# Sorting by index
print(df.sort_index())

# --- Grouping and Aggregation ---

# Group by one column and calculate the mean of another
df_group = pd.DataFrame({'category': ['A', 'B', 'A', 'B'], 'value': [10, 20, 15, 25]})
print(df_group.groupby('category')['value'].mean())

# Group by multiple columns and apply multiple aggregations
print(df_group.groupby('category').agg({'value': ['sum', 'min', 'max']}))

# --- Merging and Joining DataFrames ---

df1 = pd.DataFrame({'key': ['A', 'B', 'C', 'D'], 'value1': [1, 2, 3, 4]})
df2 = pd.DataFrame({'key': ['B', 'D', 'E', 'F'], 'value2': [5, 6, 7, 8]})

# Inner merge (default) - only common keys
merged_inner = pd.merge(df1, df2, on='key', how='inner')
print(merged_inner)

# Left merge - all keys from left, matching from right
merged_left = pd.merge(df1, df2, on='key', how='left')
print(merged_left)

# Right merge - all keys from right, matching from left
merged_right = pd.merge(df1, df2, on='key', how='right')
print(merged_right)

# Outer merge - all keys from both
merged_outer = pd.merge(df1, df2, on='key', how='outer')
print(merged_outer)

# Concatenating DataFrames (stacking rows)
df_concat_rows = pd.concat([df1, df2], ignore_index=True)
print(df_concat_rows)

# Concatenating DataFrames (stacking columns)
df_concat_cols = pd.concat([df1, df2], axis=1)
print(df_concat_cols)

# --- Reshaping Data ---

# Pivot Table (useful for summarizing data)
df_pivot = pd.DataFrame({
    'date': ['2023-01-01', '2023-01-01', '2023-01-02', '2023-01-02'],
    'city': ['NY', 'SF', 'NY', 'SF'],
    'temp': [20, 15, 22, 18]
})
pivot_table = df_pivot.pivot_table(index='date', columns='city', values='temp')
print(pivot_table)

# Melting (transforming wide to long format)
melted_df = df_pivot.melt(id_vars=['date', 'city'], var_name='metric', value_name='value')
print(melted_df)

# --- Data Type Conversion ---

# Convert a column to a specific data type
df['col1'] = df['col1'].astype(str)
print(df.dtypes)

# Convert to numeric, coercing errors
df_str_num = pd.DataFrame({'A': ['1', '2', 'abc', '4']})
df_str_num['A_numeric'] = pd.to_numeric(df_str_num['A'], errors='coerce')
print(df_str_num)

# --- Working with Dates and Times ---

# Create a Series of datetime objects
dates = pd.to_datetime(['2023-01-01', '2023-01-02', '2023-01-03'])
df_dates = pd.DataFrame({'event_date': dates, 'value': [10, 12, 15]})
print(df_dates)

# Extract year, month, day, etc.
df_dates['year'] = df_dates['event_date'].dt.year
df_dates['month'] = df_dates['event_date'].dt.month
df_dates['day'] = df_dates['event_date'].dt.day
print(df_dates)

# Set datetime column as index
df_dates_indexed = df_dates.set_index('event_date')
print(df_dates_indexed)

# Resampling time series data
# Requires a datetime index
# Example: df_dates_indexed.resample('D').mean()

# --- Input/Output ---

# Read from CSV
# df_csv = pd.read_csv('your_file.csv')

# Write to CSV
# df.to_csv('output.csv', index=False) # index=False to avoid writing DataFrame index

# Read from Excel
# df_excel = pd.read_excel('your_file.xlsx', sheet_name='Sheet1')

# Write to Excel
# df.to_excel('output.xlsx', sheet_name='MySheet', index=False)

# Read from JSON
# df_json = pd.read_json('your_file.json')

# Write to JSON
# df.to_json('output.json', orient='records') # orient can be 'records', 'columns', 'index', etc.

# --- Miscellaneous ---

# Apply a function element-wise (using map for Series)
s_map = pd.Series([1, 2, 3])
s_mapped = s_map.map({1: 'one', 2: 'two', 3: 'three'})
print(s_mapped)

# Resetting index (turns index into a column)
df_reset = df.reset_index()
print(df_reset)

# Duplicated rows
df_dup = pd.DataFrame({'A': [1, 2, 1], 'B': ['x', 'y', 'x']})
print(df_dup.duplicated())

# Drop duplicated rows
print(df_dup.drop_duplicates())

# Rename columns
df_renamed = df.rename(columns={'col1': 'Column_One', 'col2': 'Column_Two'})
print(df_renamed)

# Pipe (chaining operations)
def add_one(df_local):
    df_local['col1'] = df_local['col1'] + 1
    return df_local

def multiply_by_two(df_local):
    df_local['col1'] = df_local['col1'] * 2
    return df_local

# Using the original df for pipe example
df_piped = df.pipe(add_one).pipe(multiply_by_two)
print(df_piped)
