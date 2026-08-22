# 1. Title
**Understanding Your Data Part 2: Univariate Analysis (EDA on Titanic Dataset)**

## 2. Overview
This session is the second video in the "Understanding Your Data" sub-series, following the previous video's 7 basic questions. It introduces EDA (Exploratory Data Analysis) and focuses specifically on **Univariate Analysis** — independently analyzing one column/variable at a time. 

Using the Titanic dataset, the speaker demonstrates different visualization techniques for categorical columns (countplot, pie chart) and numerical columns (histogram, distplot/KDE, boxplot), along with summary statistics (min, max, mean) and the concept of skewness. The next video will cover bivariate/multivariate analysis.

## 3. Detailed Notes

### 3.1 Introduction: What Is EDA and Univariate Analysis?
- **EDA (Exploratory Data Analysis):** its overall purpose is to understand data "inside-out."
- The most important approaches within EDA are: Univariate, Bivariate, and Multivariate Analysis.
- **Terminology:** "Uni" = single, "variate" = variable. Univariate analysis means analyzing a single variable (one column) independently.
- Analyzing two columns together = bivariate analysis.
- Analyzing more than two columns together = multivariate analysis.

### 3.2 Prerequisite Concept: Numerical vs. Categorical Data
Data broadly falls into two types:
- **Numerical data:** numbers (e.g., height, weight, age, phone battery capacity).
- **Categorical data:** categories (e.g., country, gender, college branch).
- When doing univariate analysis, the first question to ask is: *is this column numerical or categorical?* This determines the plotting approach.
- **Prerequisite skills:** Familiarity with Seaborn and Matplotlib.

### 3.3 The Titanic Dataset — Column Overview
Recap of the columns (one row per passenger, target = `Survived`):
- `PassengerId`: sequential passenger ID.
- `Survived`: target column (0/1).
- `Pclass`: passenger class (1 = wealthiest, 3 = cheapest).
- `Name`: passenger name.
- `Sex`: gender.
- `Age`: passenger age.
- `SibSp`: traveling with sibling/spouse.
- `Parch`: traveling with parent/child.
- `Ticket`: ticket number.
- `Fare`: ticket cost.
- `Cabin`: cabin allocation (mainly first class).
- `Embarked`: boarding station (S = Southampton, C = Cherbourg, Q = Queenstown).

### 3.4 Classifying Each Column as Categorical or Numerical
- `PassengerId`: numerical, but not useful for prediction.
- `Survived`: categorical (0 or 1).
- `Pclass`: categorical (1, 2, 3).
- `Sex`: categorical.
- `Age`: numerical.
- `SibSp` and `Parch`: technically numeric but treated as categorical.
- `Fare`: numerical.
- `Embarked`: categorical.
- (`Name`, `Ticket`, `Cabin`: too many unique categories for basic categorical tools).

### 3.5 Univariate Analysis: Categorical Columns

#### Tool 1: Countplot
Shows the frequency count of each category within a categorical column — functionally equivalent to `value_counts()`, but visualized as a bar chart.
```python
import seaborn as sns
sns.countplot(df['Survived'])
```
- **General rule:** for any categorical column, the countplot is the go-to first visualization.
- *Examples:* `Pclass` showed most in class 3, fewest in class 2. `Sex` showed more males. `Embarked` showed most boarded from Southampton.

#### Tool 2: Pie Chart
Used when percentage-based information is desired instead of raw counts.
```python
df['Survived'].value_counts().plot(kind='pie', autopct='%0.1f%%')
```
- `autopct` is needed to display percentage labels on the slices.
- *Results:* Survived: 61.6% died, 38.4% survived. Sex: 65% male, 35% female.

### 3.6 Univariate Analysis: Numerical Columns
Numerical/continuous data requires different tools since values span a continuous range.

#### Tool 1: Histogram
Divides a numerical column's range into bins and plots how many data points fall into each bin.
```python
import matplotlib.pyplot as plt
plt.hist(df['Age'])
```
- Helps understand distribution (how many on lower end vs. higher end).
- Adjusting the `bins` parameter (e.g., 5 vs 50) changes the granularity.

#### Tool 2: Distplot (Histogram + KDE)
An extension of the histogram, combining it with a KDE (Kernel Density Estimation) smoothed curve.
```python
sns.distplot(df['Age'])
```
- This curve is the **PDF (Probability Density Function)**.
- y-axis = probability, x-axis = value. 
- *Interpretation:* The probability of a passenger being exactly 40 is ~1.4%; exactly 60 is ~0.5%.

#### Tool 3: Boxplot
Provides a five-number summary of numerical data and identifies outliers.
```python
sns.boxplot(df['Fare'])
```
- **Statistical concepts:** Median (50th percentile), Q1 (25th percentile), Q3 (75th percentile).
- **IQR (Interquartile Range)** = Q3 - Q1.
- Calculated min (lower whisker) = Q1 - 1.5 × IQR.
- Calculated max (upper whisker) = Q3 + 1.5 × IQR.
- **Outliers:** Points outside this range. The boxplot for `Fare` showed a massive outlier at $500.

