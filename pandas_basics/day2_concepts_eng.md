# Pandas Live Session - Day 2

## 🎯 Session Goals

- Practice selecting data based on specific conditions
- Handle missing values
- Handle duplicates

---

## 1. Data Selection, Sorting, and Modification

### 1.1 Data Selection

#### `iloc` vs `loc`
- `iloc`: Select data using integer positions
- `loc`: Select data using label-based indexes

#### `iloc` examples:
```python
df.iloc[1, 3]  # Single cell

df.iloc[[0, 3, 4], [0, 1, 5, 6]]  # Fancy indexing

df.iloc[:3, :5]  # Slicing
```

#### `loc` examples:
```python
df.loc[5, 'class']  # Single cell

df.loc[2:5, ['age', 'fare', 'who']]  # Fancy indexing

df.loc[:6, 'class':'deck']  # Slicing
```

#### `loc` with Conditions:
```python
cond = (df['age'] >= 70)
df.loc[cond]  # Filtered rows

df.loc[cond, 'age'] = -1  # Replace values
```

#### Multiple Conditions:
```python
cond1 = (df['fare'] > 30)
cond2 = (df['who'] == 'woman')

df.loc[cond1 & cond2]
df.loc[cond1 | cond2]
```

### `isin()`
```python
sample['name'].isin(['kim', 'lee'])
condition = sample['name'].isin(['kim', 'lee'])
sample.loc[condition]
```

### `select_dtypes()`
```python
df.select_dtypes(include=[float, bool])
df.select_dtypes(exclude=['int64'])
df.select_dtypes(include=[float, object], exclude=['int64'])
```

---

### 1.2 Sorting
```python
df.sort_values(by=['col1', 'col2'], ascending=[False, True])
```

---

### 1.3 Data Type and Structure Changes

#### `astype()`
```python
df['column'] = df['column'].astype('int32')
```

#### `copy()`
```python
df_copy = df.copy(deep=True)
```

#### Add Row - `append()`
```python
df.append(df2, sort=True, ignore_index=True)
```

#### Add Column - `insert()`
```python
df.insert(3, 'col4', [10, 11, 12])
```

#### Remove Rows/Columns - `drop()`
```python
df.drop(index='row3', inplace=True)
df.drop(columns=['col1', 'col2'], inplace=True)
```

#### Set Index - `set_index()`
```python
df.set_index(keys='col1', inplace=True)
```

#### Change Index - `reindex()`
```python
df.reindex(columns=col2, fill_value='-')
```

#### Reset Index - `reset_index()`
```python
df.reset_index(inplace=True)
```

---

## 2. Handling Missing Values

### 2.1 Check Missing Values
```python
df.isna()
df.isna().sum()
df['col'].isna()
```

### 2.2 Check Non-Missing
```python
df.notna()
df.notna().sum()
```

### 2.3 Remove Missing - `dropna()`
```python
df.dropna(axis=0, how='any', inplace=True)
df.dropna(axis=1, how='all', inplace=True)
df.dropna(subset=['col1', 'col2'])
```

### 2.4 Fill Missing - `fillna()`
```python
df.fillna('A', inplace=True)

df.fillna(value={'col1': 'A', 'col2': 'B'})
```

---

## 3. Handling Duplicates

### 3.1 Check Duplicates - `duplicated()`
```python
df.duplicated(keep='first')
df.duplicated(keep='last')
df.duplicated(keep=False)
```

### 3.2 Remove Duplicates - `drop_duplicates()`
```python
df.drop_duplicates(inplace=True)
df.drop_duplicates(subset=['col1', 'col2'])
```

---

© TeamSparta
