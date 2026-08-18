# 1. Title
**Data Gathering Part 2: Working with JSON and SQL**

## 2. Overview
This session (Day 16) continues the Data Gathering series, following the previous session on CSV files. The video covers two additional major data formats/sources: JSON (JavaScript Object Notation) and SQL databases. 

For JSON, the speaker demonstrates loading a recipe/cuisine classification dataset and a currency exchange rate dataset (from a URL) using `pd.read_json()`. For SQL, the speaker demonstrates the full workflow of importing a `.sql` database file using XAMPP/phpMyAdmin (MySQL), connecting to it from Python via the `mysql-connector` library, and querying it into a Pandas DataFrame using `pd.read_sql()`. The next session will cover fetching data from APIs.

*(Note on transcript: The latter portion of the provided transcript is a duplicate of content already covered in the previous "Day" session on CSV files. Since this material was already documented in detail, it is not repeated here to avoid redundancy — only the new JSON and SQL content unique to this session is covered below).*

## 3. Detailed Notes

### 3.1 Introduction: Why JSON and SQL Matter
- Continuing the Data Gathering series: the previous session covered CSV files; this session covers JSON and SQL.

### 3.2 What Is JSON?
- **JSON** stands for JavaScript Object Notation and is described as a universal format — meaning it can be understood/parsed by almost all programming languages.
- **Most important use case:** JSON is the typical format returned when querying an API running on a server.
- On Kaggle, some datasets are provided specifically in JSON format.

### 3.3 What Is SQL?
- **SQL** stands for Structured Query Language. It allows pulling data directly from a database into a Pandas DataFrame.
- Many Kaggle datasets are provided in SQL format.

### 3.4 Working with JSON
**Setup**
First step: `import pandas as pd`.

**Example 1: Recipe/Cuisine Dataset (`train.json`)**
- A recipe dataset where each entry represents a cuisine (e.g., Jamaican, Mexican) along with its list of ingredients.
- Framed as a classification problem (ingredients → cuisine type).
- **Loading JSON into Pandas:**
```python
df = pd.read_json('train.json')
```
- Functionally analogous to `read_csv`.
- Result: a DataFrame with a cuisine column and an ingredients column (ingredients stored as a list).
- `read_json` documentation includes many of the same parameters seen in `read_csv` (e.g., `dtype`, `convert_dates`, `encoding`, `chunksize`, `nrows`).

**Example 2: Loading JSON from a URL**
`read_json` can load data directly from a URL (e.g., JSON data served by an API):
```python
df = pd.read_json('<url>')
```
- Example demonstrated: a currency exchange rate dataset loaded directly from a URL.

### 3.5 Working with SQL
**Dataset and Preparation**
- **Example dataset:** the "World Cities" dataset from Kaggle, provided in `.sql` format.
- **Goal:** convert this `.sql` file into a Pandas DataFrame.
- **Step 1:** Download the `.sql` file from Kaggle.

**Setting Up a Local Database (XAMPP)**
- To use a `.sql` file, it must be loaded into a database on your machine (e.g., MySQL via XAMPP).
- **Software used:** XAMPP. Start the Apache web server and the MySQL database server.
- Navigate to `localhost/phpmyadmin` in a browser.

**Creating and Importing the Database**
- In phpMyAdmin, click "New" to create a new database (e.g., `world`).
- Import the `.sql` file into this new database.
- After import, three tables are created within the `world` database: `city`, `country`, and `countrylanguage`.

### 3.6 Connecting Python to MySQL
To bring this database data into Python/Pandas, the `mysql-connector` library is used.
```bash
# Installation:
pip install mysql-connector
```

```python
# Import
import mysql.connector

# Creating a connection to the database:
conn = mysql.connector.connect(
    host='localhost',
    user='root',
    password='',
    database='world'
)
```
- Running this returns a MySQL connection object, stored in the variable `conn`.

### 3.7 Querying the Database into a DataFrame
Pandas provides the `pd.read_sql()` function, which takes a SQL query and the connection object.
- **Example — loading the entire city table:**
```python
import pandas as pd
df = pd.read_sql("SELECT * FROM city", conn)
```

