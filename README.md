# Python-Social-Media-Engagement-Data-Analysis
The project covers data cleaning, descriptive analysis, exploratory data analysis (EDA), statistical analysis, correlation analysis, outlier detection, and interactive visualizations to understand user engagement, impressions, likes, comments, shares, watch time, sentiment, device usage, and posting patterns.




## 📌 About the Project

This project focuses on analyzing **5,000 social media records** using Python to understand engagement patterns, content performance, user behavior, posting time, device usage, sentiment, and relationships between numerical variables.

The project follows a complete data analysis workflow:

**Data Collection → Data Cleaning → Feature Engineering → EDA → Statistical Analysis → Visualization → Insights**

---

## 🎯 Project Objectives

* Clean and prepare raw social media data
* Handle missing and duplicate values
* Correct data types and inconsistent values
* Perform exploratory data analysis
* Analyze categorical and numerical variables
* Create meaningful features
* Study correlations and relationships
* Detect and handle outliers
* Perform statistical analysis
* Create static and interactive visualizations
* Generate meaningful business-oriented insights

---

## 📂 Dataset

**Dataset:** `social_media_engagement_5000.csv`

**Records:** 5,000

### Main Variables

| Category    | Variables                                           |
| ----------- | --------------------------------------------------- |
| User        | `user_id`, `age`, `gender`, `country`               |
| Content     | `post_id`, `post_type`, `post_category`, `hashtags` |
| Engagement  | `likes`, `comments`, `shares`, `engagement_rate`    |
| Performance | `impression_count`, `watch_time_sec`                |
| Account     | `follower_count`, `is_verified`                     |
| Behavior    | `device_type`, `posted_at`                          |
| Sentiment   | `sentiment`                                         |

---

## 🛠️ Technologies Used

### Programming Language

* Python

### Libraries

* NumPy
* Pandas
* Matplotlib
* Seaborn
* Plotly

### Development Environment

* Jupyter Notebook
* Google Colab

---

## 🔄 Analysis Workflow

```text
Raw Dataset
     ↓
Data Understanding
     ↓
Data Cleaning
     ↓
Data Formatting
     ↓
Feature Engineering
     ↓
Exploratory Data Analysis
     ↓
Data Wrangling
     ↓
Statistical Analysis
     ↓
Correlation Analysis
     ↓
Visualization
     ↓
Insights
     ↓
Conclusion
```

---

## 🧹 1. Data Cleaning

The dataset was prepared for analysis by handling:

* Missing values
* Duplicate records
* Incorrect data types
* Inconsistent categorical values
* Unrealistic values
* Date and time formatting
* Data quality issues

Common Pandas techniques used:

```python
df.isnull().sum()
df.drop_duplicates()
df.fillna()
df.dropna()
pd.to_datetime()
pd.to_numeric()
```

---

## 🔧 2. Feature Engineering

New features were created to support deeper analysis.

### Engagement Score

```python
df["engagement_score"] = (
    df["likes"] +
    df["comments"] +
    df["shares"]
)
```

### Hashtag Count

```python
df["hashtag_count"] = (
    df["hashtags"]
    .fillna("")
    .str.count("#")
)
```

### Log Transformation

```python
df["log_likes"] = np.log1p(df["likes"])
df["log_comments"] = np.log1p(df["comments"])
df["log_shares"] = np.log1p(df["shares"])
df["log_followers"] = np.log1p(df["follower_count"])
```

---

## 🔍 3. Exploratory Data Analysis

The dataset was explored using:

```python
df.head()
df.tail()
df.shape
df.columns
df.info()
df.dtypes
df.describe()
```

Categorical analysis included:

```python
df["post_type"].value_counts()
df["post_type"].unique()
df["post_type"].nunique()
```

GroupBy analysis was used to compare:

* Post types
* Countries
* Sentiments
* Engagement rates
* User behavior

---

## 📐 4. Statistical Analysis

Four major areas of analysis were included:

### 1️⃣ Descriptive Analysis

Used to summarize the dataset.

* Mean
* Median
* Mode
* Percentiles
* Standard deviation
* Variance

### 2️⃣ Exploratory Analysis

Used to identify:

* Patterns
* Trends
* Relationships
* Distributions
* Outliers

### 3️⃣ Statistical Analysis

Used to understand:

* Data spread
* Variation
* Skewness
* Kurtosis
* Numerical behavior

### 4️⃣ Visual & Interactive Analysis

Used to communicate findings through:

* Matplotlib
* Seaborn
* Plotly

---

## 🚨 5. Outlier Analysis

