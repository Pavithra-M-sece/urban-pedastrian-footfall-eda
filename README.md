# Evaluating Urban Pedestrian Footfall Dynamics Using Exploratory Data Analysis and Seaborn Visualizations

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-150458?logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0)
![SciPy](https://img.shields.io/badge/SciPy-Statistical_Analysis-8CAAE6?logo=scipy)
![Google Colab](https://img.shields.io/badge/Google_Colab-Notebook-F9AB00?logo=googlecolab)
![Domain](https://img.shields.io/badge/Domain-Smart_Cities_%26_Mobility-2E8B57)


## 📌 Project Overview

Urban pedestrian counting systems collect hourly pedestrian movement data from sensors installed at railway stations, commercial streets, university entrances, parks, and other public locations.

However, raw sensor data can contain missing values, duplicate records, sensor outages, abnormal spikes, and highly skewed distributions. Analysing such data without proper preprocessing may lead to misleading conclusions about pedestrian movement.

This project evaluates urban pedestrian footfall dynamics through **data cleaning, feature engineering, Exploratory Data Analysis (EDA), statistical validation, anomaly detection, and Seaborn visualizations**.

The analysis investigates temporal, spatial, weather-related, event-related, and behavioural patterns in pedestrian activity to generate insights that can support smart-city planning, public transportation management, crowd control, and infrastructure development.

> **Important:** This project uses a reproducible synthetic dataset designed to resemble the structure of open pedestrian-counting data. The findings demonstrate the analysis workflow and the assumptions used to generate the data; they are not verified measurements of an actual city.

## 🎯 Objectives

- Load and inspect hourly pedestrian count data from multiple sensor locations.
- Identify and handle duplicate records, sensor outages, missing values, and extreme spikes.
- Perform feature engineering on timestamps to derive hourly, daily, weekly, monthly, and seasonal attributes.
- Analyse pedestrian count distributions and compare activity across locations.
- Identify weekday, weekend, and time-of-day footfall patterns.
- Investigate associations between pedestrian activity, rainfall, temperature, public holidays, and events.
- Apply correlation analysis and the Mann–Whitney U test to validate selected patterns.
- Detect anomalous location-days using z-score analysis.
- Develop informative visualizations using Seaborn and Matplotlib.
- Translate analytical findings into actionable recommendations for urban planners.

## 🗂️ Dataset Description

The notebook generates a synthetic hourly pedestrian-count dataset using a fixed random seed for reproducibility.

Its schema follows the general structure of datasets such as the City of Melbourne Pedestrian Counting System.

| Attribute | Description |
|---|---|
| Locations | 5 sensor locations |
| Start date | 01 January 2023 |
| End date | 31 December 2024 |
| Time coverage | Hourly |
| Days | 731 |
| Raw records | 87,760 |
| Clean records | 87,650 |
| Data type | Synthetic time-series data |

### Sensor Locations

1. **Railway Station** – Represents public transportation-related pedestrian movement.
2. **Central Market Street** – Represents commercial and retail pedestrian activity.
3. **University Gate** – Represents student and campus-related movement.
4. **Riverside Promenade** – Represents recreational and leisure activity.
5. **Tech Park Junction** – Represents office and technology-sector commuting.

### Dataset Features

| Column | Description |
|---|---|
| `Date_Time` | Timestamp of the hourly observation |
| `Sensor_Name` | Name of the pedestrian counting location |
| `Hourly_Counts` | Number of pedestrians recorded during the hour |
| `Temperature_C` | Temperature in degrees Celsius |
| `Rain` | Rain indicator |
| `Event` | Indicator for event-related activity |
| `Public_Holiday` | Indicator for public holidays |

### Using Real-World Data

The analysis can be adapted to a real pedestrian-counting dataset, such as the City of Melbourne Pedestrian Counting System.

To use a real dataset:

1. Set `USE_SYNTHETIC = False` in the notebook, if supported by the implemented code.
2. Upload the real CSV file to Google Colab.
3. Map its timestamp, location, and pedestrian count columns to the notebook's expected schema.
4. Review the data-cleaning rules and feature-engineering logic.
5. Rerun the analysis and interpret the results using the real observations.

The real-data workflow depends on the input format and the data-loading logic implemented in the notebook.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python 3 | Core programming language |
| Pandas | Data manipulation, cleaning, aggregation, and analysis |
| NumPy | Numerical operations and feature calculations |
| Seaborn | Statistical data visualization |
| Matplotlib | Chart generation and customization |
| SciPy | Statistical tests, skewness, and kurtosis |
| Google Colab | Cloud-based notebook execution |
| Jupyter Notebook | Interactive development and analysis |

## 🔄 Project Workflow

The project follows a structured data-analysis pipeline.

```text
Raw Hourly Pedestrian Data
            |
            v
      Data Loading
            |
            v
     Data Inspection
            |
            v
      Data Cleaning
  - Duplicate removal
  - Outage identification
  - Missing-value handling
  - Extreme-spike treatment
            |
            v
    Feature Engineering
  - Hour and weekday
  - Month and season
  - Day type
  - Part of day
            |
            v
 Exploratory Data Analysis
  - Spatial analysis
  - Temporal analysis
  - Weather and event analysis
            |
            v
  Statistical Validation
  - Correlation analysis
  - Mann–Whitney U test
            |
            v
    Anomaly Detection
            |
            v
 Visualizations and Findings
            |
            v
 Urban Planning Recommendations
```

## 🧹 Data Cleaning and Preprocessing

The raw dataset is processed to improve data quality before performing exploratory analysis.

| Step | Operation | Records or values affected |
|---|---|---:|
| 1 | Remove duplicate records | 40 records removed |
| 2 | Flag sensor outages | 73 hours flagged |
| 3 | Interpolate short gaps of at most 3 hours | 1,052 values filled |
| 4 | Drop rows that remain missing | 70 records removed |
| 5 | Winsorize extreme spikes using median + 8 × scaled MAD | 88 values capped |

**Scaled MAD** refers to the median absolute deviation adjusted using a scaling factor to estimate variability robustly.

These preprocessing operations are designed to reduce the effect of data-quality problems while retaining useful pedestrian movement patterns.

The reported counts describe the project's current synthetic-data workflow and should be verified against the final notebook outputs.

## ⚙️ Feature Engineering

Time-related features are extracted from the timestamp to support detailed temporal analysis.

| Feature | Purpose |
|---|---|
| Hour | Identify peak pedestrian hours |
| Weekday | Compare activity across days of the week |
| Month | Study monthly changes |
| Season | Examine seasonal patterns |
| Day Type | Classify weekdays and weekends |
| Part of Day | Compare morning, afternoon, evening, and night activity |

Additional derived features may be used to calculate daily totals, location-wise averages, rolling averages, normalized hourly profiles, and location-day anomaly scores.

## 📊 Exploratory Data Analysis

### 1. Distribution Analysis

Examines the distribution of hourly pedestrian counts using histograms, density plots, box plots, and descriptive statistics.

The analysis helps identify:

- Skewness and variability.
- Extreme observations.
- Differences between typical and unusually busy periods.
- The suitability of robust statistical measures.

### 2. Spatial Analysis

Compares pedestrian movement across the five sensor locations using aggregated counts and statistical visualizations.

This analysis identifies locations associated with commuting, commercial activity, campus traffic, and recreational movement.

### 3. Temporal Analysis

Investigates pedestrian movement at different time scales:

- Hourly footfall patterns.
- Weekday and weekend differences.
- Day-of-week patterns.
- Monthly and seasonal changes.
- Morning, afternoon, evening, and night activity.

### 4. Weather and Event Analysis

Examines how pedestrian counts vary with rainfall, temperature, events, and public holidays.

These analyses identify associations between contextual variables and footfall changes. They do not independently establish causal relationships.

### 5. Statistical Validation

The project uses statistical methods to evaluate selected patterns.

**Mann–Whitney U test:** Compares two independent groups, such as weekday and weekend pedestrian counts, without requiring normally distributed observations.

**Correlation analysis:** Examines the strength and direction of associations between numerical variables.

**Skewness and kurtosis:** Describe the shape and tail behaviour of pedestrian count distributions.

### 6. Anomaly Detection

Uses z-scores to identify unusual location-day observations.

An observation with an absolute z-score greater than 3 is flagged as potentially anomalous:

\[
|z| > 3
\]

Anomalies are reviewed as unusually high or low observations relative to the selected baseline. They may reflect real events, unusual pedestrian activity, or remaining data-quality issues.

## 📈 Visualizations

The project is designed to generate the following visualizations using Seaborn and Matplotlib.

| Visualization | Purpose |
|---|---|
| Histograms | Understand pedestrian count distributions |
| Bar plots | Compare average or total footfall by location |
| Box plots | Examine variability and extreme observations |
| Violin plots | Compare distributions across groups |
| Hourly line plots | Identify daily movement patterns |
| Confidence-interval plots | Assess uncertainty around group estimates |
| Weekday × hour heatmaps | Identify recurring time-based patterns |
| Location × hour heatmaps | Compare normalized activity profiles |
| Correlation matrices | Explore relationships between numerical variables |
| Scatter plots with regression curves | Investigate associations between variables |
| Rolling-average plots | Examine smoothed trends |
| Z-score anomaly plots | Highlight unusual location-day observations |
| Executive dashboard | Present key indicators and findings |

### Sample Chart Gallery

After running the notebook and exporting the figures, save the actual chart images inside the `figures/` directory and update the filenames below to match the exported files.

#### Weekday vs. Hour Heatmap

![Weekday vs. Hour Heatmap](figures/weekday_hour_heatmap.png)

#### Pedestrian Footfall by Location

![Pedestrian Footfall by Location](figures/location_comparison.png)

#### Hourly Footfall Trends

![Hourly Footfall Trends](figures/hourly_footfall_trends.png)

#### Weather Impact Analysis

![Weather Impact Analysis](figures/weather_impact.png)

#### Anomaly Detection

![Anomaly Detection](figures/anomaly_detection.png)

#### Executive Dashboard

![Executive Dashboard](figures/executive_dashboard.png)

> If these image files have not been exported yet, the images will not display until you add the corresponding files to your repository.

## 🔍 Key Findings

The following findings are reported by the current synthetic-data analysis. They should be interpreted in the context of the dataset's generation assumptions.

### 1. Pedestrian Count Distribution

- The distribution is strongly right-skewed, with a reported skewness of **2.22**.
- Median-based summaries and rank-based statistical tests are useful for understanding distributions that are not symmetric.

### 2. Location-Wise Footfall

- Railway Station accounts for a reported **36.0%** of total footfall.
- Riverside Promenade accounts for a reported **10.1%** of total footfall.
- The five locations exhibit different movement patterns because they represent different types of urban activity.

### 3. Peak Hours

- The reported city-wide weekday peak occurs at **18:00 (6 PM)**.
- The reported weekend peak occurs at **13:00 (1 PM)**.

These patterns illustrate how commuting and leisure activity can produce different peak periods.

### 4. Weekend vs. Weekday Changes

| Location | Reported Weekend Change |
|---|---:|
| Tech Park Junction | -79% |
| University Gate | -75% |
| Railway Station | -35% |
| Central Market Street | +10% |
| Riverside Promenade | +172% |

The analysis reports statistical significance at **p < 0.001** for these comparisons.

The percentage changes depend on the comparison baseline and aggregation method used in the notebook.

### 5. Rainfall Impact

The reported daily footfall reductions associated with rain range from approximately **14% at Railway Station to 62% at Riverside Promenade**.

This illustrates how different location types can exhibit different weather sensitivities in the synthetic dataset.

### 6. Event-Related Activity

The reported event-associated footfall increases reach approximately **66%** at some leisure and retail locations, with relatively little change at the university and technology park locations.

### 7. Anomaly Detection

- Five anomalous location-days were reported using an absolute z-score threshold greater than 3.
- These observations were unusually busy days at Central Market Street and Riverside Promenade.

### 8. Robustness Checks

The project reports that selected patterns remain stable when alternative spike thresholds, anomaly thresholds, and rainfall-effect definitions are applied.

The final notebook should contain the relevant comparisons to substantiate these robustness claims.

## 🏙️ Recommendations for Urban Planners

| Analytical Insight | Recommended Action |
|---|---|
| Transit and office locations exhibit weekday commuter peaks | Improve public transport coordination and deploy crowd-management staff during peak periods |
| Retail areas experience afternoon and weekend activity | Schedule cleaning, waste collection, and security around busy periods |
| Recreational areas experience stronger weekend activity | Provide suitable pedestrian facilities, shelters, and accessible pathways |
| Rainfall effects differ by location | Prioritize weather protection where observed reductions are greatest |
| Events can produce large pedestrian surges | Coordinate event calendars with transport operators and crowd-management teams |
| Sensor data contain outages and spikes | Implement automated data-quality checks before information reaches planning dashboards |

These recommendations are intended as planning hypotheses to validate with real-world pedestrian counts and local operational data.

## 📁 Repository Structure

```text
urban-pedastrian-footfall-eda/
│
├── README.md
│
├── Pedestrian_Footfall_EDA.ipynb
│
├── Pedestrian_Footfall_DS_Project_Report.docx
│
├── pedestrian_footfall_clean.csv
│
├── location_summary.csv
│
└── figures/
    ├── weekday_hour_heatmap.png
    ├── location_comparison.png
    ├── hourly_footfall_trends.png
    ├── weather_impact.png
    ├── anomaly_detection.png
    └── executive_dashboard.png
```

The notebook, report, CSV files, and chart images should be added to the repository as they become available. Keep the figure filenames consistent with the README image links.

## 🚀 How to Run the Project

### Option 1: Google Colab

The recommended method is to run the notebook in Google Colab.

**[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Pavithra-M-sece/urban-pedastrian-footfall-eda/blob/main/Pedestrian_Footfall_EDA.ipynb)**

Steps:

1. Open the notebook using the Colab badge above.
2. Select **Runtime → Run all**.
3. Wait for data generation, preprocessing, statistical analysis, and visualizations to finish.
4. Review the generated charts and analytical results.
5. Download the exported CSV files and chart images if required.
6. Upload the resulting files to the GitHub repository.

The notebook must be uploaded to GitHub with the exact filename used in the Colab link for this badge to work.

### Option 2: Run Locally

**Prerequisites**

- Python 3
- Jupyter Notebook
- Required Python libraries

Install the dependencies:

```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
```

Clone the repository:

```bash
git clone https://github.com/Pavithra-M-sece/urban-pedastrian-footfall-eda.git
```

Navigate to the project directory:

```bash
cd urban-pedastrian-footfall-eda
```

Launch Jupyter Notebook:

```bash
jupyter notebook Pedestrian_Footfall_EDA.ipynb
```

Run the notebook cells sequentially or select **Run All**.

### Expected Outputs

After a successful run, the notebook is intended to produce:

- A cleaned pedestrian footfall dataset.
- Location-wise summary statistics.
- Statistical test results and correlation analysis.
- Pedestrian footfall visualizations.
- Anomaly detection results.
- Findings and planning recommendations.

The actual output filenames and export locations depend on the notebook implementation.

## ⚠️ Limitations

1. **Synthetic dataset:** Results reflect the assumptions used to generate the data rather than measurements from a real city.
2. **Observational analysis:** Associations do not establish causal relationships.
3. **Limited location coverage:** Only five representative locations are included.
4. **Count-based data:** The analysis does not directly measure pedestrian dwell time, individual movement, or origin-destination flows.
5. **Rainfall representation:** A daily rain indicator does not capture hourly rainfall intensity or duration.
6. **Sensor quality:** Interpolation and spike treatment can alter observations and require careful validation.
7. **Generalizability:** Findings should not be directly applied to another city without validating them against local data.

## 🔮 Future Enhancements

- Apply the pipeline to real open pedestrian-counting datasets.
- Add hourly rainfall, temperature, transit timetables, and event calendars.
- Develop pedestrian footfall forecasting models using gradient boosting, Prophet, or LSTM networks.
- Cluster locations using normalized hourly activity profiles.
- Build an interactive Streamlit dashboard with configurable filters.
- Implement automated sensor-outage monitoring and abnormal-crowding alerts.
- Compare multiple cities and evaluate whether the observed patterns generalize.
- Add model evaluation, uncertainty estimates, and automated reporting where forecasting is implemented.

## 🎓 Learning Outcomes

This project demonstrates practical application of:

- Data loading, inspection, and preprocessing.
- Missing-value treatment and outlier handling.
- Time-based feature engineering.
- Exploratory Data Analysis using Pandas and Seaborn.
- Statistical testing using SciPy.
- Correlation analysis and anomaly detection.
- Data storytelling and evidence-based recommendations.
- Reproducible notebook-based analytics.

## 👩‍💻 Author

**PAVITHRA M**

B.E. Computer Science and Engineering  
Sri Eshwar College of Engineering, Coimbatore  
Batch: 2024–2028

**GitHub Repository:**  
https://github.com/Pavithra-M-sece/urban-pedastrian-footfall-eda

---

## 📜 Academic Use

This project was developed for academic learning in data analytics and exploratory data analysis, with a focus on smart cities and pedestrian mobility.

**Note:** All reported results should be checked against the final notebook outputs before academic submission or use in a real-world planning context.
