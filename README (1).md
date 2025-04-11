# 📊 Nike Sales Dashboard - Power BI Project

## 📁 Project Overview

This repository contains an interactive **Power BI dashboard** analyzing key sales and performance metrics for Nike products. The dashboard enables dynamic exploration of data trends and insights to support business decision-making.

## 🧰 Features

- 🚀 Interactive visuals with slicers for year, product, and region  
- 📅 Monthly and daily KPIs tracking ambulance car data and orders  
- 📈 Custom DAX measures for:
  - Total number of ambulance cars  
  - Daily and monthly averages per car  
  - Orders and distances per car  
- 📊 Clean, user-friendly design with dynamic data storytelling

## 📌 Key Measures (DAX Logic)

```DAX
-- 1. Number of Ambulance Cars
Ambulance Car Count =
DISTINCTCOUNT(CMT[Ambulance Plate])

-- 2. Average Ambulance Car Per Day
Avg Ambulance Car Per Day =
AVERAGEX(VALUES(CMT[Call Receive]), CALCULATE(DISTINCTCOUNT(CMT[Ambulance Plate])))

-- 3. Monthly Average Ambulance Car
Monthly Avg Ambulance Car =
AVERAGEX(
    VALUES(DATE(YEAR(CMT[Call Receive]), MONTH(CMT[Call Receive]), 1)),
    CALCULATE(DISTINCTCOUNT(CMT[Ambulance Plate]))
)

-- 4. Daily Average Orders per Ambulance Car
Daily Avg Orders Per Car =
DIVIDE(CALCULATE(COUNTROWS(CMT)), CALCULATE(DISTINCTCOUNT(CMT[Ambulance Plate])))

-- 5. Monthly Avg Orders per Ambulance Car
Monthly Avg Orders Per Car =
AVERAGEX(
    VALUES(DATE(YEAR(CMT[Call Receive]), MONTH(CMT[Call Receive]), 1)),
    DIVIDE(CALCULATE(COUNTROWS(CMT)), CALCULATE(DISTINCTCOUNT(CMT[Ambulance Plate])))
)

-- 6. Monthly Avg Distance per Ambulance Car
Monthly Avg Distance Per Car =
AVERAGEX(
    VALUES(DATE(YEAR(CMT[Call Receive]), MONTH(CMT[Call Receive]), 1)),
    DIVIDE(SUM(CMT[Distance]), CALCULATE(DISTINCTCOUNT(CMT[Ambulance Plate])))
)

-- 7. Daily Avg Distance per Ambulance Car
Daily Avg Distance Per Car =
AVERAGEX(
    VALUES(CMT[Call Receive]),
    DIVIDE(SUM(CMT[Distance]), CALCULATE(DISTINCTCOUNT(CMT[Ambulance Plate])))
)
```

## 📂 File

- `Nike Dashboard.pbix` – Main Power BI file containing the report and DAX logic.

## 🧑‍💻 How to Use

1. Download or clone the repository.
2. Open the `.pbix` file in **Power BI Desktop**.
3. Explore or customize visuals and DAX formulas as needed.

## 📝 Author

- Dr. Mohamed Wahid Suleiman  
- Data Analysis Engineer @ Microsoft  
- Educational Technology Associate Professor