The **IQR method** was used to identify extreme values, particularly for `engagement_rate`.

```python
Q1 = df["engagement_rate"].quantile(0.25)
Q3 = df["engagement_rate"].quantile(0.75)

IQR = Q3 - Q1

lower_limit = Q1 - 1.5 * IQR
upper_limit = Q3 + 1.5 * IQR
```

This helped reduce the influence of extreme values during analysis.

---

## 🔗 6. Correlation Analysis

Correlation analysis was performed on numerical variables to understand relationships between:

* Likes
* Comments
* Shares
* Watch time
* Impressions
* Followers
* Engagement rate

```python
numeric_columns = df.select_dtypes(include=np.number)

correlation_matrix = numeric_columns.corr()
```

A **correlation heatmap** was created using Seaborn.

---

## 📊 7. Data Visualization

### Matplotlib

* Scatter Plot
* Line Chart
* Bar Chart
* Pie Chart
* Histogram
* Box Plot

### Seaborn

* Count Plot
* Bar Plot
* Violin Plot
* Pair Plot
* Heatmap
* Swarm Plot

### Plotly

* Interactive Line Chart
* Interactive Bar Chart
* Interactive Scatter Plot
* Interactive Bubble Chart

---

## 📈 Key Analysis Areas

### 🎯 Content Performance

Analyzed:

* Post type engagement
* Post category performance
* Country-level engagement

### 👥 User Trends

Analyzed:

* Age and engagement
* Verified vs. unverified accounts

### ⏰ Behavioral Patterns

Analyzed:

* Posting hour and impressions
* Device type and watch time

### 😊 Sentiment Analysis

Analyzed:

* Positive sentiment
* Neutral sentiment
* Negative sentiment
* Engagement differences by sentiment

### 🔢 Numerical Relationships

Analyzed relationships between:

* Likes and impressions
* Comments and shares
* Watch time and engagement
* Engagement rate and other numerical variables

---

## 📊 Visualizations

The project includes visualizations such as:

* 📈 Daily Engagement Trend
* 📊 Posts by Category
* 📉 Likes vs. Impressions
* 🥧 Gender Distribution
* 📊 Age Distribution
* 📦 Engagement Rate Distribution
* 🔥 Correlation Heatmap
* 📱 Device Watch Time
* 😊 Sentiment Analysis
* 🔗 Pair Plot
* 🐝 Engagement Rate by Device

---

## 📁 Project Structure

```text
Python-Social-Media-Engagement-Data-Analysis/
│
├── README.md
│
├── dataset/
│   └── social_media_engagement_5000.csv
│
├── notebooks/
│   └── Social_Media_Engagement_Analysis.ipynb
│
├── images/
│   ├── correlation_heatmap.png
│   ├── daily_engagement_trend.png
│   ├── likes_vs_impressions.png
│   ├── post_type.png
│   ├── category_analysis.png
│   ├── gender_distribution.png
│   ├── age_distribution.png
│   ├── engagement_rate.png
│   ├── device_watch_time.png
│   └── sentiment_analysis.png
│
└── documentation/
    └── project_documentation.pdf
```

---

## 🧠 Skills Demonstrated

**Python**

* Data preprocessing
* Data manipulation
* Data analysis

**Pandas**

* Data cleaning
* GroupBy
* Aggregation
* Data wrangling

**NumPy**

* Numerical operations
* Missing-value handling
* Log transformation

**Visualization**

* Matplotlib
* Seaborn
* Plotly

**Statistics**

* Mean
* Median
* Mode
* Standard deviation
* Variance
* Percentiles
* Skewness
* Kurtosis
* Outlier detection

---

## 📚 Key Learning Outcomes

Through this project, I practiced:

* Data cleaning
* Data preprocessing
* Exploratory Data Analysis
* Feature engineering
* Data wrangling
* Statistical analysis
* Correlation analysis
* Outlier detection
* Data visualization
* Interactive visualization
* Data interpretation
* Insight generation

---

## 🚀 Future Improvements

Future versions of this project could include:

* Machine Learning for engagement prediction
* Sentiment classification
* Engagement-rate prediction
* Time-series forecasting
* Power BI dashboard
* Tableau dashboard
* Advanced interactive dashboard
* Predictive analytics
* Automated reporting

---

## 👩‍💻 Author

### M. Kalaivani

**Aspiring Data Analyst**

**Skills:**
Python • NumPy • Pandas • Matplotlib • Seaborn • Plotly • SQL • Data Analysis • Data Visualization

---

## ⭐ Project

If you find this project useful, feel free to explore the notebook and analysis.

**Thank you for visiting my project!** 🚀
