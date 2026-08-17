# 1. Title
**Data Gathering Part 1: Working with CSV Files (Pandas read_csv Deep Dive)**

## 2. Overview
This session begins a 4-video series on **Data Gathering** — the step following problem framing in the ML DLC — emphasizing that data is central to machine learning success. 

This first video focuses specifically on working with CSV files using Pandas' `read_csv()` function, covering roughly 15-16 parameters in depth so viewers have a lasting reference for handling CSV-related issues in the future. The session is a live, code-heavy walkthrough in Jupyter Notebook covering loading from local files and URLs, and numerous `read_csv` parameters (`sep`, `names`, `index_col`, `header`, `usecols`, `squeeze`, `skiprows`, `nrows`, `encoding`, `error_bad_lines`, `dtype`, `parse_dates`, `converters`, `na_values`, and `chunksize`).

## 3. Detailed Notes

### 3.1 Why Data Gathering Matters
- The previous session covered how to frame a machine learning problem; from this session onward (next 3-4 videos), the focus shifts to data gathering.
- **Core reasoning:** everything in ML is about data. A very good algorithm given little data will perform poorly, whereas even a comparatively weaker algorithm given a lot of data can perform well.
- **Goal of this mini-series:** learn to bring in data from different sources so that in the future, given any problem statement requiring data, the viewer can source it.

### 3.2 Overview of the 4-Video Data Gathering Series
1. **Video 1 (this session):** Working with CSV files — the most common format (~90% of datasets).
2. **Video 2:** JSON and SQL databases — JSON is common for APIs and Kaggle; SQL for databases.
3. **Video 3:** Fetching data from APIs — pulling data from a website's server.
4. **Video 4:** Web Scraping — used when no direct data source or API is available.

### 3.3 What Is a CSV File?
- **CSV (Comma Separated Values):** Each row of data occupies one line, and values are separated by commas.
- **TSV (Tab Separated Values):** Nearly identical to CSV, but values are separated by tabs instead of commas.

### 3.4 Setup and the read_csv Function
- The core function covered is `pd.read_csv()`.
- The notebook serves as a long, detailed reference addressing different edge cases, rather than a quick demo.

### 3.5 Loading CSV Files: Local File vs. URL
**From a Local File:**
If a CSV file is in the same folder as the notebook:
```python
df = pd.read_csv('train.csv')
```

**From a URL (e.g., GitHub):**
To load a remote CSV directly into Python without downloading:
```python
import pandas as pd
import requests
from io import StringIO

url = "your_url_here"
headers = {"User-Agent": "Mozilla/5.0"} # Example header
req = requests.get(url, headers=headers)
data = StringIO(req.text)
df = pd.read_csv(data)
```

### 3.6 read_csv Parameters Covered

#### sep
Controls the delimiter. Default is comma `,`. For TSV files, override with `\t`.
```python
df = pd.read_csv('movie_titles_metadata.tsv', sep='\t')
```

#### names
Provides column names when the file lacks a header row, preventing the first data row from being used as headers.
```python
df = pd.read_csv('movie_titles_metadata.tsv', sep='\t', 
                 names=['sno', 'movie_name', 'release_year', 'rating', 'votes', 'genre'])
```

#### index_col
Designates an existing column as the dataframe index.
```python
df = pd.read_csv('aug_train.csv', index_col='enrollee_id')
```

#### header
Specifies which row index should be treated as the column headers (useful if a bad row precedes the headers).
```python
df = pd.read_csv('test.csv', header=1)
```

#### usecols
Imports only a specified subset of columns, saving memory.
```python
df = pd.read_csv('aug_train.csv', usecols=['enrollee_id', 'gender', 'education_level'])
```

#### squeeze
If extracting a single column, setting `squeeze=True` returns a Series instead of a DataFrame. (Note: Deprecated in newer Pandas versions, often replaced by `.squeeze()`).
```python
s = pd.read_csv('aug_train.csv', usecols=['enrollee_id'], squeeze=True)
```

#### skiprows and nrows
- **skiprows:** Excludes specific row indices.
  ```python
  df = pd.read_csv('file.csv', skiprows=[0, 1])
  ```
- **nrows:** Restricts how many rows are imported (useful for large datasets).
  ```python
  df = pd.read_csv('file.csv', nrows=100)
  ```

#### encoding
Addresses character encoding issues. Default is UTF-8. If a dataset throws a decoding error, specify the correct encoding (e.g., `latin1`).
```python
df = pd.read_csv('zomato.csv', encoding='latin1')
```

