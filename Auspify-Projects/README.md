# 📊 Netflix Data Analysis Using Python


---

## 📌 Project Overview

This repository contains my complete **Netflix Data Analysis project**, completed as part of my **Data Analysis Using Python Internship at Auspify**.

The project consists of **six tasks**, covering the complete data analysis workflow — from **data cleaning and exploratory analysis to visualization, trend analysis, and business insights**.

The main objective of this project was to analyze the Netflix titles dataset using Python and transform raw data into meaningful, data-driven insights.

---

## 🎯 Project Objectives

- Clean and preprocess the Netflix dataset
- Understand the structure and quality of the data
- Analyze Movies and TV Shows
- Analyze Netflix content across different countries
- Identify content trends by release year
- Analyze content ratings and genres
- Create meaningful data visualizations
- Identify important patterns and trends
- Generate actionable business insights
- Prepare a final analytical report

---

# 🗂️ Project Tasks

## 🔹 Task 1 — Netflix Data Cleaning

The first task focused on cleaning and preparing the Netflix dataset for further analysis.

### Work Performed

- Loaded the dataset using Pandas
- Inspected the dataset structure
- Checked column names and data types
- Identified missing values
- Checked duplicate records
- Standardized relevant columns
- Handled formatting inconsistencies
- Prepared the cleaned dataset for analysis

### Data Quality Checks

```python
df.shape
df.info()
df.isnull().sum()
df.duplicated().sum()
```

### Output

The cleaned dataset was saved as:

`netflix_cleaned.csv`

---

## 🔹 Task 2 — Netflix Content Type Analysis

This task focused on understanding the distribution of **Movies and TV Shows** in the Netflix catalog.

### Work Performed

- Counted Movies and TV Shows
- Compared content types
- Calculated the difference between Movies and TV Shows
- Calculated the Movie-to-TV Show ratio
- Created visualizations
- Extracted meaningful insights

### Key Finding

Movies represent a significantly larger portion of the Netflix catalog than TV Shows.

---

## 🔹 Task 3 — Country-Wise Netflix Content Analysis

This task analyzed the distribution of Netflix content across different countries.

Since some titles contain multiple countries in a single record, the `country` column was transformed before analysis.

### Work Performed

- Extracted multiple countries from individual records
- Used `split()` to separate country values
- Used `explode()` to create individual country entries
- Removed unnecessary whitespace
- Counted content associations by country
- Identified the Top 10 countries
- Calculated rankings and percentages
- Created visualizations

### Main Transformation

```python
country_data = (
    df["country"]
    .dropna()
    .str.split(",")
    .explode()
    .str.strip()
)
```

### Top Countries

| Rank | Country | Content Count |
|---:|---|---:|
| 1 | United States | 3,240 |
| 2 | India | 1,057 |
| 3 | United Kingdom | 638 |
| 4 | Pakistan | 421 |
| 5 | Canada | 271 |
| 6 | Japan | 259 |
| 7 | South Korea | 214 |
| 8 | France | 213 |
| 9 | Spain | 182 |

### Key Findings

- The **United States** had the highest number of content-country associations.
- **India** ranked second.
- Netflix has a strong international presence across multiple countries.

> **Note:** A single title can be associated with multiple countries. Therefore, these values represent **country-content associations**, not necessarily unique titles produced exclusively by each country.

---

## 🔹 Task 4 — Netflix Trend Analysis by Release Year

This task focused on analyzing how Netflix content has changed across different release years.

### Work Performed

- Analyzed the `release_year` column
- Counted titles by release year
- Sorted yearly content counts
- Identified years with high content volume
- Compared content counts across years
- Calculated yearly changes
- Created trend visualizations
- Identified important patterns

### Main Analysis

```python
yearly_content = (
    df["release_year"]
    .value_counts()
    .sort_index()
)
```

### Key Insight

The release-year analysis provides an understanding of how the Netflix content catalog has evolved over time and highlights periods of higher and lower content volume.

---

## 🔹 Task 5 — Netflix Content Rating & Genre Analysis

This task focused on analyzing Netflix content ratings and genre/category distribution.

### Content Rating Analysis

#### Work Performed

- Counted different content ratings
- Identified the most common ratings
- Analyzed rating distribution
- Created visualizations

### Top Content Ratings

| Rating | Count |
|---|---:|
| TV-MA | 3,205 |
| TV-14 | 2,157 |
| TV-PG | 861 |
| R | 799 |
| PG-13 | 490 |
| TV-Y7 | 333 |
| TV-Y | 306 |
| PG | 287 |
| TV-G | 220 |
| NR | 79 |

