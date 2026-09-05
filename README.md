# District-Level Disparities in Anganwadi Infrastructure and Nutrition Service Coverage

> A district-level analysis of Anganwadi Centre (AWC) infrastructure and ICDS nutrition service delivery, examining disparities in infrastructure availability, service coverage, beneficiary participation, and regional performance.

---

##  📌 Project Overview

This project analyses district-level Anganwadi infrastructure and nutrition service coverage data using Python.

The analysis focuses on:

  -	Anganwadi Centre (AWC) availability and infrastructure status
  -	Access to basic amenities (drinking water, toilets, electricity, own building)
  -	Nutrition service coverage (Supplementary Nutrition Programme, Hot Cooked Meal, Take-Home Ration)
  -	Beneficiary participation (children 0-6 years, pregnant & lactating women, adolescent girls)
  -	Growth monitoring and malnutrition indicators (underweight, stunting, wasting where available)
  -	State-wise and district-wide disparities
  -	Rural vs urban infrastructure gaps
  -	Staffing and functionality of AWCs

The project applies **data cleaning, data transformation, feature engineering, statistical analysis, exploratory data analysis (EDA), visualization and insight generation**.

---

## 🎯 Objectives

## 1. Infrastructure Availability Analysis

  -	Analyse the proportion of AWCs with own building, pucca/kutcha structures, drinking water, toilets, and electricity across districts.
  -	Compare infrastructure availability between rural and urban AWCs.
    
## 2. Nutrition Service Coverage Analysis

  -	Evaluate coverage of Supplementary Nutrition Programme (SNP), Hot Cooked Meals, and Take-Home Ration across districts.
  -	Examine service delivery gaps between high- and low-coverage districts.
    
## 3. Beneficiary Participation Analysis

  -	Analyse participation of children (0-3 years, 3-6 years), pregnant and lactating women, and adolescent girls.
  -	Study enrolment versus actual service utilization.
    
## 4. District Performance & Disparity Assessment

  -	Identify high- and low-performing districts based on infrastructure completeness and service coverage.
  -	Highlight state-wise and district-wide disparities in AWC functionality.

---
## ❓ Problem Statement

The raw Anganwadi/ICDS dataset contains information on AWC infrastructure, staffing, beneficiary enrolment, and nutrition service delivery. 

However, the raw data does not directly reveal which districts face the greatest infrastructure gaps, how service coverage varies across regions, or where nutrition delivery is falling short of enrolment.

This project uses Python-based analysis and visualization to identify these patterns and convert raw Anganwadi/ICDS data into meaningful, district-level insights that can support policy and resource-allocation decisions.

---

## 📂 Dataset Information

| Attribute |	Details |
| Dataset |	District-Level Anganwadi Infrastructure & Nutrition Service Coverage Data |
| Period |	(2023-2024) |
| Records |(12458) |
| Original Variables 24| (64 column count) |
| Geography	| State:36 unique values and District:777 unique values |
| Domain | Public Health / Nutrition / Child Development (ICDS) |
| Platform | Google Collab |
| Language | Python |

---

## 🛠️ Tools & Technologies

  - **Python**
  -	**Pandas**
  -	**NumPy**
  -	**Matplotlib**
  -	**Seaborn**
  -	**Google Collab**

---

## 🔄 Project Workflow

```text
Raw Dataset
     ↓
Data Inspection
     ↓
Data Cleaning
     ↓
Missing Value Analysis
     ↓
Duplicate Detection
     ↓
Data Transformation
     ↓
Feature Engineering
     ↓
Statistical Analysis
     ↓
Univariate Analysis
     ↓
Bivariate Analysis
     ↓
Multivariate Analysis
     ↓
Insights & Interpretation
     ↓
Key Findings
     ↓
Recommendations
     ↓
Conclusion
```

---

## 🧹 Data Cleaning

The raw Anganwadi/ICDS dataset was cleaned and prepared before analysis to improve data quality and consistency.

### Cleaning Steps

1. **Remove unnecessary columns**
   - Removed columns not required for the analysis (e.g. internal codes, duplicate identifiers).
     
2. **Handle duplicate records**
   - Checked the dataset for duplicate AWC/district entries and handled them during preparation.
   
3. **Handle missing values**
   - Checked missing values across infrastructure and beneficiary columns.
   - Imputed or removed as appropriate.
   - Derived coverage-ratio fields with undefined denominators filled with 0.

4. **Clean text and category fields**
   - Checked state and district names for inconsistent formatting.
   - Checked and handles leading/trailing spaces.
   - Checked capitalization/title-case consistency.
     
5. **Check numerical fields**
   - Reviewed beneficiary counts, infrastructure counts, and coverage percentages for invalid or out-of-range values.
     
