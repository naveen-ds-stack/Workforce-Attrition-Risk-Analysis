# Employee Attrition Analysis Dashboard

An end-to-end HR analytics project built entirely in Excel, covering raw data intake, data cleaning, feature engineering, statistical analysis, and an interactive dashboard for exploring employee attrition.

## Overview

This project analyzes attrition across **1,000 employees** spanning **7 departments**, sourced from an HR Information System. The workbook is structured as a five-stage pipeline, all within a single `.xlsx` file, so the entire workflow (from raw, messy data to a polished interactive dashboard) is transparent and auditable.

**Headline numbers:**

| Metric | Value |
|---|---|
| Total Employees | 1,000 |
| Attrition Rate | 37.9% |
| Retention Rate | 62.1% |
| Avg Monthly Salary | ₹91,316 |
| Avg Tenure | 10.4 yrs |
| Avg Age | 41.5 yrs |
| Avg Job Satisfaction | 3.0 / 5 |

## Workbook Structure

| Sheet | Purpose |
|---|---|
| `Raw_Data` | Original 1,000-row, 18-column dataset, including intentional missing values for cleaning practice |
| `Data_cleaning` | Cleaned dataset (27 columns) with imputed values, validated business rules, and 7 newly engineered columns |
| `Documentation` | Full data quality audit trail: null checks, domain logic validation, outlier detection methodology, and a step-by-step cleaning log |
| `Analysis` | Key metrics plus six breakdown tables (Department, Age Group, Salary Band, Tenure Group, OverTime, Business Travel) with computed attrition rates and risk flags |
| `Dashboard` | Interactive one-page view with slicers, KPI cards, and six charts |

## Data Cleaning & Quality Checks

- **Missing values:** 38 total across Age, Department, Monthly_Salary, and Job_Satisfaction, each imputed with a documented method (median, mode, or "Unknown" category)
- **Domain logic validation:** rules like "Years_At_Company cannot exceed Age minus 21" applied to catch impossible records
- **Outlier detection:** IQR method for Age and Salary, Z-score method for Distance_From_Home, all checked and confirmed clean
- **Duplicate check:** 0 duplicate records found

## Feature Engineering

Seven new columns were derived from raw fields to make analysis and dashboard filtering easier:

- `Attrition_Flag`: numeric 1/0 version of Attrition
- `Age_Group`: Young (<30), Mid (30-40), Senior (40-50), Veteran (50+)
- `Salary_Band`: Low (<50K), Mid (50-80K), High (80-120K), Premium (120K+)
- `Tenure_Group`: New (<2 yrs), Developing (2-5), Established (5-10), Veteran (10+)
- `Satisfaction_Label`, `Performance_Label`, `WLB_Label`: text labels mapped from 1-5 numeric scores

## Key Findings

- **Sales (42.4%) and Finance (40.6%)** departments show the highest attrition, pointing to workload or compensation issues
- **New employees (<2 yrs)** leave at 46.7%, the highest of any tenure group, signaling an onboarding and early-engagement gap
- **Young employees (<30)** leave at 47.3%, the highest of any age group, suggesting a need for clearer career growth paths
- **Overtime workers** leave at 43.7% versus 32.8% for non-overtime staff, a critical and immediately actionable signal
- **Frequent travelers** leave at 44.5%, suggesting travel allowances or hybrid arrangements could help
- **HR (22.5%)** has the lowest attrition of any department, worth studying for practices that could be replicated elsewhere
- Salary alone doesn't appear to be the primary driver: the Low salary band actually has one of the lowest attrition rates (28.9%), while High salary band (80-120K) attrition is the highest at 41%

## Dashboard Features

- **Slicers:** Department, Gender (interactive cross-filtering across all visuals)
- **KPI cards:** Total Employees, Employees Left, Attrition Rate, Retention Rate, Avg Salary, Avg Tenure, Avg Age
- **Charts:** Attrition by Department, Age Group, Salary Band, and Tenure Group (bar charts); Attrition by OverTime (stacked bar); Attrition by Business Travel (donut)

## How to Use

1. Download `Employee_Attrition_Analysis.xlsx` and open it in Excel
2. Go to the **Dashboard** tab for the interactive view
3. Use the Department and Gender slicers to filter all charts and KPIs at once
4. Open the **Analysis** tab to see the underlying breakdown tables behind each chart
5. Check the **Documentation** tab for the full data cleaning and validation methodology

## Tools & Techniques

- Excel PivotTables and PivotCharts
- Slicers for interactive, cross-chart filtering
- Formulas: `COUNTIF`, `AVERAGE`, `QUARTILE`, `SKEW`, `STDEV`, nested `IF` for binning
- Data cleaning: median/mode imputation, domain validation rules, IQR and Z-score outlier detection
- Feature engineering: 7 derived categorical fields built from continuous and ordinal source data

## Planned Enhancements

- Additional slicers for OverTime, Business_Travel, Age_Group, and Tenure_Group to enable deeper drill-down
- A toggle to isolate "Left" vs "Stayed" employees across all visuals simultaneously

## License

This project is open for personal and educational use. Update this section with your preferred license (e.g., MIT) before publishing.