### Key Finding

**TV-MA** was the most common content rating, followed by **TV-14** and **TV-PG**.

### Genre Analysis

The `listed_in` column contains multiple genres/categories for some titles, so it was transformed before analysis.

```python
genre_data = (
    df["listed_in"]
    .dropna()
    .str.split(",")
    .explode()
    .str.strip()
)

genre_counts = genre_data.value_counts()
```

### Top Genres / Categories

| Rank | Genre / Category | Count |
|---:|---|---:|
| 1 | International Movies | 2,752 |
| 2 | Dramas | 2,426 |
| 3 | Comedies | 1,674 |
| 4 | International TV Shows | 1,349 |
| 5 | Documentaries | 869 |
| 6 | Action & Adventure | 859 |
| 7 | TV Dramas | 762 |
| 8 | Independent Movies | 756 |
| 9 | Children & Family Movies | 641 |
| 10 | Romantic Movies | 616 |

### Key Finding

International Movies, Dramas, and Comedies were among the most frequently occurring categories in the dataset.

> **Note:** Genre counts represent **genre-content associations**, because a single title can belong to multiple genres.

---

# 🔹 Task 6 — Netflix Business Insights Report

Task 6 was the final and advanced stage of the project.

The objective was to combine the analysis from previous tasks and convert the findings into **business-oriented insights and recommendations**.

---

## Exploratory Data Analysis

The cleaned dataset was explored to understand its overall structure and characteristics.

### EDA Summary

| Metric | Result |
|---|---:|
| Total Records | 8,790 |
| Total Columns | 10 |
| Unique Titles | 8,787 |
| Unique Release Years | 74 |
| Movies | 6,126 |
| TV Shows | 2,664 |

### EDA Included

- Dataset structure
- Data types
- Missing values
- Duplicate records
- Statistical information
- Unique values
- Content type distribution

---

## Key Content Trends & Patterns

The following areas were analyzed:

- Movies vs TV Shows
- Release-year trends
- Content ratings
- Genre distribution
- International content

### Major Findings

- Movies form the majority of the Netflix catalog.
- TV-MA is the most common content rating.
- TV-14 is another major rating category.
- International Movies have the highest genre-content associations.
- Dramas and Comedies are among the leading categories.
- International TV Shows also have a significant presence.
- Release-year analysis highlights changes in content volume over time.

---

## 📈 Visualizations

Multiple visualizations were created throughout the project to communicate the findings clearly.

### Main Visualizations

- Movies vs TV Shows
- Netflix Content Trend by Release Year
- Content Rating Distribution
- Top 10 Netflix Genres
- Country-Wise Content Distribution
- Supporting analysis charts

### Visualization Library

**Matplotlib** was primarily used for creating the visualizations.

---

# 💼 Business Insights

The analytical findings were converted into business-oriented insights.

### 1. Content Strategy

Movies represent a significantly larger portion of the catalog.

**Recommendation:**  
Maintain a strong movie portfolio while selectively expanding TV Show content based on audience demand and performance.

### 2. Audience Targeting

TV-MA and TV-14 are among the most common content ratings.

**Recommendation:**  
Continue serving mature and teenage audiences while maintaining a balanced selection of family-friendly content.

### 3. Genre Strategy

International Movies, Dramas, and Comedies are among the leading categories.

**Recommendation:**  
Continue investing in successful genres while monitoring emerging categories for new content opportunities.

### 4. International Content

International Movies and International TV Shows have a strong presence in the dataset.

**Recommendation:**  
Continue expanding localized and regional content to strengthen Netflix's global reach.

### 5. Content Production Trends

Release-year analysis shows how content volume changes across different periods.

**Recommendation:**  
Use historical trends and audience data to support future content production, acquisition, and investment decisions.

---

# 💡 Business Recommendations

Based on the overall analysis, the following recommendations can be considered:

1. Maintain a strong movie portfolio while selectively expanding TV Shows.
2. Continue investing in mature and teenage-oriented content while maintaining family-friendly options.
3. Expand localized and international content based on regional audience demand.
4. Monitor genre trends to identify emerging content opportunities.
5. Use historical release trends to improve future content planning.
6. Combine content analysis with regional and audience-level data for better decision-making.
7. Incorporate additional metrics such as views, watch time, ratings, and revenue for deeper business analysis.

---

# 🔄 Complete Project Workflow

