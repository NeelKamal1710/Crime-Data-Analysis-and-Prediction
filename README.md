# 🔍 Los Angeles Crime Data Analysis & Forecasting

![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![Pandas](https://img.shields.io/badge/Pandas-EDA-green) ![ARIMA](https://img.shields.io/badge/ARIMA-Forecasting-orange) ![Prophet](https://img.shields.io/badge/Prophet-Forecasting-red) ![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

A full-cycle data analytics project covering **data cleaning**, **exploratory data analysis (EDA)**, and **time series forecasting** on 800K+ real-world crime records from the Los Angeles Police Department (LAPD).

---

## 📌 Project Overview

This project analyzes the [LAPD Crime Data (2020–Present)](https://data.lacity.org/Public-Safety/Crime-Data-from-2020-to-Present/2nrs-mtv8) to uncover temporal patterns, regional disparities, demographic trends, and to forecast future crime rates using statistical time series models.

**Business relevance:** The analytical pipeline mirrors real-world operational analytics — cleaning raw transactional data, building KPI-level insights, and developing forecasting models that can support resource planning and public safety decision-making.

---

## 📂 Repository Structure

```
Crime-Data-Analysis-and-Prediction/
│
├── IE6400_Project_1.ipynb      # Main analysis notebook (EDA + Forecasting)
└── README.md                   # Project documentation
```

---

## 📊 Dataset

| Attribute | Details |
|-----------|---------|
| **Source** | Los Angeles Open Data Portal (data.lacity.org) |
| **Size** | 811,663 rows × 28 columns |
| **Period** | January 2020 – 2023 |
| **Key Fields** | Date Reported, Date Occurred, Time, Area Name, Crime Type, Victim Age/Sex/Descent, Premise, Weapon, Location (Lat/Lon) |

---

## 🔧 Part 1 — Data Cleaning

Raw LAPD data required significant preprocessing before analysis:

- **Missing Value Treatment:** Identified 12 columns with null values via `df.isnull().sum()`. Imputed object-type columns with mode; integer-type columns with mean.
- **Duplicate Removal:** Detected and removed duplicate rows to prevent analytical bias.
- **Data Type Conversion:** Converted `Date Rptd`, `DATE OCC`, and `TIME OCC` to proper datetime types; cast `Premis Cd` to integer.
- **Outlier Detection:** Applied the IQR method to flag and handle extreme values in numeric columns, ensuring robust downstream analysis.

---

## 🔍 Part 2 — Exploratory Data Analysis (EDA)

Nine analytical questions were addressed:

### 1. Overall Crime Trends (2020–2023)
- Persistent year-over-year increase in reported incidents
- 2022 recorded the highest annual crime count

### 2. Seasonal Patterns
- Clear seasonality detected — July consistently shows peak crime rates across all years
- Monthly averages visualized across 4-year span

### 3. Most Common Crime Type
- **Vehicle Stolen** emerged as the most frequent crime type (~80K+ incidents)
- Sustained high frequency observed across all years

### 4. Regional Crime Disparities
- Analyzed crime by `AREA NAME` across 21 LAPD divisions
- **77th Street** area recorded the highest total crime volume

### 5. Economic Correlations
- Cross-referenced crime data with income/economic indicators using lat/lon coordinates
- Grand theft and burglary showed the strongest correlation with mean income levels

### 6. Day-of-Week Patterns
- **Friday** recorded the highest frequency of Vehicle Stolen and Battery-Simple Assault
- Weekly crime frequency remained relatively consistent with mild Friday spikes

### 7. COVID-19 Impact Analysis
- Pre/post COVID-19 onset (March 2020) comparison revealed an initial dip followed by a strong rebound and sustained increase through 2022

### 8. Outlier & Geospatial Analysis
- Identified outliers in victim age distribution using IQR + boxplots
- Geospatial clustering revealed high-density crime zones in specific LAPD divisions

### 9. Demographic Patterns
- Ages 18–34 are most represented across top crime types
- Males are disproportionately represented except in "Intimate Partner – Simple Assault"

---

## 📈 Part 3 — Time Series Forecasting

Forecasted monthly crime volume for the next period using two models:

### ARIMA (Autoregressive Integrated Moving Average)
- Applied Augmented Dickey-Fuller (ADF) test to assess stationarity
- Tuned ARIMA parameters based on ADF results
- Train/test split applied for model validation

### Facebook Prophet
- Configured using ADF test results for optimal seasonality settings
- Captured both trend and seasonal components with confidence intervals
- Produced more stable and interpretable forecasts than ARIMA for this dataset

| Model | Strengths in This Context |
|-------|--------------------------|
| ARIMA | Strong on stationary data, interpretable parameters |
| Prophet | Handles seasonality and trend changes robustly |

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| Language | Python 3.8+ |
| Data Manipulation | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Time Series | statsmodels (ARIMA), Prophet |
| Statistical Tests | Augmented Dickey-Fuller (ADF) |
| Environment | Jupyter Notebook |

---

## ▶️ How to Run

```bash
# 1. Clone the repository
git clone https://github.com/NeelKamal1710/Crime-Data-Analysis-and-Prediction.git
cd Crime-Data-Analysis-and-Prediction

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn statsmodels prophet jupyter

# 3. Download the dataset
# Source: https://data.lacity.org/Public-Safety/Crime-Data-from-2020-to-Present/2nrs-mtv8
# Save as: Crime_Data_from_2020_to_Present.csv in the project root

# 4. Launch the notebook
jupyter notebook IE6400_Project_1.ipynb
```

---

## 💡 Key Insights

- Vehicle theft is the most persistent and high-volume crime in LA, peaking in summer months and on Fridays
- Crime rebounded sharply post-COVID, suggesting lockdown-era suppression followed by catch-up effects
- Geographic concentration of crime in specific LAPD divisions suggests targeted resource allocation would be more effective than city-wide approaches
- Prophet outperformed ARIMA for this dataset due to strong seasonality and multi-year trend shifts

---

## 🚀 Future Enhancements

- Integrate real-time LAPD data via API for live dashboard updates
- Build an automated ETL pipeline (Apache Airflow) to refresh data monthly
- Deploy forecasting models as a REST API for law enforcement planning tools
- Add socioeconomic feature engineering to improve prediction accuracy

---

## 👤 Author

**Neel Kamal**  
[LinkedIn](https://www.linkedin.com/in/neel-kamal-90ba53136/) | [GitHub](https://github.com/NeelKamal1710) | [Tableau Portfolio](https://public.tableau.com/app/profile/neel.kamal7751/vizzes)

---

## 📄 License

This project uses publicly available government data from the City of Los Angeles Open Data Portal. For academic and portfolio use only.
