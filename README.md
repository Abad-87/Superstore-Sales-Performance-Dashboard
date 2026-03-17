<div align="center">

<!-- Banner -->
<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0c447c&height=200&section=header&text=Superstore%20Sales%20Analytics&fontSize=40&fontColor=ffffff&fontAlignY=38&desc=End-to-end%20Business%20Intelligence%20Dashboard&descAlignY=58&descSize=16"/>

<!-- Badges -->
<p>
  <img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black"/>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/DAX-185fa5?style=for-the-badge&logo=microsoft&logoColor=white"/>
  <img src="https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white"/>
</p>

<p>
  <img src="https://img.shields.io/badge/Records-9%2C994-0c447c?style=flat-square"/>
  <img src="https://img.shields.io/badge/Revenue-$2.30M-1d9e75?style=flat-square"/>
  <img src="https://img.shields.io/badge/Period-2014--2017-ba7517?style=flat-square"/>
  <img src="https://img.shields.io/badge/Customers-793-a32d2d?style=flat-square"/>
</p>

</div>

---

## 📌 Overview

A full **business intelligence pipeline** built on the Sample Superstore dataset — from raw Excel data to a client-ready interactive dashboard. This project answers the key questions every business should be asking:

> *Which products generate the most revenue? Where is profit leaking? Which regions and segments should the business double down on?*

---

## 📊 Key Findings at a Glance

| Metric | Value |
|---|---|
| 💰 Total Revenue | **$2,297,201** |
| 📈 Total Profit | **$286,397** |
| 🎯 Profit Margin | **12.5%** |
| 🛒 Total Orders | **5,009** |
| 👥 Unique Customers | **793** |
| 🚀 YoY Growth (2017) | **+20.4%** |

---

---

## 🔍 Analysis Breakdown

### 📦 Revenue by Category

| Category | Revenue | Profit | Margin |
|---|---|---|---|
| 🖥️ Technology | $836,154 | $145,454 | **17.4%** |
| 🪑 Furniture | $741,999 | $18,451 | **2.5%** |
| 📎 Office Supplies | $719,047 | $122,490 | **17.0%** |

### 🌍 Regional Performance

| Region | Revenue | Profit | Margin |
|---|---|---|---|
| 🏆 West | $725,458 | $108,418 | **14.9%** |
| East | $678,781 | $91,523 | 13.5% |
| South | $391,722 | $46,749 | 11.9% |
| ⚠️ Central | $501,240 | $39,706 | **7.9%** |

### 🔴 Loss-Making Sub-Categories

| Sub-Category | Margin |
|---|---|
| Tables | **-8.6%** |
| Bookcases | **-3.0%** |
| Supplies | **-2.5%** |

---

## ⚙️ Tech Stack

```
Data Extraction  →  Python (pandas)
Data Modeling    →  Power BI Desktop + DAX
Visualization    →  Power BI 
Date Intelligence→  Custom DAX Date Table
```

---

## 🧮 Core DAX Measures

<details>
<summary><b>Click to expand all DAX measures</b></summary>

```dax
-- Core KPIs
Total Revenue    = SUM(Orders[Sales])
Total Profit     = SUM(Orders[Profit])
Profit Margin %  = DIVIDE([Total Profit], [Total Revenue], 0)
Total Orders     = DISTINCTCOUNT(Orders[Order ID])
Avg Order Value  = DIVIDE([Total Revenue], [Total Orders], 0)

-- Year over Year
YoY Revenue Growth % =
DIVIDE(
    [Total Revenue] - CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('Date Table'[Date])),
    CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('Date Table'[Date])),
    0
)

-- Time Intelligence
YTD Revenue = CALCULATE([Total Revenue], DATESYTD('Date Table'[Date]))
YTD Profit  = CALCULATE([Total Profit],  DATESYTD('Date Table'[Date]))

-- Revenue % of Total
Revenue % of Total =
DIVIDE(
    [Total Revenue],
    CALCULATE([Total Revenue], ALL(Orders)),
    0
)
```

</details>

---

## 🗓️ Date Table Setup

```dax
Date Table =
ADDCOLUMNS(
    CALENDAR(DATE(2014,1,1), DATE(2017,12,31)),
    "Year",         YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month Name",   FORMAT([Date], "MMM"),
    "Quarter",      "Q" & QUARTER([Date]),
    "Week Number",  WEEKNUM([Date]),
    "Day",          DAY([Date]),
    "Weekday",      FORMAT([Date], "ddd"),
    "Year-Month",   FORMAT([Date], "YYYY-MMM")
)
```

> ⚠️ Create via **Modeling → New Table**, then mark as Date Table and link to `Orders[Order Date]`

---

## 💡 Business Recommendations

```
✅  GROW   →  Push Technology (esp. Copiers, Accessories) — 37% margin
✅  GROW   →  Invest in West region — highest margin at 14.9%
⚠️  FIX    →  Reprice Tables & Bookcases — currently losing money
⚠️  FIX    →  Investigate Central region discounting practices
📅  PLAN   →  Scale up inventory/staffing before Q4 (Nov peak)
📅  PLAN   →  Launch Q1–Q2 campaigns to reduce seasonal revenue dips
```

---
<p>Made with 📊 Python · Power BI · DAX</p>

</div>
