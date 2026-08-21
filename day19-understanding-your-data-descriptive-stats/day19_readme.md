# 1. Title
**Understanding Your Data Part 1: 8 Basic Questions to Ask (Titanic Dataset)**

## 2. Overview
This session (Day 19) begins a 4-video sub-series called "Understanding Your Data", following the completed Data Gathering series. 

This first video covers 8 basic questions every practitioner should ask immediately after receiving a new dataset, demonstrated live on the well-known Titanic dataset from Kaggle. The questions cover data size, data preview, column data types, missing values, mathematical/statistical summary, duplicate values, and correlation between columns. The next three videos in this sub-series will cover univariate EDA, multivariate EDA, and an automated EDA tool (Pandas Profiling).

## 3. Detailed Notes

### 3.1 Introduction and Roadmap
- Having completed Data Gathering, the focus shifts to what to do first to understand what's inside a dataset once you have it.
- **Roadmap for the 4-video sub-series:**
  1. Today's video: 8 basic questions to ask when you first get your data.
  2. Tomorrow's video: Begin EDA (Exploratory Data Analysis), starting with Univariate Data Analysis.
  3. Next video: Continue EDA with Multivariate Analysis.
  4. Final video: Pandas Profiling (automated EDA).
- **Dataset used:** the well-known Titanic dataset from Kaggle.
- **Setup:** Pandas already imported, dataset loaded into a variable named `df`.

### 3.2 Question 1: How Big Is the Data?
The first question that comes to mind: how large is the dataset (rows/columns)?
```python
df.shape
```
- Knowing this upfront matters because data size affects how you approach the rest of the work.

### 3.3 Question 2: What Does the Data Look Like?
```python
df.head()
```
- Returns the top 5 rows for a quick preview.

**Speaker's personal preference — using `sample()` instead:**
`head()` can introduce bias, since the first rows are sometimes systematically similar.
```python
df.sample(5)
```
- Returns 5 random rows, giving a more representative overview and reducing the risk of drawing a biased conclusion.

### 3.4 Question 3: What Are the Data Types of Each Column?
```python
df.info()
```
- Shows the count of non-null values, data type for each column, and overall memory usage.
- **Memory optimization insight:** some numerical columns are unnecessarily stored as floats when they could be integers. Converting them can reduce memory usage, which speeds up algorithms on very large datasets.

### 3.5 Question 4: Are There Missing Values in the Data?
Missing values are problematic, so it's important to know upfront whether they exist and how many there are.
```python
df.isnull().sum()
```
- Returns a Series showing the number of missing values per column.
- **Why this matters:** helps decide whether to fill (impute) or drop columns/rows. E.g., `Cabin` (missing 687/891) might be dropped entirely, whereas `Age` (missing 177) is a good candidate for filling.

### 3.6 Question 5: How Does the Data Look Mathematically?
Use Pandas' built-in `describe()` function for a high-level mathematical summary of all numerical columns:
```python
df.describe()
```
- Returns: count, mean, standard deviation, minimum, 25th/50th/75th percentiles, and maximum.
- **Note:** categorical/ID columns (like `PassengerId` and `Survived`) aren't meaningful here.
- **Insight on `Age` column:** Mean age is ~29-30, minimum is 0.42 (infant), 50th percentile is 28. Helps spot anomalies quickly.

### 3.7 Question 6: Does the Data Contain Duplicate Values?
Duplicate rows can cause problems in ML algorithms.
```python
df.duplicated().sum()
```
- Returns the total count of duplicate rows.
```python
df.drop_duplicates()
```
- Removes them if any exist.

### 3.8 Question 7: Is There Any Correlation Between the Columns?
Correlation describes how one variable changes in relation to another.
- **Why it matters:** helps identify which input columns have little to no relationship with the output/target column, so they can potentially be dropped.
```python
df.corr()
df.corr()['Survived']
```
- **Findings discussed:**
  - `Fare` shows a strong positive correlation (~0.25) with survival (wealthier passengers likely prioritized).
  - `Pclass` shows a strong negative correlation (third-class passengers had highest casualties).
  - `PassengerId` shows almost no correlation (~-0.005), carrying no predictive value.

### 3.9 Closing Remarks
- The purpose was to build initial clarity about the data.
- The next video will move into EDA using plots/graphs to gain further insight.

## 4. Key Concepts
- A structured set of upfront questions helps build a clear initial understanding of a new dataset.
- These questions cover: data size, representative preview, data types, missing values, statistical summary, duplicate rows, and correlation.
- Choosing `sample()` over `head()` reduces bias in previews.
- Understanding data types reveals memory optimization opportunities.
- Correlation analysis gives an early signal about which features are predictive vs. irrelevant.

## 5. Important Definitions
- **`df.shape`:** Returns the number of rows and columns.
- **`df.head()`:** Returns the first 5 rows.
- **`df.sample(n)`:** Returns `n` randomly selected rows.
- **`df.info()`:** Displays non-null counts, data types, and memory usage.
- **`df.isnull().sum()`:** Returns the exact count of missing values per column.
- **`df.describe()`:** Returns a statistical summary for numerical columns.
- **`df.duplicated().sum()`:** Returns the total count of duplicate rows.
- **`df.drop_duplicates()`:** Removes duplicate rows.
- **`df.corr()`:** Computes the Pearson correlation coefficient between numerical columns.
- **Pearson Correlation Coefficient:** A statistical measure (-1 to 1) indicating the strength and direction of linear relationships.

## 6. Algorithms / Workflows

### Workflow: 8 Basic Questions to Ask When First Receiving a Dataset
1. **How big is the data?** → `df.shape`
2. **What does the data look like?** → `df.sample(n)`
3. **What is the data type of each column?** → `df.info()`
4. **Are there missing values in the data?** → `df.isnull().sum()`
5. **How does the data look mathematically?** → `df.describe()`
6. **Are there duplicate values in the data?** → `df.duplicated().sum()`
7. **Is there correlation between the columns?** → `df.corr()['<target_column>']`
*(Note: The video title references "8 basic questions", but only explicitly names 7 distinct method-and-question pairs.)*

## 7. Examples
- **Titanic Dataset:** Used as the running example (891 rows, 12 columns).
- **Cabin column:** Missing 687 values (candidate for dropping).
- **Age column:** Missing 177 values (candidate for filling). `describe()` showed a minimum of 0.42 (infant).
- **Correlation with Survived:** `Fare` positive, `Pclass` strongly negative, `PassengerId` near zero.

## 8. Best Practices and Tips
- Prefer `df.sample(n)` over `df.head()` to avoid biased conclusions from ordered data.
- Use `df.info()` early to spot memory optimization opportunities (e.g., float to integer conversion).
- Check missing values (`df.isnull().sum()`) before deciding whether to drop or fill specific columns.
- Use `df.describe()` to catch statistical anomalies early.
- Always check for and remove duplicate rows before analysis.
- Use correlation analysis as an early signal for identifying useful vs. droppable columns.

## 9. Key Takeaways
- This session introduced a structured set of foundational questions to ask immediately upon receiving a dataset.
- These methods reveal concrete, actionable insights (e.g., dropping heavy-missing columns, uncovering statistical profiles, and identifying predictive correlations).
- These initial questions build a foundational "clear picture" of a dataset before moving into deeper Exploratory Data Analysis (EDA).