### 3.7 Other Plots Mentioned (Not Covered in Depth)
- Violin plot, Rug plot, and Swarm plot (less frequently used, available in Seaborn).

### 3.8 Additional Numerical Summary Statistics
Beyond plots, simple Pandas functions extract key summaries directly:
```python
df['Age'].min()    # 0.42
df['Age'].max()    # 80
df['Age'].mean()   # 29.69
```

### 3.9 Skewness
The distplot curve reveals if data is skewed.
- **Symmetrical:** Peaks perfectly in the center (Normal Distribution).
- **Skewed:** E.g., salaries (most earn low, very few earn extremely high).
```python
df['Age'].skew()
```
- 0 = perfectly symmetrical.
- Positive = positively skewed (right-skew).
- Negative = negatively skewed (left-skew).

### 3.10 Closing Remarks
- Univariate analysis gives a somewhat improved understanding of the dataset.
- Next video covers bivariate and multivariate analysis for richer insights.

## 4. Key Concepts
- EDA aims to understand data "inside-out" using univariate, bivariate, and multivariate analysis.
- The choice of technique depends on whether a column is categorical (countplot, pie chart) or numerical (histogram, distplot, boxplot, summary stats).
- A histogram shows exact counts in a range; a PDF (distplot) shows probability.
- Boxplot whiskers systematically flag potential outliers using the IQR formula.
- Skewness describes the asymmetry of a numerical distribution.

## 5. Important Definitions
- **Univariate Analysis:** Independent analysis of a single variable.
- **Categorical Data:** Data representing limited distinct groups.
- **Numerical Data:** Continuous numeric values.
- **Countplot:** A Seaborn plot showing the frequency count of categories.
- **Pie Chart:** Shows the percentage breakdown of categories.
- **Histogram:** Divides numeric range into bins and counts data points.
- **Distplot:** Combines a histogram with an overlaid KDE curve.
- **KDE / PDF:** Kernel Density Estimation / Probability Density Function. Estimates underlying probability distribution.
- **Boxplot:** Provides a five-number summary and visually flags outliers.
- **IQR (Interquartile Range):** Q3 minus Q1.
- **Outlier:** A data point falling outside the calculated whisker range.
- **Skewness:** A statistical measure of asymmetry.

## 6. Algorithms / Workflows

### Workflow: Univariate Analysis of a Categorical Column
1. Identify the column as categorical.
2. Plot a countplot: `sns.countplot(df['<column>'])`.
3. Optionally plot a pie chart: `df['<column>'].value_counts().plot(kind='pie', autopct='%0.1f%%')`.
4. Interpret the distribution.

### Workflow: Univariate Analysis of a Numerical Column
1. Identify the column as numerical.
2. Plot a histogram to see bin counts: `plt.hist(df['<column>'])`.
3. Plot a distplot for a smoothed probability view (PDF): `sns.distplot(df['<column>'])`.
4. Plot a boxplot to identify outliers and five-number summary: `sns.boxplot(df['<column>'])`.
5. Compute summary statistics: `.min()`, `.max()`, `.mean()`.
6. Compute skewness: `df['<column>'].skew()`.

## 7. Examples
- **Survived:** Countplot showed more deaths; pie chart showed 61.6% died.
- **Pclass:** Most passengers in class 3, fewest in class 2.
- **Age:** Histogram bulk concentrated between 18–40; min = 0.42. Boxplot showed median ~28 and max whisker ~65.
- **Fare:** Boxplot showed heavy skew toward low values, with extreme outliers ($500).
- **PDF interpretation:** Age 40 probability = ~1.4%; Age 60 probability = ~0.5%.

## 8. Best Practices and Tips
- Always determine whether a column is categorical or numerical first.
- For categorical columns, start with a countplot. Use a pie chart for percentages.
- For numerical columns, use histograms for raw distribution, distplots for probability/skew, and boxplots for outliers.
- Treat boxplot-flagged outliers as candidates for investigation/removal before ML modeling.
- Adjust histogram bin counts if the default doesn't reveal the shape clearly.
- Don't stop at single visualizations; consider follow-up questions to uncover hidden patterns.

## 9. Key Takeaways
- Univariate analysis is the practice of independently analyzing each column in a dataset, forming a core part of EDA.
- Analysis choices depend entirely on the categorical vs. numerical nature of the column.
- The distplot's KDE curve (PDF) provides probability-based insight beyond a simple histogram.
- The boxplot is a key tool for systematically identifying outliers via the IQR formula.
- Deep statistical grounding (percentiles, IQR, distributions) enhances numerical EDA capabilities.
