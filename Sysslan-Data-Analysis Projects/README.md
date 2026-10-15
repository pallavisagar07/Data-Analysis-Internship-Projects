# Train Schedule Analysis

## Project Overview

The Train Schedule Analysis project focuses on exploring, validating, analyzing, and visualizing railway schedule data using Python. The project is divided into four levels, progressing from basic data exploration to data validation and visualization.

The objective is to understand train routes, station frequency, route distances, and journey-duration patterns while developing practical data analysis skills.

## Objectives

- Explore the structure and characteristics of the train schedule dataset.
- Analyze train-wise station records and route distances.
- Calculate journey-duration estimates for trains.
- Identify railway stations with high train frequency.
- Validate data quality by checking missing values, duplicates, and distance progression.
- Create visualizations to communicate important findings.
- Summarize the results in a structured project report.

## Tools and Technologies

- **Python** — programming and analysis
- **Pandas** — data manipulation, grouping, and aggregation
- **NumPy** — numerical operations
- **Matplotlib** — data visualization
- **Seaborn** — statistical visualizations
- **Jupyter Notebook** — interactive development environment

## Dataset Description

The project uses a train schedule dataset containing station-level information for trains.

- **Total records:** 186,074
- **Total columns:** 12
- **Unique trains:** 11,113
- **Unique station names:** Approximately 8,099

### Dataset Columns

| Column | Description |
|---|---|
| `SN` | Station sequence or record number |
| `Train_No` | Train identification number |
| `Station_Code` | Railway station code |
| `1A` | First AC-related field |
| `2A` | Second AC-related field |
| `3A` | Third AC-related field |
| `SL` | Sleeper-related field |
| `Station_Name` | Name of the railway station |
| `Route_Number` | Route number recorded in the dataset |
| `Arrival_time` | Scheduled arrival time |
| `Departure_Time` | Scheduled departure time |
| `Distance` | Recorded distance along the train route |

## Project Structure

```text
Sysslan-Data-Analysis Projects/
│
├── README.md
│
├── Train_Schedule_Analysis_Data_Review_Level_1.ipynb
│
├── Train_Schedule_Analysis_Data_Processing_Level2.ipynb
│
├── Train_Schedule_Analysis_Level3.ipynb
├──  train_schedule_verified.csv
│
└── Train_Schedule_Analysis_Level4.ipynb
```

## Level 1: Data Exploration

### Tasks Performed

- Loaded and inspected the dataset.
- Examined dataset dimensions, columns, and data types.
- Identified the number of unique trains and station names.
- Analyzed the number of station records associated with each train.
- Identified trains with high and low station-record counts.
- Explored starting stations, ending stations, and train route information.

### Key Findings

- The dataset contains 186,074 records and 12 columns.
- There are 11,113 unique trains.
- Train 53041 has 118 station records, the highest count observed in the analysis.
- A minimum of two station records was observed for some trains.

### Outcome

This level established an understanding of the dataset's structure and provided a foundation for further analysis.

## Level 2: Basic Data Analysis

### Tasks Performed

- Examined arrival and departure time fields.
- Converted time fields for duration calculations.
- Calculated initial journey-duration estimates for individual trains.
- Calculated maximum recorded route distance for each train.
- Classified trains into Short, Medium, and Long route categories.
- Calculated station-wise unique train frequency.

### Route Classification

The following distance thresholds were used:

| Category | Route Distance |
|---|---|
| Short | Up to 38 km |
| Medium | Above 38 km and up to 324 km |
| Long | Above 324 km |

These thresholds were derived from the dataset's distance distribution and are specific to this analysis.

### Key Findings

- CST-MUMBAI had the highest station train frequency, with 1,027 unique trains.
- KALYAN JN had 828 unique trains.
- THANE had 796 unique trains.
- The route-distance distribution had a median of 82 km and a maximum recorded distance of 4,260 km.

### Outcome

This level provided an initial understanding of journey durations, route distances, route categories, and station-wise train frequency.

## Level 3: Data Validation and Export

### Tasks Performed

