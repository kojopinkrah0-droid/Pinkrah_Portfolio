Air Quality & Public Health Impact Analysis

 Project Overview
This portfolio project analyzes 88,489 air-quality and health observations across 8 cities using Python and Power BI. The objective is to explore pollution patterns, quantify relationships between pollutants and hospital admissions, and communicate findings through a business-style dashboard.

 Tools
- Python: pandas, NumPy, Matplotlib
- Power BI: Power Query, DAX, interactive visuals
- GitHub: version control and project documentation

 Dataset Fields
`city`, `date`, `aqi`, `pm2_5`, `pm10`, `no2`, `o3`, `temperature`, `humidity`, `hospital_admissions`, `population_density`, `hospital_capacity`

 Data Quality
- Rows: 88,489
- Cities: 8
- Missing values: 0
- Duplicate rows: 0
- Date range: 2020-01-01 to 2262-04-10

> Data caveat: The unusually long date range suggests this may be a synthetic or simulated dataset. Results are appropriate for demonstrating analytical skills, but should not be presented as causal or verified epidemiological evidence without validating the original source.

 Key Findings
1. PM2.5 is the strongest observed pollution-related predictor of hospital admissions, with a Pearson correlation of approximately 0.39.
2. Average hospital admissions increase from approximately 6.23 in the lowest PM2.5 quartile to 9.91 in the highest quartile.
3. The dataset's overall AQI field has almost zero linear correlation with hospital admissions, making pollutant-level analysis more informative.
4. City-average AQI values are broadly high and close together; Los Angeles has the highest average AQI in this dataset at about 253.07, while Tokyo is lowest among the eight at about 247.56.
5. Population-density groups have very similar average admission counts in this dataset, suggesting density alone is not a strong discriminator of the generated health outcome.

Suggested Repository Structure
text
air-quality-health-portfolio/
├── README.md
├── data/
│   └── air_quality_health_dataset.csv
├── notebooks/
│   └── air_quality_analysis.ipynb
├── src/
│   └── air_quality_analysis.py
├── outputs/
│   ├── city_summary.csv
│   ├── correlation_matrix.csv
│   └── charts/
└── powerbi/
    ├── POWER_BI_GUIDE.md
    └── air_quality_health_dashboard.pbix   # create in Power BI Desktop


 Analysis Workflow
1. Load and inspect the dataset.
2. Validate missing values, duplicates and data types.
3. Convert the date field and engineer date-related features.
4. Create AQI categories and a hospital-capacity-utilization metric.
5. Produce descriptive city and pollutant summaries.
6. Examine correlations with hospital admissions.
7. Compare admissions across PM2.5 quartiles.
8. Build Python visualizations.
9. Reproduce the core analysis as an interactive Power BI dashboard.
10. Document limitations and business/public-health implications.

Visualizations
Recommended portfolio visuals:
- Average AQI by City
- Average Hospital Admissions by City
- PM2.5 vs Hospital Admissions scatter plot
- Hospital Admissions by PM2.5 Quartile
- AQI Category Distribution
- Monthly PM2.5 Pattern
- Power BI executive dashboard

 Business / Public-Health Interpretation
The clearest analytical signal is the positive relationship between PM2.5 and hospital admissions. In this dataset, higher fine-particulate exposure is associated with higher admission counts. This supports prioritizing pollutant-specific monitoring rather than relying only on a composite AQI measure.

However, this is an association, not proof of causation. A real epidemiological study would need additional controls such as age distribution, pre-existing conditions, socioeconomic status, seasonality, healthcare access, and verified exposure measurements.

How to Run
```bash
pip install pandas numpy matplotlib
python src/air_quality_analysis.py
```

For the notebook:
```bash
jupyter notebook notebooks/air_quality_analysis.ipynb
```

Power BI
Follow `POWER_BI_GUIDE.md` to build three dashboard pages:
1. Executive Overview
2. Pollution & Health Relationship
3. City & Capacity Analysis

GitHub Portfolio Tips
- Add a screenshot of the final Power BI dashboard near the top of this README.
- Keep the notebook clean and well-commented.
- Add a short “What I learned” section after building the dashboard.
- Use a descriptive repository name such as `air-quality-health-analysis`.
- Pin the repository on your GitHub profile.