- **Filtering with SQL WHERE clauses:** standard SQL syntax can be used to filter data at load time.
```python
# Only Indian cities
df = pd.read_sql("SELECT * FROM city WHERE countrycode LIKE 'IND'", conn)

# Filtering life expectancy
df = pd.read_sql("SELECT * FROM country WHERE lifeexpectancy > 60", conn)
```

**Additional read_sql parameters:**
- `index_col` — designate a specific column as the DataFrame's index.
- Chunking support — loading data in chunks to avoid excessive RAM usage.

### 3.8 Closing Remarks
- This session covered how to work with JSON and SQL data formats.
- The next session will cover fetching data from an API to build a dataset.

## 4. Key Concepts
- JSON and SQL are, alongside CSV, among the most common data formats/sources encountered in real-world ML work.
- `pd.read_json()` functions similarly to `pd.read_csv()`, supporting loading from both local files and URLs.
- Working with SQL data requires hosting the `.sql` file's data in a database, establishing a Python-to-database connection, and querying it into a DataFrame using `pd.read_sql()`.
- SQL queries passed to `read_sql()` can include full SQL functionality (e.g., WHERE clause filtering).

## 5. Important Definitions
- **JSON (JavaScript Object Notation):** A universal, cross-language data interchange format, common for APIs.
- **SQL (Structured Query Language):** A language used to query and manage data in relational databases.
- **pd.read_json():** A Pandas function used to load JSON-formatted data directly into a DataFrame.
- **XAMPP:** Software used to set up a local web server (Apache) and database server (MySQL) environment.
- **phpMyAdmin:** A web-based interface used to manage MySQL databases.
- **mysql-connector:** A Python library enabling Python code to communicate with a MySQL database.
- **pd.read_sql():** A Pandas function that takes a SQL query string and a database connection object, and returns a DataFrame.

## 6. Algorithms / Workflows

### Workflow: Loading JSON Data into Pandas
**From a local file:**
```python
import pandas as pd
df = pd.read_json('filename.json')
```
**From a URL:**
```python
df = pd.read_json('<url>')
```

### Workflow: Loading SQL Data into Pandas
1. **Download** the target `.sql` file.
2. **Install and set up XAMPP** (start Apache and MySQL).
3. **Create and populate a database via phpMyAdmin** (Import the `.sql` file).
4. **Install the Python-MySQL bridge library:**
   ```bash
   pip install mysql-connector
   ```
5. **Connect to the database from Python:**
   ```python
   import mysql.connector
   conn = mysql.connector.connect(host='localhost', user='root', password='', database='world')
   ```
6. **Query the database into a DataFrame:**
   ```python
   import pandas as pd
   df = pd.read_sql("SELECT * FROM <table_name>", conn)
   ```

## 7. Examples
- **`train.json` (Recipe/Cuisine dataset):** ~39,000 dishes with cuisine type and ingredient list columns.
- **Currency Exchange Rate dataset (via URL):** Loaded directly from a URL using `read_json`, resulting in 160 rows.
- **World Cities SQL dataset:** Imported into a local MySQL database via XAMPP, used to demonstrate the full SQL-to-DataFrame workflow, including filtering examples (e.g., cities in India vs. USA).

## 8. Best Practices and Tips
- When working with JSON data, check the `read_json` documentation for parameters analogous to those in `read_csv` (encoding, chunking, etc.).
- For SQL-format datasets (`.sql` files), the XAMPP + phpMyAdmin + `mysql-connector` + `read_sql` workflow is the simplest reliable approach for beginners.
- Take advantage of full SQL query syntax (e.g., WHERE clauses) within `read_sql()` calls to filter and shape data precisely at load time.
- Experiment with different JSON and SQL datasets from Kaggle to build familiarity.

## 9. Key Takeaways
- This session extended the Data Gathering series to cover JSON and SQL, two very commonly encountered data formats.
- `pd.read_json()` mirrors `pd.read_csv()` in usage and supports loading from both local files and URLs.
- Working with SQL data requires a multi-step setup involving a database host, a Python connector, and `read_sql()`.
- SQL's full query power can be leveraged directly within `read_sql()` calls for precise, efficient data loading.
- The next session will cover fetching data from APIs.
