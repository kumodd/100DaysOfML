# 1. Title
**Understanding Your Data Part 3: Bivariate & Multivariate Analysis**

## 2. Overview
This session is the third video in the "Understanding Your Data" sub-series, following the previous videos on 7 basic questions and univariate analysis. It covers **bivariate analysis** (two columns) and **multivariate analysis** (more than two columns).

The analysis is organized around the three possible column-type combinations: numerical-numerical, numerical-categorical, and categorical-categorical. Four datasets are used throughout — `tips`, `Titanic`, `flights`, and `Iris` (all from Seaborn, except `Titanic` which was used previously) — to demonstrate scatter plots, bar plots, box plots, distplots, crosstabs, heatmaps, clustermaps, pairplots, and line plots. The next video will cover an automation tool (Pandas Profiling) to speed up this kind of analysis.

## 3. Detailed Notes

### 3.1 Introduction and Setup
- **Recap:** Basic questions → Univariate analysis → Bivariate/Multivariate analysis.
- **Bivariate analysis:** analyzing exactly two columns together.
- **Multivariate analysis:** analyzing more than two columns together.
- **Four datasets used:**
  1. `tips`: restaurant data (total bill, tip, gender, smoker, day, time, party size).
  2. `Titanic`: passenger data.
  3. `flights`: US flights data (year, month, passengers).
  4. `Iris`: flower species data (sepal length/width, petal length/width, species).
- **Core framing:** What is the data type of each column? This determines the plotting technique (numerical-numerical, categorical-categorical, or numerical-categorical).

### 3.2 Combination 1: Numerical–Numerical
**Tool: Scatter Plot**
Used to explore the relationship between two numerical columns.
```python
# Example: tips dataset (total_bill vs. tip)
sns.scatterplot(x='total_bill', y='tip', data=tips)
```
- **Result:** A clear linear relationship — as the bill increases, the tip tends to increase.

**Extending to Multivariate Analysis:**
You can layer more variables onto a scatterplot:
```python
# hue (color) -> categorical
sns.scatterplot(x='total_bill', y='tip', data=tips, hue='sex')

# style (marker shape) -> categorical
sns.scatterplot(x='total_bill', y='tip', data=tips, hue='sex', style='smoker')

# size (marker size) -> numerical/categorical
sns.scatterplot(x='total_bill', y='tip', data=tips, hue='sex', style='smoker', size='size')
```
- **Result:** A single graph displaying 5 different dimensions of information simultaneously!

### 3.3 Combination 2: Numerical–Categorical
**Tool: Bar Plot**
```python
# Example: Titanic (Pclass vs Age)
sns.barplot(x='Pclass', y='Age', data=titanic)
```
- Shows the average age per class. (Adding `hue='Sex'` makes it multivariate).

**Tool: Box Plot (extended)**
```python
sns.boxplot(x='Sex', y='Age', data=titanic)
```
- Side-by-side boxplots show five-number summaries per category. Adding `hue='Survived'` shows survival patterns within age and gender.

**Tool: Distplot / KDE (extended)**
```python
sns.distplot(titanic[titanic['Survived'] == 0]['Age'], hist=False)
sns.distplot(titanic[titanic['Survived'] == 1]['Age'], hist=False)
```
- Overlays multiple PDFs. *Insight:* Very young children had a higher probability of surviving than dying, while adults aged 15-30 had a higher probability of dying.

### 3.4 Combination 3: Categorical–Categorical
**Tool: Crosstab**
Tabulates the relationship between two categorical columns.
```python
pd.crosstab(titanic['Pclass'], titanic['Survived'])
```

**Tool: Heatmap**
Visualizes a crosstab's numeric grid.
```python
sns.heatmap(pd.crosstab(titanic['Pclass'], titanic['Survived']))
```

**Refining with Percentages via `groupby`**
Raw counts don't control for total group size. Percentages are better.
```python
(titanic.groupby('Pclass')['Survived'].mean() * 100).plot(kind='bar')
```

**Tool: Clustermap**
Groups similar categories together using a hierarchical tree structure (dendrogram).
```python
sns.clustermap(pd.crosstab(titanic['SibSp'], titanic['Survived']))
```

### 3.5 Special Tool: Pairplot (Numerical-Numerical, Scaled Up)
Automatically generates a grid of scatterplots for *every* pair of numerical columns.
```python
# Example: Iris dataset
sns.pairplot(iris, hue='species')
```
- Extremely valuable when a dataset has many numerical columns.

