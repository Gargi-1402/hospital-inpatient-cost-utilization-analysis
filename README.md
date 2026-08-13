
# Hospital Inpatient Cost & Utilization Analysis

## Overview

This project analyzes more than 2.1 million inpatient hospital discharge records from the New York State SPARCS dataset to understand where inpatient spending is concentrated and how hospital resource utilization varies across different patient and admission characteristics.

I built the project to combine my healthcare background with practical analytics. Rather than looking at cost alone, I wanted to understand how factors such as diagnosis, severity of illness, admission type, length of stay, facility, and patient disposition relate to inpatient resource use.

The analysis was carried out in two stages: Python was used for data preparation and exploratory analysis, followed by Power BI for the final analysis and interactive dashboard.

The final dashboard is organized into three pages covering:

- Hospital inpatient cost and utilization
- Resource utilization and cost efficiency
- Hospital and patient-level patterns

## Business Problem

Hospital inpatient care involves a large number of admissions, diagnoses, and resource-intensive cases, making it difficult to see where costs are concentrated from the raw data alone.

The main goal of this project was to understand the major drivers of inpatient spending and resource utilization. I focused on questions such as:

- Which diagnoses contribute the most to total inpatient cost?
- How does cost vary with severity of illness?
- How do different admission types contribute to overall spending?
- How does length of stay relate to inpatient cost?
- How does average cost per day vary across severity levels and facilities?
- What patterns can be observed in patient disposition and other patient-level characteristics?

The analysis is descriptive rather than causal. The dashboard highlights patterns in the data that could be investigated further by hospital operations or finance teams.

## Objectives

The project aimed to:

1. Identify major contributors to inpatient spending.
2. Compare cost and utilization patterns across severity and admission types.
3. Examine length of stay and cost efficiency metrics.
4. Compare facility-level average cost per day.
5. Present the findings through an interactive Power BI dashboard that can be used for exploratory analysis.

## Dataset

The project uses the **New York State SPARCS Hospital Inpatient Discharges (De-Identified)** dataset.

SPARCS (Statewide Planning and Research Cooperative System) contains de-identified information on hospital inpatient discharges in New York State. The dataset includes information on diagnoses, procedures, length of stay, patient characteristics, admission type, severity of illness, patient disposition, and financial measures such as total charges and total costs.

For this project, the original dataset was processed in Python and reduced to the fields relevant to the analysis before being used in Power BI.

### Dataset at a glance

- **Records:** 2.1M+ inpatient discharges
- **Geographic scope:** New York State
- **Data type:** De-identified hospital inpatient discharge data
- **Source:** New York State Open Data
- **Primary financial measure:** Total Costs
- **Key utilization measure:** Length of Stay

## Data Preparation & Methodology

The original SPARCS data was first processed in Google Colab using Python and Pandas before being brought into Power BI.

Because of the size of the dataset, the CSV was processed in chunks of 100,000 rows rather than loading the entire file into memory at once.

The main preparation steps were:

- Inspected the dataset structure, data types, and relevant financial fields.
- Checked missing values across the dataset using chunk-based processing.
- Selected the fields relevant to the project to reduce the dataset to 31 columns.
- Converted `Length of Stay` to a numeric format, with invalid values treated as missing.
- Cleaned `Total Charges` and `Total Costs` by removing comma formatting and converting them to numeric values.
- Exported the processed data as a Snappy-compressed Parquet file.
- Loaded the processed data back into Python to verify its structure, data types, missing values, and key categorical fields.
- Performed exploratory analysis across severity of illness and admission type before developing the Power BI dashboard.

Power BI was then used for the final analysis, measures, filtering, and interactive visualization.

### Key Metrics

The dashboard uses metrics such as:

- Total Admissions
- Total Inpatient Cost
- Median Cost
- Median Length of Stay
- Average Length of Stay
- Average Cost per Day
- 95th Percentile Cost
- High-Cost Admission Rate

## Dashboard

The final Power BI dashboard is organized into three pages, with each page looking at inpatient care from a different perspective.

### Page 1 — Hospital Inpatient Cost & Utilization Analysis

This page provides an overall view of inpatient spending and utilization.

**Key metrics:**
- Total Admissions
- Total Inpatient Cost
- Median Cost
- Median Length of Stay

**Visuals:**
- Top 10 Diagnoses by Total Inpatient Cost
- High-Cost Admission Rate by Severity
- Total Cost by Admission Type

The page is intended to establish where inpatient spending is concentrated and how overall cost patterns differ across diagnoses, severity levels, and admission types.

### Page 2 — Resource Utilization & Cost Efficiency

This page focuses on the relationship between hospital resource use and inpatient cost.