- Checked for missing values in all columns.
- Checked relevant text fields for empty and whitespace-only values.
- Identified exact duplicate rows.
- Investigated repeated train and station-code combinations.
- Checked whether route distances decreased in the recorded station sequence.
- Exported the verified dataset for subsequent analysis.

### Data Validation Results

| Validation Check | Result |
|---|---:|
| Missing values | 0 |
| Exact duplicate rows | 0 |
| Repeated train and station-code combinations investigated | 30 |
| Distance decreases found in the checked sequence | 0 |

Repeated train and station-code combinations were investigated rather than automatically removed because a train may revisit the same station.

### Exported Dataset

The resulting dataset was exported as:

`train_schedule_verified.csv`

### Outcome

This level emphasized the importance of validating data before relying on analytical results. The exported dataset was prepared for use in Level 4.

## Level 4: Basic Analysis and Visualization

### Task 4.1: Compare Average Journey Durations Across Route Types

- Calculated journey-duration estimates for individual trains.
- Combined journey durations with route-distance categories.
- Calculated average journey duration for Short, Medium, and Long routes.
- Created a bar chart to compare the average durations.

**Key finding:** The Long route category had the highest calculated average journey duration, at 11.86 hours.

### Task 4.2: Identify High-Traffic Stations

- Counted unique trains associated with each station.
- Sorted stations by train frequency.
- Identified and visualized the top 10 stations.

**Top stations identified:**

| Station | Unique Train Frequency |
|---|---:|
| CST-MUMBAI | 1,027 |
| KALYAN JN | 828 |
| THANE | 796 |
| SEALDAH | 745 |
| CHENNAI BEAC | 738 |
| HOWRAH JN. | 699 |
| DADAR | 598 |
| DUM DUM JN. | 463 |
| KURLA | 462 |
| TAMBARAM | 434 |

### Task 4.3: Create Basic Visualizations

Created visualizations to explore:

- Average journey duration across route categories.
- Top 10 stations by train frequency.
- Distribution of trains by route category.
- Distribution of train route distances.

### Route Category Distribution

| Route Category | Number of Trains |
|---|---:|
| Short | 2,834 |
| Medium | 5,502 |
| Long | 2,777 |
| **Total** | **11,113** |

**Key observation:** Medium routes represent the largest category, with 5,502 trains.

### Task 4.4: Summarize Key Observations

The analysis brought together findings about journey duration, station frequency, route categories, and route-distance distribution.

### Outcome

This level demonstrated how visualizations can make data comparisons easier and help communicate findings from a large dataset.

## Important Limitations

- The `Route_Number` column contains only the value `1` in this dataset, so it cannot support comparisons between multiple route numbers.
- Arrival and departure fields contain clock times without explicit journey dates.
- Some `00:00:00` values may be endpoint markers rather than actual midnight times.
- The initial journey-duration calculation assumes at most one midnight crossing and should be validated before being interpreted as definitive travel time.
- The distance progression check does not independently establish that every recorded geographical route is correct.
- Station train frequency counts unique train numbers associated with a station; they do not measure passenger numbers or daily passenger traffic.

## How to Run the Project

1. Download or clone the project repository.
2. Install Python and the required libraries if they are not already installed.
3. Open the project in Jupyter Notebook or JupyterLab.
4. Run the notebooks in order, starting with Level 1 and continuing through Level 4.
5. Ensure `train_schedule_verified.csv` is available in the Level-3 folder.
6. Adjust relative file paths if your local folder structure differs.

### Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

## Conclusion

The Train Schedule Analysis project provided practical experience in data exploration, aggregation, validation, and visualization using Python.

Across four levels, the project explored train and station records, analyzed route distances and journey-duration estimates, investigated data quality, identified high-frequency stations, and created visualizations to communicate findings.

The project also demonstrated an important lesson in data analysis: results must be interpreted carefully, and successful code execution alone does not guarantee that every result accurately represents real-world conditions.

---

**Project:** Train Schedule Analysis  
**Focus:** Data Exploration, Data Validation, Analysis, and Visualization  
**Tools:** Python, Pandas, NumPy, Matplotlib, Seaborn, and Jupyter Notebook
