# 🔐 Cybersecurity Threat Intelligence & Attack Monitoring Dashboard
### Data Handling & Visualisation Project | NMIMS, Chandigarh Campus

![PowerBI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?style=flat&logo=powerbi)
![DAX](https://img.shields.io/badge/DAX-Functions-orange?style=flat)
![Data](https://img.shields.io/badge/Dataset-999%2B%20Rows-blue?style=flat)
![Pages](https://img.shields.io/badge/Dashboard-3%20Pages-green?style=flat)

---

## 📌 Project Overview

An interactive **Cybersecurity Threat Intelligence and Attack Monitoring Dashboard** built using **Power BI**, designed to simulate a real-world **Security Operations Center (SOC)** environment. The dashboard transforms large-scale raw cybersecurity data into actionable visual insights — helping identify attack patterns, classify threat severity, and detect geographic hotspots.

Built as part of the **Data Handling & Visualisation (DHV)** course at **NMIMS, Chandigarh Campus** under the guidance of **Dr. Ashish Mogra**.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🌍 Global Threat Analysis | Attack trends across countries and industries (2015–2024) |
| 🇮🇳 India Regional Analysis | State-wise cybercrime data using CII Report (2019–2021) |
| 📊 KPI Cards | Total Loss, Users Impacted, Incident Count, Resolution Time |
| 🗺️ Geographic Maps | World map & India map for hotspot visualization |
| 🔍 Severity Classification | High / Medium / Low attack impact distribution |
| 🔎 Drill-down Filters | Filter by Year, State/UT, Attack Type, Industry |
| 📈 Trend Analysis | Year-over-year financial loss & user impact trends |
| ⚖️ Industry Comparison | Banking, IT, Healthcare, Government, Education |

---

## 🗂️ Datasets Used

| Dataset | Description | Source |
|---|---|---|
| Global Cybersecurity Threats 2015–2024 | 10 columns, 999+ rows — country, attack type, financial loss, affected users, industry, defense mechanism, resolution time | Kaggle |
| Attack_desc | Maps Attack IDs to Attack Types (Malware, Phishing, Ransomware, DDoS, MitM, SQL Injection) | Kaggle |
| CII Report (India) | State/UT-wise cybercrime data for 2019, 2020, 2021 including chargesheeting rates and projected population | CII |

---

## 🛠️ Tech Stack

- **Tool:** Microsoft Power BI Desktop
- **Data Processing:** Power Query Editor
- **Calculated Measures:** DAX (Data Analysis Expressions)
- **Visualizations:** Bar charts, Donut charts, Pie charts, Line charts, Combo charts, Maps, Tables, KPI Cards

---

## ⚙️ Data Preprocessing (Power Query Editor)

### Dataset 1 — Global Cybersecurity Threats:
- Changed data types (text → numeric, proper date formatting)
- Merged with Attack_desc dataset via `Attack_ID`
- Expanded merged column and renamed to `Attack Type`
- Removed `Attack_ID` column after merging

### Dataset 2 — Attack_desc:
- No preprocessing required

### Dataset 3 — CII Report (India):
- Changed data types for all year columns and rate columns
- Replaced placeholder `"-"` values with `0` in year and chargesheeting rate columns
- Filtered out null rows

---

## 📐 DAX Measures

### Global Cybersecurity Data:
```dax
Total Loss = SUM('Global_Cybersecurity_Threats'[Financial Loss in Million Dollar])

Total Incidents = COUNTROWS('Global_Cybersecurity_Threats')

Total Users Impacted = SUM('Global_Cybersecurity_Threats'[Number of Affected Users])

Avg Resolution Time = AVERAGE('Global_Cybersecurity_Threats'[Incident Resolution Time (in Hours)])

Avg Financial Loss = AVERAGE('Global_Cybersecurity_Threats'[Financial Loss in Million Dollar])

% of Total Loss = DIVIDE([Total Loss], CALCULATE([Total Loss], ALL('Global_Cybersecurity_Threats')))

Country Rank = RANKX(ALL('Global_Cybersecurity_Threats'[Country]), [Total Loss], , DESC)
```

### CII Report (India):
```dax
Crimes 2019 = SUM(CIIReport[2019])
Crimes 2020 = SUM(CIIReport[2020])
Crimes 2021 = SUM(CIIReport[2021])

Avg Chargesheeting Rate = AVERAGE(CIIReport[Chargesheeting Rate (2021)])

State Rank = RANKX(ALL(CIIReport[State/UT]), [Crimes 2021], , DESC)
```

---

## 📊 Dashboard Structure

### Page 1 — Homepage
- KPI Cards: Total Loss (₹151.47K) · Total Users Impacted (2bn) · Crimes 2021 (53K)
- Bar Chart: Top 5 countries by affected users
- Bar Chart: Top 5 Indian states by cybercrime rate
- Navigation buttons → Global Threats & India Regional Analysis

### Page 2 — Global Threats
- KPI Cards: Total Loss · Affected Users (1.51bn) · Max Duration (3000 hrs) · Attack Count
- Horizontal Bar Chart: Financial loss by country
- Donut Chart: Loss distribution by attack type
- Pie Chart: Severity distribution (High 50.43% · Medium 25.13% · Low 24.43%)
- Table: Industry-wise incidents, loss, users (Banking, IT, Healthcare, Education, Government)
- World Map: Geographic attack distribution
- Clustered Column Chart: Attack source vs impact
- Line Chart: Yearly trends (2015–2024)
- Combo Chart: Loss by industry + percentage

### Page 3 — India Regional Analysis
- KPI Cards: Crime 2019 (45K) · Crime 2020 (50.04K) · Crime 2021 (53K) · Avg Rate (45.83)
- Bar Chart: State-wise cybercrime rate (Telangana highest at 27.3)
- Donut Chart: State-wise population distribution
- Table: Exact crime numbers per state (2020 & 2021)
- India Map: Regional crime hotspot visualization
- Pie Chart: State contribution to total crimes
- Column Chart: Multi-year comparison (2019–2021)
- Combo Line Chart: Chargesheeting rate vs crime rate

---

## 📸 Dashboard Screenshots

> *(Add your Power BI dashboard screenshots here)*

| Homepage | Global Threats | India Regional Analysis |
|---|---|---|
| ![Home](D:/git projects/Cybersecurity/Homepage.jpeg) | ![Global](screenshots/global_threats.png) | ![India](screenshots/india_analysis.png) |

---

## 🔑 Key Insights

- 📍 **Telangana** recorded the highest cybercrime rate among all Indian states
- 💸 **IT and Banking** sectors faced the highest financial losses globally
- ⚠️ **High-severity** attacks account for over **50%** of all incidents
- 📈 Cyberattack financial losses show an **increasing trend** from 2015 to 2024
- 🎣 **Phishing, DDoS, and SQL Injection** are the most financially damaging attack types

---

## 📁 Repository Contents

```
cybersecurity-powerbi-dashboard/
│
├── screenshots/                  # Dashboard page screenshots
│   ├── homepage.png
│   ├── global_threats.png
│   └── india_analysis.png
├── data/                         # Source datasets (if shareable)
│   ├── Global_Cybersecurity_Threats_2015-2024.xlsx
│   ├── Attack_desc.xlsx
│   └── CII_Report.xlsx
├── Cybersecurity_Dashboard.pbix  # Power BI file
├── Project_Report.pdf            # Full project report
└── README.md
```

---

## 👩‍💻 Author

**Ashna Bansal**
SAP ID: 70572400052
NMIMS, Chandigarh Campus — School of Technology Management and Engineering

---

## 🙏 Acknowledgements

- **Dr. Ashish Mogra** — Project guide, NMIMS Chandigarh Campus
- [Kaggle](https://www.kaggle.com/) — Data source for cybersecurity datasets
- [Microsoft Power BI](https://powerbi.microsoft.com/) — Dashboard and visualization tool
- [CII (Cyber Intelligence India)](https://www.mha.gov.in/) — India cybercrime statistics