**Key metrics:**
- Average Length of Stay
- Median Length of Stay
- Average Cost per Day
- 95th Percentile Cost

**Visuals:**
- Total Inpatient Cost vs Length of Stay by Severity
- Average Cost per Day by Severity
- Average Length of Stay by Admission Type

This page helps examine how length of stay and cost vary across different severity and admission categories.

### Page 3 — Hospital Utilization & Patient Analysis

The final page moves from overall cost patterns to facility and patient-level comparisons.

**Visuals:**
- Top 10 Facilities by Average Cost per Day
- Patient Disposition Distribution
- Average Cost per Day by Gender

This page highlights differences in average cost per day across facilities and patient groups, while also showing how inpatient encounters ended through patient disposition.

## Key Findings

A few patterns stood out from the analysis:

### 1. Inpatient spending is highly concentrated by diagnosis

Septicemia was the largest contributor to total inpatient cost, accounting for approximately **$5.81 billion** in the dataset. This was substantially higher than the next-largest diagnosis category.

This suggests that a relatively small number of diagnosis groups can account for a large share of overall inpatient spending and may warrant deeper investigation.

### 2. High-cost admissions increase sharply with severity

The share of admissions classified as high-cost increased substantially with severity of illness. It was approximately **0.56% for Minor severity** compared with **24.1% for Extreme severity**.

This represents a large difference in the likelihood of an admission falling into the high-cost category and highlights severity as an important dimension when examining inpatient costs.

### 3. Emergency admissions account for a large share of inpatient spending

Emergency admissions contributed approximately **$35.78 billion**, or about **66.9% of total inpatient cost** in the dataset.

This makes emergency admissions an important area for understanding inpatient resource utilization and cost concentration.

### 4. Cost per day does not necessarily increase with severity

The analysis showed an important distinction between total cost and cost per day. Average cost per day was not highest for the most severe cases.

This is a useful reminder that different cost metrics can tell different stories. Severity may be strongly associated with high total costs while average daily cost can behave differently because it is influenced by length of stay and the distribution of costs across admissions.

### 5. Facility-level comparisons need to be interpreted carefully

The dashboard shows substantial variation in average cost per day across facilities. However, a higher average cost per day should not automatically be interpreted as inefficiency.

Differences in patient mix, severity, hospital type, and the kinds of cases treated can affect facility-level costs. A more detailed case-mix-adjusted analysis would be needed before making conclusions about relative efficiency.

## Business Implications

The findings point to a few areas that could be explored further from a hospital operations and cost-management perspective:

- **Diagnosis-level cost concentration:** High-cost diagnosis groups such as septicemia could be examined in more detail to understand the underlying resource and care-pathway drivers.
- **Severity and high-cost admissions:** The strong difference in high-cost admission rates across severity levels suggests that severity is an important dimension for cost monitoring and resource planning.
- **Emergency admissions:** Since emergency admissions account for a large share of total inpatient spending, they could be a useful area for further investigation into admission patterns, length of stay, and resource utilization.
- **Facility variation:** Differences in average cost per day across facilities could be investigated further, but meaningful benchmarking would require additional context such as case mix and hospital type.

These findings are intended to identify areas for further investigation rather than prescribe specific operational changes.

## Limitations

There are several limitations to keep in mind when interpreting the analysis:

- The analysis is **descriptive** and does not establish causal relationships.
- Facility-level cost comparisons are not adjusted for case mix, severity, hospital type, or other factors that may influence cost.
- The dataset represents a specific discharge year, so the dashboard does not show how these patterns change over time.
- Average cost per day and total inpatient cost measure different aspects of resource use and should not be interpreted interchangeably.
- Some records contain unknown or missing category values, which may affect certain comparisons.
- The analysis focuses on the variables available in the SPARCS dataset and does not include factors such as detailed clinical outcomes or hospital-specific budget information.

  ## Tools & Technologies

- **Python (Pandas):** Data preparation and exploratory analysis
- **Google Colab:** Python-based data processing
- **Parquet:** Storage of the processed dataset
- **Power BI:** Data modeling, measures, interactive analysis, and dashboard development

  ## Dashboard

The Power BI dashboard is included in the `powerbi` folder, with screenshots of the three pages available in the `images` folder.

The dashboard can be explored through the `.pbix` file in Power BI Desktop. A PDF export is also included for a quick overview without opening Power BI.

## Data Source

This project uses the **New York State SPARCS Hospital Inpatient Discharges (De-Identified)** dataset from the New York State Open Data platform.

The raw dataset is not included in this repository because of its size and data-distribution considerations.

The `data/README.md` file provides the dataset name, source, and instructions for accessing the original data.
