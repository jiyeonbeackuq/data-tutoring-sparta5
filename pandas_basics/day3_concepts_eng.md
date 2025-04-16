# Pandas Live Session - Week 3 Summary (Translated)

## 🎯 Session Goals

- Apply functions to DataFrames
- Handle time series data
- Use groupby and pivot_table for aggregations

---

## 1. Applying Functions

### 1.1 `apply()`
Apply custom functions to rows or columns.
```python
df.apply(func, axis=0)
```
- `axis=0`: Apply function to each column
- `axis=1`: Apply function to each row

#### Example
```python
def perform_operation(row):
    if row['operation'] == 'square':
        return row['value'] ** 2
    elif row['operation'] == 'double':
        return row['value'] * 2
    elif row['operation'] == 'negate':
        return -row['value']

df['result'] = df.apply(perform_operation, axis=1)
```

### 1.2 `lambda`
Anonymous one-liner function.
```python
df['ID'] = df['order_id'].apply(lambda x: x[:5])
```

---

## 2. Grouping & Pivoting

### 2.1 `groupby()`
Group data and compute summary statistics.
```python
df.groupby(['sex', 'pclass'])[['survived', 'age']].agg(['mean', 'sum'])
```

### 2.2 `pivot_table()`
Pivot table-like summary.
```python
df.pivot_table(index='who', columns='pclass', values='survived', aggfunc=['sum', 'mean'])
```

### 2.3 Descriptive Stats
- `mean()`, `median()`, `mode()`, `std()`, `var()`
- `quantile()`, `corr()`, `cumsum()`, `cumprod()`

Example:
```python
df.mean()
df.corr()
df.quantile(0.75)
```

---

## 3. Time Series

### 3.1 `pd.to_datetime()`
Convert string to datetime.
```python
pd.to_datetime('2019-1-1 12')
```

### 3.2 `pd.date_range()`
Generate a range of dates.
```python
pd.date_range('2018-1-1', '2019-1-2')
```

### 3.3 `datetime` Module
Work with dates/times manually.
```python
import datetime
now = datetime.datetime.now()
dt = datetime.datetime.strptime("2022-03-01 12:30:45", "%Y-%m-%d %H:%M:%S")
```

Format datetime:
```python
str_date = now.strftime("%Y-%m-%d %H:%M:%S")
```

Compute timedelta:
```python
delta = datetime.datetime(2022, 3, 1) - datetime.datetime(2022, 2, 28)
```

---

© TeamSparta