#### error_bad_lines (or on_bad_lines)
Skips rows with an inconsistent number of fields instead of throwing a ParserError.
```python
df = pd.read_csv('book_dataset.csv', sep=';', encoding='latin1', error_bad_lines=False)
# In newer Pandas: on_bad_lines='skip'
```

#### dtype
Overrides automatic datatype inference to save memory (e.g., forcing a binary float to an int).
```python
df = pd.read_csv('aug_train.csv', dtype={'target': 'int'})
```

#### parse_dates
Converts date-like string columns into proper `datetime64` types.
```python
df = pd.read_csv('deliveries.csv', parse_dates=['Date'])
```

#### converters
Applies a custom transformation function to a specific column during loading.
```python
def rename(name):
    if name == "Royal Challengers Bangalore": return "RCB"
    return name

df = pd.read_csv('ipl_data.csv', converters={'team1': rename})
```

#### na_values
Specifies additional non-standard placeholder values (like hyphens or specific strings) that should be treated as NaN.
```python
df = pd.read_csv('aug_train.csv', na_values=['Male']) # Example only
```

#### chunksize
Loads a huge dataset in manageable row-count chunks via iteration, useful when the file exceeds available RAM.
```python
dfs = pd.read_csv('large_dataset.csv', chunksize=5000)
for chunk in dfs:
    print(chunk.shape)
```

## 4. Key Concepts
- Data gathering is the critical first practical step of the ML pipeline. Quality directly determines model performance.
- CSV is the easiest and most common ML format.
- Pandas' `read_csv()` function is highly configurable via numerous parameters to handle delimiter mismatches, missing headers, unwanted columns, non-standard encodings, malformed rows, and memory constraints.
- Understanding these parameters allows a practitioner to handle nearly any real-world CSV loading issue.

## 5. Important Definitions
- **CSV (Comma Separated Values):** A file format where rows are lines and values are separated by commas.
- **TSV (Tab Separated Values):** Similar to CSV, but tab-separated.
- **JSON (JavaScript Object Notation):** A universal data interchange format.
- **ParserError:** An error thrown when a CSV row has a different number of fields than expected.
- **chunksize:** Parameter to load data in smaller iterative pieces to prevent memory overload.

## 6. Algorithms / Workflows

### General Troubleshooting Workflow for read_csv Issues
- **All data in one column:** check and fix `sep` (`\t`).
- **No column headers:** use `names` to supply them manually.
- **Headers misidentified:** use `header` to point to the correct row index.
- **Redundant ID column:** use `index_col`.
- **Only some columns needed:** use `usecols`.
- **Exclude specific rows or limit size:** use `skiprows` or `nrows`.
- **UTF-8 decoding error:** use `encoding='latin1'`.
- **ParserError (field count mismatch):** use `error_bad_lines=False` (or `on_bad_lines='skip'`).
- **Inefficient datatypes:** use `dtype`.
- **Dates read as strings:** use `parse_dates`.
- **Transformations needed during load:** use `converters`.
- **Non-standard missing values:** use `na_values`.
- **Out of Memory (RAM) errors:** use `chunksize`.

## 7. Examples
- **GitHub URL Data:** Used `requests` and `StringIO` to load remote data.
- **TSV (`movie_titles_metadata.tsv`):** Showed how to fix missing headers and tab separators.
- **Header Offset (`test.csv`):** Fixed an issue where an extra "0" ruined the header detection.
- **Encoding Error (`zomato.csv`):** Fixed a UTF-8 error with `latin1`.
- **ParserError (Book dataset):** Handled inconsistent semicolon fields.
- **Chunking (190,000 rows):** Split a massive file into 5,000-row iterables.

## 8. Best Practices and Tips
- Treat this notebook as a lasting reference for CSV-loading issues.
- When encountering a UTF-8 decoding error, recognize it immediately as an encoding parameter issue.
- When encountering a ParserError with a mismatched field count, use `error_bad_lines=False` to skip malformed data.
- Check datatypes with `df.info()` early, and cast to smaller integer types to save memory.
- Always convert date strings with `parse_dates` to allow proper time-series filtering later.
- For extremely large files that crash your notebook, rely on `chunksize` to iterate through the data.

## 9. Key Takeaways
- Data gathering starts a 4-part series covering CSV, JSON/SQL, APIs, and web scraping.
- `read_csv()` is incredibly powerful, and its parameters are designed for real-world messy data.
- Recognizing error signatures (e.g., ParserError, UTF-8 errors) helps quickly diagnose which parameter to tweak.
- Chunking is a crucial technique for large-scale data science when RAM is a bottleneck.