6. **Check data types**
   - Verified and converted data types where required for analysis.
    
7. **Outlier review**
   - Extreme observations (e.g. districts with unusually low/high AWC counts) reviewed before statistical analysis.

8. **Final data validation**
   - Performed final null-value checks and verified the cleaned dataset structure before EDA and statistical analysis.

---

## ⚙️ Feature Engineering

### Total AWCs with Basic Amenities

```python
df["AWCs_With_Basic_Amenities"] = (
    df["AWCs_With_Drinking_Water"]
    & df["AWCs_With_Toilet"]
    & df["AWCs_With_Electricity"]
)
```

### Infrastructure Completeness Score

```python
df["Infra_Completeness_Score"] = (
    df["Own_Building_Pct"]
    + df["Drinking_Water_Pct"]
    + df["Toilet_Pct"]
    + df["Electricity_Pct"]
)
```

### Nutrition Coverage Ratio

```python
df["Nutrition_Coverage_Ratio"] = (
    df["Beneficiaries_Receiving_SNP"] /
    df["Total_Enrolled_Beneficiaries"]
)
```

### Service Utilization Gap

```python
df["Service_Utilization_Gap"] = (
    df["Total_Enrolled_Beneficiaries"]
    - df["Beneficiaries_Receiving_SNP"]
)
```

---

 📊 Statistical Analysis

The project uses:

-	Mean
-	Median
-	Mode
-	Variance
-	Standard Deviation
-	Skewness
- Kurtosis
  
These measures are used to understand the central tendency, variability, distribution, and extreme observations across infrastructure and coverage variables (e.g. Infra Completeness Score, Nutrition Coverage Ratio, Total Enrolled Beneficiaries, SNP Beneficiaries).

<img width="1187" height="530" alt="image" src="https://github.com/user-attachments/assets/ef046979-3c26-4dcf-afc0-beba024c6b65" />


---

# 📈 Exploratory Data Analysis

# 1. Univariate Analysis 

 - Distribution of Infrastructure Completeness Score across districts

 - Distribution of Nutrition Coverage Ratio across districts
 - Distribution of Total Enrolled Beneficiaries

# 2. Bivariate Analysis

 - District-wise comparison of Infra Completeness Score vs Nutrition Coverage Ratio
 - Rural vs Urban infrastructure availability comparison
 - Relationship between AWC staffing levels and service coverage

# 3. Multivariate Analysis

•	State-wise heatmap of infrastructure completeness across districts
•	Top/bottom 10 districts by Nutrition Coverage Ratio
•	Beneficiary category-wise participation (children vs pregnant/lactating women vs adolescent girls) across states
•	Year-wise or period-wise trend of infrastructure improvement (if multi-year data available)
Add your actual charts and interpretations here, following the same "Objective → Chart → Interpretation" pattern used in the PMFBY sample.

---

#  🔑 Key Findings

 - Fill in once analysis is complete — e.g.:
    - Infrastructure completeness varies considerably across districts, with a subset of  districts lagging significantly behind the national/state average.
    - Nutrition service coverage does not always match enrolment, indicating a service utilization gap in certain districts.
    -	Rural AWCs show comparatively lower access to basic amenities than urban AWCs.
    -	A small number of districts account for disproportionately low infrastructure scores, indicating priority areas for intervention.

---

# 💡 Business / Policy Insights

### Infrastructure

Districts with low Infra Completeness Scores indicate priority areas for AWC building upgrades, water, toilet, and electricity provisioning.

### Nutrition Coverage

Gaps between enrolment and SNP/THR delivery highlight potential supply-chain or last-mile delivery issues.

### Beneficiary Participation

Differences in participation across beneficiary categories (children, pregnant/lactating women, adolescent girls) point to areas needing targeted outreach.

### Regional Performance

State- and district-level disparities show that ICDS service delivery is not uniform, informing resource-allocation priorities.
 
# 🧠 Analytical Framework

## Descriptive Analysis — What Happened?

Summarizes infrastructure availability, nutrition coverage, and beneficiary participation using descriptive statistics and visualizations.

## Diagnostic Analysis — Why Did It Happen?

Identifies differences across states, districts, and rural/urban settings. 
High variance/skewness would indicate substantial disparity and extreme observations. 
These are observed patterns, not confirmed causal relationships without additional external data (e.g. funding, staffing, terrain).

## Predictive Analysis — What May Happen?

Historical trends (if multi-year data is available) can support future estimation of infrastructure improvement pace and coverage growth, given a suitable model and validation.

