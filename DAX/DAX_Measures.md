# DAX Measures — Food Manufacturing BI Analytics

This file contains the main DAX measures used in the Power BI dashboard.

> **Note:** The dataset is illustrative/simulated for portfolio purposes. Measure names and table/column names should match the final PBIX model.

## 1. Date Table

### Date Table
```DAX
Date_Table =
CALENDAR(
    MIN(Workforce_Data[Production_Date]),
    MAX(Workforce_Data[Production_Date])
)
```

### Year
```DAX
Year = YEAR(Date_Table[Date])
```

### Month Number
```DAX
Month Number = MONTH(Date_Table[Date])
```

### Month
```DAX
Month = FORMAT(Date_Table[Date], "MMM")
```

### Month Year
```DAX
Month Year = FORMAT(Date_Table[Date], "MMM YYYY")
```

## 2. Workforce & Labour Measures

### Total Good Production
```DAX
Total Good Production =
SUM(Workforce_Data[Accepted_Good_Qty_Units])
```

### Total Labour Hours
```DAX
Total Labour Hours =
SUM(Workforce_Data[Labour_Hours])
```

### Units per Labour Hour
```DAX
Units per Labour Hour =
DIVIDE(
    [Total Good Production],
    [Total Labour Hours],
    0
)
```

### Actual Productivity
```DAX
Actual Productivity =
DIVIDE(
    [Total Good Production],
    [Total Labour Hours],
    0
)
```

### Benchmark Productivity
```DAX
Benchmark Productivity =
DIVIDE(
    SUMX(
        Workforce_Data,
        Workforce_Data[Benchmark_Productivity]
            * Workforce_Data[Labour_Hours]
    ),
    [Total Labour Hours],
    0
)
```

### Workforce Efficiency %
```DAX
Workforce Efficiency % =
DIVIDE(
    [Actual Productivity],
    [Benchmark Productivity],
    0
)
```

### Average Present Workers
```DAX
Avg Present Workers =
AVERAGE(Workforce_Data[Present_Workers])
```

### Average Required Workers
```DAX
Avg Required Workers =
AVERAGE(Workforce_Data[Required_Workers])
```

### Average Manpower Gap
```DAX
Avg Manpower Gap =
[Avg Required Workers] - [Avg Present Workers]
```

## 3. Production Planning Measures

### Planned Production
```DAX
Planned Production =
SUM(Workforce_Data[Planned_Good_Qty_Units])
```

### Required Labour Hours
```DAX
Required Labour Hours =
SUM(Workforce_Data[Required_Labour_Hours])
```

### Total Required Workers
```DAX
Total Required Workers =
SUM(Workforce_Data[Required_Workers])
```

## 4. Manpower Status Measures

### Shortage Observations
```DAX
Shortage Observations =
CALCULATE(
    COUNTROWS(Workforce_Data),
    Workforce_Data[Manpower_Gap] > 0
)
```

### Surplus Observations
```DAX
Surplus Observations =
CALCULATE(
    COUNTROWS(Workforce_Data),
    Workforce_Data[Manpower_Gap] < 0
)
```

### Balanced Observations
```DAX
Balanced Observations =
CALCULATE(
    COUNTROWS(Workforce_Data),
    Workforce_Data[Manpower_Gap] = 0
)
```

### Shortage Rate %
```DAX
Shortage Rate % =
DIVIDE(
    [Shortage Observations],
    COUNTROWS(Workforce_Data),
    0
)
```

## 5. Operational Measures

### Total Downtime Minutes
```DAX
Total Downtime Minutes =
SUM(Workforce_Data[Downtime_Minutes])
```

### Average Downtime Minutes
```DAX
Avg Downtime Minutes =
AVERAGE(Workforce_Data[Downtime_Minutes])
```

### Total Overtime Hours
```DAX
Total Overtime Hours =
SUM(Workforce_Data[Overtime_Hours])
```

## 6. KPI Mapping

| Dashboard KPI | DAX Measure |
|---|---|
| Workforce Efficiency | `[Workforce Efficiency %]` |
| Units / Labour Hour | `[Units per Labour Hour]` |
| Present Workers | `[Avg Present Workers]` |
| Required Workers | `[Avg Required Workers]` |
| Manpower Gap | `[Avg Manpower Gap]` |

## 7. Workforce Dashboard Visual Mapping

### Workforce Efficiency Trend
- Axis: `Date_Table[Month Year]`
- Values: `[Workforce Efficiency %]`
- Legend: None

### Efficiency by Production Line
- Axis: `Workforce_Data[Production_Line]`
- Values: `[Workforce Efficiency %]`

### Efficiency by Shift
- Axis: `Workforce_Data[Shift]`
- Values: `[Workforce Efficiency %]`

### Present vs Required Workers by Production Line
- Axis: `Workforce_Data[Production_Line]`
- Values: `[Avg Present Workers]`, `[Avg Required Workers]`

### Manpower Gap by Production Line
- Axis: `Workforce_Data[Production_Line]`
- Values: `[Avg Manpower Gap]`

### Manpower Gap by Shift
- Axis: `Workforce_Data[Shift]`
- Values: `[Avg Manpower Gap]`

## 8. Core Business Logic

**Present Workers × Production Hours**
→ Labour Hours

**Accepted Good Quantity ÷ Labour Hours**
→ Actual Productivity

**Actual Productivity ÷ Benchmark Productivity × 100**
→ Workforce Efficiency

**Planned Good Quantity ÷ Benchmark Productivity**
→ Required Labour Hours

**Shift Hours − Planned Downtime**
→ Effective Hours per Worker

**Required Labour Hours ÷ Effective Hours per Worker**
→ Required Workers

**Required Workers − Present Workers**
→ Manpower Gap

## 9. Modeling Notes

- Use DAX measures for rates and KPIs instead of summing raw percentage columns.
- `Date_Table[Date]` should have a one-to-many relationship to `Workforce_Data[Production_Date]`.
- `Date_Table[Month Year]` should be sorted chronologically.
- Positive manpower gap = potential shortage.
- Negative manpower gap = potential surplus.
- Zero manpower gap = balanced.

## 10. Benchmark Methodology

The workforce prototype uses a **P75 historical productivity benchmark**.

The purpose is to represent a strong but realistically achievable historical performance level rather than using the average or the absolute maximum.

With real company data, the benchmark should be validated with operations and may be refined by **Product + Production Line + Shift** when sufficient historical observations exist.

## Author

**Abhishek Sinha**

MSc Data Science | Data Analytics | Power BI | SQL | Excel | Python