### 3.6 Combination 4 (Special Case): Numerical–Numerical Over Time — Line Plot
Used specifically when the X-axis represents time (year, month, date).
```python
# Preparing yearly totals
new = flights.groupby('year').sum().reset_index()

sns.lineplot(x='year', y='passengers', data=new)
```

**Pivot Table + Heatmap/Clustermap**
```python
pivot = flights.pivot_table(values='passengers', index='month', columns='year')
sns.heatmap(pivot)
sns.clustermap(pivot)
```

### 3.7 Closing Remarks
- Practice applying these tools. EDA is a hands-on, iterative skill: "asking questions continuously and answering them".
- Next video covers Pandas Profiling (automated analysis).

## 4. Key Concepts
- Bivariate/Multivariate analysis extends univariate analysis by revealing relationships and interactions between variables.
- The choice of visualization technique depends strictly on the combination of data types involved.
- Seaborn's scatterplot supports `hue`, `style`, and `size`, enabling one plot to convey up to 5 dimensions of information.
- Percentage-based comparisons (via `groupby().mean()`) are more meaningful than raw counts when comparing groups of different sizes.
- `Heatmaps` and `Clustermaps` visualize large numeric grids. Clustermaps additionally reveal hierarchical similarities.

## 5. Important Definitions
- **Bivariate Analysis:** Analysis involving exactly two columns together.
- **Multivariate Analysis:** Analysis involving more than two columns together.
- **Scatter Plot:** Visualizes relationships between two numerical variables.
- **Bar Plot:** Shows an aggregated numerical value (usually average) across categories.
- **Crosstab:** A summary table showing the frequency counts between two categorical columns.
- **Heatmap:** Visualizes a grid of numeric values using color intensity.
- **Clustermap:** A heatmap that reorders rows/columns based on similarity, using a dendrogram.
- **Pairplot:** Generates scatterplots for all pairs of numerical columns.
- **Line Plot:** A scatterplot with connected points, used for time-based X-axes.
- **Pivot Table:** Reshapes data into a grid format across two dimensions.

## 6. Algorithms / Workflows

### Workflow: Choosing a Bivariate/Multivariate Analysis Technique
1. **Numerical–Numerical:** `sns.scatterplot()` (extend with `hue`, `style`, `size`).
2. **Numerical–Categorical:** `sns.barplot()`, `sns.boxplot()`, or `sns.distplot()` (overlaying multiple filtered PDFs).
3. **Categorical–Categorical:** `pd.crosstab()`, `sns.heatmap()`, `sns.clustermap()`, or `groupby().mean()` for percentages.
4. **Time-Series:** `sns.lineplot()`.
5. **Broad Overview:** `sns.pairplot()` for many numerical columns.

### Workflow: Pivot Tables to Heatmaps
1. Use `.pivot_table(values=..., index=..., columns=...)`.
2. Pass the resulting table into `sns.heatmap()` or `sns.clustermap()`.

## 7. Examples
- **Tips:** Scatter plot packed 5 dimensions (`total_bill`, `tip`, `sex`, `smoker`, `size`).
- **Titanic (Age distplot split by Survived):** Revealed children were prioritized for survival, while young adults (15-30) had high death rates.
- **Titanic (Pclass vs. Survived):** Pclass 1 had 62% survival, Pclass 3 had 24%.
- **Iris:** Pairplot instantly showed `petal_length` and `sepal_length` could clearly differentiate the three flower species.
- **Flights:** Clustermap grouped summer months (July/August) together as behaving similarly.

## 8. Best Practices and Tips
- Always identify the data types of the columns involved first.
- Use `hue`, `style`, and `size` to supercharge simple scatter plots into multivariate dashboards.
- Prefer percentage-based comparisons over raw frequency counts to avoid misleading conclusions due to unequal group sizes.
- Treat EDA as an iterative process: every answered question should prompt a deeper follow-up question.
- Reserve line plots specifically for sequential/time-series data.

## 9. Key Takeaways
- This session provided a comprehensive toolkit for bivariate and multivariate EDA based on column data types.
- Distplot/KDE comparisons across categories (e.g. overlapping survivor and non-survivor curves) reveal deep, non-obvious patterns hidden in raw data.
- EDA is fundamentally an iterative, question-driven process. The goal is to uncover the hidden story in the dataset.
- The next step is automating much of this manual plotting using Pandas Profiling.