```text
                    Netflix Dataset
                          │
                          ▼
                Data Cleaning & Preparation
                          │
                          ▼
                Exploratory Data Analysis
                          │
             ┌────────────┼────────────┐
             ▼            ▼            ▼
       Content Type    Country      Release Year
         Analysis      Analysis       Analysis
             │            │            │
             └────────────┼────────────┘
                          ▼
                 Rating & Genre Analysis
                          │
                          ▼
                   Data Visualization
                          │
                          ▼
                  Business Insights
                          │
                          ▼
                    Recommendations
                          │
                          ▼
                 Final Analytical Report
```

---

# 🛠️ Tools & Technologies

| Tool / Technology | Purpose |
|---|---|
| **Python** | Data analysis and programming |
| **Pandas** | Data cleaning, transformation, and analysis |
| **NumPy** | Numerical operations |
| **Matplotlib** | Data visualization |
| **Jupyter Notebook** | Interactive analysis and documentation |
| **CSV** | Dataset storage |
| **GitHub** | Version control and project sharing |

---

# 📊 Dataset Information

The Netflix dataset contains information about Netflix titles, including:

- `show_id`
- `type`
- `title`
- `director`
- `cast`
- `country`
- `date_added`
- `release_year`
- `rating`
- `duration`
- `listed_in`
- `description`

The original dataset was cleaned and prepared before performing the analysis.

The cleaned dataset used in the later tasks is:

`netflix_cleaned.csv`

---

# 📁 Repository Structure

```text
Auspify-Projects/
│
├── README.md
│
├── Dataset.csv.xlsx
├── netflix_cleaned.csv
│
├── Netflix_Data_Cleaning_Task-1.ipynb
├── Netflix_Content_Type_Analysis_Task-2.ipynb
├── Netflix_Country_Wise_Content_Analysis_Task3.ipynb
├── Netflix_Trend_Analysis_by_Release_Year_Task4.ipynb
├── Netflix_Content_Rating_Genre_Analysis_Task5.ipynb
└── Netflix_Business_Insights_Report_Task6.ipynb
```


# 📚 Key Python Concepts Used

Throughout the project, I worked with several important Python and Pandas concepts.

### Data Loading

```python
pd.read_csv()
pd.read_excel()
```

### Data Inspection

```python
df.head()
df.shape
df.info()
df.describe()
```

### Data Quality

```python
df.isnull().sum()
df.duplicated().sum()
```

### Data Transformation

```python
.str.split()
.explode()
.str.strip()
```

### Aggregation

```python
.value_counts()
.groupby()
.sum()
.mean()
```

### Sorting and Filtering

```python
.sort_values()
.sort_index()
.head()
```

### Visualization

```python
plt.figure()
plt.bar()
plt.barh()
plt.plot()
plt.title()
plt.xlabel()
plt.ylabel()
plt.show()
```

---

# 💡 Key Learning Outcomes

This project helped me strengthen my practical understanding of:

- Data cleaning and preprocessing
- Exploratory Data Analysis
- Pandas DataFrame operations
- Missing-value handling
- Duplicate detection
- Data transformation
- String manipulation
- `split()` and `explode()`
- Grouping and aggregation
- Categorical data analysis
- Time-based trend analysis
- Data visualization
- Business insight generation
- Data-driven decision making
- Communicating analytical findings

---

# 🚀 Future Scope

This project can be extended further using additional data and advanced analytical techniques.

Possible future improvements include:

- Regional audience analysis
- Content recommendation systems
- User segmentation
- Predictive analysis
- Genre popularity forecasting
- Machine learning models
- Sentiment analysis
- Interactive dashboards using Power BI or Tableau
- Analysis of views and watch time
- Analysis of user ratings
- Revenue and business performance analysis

---

# 🏁 Conclusion

This six-task Netflix Data Analysis project provided hands-on experience with the complete **data analysis lifecycle**.

Starting with raw data, I progressed through:

**Data Cleaning → Exploratory Analysis → Content Analysis → Trend Analysis → Visualization → Business Insights**

The project helped me develop both my **technical data analysis skills** and my ability to communicate findings from data in a business-oriented manner.

It was a valuable practical learning experience that improved my confidence in using **Python, Pandas, Matplotlib, and Jupyter Notebook** for real-world data analysis.

---

# 👩‍💻 Internship

### Data Analysis Using Python Internship

**Organization:** Auspify

**Project:** Netflix Data Analysis

**Tasks Completed:** 1–6

---

## ⭐ Acknowledgement

This project was completed as part of my **Data Analysis Using Python Internship at Auspify**.

I’m grateful for the opportunity to work on a practical data analysis project and strengthen my skills through hands-on learning.

---

⭐ **If you find this project useful, feel free to explore the notebooks and analysis.**
