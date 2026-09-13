# Hepatitis C Clinical Data Analysis — Python & Power BI

## Project Overview

This portfolio project analyzes a Hepatitis C laboratory dataset containing **615 records**. It combines **Python exploratory data analysis** with a proposed **Power BI dashboard** to examine demographic patterns, clinical categories, laboratory profiles, missing data and relationships among laboratory markers.

> **Disclaimer:** This is a data-analysis portfolio project, not a medical diagnostic application.

## Tools

- Python
- pandas
- NumPy
- Matplotlib
- Jupyter Notebook
- Power BI
- Power Query
- DAX
- GitHub

## Dataset

The dataset contains:

- Record ID
- Clinical Category
- Age
- Sex
- ALB — Albumin
- ALP — Alkaline phosphatase
- ALT — Alanine aminotransferase
- AST — Aspartate aminotransferase
- BIL — Bilirubin
- CHE — Cholinesterase
- CHOL — Cholesterol
- CREA — Creatinine
- GGT — Gamma-glutamyl transferase
- PROT — Total protein

## Data Quality

- **615 records**
- **0 duplicate rows**
- Missing values:
  - ALB: 1
  - ALP: 18
  - ALT: 1
  - CHOL: 10
  - PROT: 1
- The dataset is highly class-imbalanced.

### Category distribution

| Category | Records |
|---|---:|
| Blood Donor | 533 |
| Cirrhosis | 30 |
| Hepatitis | 24 |
| Fibrosis | 21 |
| suspect Blood Donor | 7 |

## Key Findings

1. Blood Donors dominate the dataset, representing most of the 615 observations. This class imbalance should be considered when interpreting percentages or building predictive models.
2. **AST, GGT and bilirubin (BIL)** show the largest standardized differences between disease and non-disease records.
3. Cirrhosis records have markedly higher average AST and GGT than Blood Donor records in this sample.
4. Average creatinine is also substantially higher in the Cirrhosis group, while average albumin and cholesterol are lower.
5. Disease records represent **75 of 615 observations** when Hepatitis, Fibrosis and Cirrhosis are grouped together.
6. Male records have a disease-record proportion of about **14.06%**, compared with **9.24%** for female records in this sample. This is descriptive only and should not be interpreted as population-level disease risk.
7. Missing laboratory measurements should remain null during descriptive analysis rather than being replaced with zero.

## Selected Category-Level Means

- Blood Donor average AST: approximately **26.55**
- Hepatitis average AST: approximately **75.73**
- Fibrosis average AST: approximately **81.17**
- Cirrhosis average AST: approximately **107.46**

- Blood Donor average GGT: approximately **29.04**
- Hepatitis average GGT: approximately **92.58**
- Fibrosis average GGT: approximately **79.55**
- Cirrhosis average GGT: approximately **129.44**

These values describe this dataset only and are not proposed clinical thresholds.

## Repository Structure

```text
hepatitis-c-analysis/
├── README.md
├── requirements.txt
├── data/
│   └── HepatitisCdata.xlsx
├── notebooks/
│   └── hepatitis_c_analysis.ipynb
├── src/
│   └── hepatitis_c_analysis.py
├── outputs/
│   ├── category_distribution.csv
│   ├── missing_values_summary.csv
│   ├── correlation_matrix.csv
│   ├── lab_means_by_category.csv
│   └── charts/
└── powerbi/
    ├── POWER_BI_GUIDE.md
    └── hepatitis_c_dashboard.pbix
```

## Analysis Workflow

1. Import the Excel dataset.
2. Inspect dimensions, data types, duplicates and missing values.
3. Extract clean clinical category labels.
4. Create Sex Label, Disease Status and Age Group features.
5. Analyze class distribution.
6. Compare laboratory means across clinical categories.
7. Analyze disease vs non-disease laboratory profiles.
8. Explore correlations among laboratory variables.
9. Visualize AST, GGT, category distributions and demographic patterns.
10. Recreate the insights in an interactive Power BI report.
11. Document limitations and avoid causal/diagnostic claims.

## Recommended Visualizations

- Clinical Category Distribution
- Age Distribution by Category
- Average AST by Category
- Average GGT by Category
- Disease Record Rate by Sex
- AST vs GGT Scatter Plot
- Laboratory Correlation Matrix
- Power BI Executive Dashboard

## Power BI Pages

1. Executive Overview
2. Laboratory Profile
3. Disease vs Non-Disease
4. Data Quality

See `POWER_BI_GUIDE.md` for Power Query steps, DAX measures and visual recommendations.

## Run the Python Project

```bash
pip install pandas numpy matplotlib openpyxl jupyter
python src/hepatitis_c_analysis.py
```

Or run the Jupyter notebook:

```bash
jupyter notebook notebooks/hepatitis_c_analysis.ipynb
```

## Portfolio Discussion

The strongest value of this project is not simply showing charts. It demonstrates:

- Data-quality assessment
- Responsible treatment of missing clinical values
- Feature engineering
- Descriptive statistics
- Group comparison
- Correlation analysis
- Responsible interpretation of clinical data
- Python visualization
- Power BI dashboard planning
- Clear documentation for GitHub

## Limitations

- The dataset is strongly imbalanced toward Blood Donors.
- Sample-level patterns do not necessarily represent population-level risk.
- Correlation does not establish causation.
- Laboratory patterns should not be used as diagnostic thresholds.
- Additional information such as medical history, treatment status and sampling methodology would be required for clinical interpretation.
