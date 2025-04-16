# Pandas Live Session - Day 1

## 1. Introduction to Pandas

Pandas is a Python library designed to work intuitively with labeled or relational data structures. It is fast, flexible, and particularly well-suited for:

- Table-like data (like SQL tables or Excel sheets)
- Ordered or unordered time-series data
- Other types of observational/statistical datasets

### 📚 Official Documentation
https://pandas.pydata.org/docs/reference/index.html

### ✅ Importing Pandas
```python
import pandas as pd
pd.__version__
```

---

## 2. Data Structures in Pandas

### 2.1 DataFrame
- A 2-dimensional data structure (like Excel sheet)
- Has rows and columns with labeled indexes
- Each column can have its own data type (dtype)

```python
# Creating with list
pd.DataFrame([[1, 2, 3], [4, 5, 6], [7, 8, 9]], columns=['A', 'B', 'C'])

# Creating with dictionary
data = {
    'name': ['Kim', 'Lee', 'Park'],
    'age': [24, 27, 34],
    'children': [2, 1, 3]
}
df = pd.DataFrame(data)
```

### 2.2 Series
- A one-dimensional labeled array
- Each Series has an index and a value

```python
import numpy as np
arr = np.arange(100, 105)

s1 = pd.Series(arr)
s2 = pd.Series(['Manager', 'Deputy', 'Assistant', 'Staff', 'Intern'])
s3 = pd.Series([91, 2.5, 'Sports', 4, 5.16])
```

---

## 3. File I/O (Input/Output)

### 3.1 Reading Files
#### Excel
```python
excel = pd.read_excel('./filename.xlsx', sheet_name='Sheet1', engine='openpyxl')
```

#### CSV
```python
df = pd.read_csv('./filename.csv')
```

### 3.2 Saving Files
#### Excel
```python
df.to_excel('output.xlsx', index=False, sheet_name='Result')
```

#### CSV
```python
df.to_csv('output.csv', index=False)
```

---

## 4. Data Exploration

### 4.1 Viewing the Data
```python
df.head(5)
df.tail(5)
```

### 4.2 Info and Value Counts
```python
df.info()
df['column'].value_counts()
```

### 4.3 Attributes
```python
df.shape
# (rows, columns)

df.dtypes
df.columns
```

---

## 5. Combining Data

### 5.1 Concatenation
```python
pd.concat([df1, df2], axis=0, ignore_index=True)
```

### 5.2 Merging
```python
pd.merge(df1, df2, on='name', how='inner')
```

### Rename Columns
```python
df.rename(columns={'old_name': 'new_name'}, inplace=True)
```

---

## 6. Practice Setup & Tips

### Colab Setup
1. Open Colab link provided in the lecture notes
2. Save a copy to your Google Drive

### Mount Google Drive
```python
from google.colab import drive
drive.mount('/content/drive')
import os
os.chdir('/content/drive/MyDrive/data/')
os.getcwd()
```

### Shortcut Keys (Colab)
- Run cell: `Shift + Enter`
- Add cell: `Ctrl/Cmd + M + A`
- Delete cell: `Ctrl/Cmd + M + D`
- Markdown mode: `Ctrl/Cmd + M + M`

---

## 7. Learning Strategy

- 📘 **Before Session**: Study the prep VODs on data cleaning and visualization
- 💻 **During Session**: Follow along and type code in real time
- 🧪 **After Session**: Practice with the provided exercises

> Copyright © TeamSparta

