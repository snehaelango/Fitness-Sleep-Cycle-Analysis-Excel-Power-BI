# 🏃‍♀️💤 Fitness & Sleep Cycle Analysis using Power BI

---

## 📌 Project Overview
This project focuses on analyzing **fitness activity, sleep patterns, hourly intensity, and heart rate data** to gain insights into daily health behavior. The project follows an end-to-end analytics workflow where **data cleaning and feature engineering were performed in Microsoft Excel**, followed by **data modeling, DAX calculations, and interactive dashboard creation in Power BI**.

The analysis helps understand activity levels, sleep quality, and intensity patterns using real-world Fitbit fitness tracker data.

---

## 🎯 Project Objectives
- Analyze daily fitness activity and sleep patterns
- Categorize activity levels and sleep quality
- Study hourly activity intensity and heart rate behavior
- Identify trends in steps, calories burned, and sleep duration
- Build an interactive Power BI dashboard for health insights
- Apply Excel preprocessing and Power BI analytics techniques

---

## ❓ Problem Statement
Raw fitness tracker data contains unnecessary columns, inconsistent date formats, and lacks meaningful categorical fields for analysis.  
The challenge is to:
- Clean and preprocess multiple fitness-related datasets
- Create calculated columns to classify activity, sleep, intensity, and heart rate levels
- Enable time-based analysis using a date dimension
- Visualize key health metrics through an interactive dashboard

---

## 🗂 Dataset Information
**Source:** Kaggle – Fitbit Fitness Tracker Data  
**Link:** https://www.kaggle.com/datasets/marziabombaci/fitbit-data-for-bellabeat-case-study

### Tables Used
- `Facts_DailyActivity`
- `Facts_Sleep`
- `HourlyIntensities`
- `HeartRate_Seconds`

All datasets were cleaned and stored in **a single Excel workbook (separate sheets)** before importing into Power BI.

---

## 🧹 Data Cleaning & Processing (Excel)
All preprocessing was performed using **Microsoft Excel**.

### Cleaning Steps
- Removed unnecessary and irrelevant columns
- Standardized date formats (converted to Short Date)
- Renamed columns for clarity
- Handled missing and blank values
- Cleaned all four tables
- Stored cleaned tables in one Excel workbook

### Columns Removed (Daily Activity)
- TrackerDistance  
- LoggedActivitiesDistance  
- ModeratelyActiveDistance  
- LightActiveDistance  
- SedentaryActiveDistance  

---

## 📑 Calculated Columns Created (Excel)

### 🏃 Facts_DailyActivity
- **ActivityLevel**
IF(TotalSteps >= 10000, "High",
IF(TotalSteps >= 5000, "Medium", "Low"))
- **ActiveMinutes**
VeryActiveMinutes + FairlyActiveMinutes + LightlyActiveMinutes
- **SedentaryFlag**
IF(SedentaryMinutes > 600, "High Sedentary", "Normal")

---

### 💤 Facts_Sleep
- Converted `SleepDay` to Short Date
- **SleepQuality**
IF(TotalMinutesAsleep >= 420, "Good", "Poor")

---

### ⏱ HourlyIntensities
- **IntensityLevel**
IF(TotalIntensity >= 20, "High",
IF(TotalIntensity >= 10, "Medium", "Low"))

---

### ❤️ HeartRate_Seconds
- **HeartRateZone**
IF(Value < 60, "Low",
IF(Value <= 100, "Normal", "High"))

📌 *All calculated fields were created in Excel before importing into Power BI.*

---

## 📐 Data Modeling (Power BI)
After importing the cleaned data into Power BI:
- Created relationships between activity, sleep, intensity, and heart rate tables
- Implemented a Date dimension for time-based analysis

### 🗓 Date Table (DAX)
```DAX
Dim_Date =
ADDCOLUMNS (
  CALENDAR (DATE(2016,1,1), DATE(2016,12,31)),
  "Year", YEAR([Date]),
  "Month", MONTH([Date]),
  "MonthName", FORMAT([Date], "MMM"),
  "Weekday", FORMAT([Date], "DDD")
)
``` 
📊 Dashboard Overview
The Power BI dashboard contains **two pages**:

### Page 1 – Activity Overview
- KPIs: Total Steps, Calories Burned, Active Minutes
- Daily steps trend
- Activity level distribution
- Steps vs calories analysis
- Date and activity-level slicers

### Page 2 – Sleep & Health Insights
- KPIs: Average Sleep Hours, Average Heart Rate, Maximum Heart Rate
- Sleep duration trend
- Hourly activity intensity analysis
- Daily health metrics table

📸 *Dashboard screenshot is included below.*
<img width="726" height="413" alt="image" src="https://github.com/user-attachments/assets/1e293f57-2de3-4a31-978a-c5d29d21b8af" />
<img width="727" height="415" alt="image" src="https://github.com/user-attachments/assets/9c48cda7-82c6-442a-a403-645fce7e634e" />

## 🔍 Key Insights
- Majority of days fall under **Low to Medium activity levels**
- **Calories burned increase with higher step counts**, indicating a strong relationship between activity and energy expenditure
- **Hourly activity intensity** shows a clear pattern:
  - Morning activity peak
  - Afternoon dip
  - Evening rise
- **Average daily steps (3.48K)** are significantly below the target goal of **7.5K steps**
- Sleep duration and heart rate metrics provide additional context to overall health behavior
## 🛠 Tools & Techniques Used

### Tools
- **Microsoft Excel** – Data cleaning, preprocessing, and calculated column creation
- **Power BI Desktop** – Data modeling, DAX calculations, and dashboard visualization
- **GitHub** – Version control and project documentation

### Techniques
- Data cleaning and preprocessing
- Feature engineering using calculated columns
- Data modeling and relationship management
- Time-based analysis using a Date dimension
- KPI creation and performance comparison
- Interactive dashboard design using slicers and filters
## 📁 Repository Structure
```text
fitness-sleep-cycle-analysis/
│
├── Dataset/
│   └── fitbit_cleaned_data.xlsx
│
├── PowerBI_File/
│   └── fitness_sleep_dashboard.pbix
│
├── Screenshots/
│   └── dashboard.png
│
└── README.md
```
## 🚀 Conclusion
This project demonstrates a practical data analytics workflow by combining **Excel-based data preprocessing** with **Power BI modeling and visualization**. It highlights the ability to clean raw data, create meaningful features, perform time-based analysis, and present insights through interactive dashboards focused on health and lifestyle analytics.




