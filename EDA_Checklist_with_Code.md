
# 🧪 Exploratory Data Analysis (EDA) Checklist

A step-by-step checklist for performing thorough Exploratory Data Analysis on a dataset using Python and pandas.

---

## ✅ 1. Understand the Data

- **Load the data**  
  ```python
  pd.read_csv('filename.csv')
  ```

- **Check data types and structure**  
  ```python
  df.info()
  df.dtypes
  ```

- **View first few rows**  
  ```python
  df.head()
  ```

- **Understand the context (business/domain)**  
  _No code – use documentation or domain knowledge._

- **Identify the target variable**  
  _Define based on problem (if supervised learning)._

---

## ✅ 2. Data Dimensions

- **Check number of rows and columns**  
  ```python
  df.shape
  ```

- **Check unique values per column**  
  ```python
  df.nunique()
  ```

- **Count duplicate rows**  
  ```python
  df.duplicated().sum()
  ```

---

## ✅ 3. Missing Values

- **Check missing values count**  
  ```python
  df.isnull().sum()
  ```

- **Check missing values percentage**  
  ```python
  (df.isnull().mean() * 100).round(2)
  ```

- **Visualize missing data**  
  ```python
  import seaborn as sns
  sns.heatmap(df.isnull(), cbar=False)
  ```

---

## ✅ 4. Data Types and Conversion

- **Check data types**  
  ```python
  df.dtypes
  ```

- **Convert to datetime**  
  ```python
  df['col'] = pd.to_datetime(df['col'])
  ```

---

## ✅ 5. Descriptive Statistics

- **Summary stats for numeric columns**  
  ```python
  df.describe()
  ```

- **Summary stats for categorical columns**  
  ```python
  df['col'].value_counts()
  ```

- **Check skewness and kurtosis**  
  ```python
  df.skew()
  df.kurtosis()
  ```

---

## ✅ 6. Univariate Analysis

- **Histogram for numeric variables**  
  ```python
  df['col'].hist()
  ```

- **Count plot for categorical variable**  
  ```python
  sns.countplot(x='col', data=df)
  ```

- **Box plot for outliers**  
  ```python
  sns.boxplot(x='col', data=df)
  ```

---

## ✅ 7. Bivariate / Multivariate Analysis

- **Correlation matrix + heatmap**  
  ```python
  df.corr()
  sns.heatmap(df.corr(), annot=True)
  ```

- **Scatter plot**  
  ```python
  sns.scatterplot(x='col1', y='col2', data=df)
  ```

- **Box plot (numeric vs category)**  
  ```python
  sns.boxplot(x='category_col', y='numeric_col', data=df)
  ```

- **Crosstab (category vs category)**  
  ```python
  pd.crosstab(df['col1'], df['col2'])
  ```

---

## ✅ 8. Outlier Detection

- **Using IQR**  
  ```python
  Q1 = df['col'].quantile(0.25)
  Q3 = df['col'].quantile(0.75)
  IQR = Q3 - Q1
  df[(df['col'] < Q1 - 1.5*IQR) | (df['col'] > Q3 + 1.5*IQR)]
  ```

- **Handle outliers**  
  _Remove, cap, or flag based on strategy._

---

## ✅ 9. Feature Engineering

- **Create new features (e.g., date parts)**  
  ```python
  df['month'] = df['date'].dt.month
  ```

- **Binning numeric values**  
  ```python
  pd.cut(df['col'], bins=5)
  ```

- **Encoding categorical variables**  
  ```python
  pd.get_dummies(df['cat_col'])
  ```

- **Scaling/normalization**  
  ```python
  from sklearn.preprocessing import StandardScaler
  scaler = StandardScaler()
  df[['scaled_col']] = scaler.fit_transform(df[['col']])
  ```

---

## ✅ 10. Data Quality Checks

- **Check for inconsistent values**  
  ```python
  df['col'].unique()
  df['col'].value_counts()
  ```

- **Logical checks (e.g., total = sum of parts)**  
  ```python
  df['total'] == df[['part1', 'part2']].sum(axis=1)
  ```

- **Check duplicate records**  
  ```python
  df.duplicated().sum()
  ```

---

## ✅ 11. Initial Insights and Hypotheses

- _Document interesting trends and distributions._

- _Form hypotheses based on EDA findings._

- _Check for unexpected gaps or inconsistencies._

---

## ✅ 12. Visualization Summary

- **Pair plots**  
  ```python
  sns.pairplot(df)
  ```

- **Correlation heatmap**  
  ```python
  sns.heatmap(df.corr(), annot=True)
  ```

- **Boxplot for target vs feature**  
  ```python
  sns.boxplot(x='target', y='feature', data=df)
  ```
