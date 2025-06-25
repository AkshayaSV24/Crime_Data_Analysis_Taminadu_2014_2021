# 🕵️‍♀️ Crime Data Analysis – Tamil Nadu (2014–2021)

This project analyzes crime trends in Tamil Nadu between 2014 and 2021, focusing on classification, trend detection, and strategic insights using data visualization.

---

## 📊 Project Overview

- **Objective**: Identify patterns, high-risk crime categories, and influential variables using state-level crime data.
- **Scope**:
  - Analyze trends over time
  - Classify crimes by their nature
  - Generate statistical visualizations
  - Provide actionable recommendations

---

## 🧰 Tools & Technologies

- Python (pandas, tabula-py)
- Excel (Advanced Cleaning)
- Power Query 
- Power BI (Dashboards & Interactive Visuals)

---

## 📁 Data Source

- Tamil Nadu Crime Data (2014–2021)  
  [OpenCity Dataset](https://data.opencity.in/dataset/tamil-nadu-crime-data)

---

---

## 📁 Data Cleaning

- I downloaded the data as Pdf and then extracted the required tables using tabula and exported into a CSV file.

- I cleaned the data using Advanced excel and Python with pandas library and extracted again as a CSV file.

```Python

import pandas as pd

df = pd.read_csv(r'C:\Users\D E L L\Documents\Albatros\tabula-tn_cr_statistics_2014-2021.csv')

# categories

def crime_category(head):
    head = str(head).lower()
    if "murder" in head or "homicide" in head or "hurt" in head:
        return "Violent Crimes"
    elif "negligence" in head:
        return "Negligence-Based"
    elif "dowry" in head or "harassment" in head or "assault on women" in head:
        return "Crimes Against Women"
    elif "suicide" in head:
        return "Self-Inflicted Acts"
    else:
        return "Other IPC Crimes"

df["Category"] = df["Crime Head"].apply(crime_category)

df.to_csv('Crime_Analysis.csv')
```

- Then Loaded and Transformed the data into the power query for adding custom columns and new measures, then finally into Power BI workspace.

```DAX

# Custom Columns :

Total_Incidence = [2014_Incidence] + [2015_Incidence] + [2016_Incidence] +
[2017_Incidence] + [2018_Incidence] + [2019_Incidence] + [2020_Incidence] + [2021_Incidence]

Total_Crime_rate = [2014_Crime _rate] + [2015_Crime _rate] + [2016_Crime _rate] +
[2017_Crime _rate] + [2018_Crime _rate] + [2019_Crime _rate] + [2020_Crime _rate] + [2021_Crime _rate]

# New Measure:

Average_Crime_rate = 
AVERAGEX(
    'Crime_Analysis',
    'Crime_Analysis'[Total_Crime_rate] / 8
)

Average_Incidence = 
AVERAGEX(
    'Crime_Analysis',
    'Crime_Analysis'[Total_Incidence] / 8
)
```

## 📌 Key Features

- **Classification of Crimes**:
  - Violent Crimes – Murder, Attempt to Murder, Culpable Homicide, Grievous Hurt
  - Negligence-Based Crimes – Causing Death by Negligence, Road/Rail/Medical Negligence
  - Crimes Against Women - Dowry Deaths, Sexual Harassment, Assault on Women
  - Self-Inflicted Acts - Attempt to Commit Suicide, Abetment of Suicide
  - Other IPC Crimes - Wrongful Restraint, Acid Attack, etc.

- **Visual Insights**:
  - Key Influencers, Waterfall Charts, Correlation Heatmaps.
- **Recommendations**:
  - Community policing, education, conflict resolution, predictive policing, infrastructure audits.

---

## 🧠 Insights

- Violent crimes and negligence-based offenses dominate crime statistics.
- “Hurt” and “Simple Hurt” account for the majority of incidents.
- Strong correlation between crime rate and total incidence.

---

## 📎 Deliverables

- 📄 Cleaned CSV dataset
- 🐍 Python scripts for data extraction and preprocessing
- 📊 Interactive Power BI dashboard
- 🎯 Insight-driven presentation deck (PPTX)

---

### 📊 Dashboard 
Page 1 - ![Image](https://github.com/user-attachments/assets/ef1e8995-de96-4f23-848f-613458a835ef)
Page 2 - ![Image](https://github.com/user-attachments/assets/e014f02a-0a75-41da-838c-9eb0f766b720)
Correlation Heat Map - ![Image](https://github.com/user-attachments/assets/b5269c0c-54e2-4b8b-bb65-c77d1386ca9d)

## 📊 Dashboard Highlights

- **Page 1**: Overview of crime types and total incidence across years.
- **Page 2**: Key Influencer chart showing impact of average crime rate on total incidents.
- **Correlation Heatmap**: Shows variable relationships (e.g., crime rate vs. incidence), supporting predictive modeling opportunities.


## Report with Insights and Recommendations

[Crime Data Analysis_Albattros_akshaya.pptx](https://github.com/user-attachments/files/20905412/Crime.Data.Analysis_Albattros_akshaya.pptx)

### ✅ Conclusion

- This project enhanced my skills in data cleaning, classification, and visual storytelling using real-world crime data.
- By identifying key crime categories and their trends, the analysis supports data-driven policy making and highlights the potential of predictive analytics in public safety.