## Prescriptive Analysis — What Should Be Done?

  -	Prioritize low-infrastructure districts for capital investment.
  -	Investigate districts with large enrolment-to-service gaps.
  -	Study high-performing districts as models for replication.
  -	Validate extreme values and data completeness before advanced modelling.

---

# 💡 Recommendations

### 1. Improve Data Quality
Validate missing values, duplicate records, inconsistent district names, and extreme observations before advanced modelling.

### 2. Target Low-Infrastructure Districts
Prioritize capital investment in districts with the lowest Infra Completeness Scores.

### 3. Close the Nutrition Coverage Gap
Investigate districts where enrolled beneficiaries are not receiving SNP/THR services.

### 4. Address Rural-Urban Gaps
Design targeted infrastructure programs for rural AWCs lagging behind urban counterparts.

### 5. Study High-Performing Districts
Analyse top-performing districts to identify replicable practices.

### 6. Monitor Beneficiary Category Trends
Track participation across children, pregnant/lactating women, and adolescent girls over time.

### 7. Strengthen Staffing Analysis
Examine whether staffing levels correlate with service coverage outcomes.

---

# 🚀 Future Scope
-	Automate the Anganwadi/ICDS analysis workflow.
-	Add new year’s/periods when updated data becomes available.
-	Build predictive models for infrastructure improvement and coverage growth.
-	Integrate malnutrition/growth-monitoring indicators (stunting, wasting, underweight) for deeper analysis.
-	Integrate socio-economic and geographic data (poverty indices, terrain, connectivity) to explain disparities.
-	Develop an interactive dashboard for policymakers.

---

# 📁 Project Structure

```text
Anganwadi-Infrastructure-Nutrition-Coverage-Analysis/
│
├── Anganwadi_Analysis.ipynb
├── anganwadi_district_data.csv
├── README.md
│
└── images/
    ├── infra_completeness_distribution.png
    ├── nutrition_coverage_distribution.png
    ├── beneficiary_distribution.png
    ├── rural_vs_urban_infra.png
    ├── infra_vs_coverage_scatter.png
    ├── state_wise_infra_heatmap.png
    ├── top10_districts_coverage.png
    ├── beneficiary_category_participation.png
    └── enrollment_vs_service_gap.png
```

---

# ▶️ How to Run

### Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn
```
### Run the Notebook

Open:poshan_final_project (2).ipynb

```text
Anganwadi_Analysis.ipynb
```
Run the cells sequentially to reproduce the data cleaning, feature engineering, statistical analysis, charts, and insights.

---

# 📚 Analysis Techniques Used
```text
✔	Data Inspection
✔	Data Cleaning
✔	Missing Value Analysis
✔	Duplicate Detection
✔	Data Validation
✔	Data Transformation
✔	Feature Engineering
✔	Descriptive Statistics (Mean, Median, Mode, Variance, Standard Deviation, Skewness, Kurtosis)
✔	Univariate Analysis
✔	Bivariate Analysis
✔	Multivariate Analysis
✔	Trend Analysis
✔	Relationship Analysis
✔	State-wise Analysis
✔	District-wise Analysis
✔	Rural vs Urban Analysis
✔	Beneficiary Demographic Analysis
✔	Business/Policy Insight Generation
```

---

# 📓 Google Collab

Add your Collab notebook link here

---

# 📌 Project Summary

| Category | Details |
|---|---|
| Project	| District-Level Disparities in Anganwadi Infrastructure and Nutrition Service Coverage |
| Domain | Public Health / Nutrition / Child Development (ICDS) |
| Period | (2023-2024) |
| Records	| (12,458) |
| Original Variables (24) |
| Language | Python |
| Analysis | Statistical Analysis + EDA |
| Visualization	| Matplotlib + Seaborn |
| Platform | Google Collab |

---

# 🏁 Conclusion

This project demonstrates how Python can be used to analyse **district-level Anganwadi infrastructure and nutrition service coverage data**, transforming raw ICDS records into meaningful insights.

The analysis is designed to identify important patterns in:

-	Infrastructure availability
-	Nutrition service coverage
-	Beneficiary participation across demographic groups
-	State-wise and district-wide disparities
-	Rural vs urban infrastructure gaps
  
Overall, the project aims to highlight where infrastructure and service-delivery disparities are greatest, supporting evidence-based prioritization for policy and resource allocation.

This project demonstrates practical skills in data pre-processing, feature engineering, statistical analysis, exploratory data analysis, data visualization, and policy-oriented insight generation using Python.

---

# 👩‍💻 Author

**PARKAVI K**

### Skills Demonstrated

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `EDA` · `Data Cleaning` · `Feature Engineering` · `Statistical Analysis` · `Data Visualization` · `Public Health/Policy Analysis`
