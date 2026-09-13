# Power BI Dashboard Guide — Hepatitis C Clinical Data

## Dashboard title
**Hepatitis C Clinical Laboratory Analysis**

> Use this project for descriptive analytics and portfolio demonstration. Do not present the dashboard as a diagnostic system.

## Power Query cleaning

1. Import the `HepatitisCdata` worksheet from the Excel workbook.
2. Rename `Column1` to `Record_ID`.
3. Set data types:
   - Record_ID: Whole Number
   - Category: Text
   - Age: Whole Number
   - Sex: Text
   - ALB, ALP, ALT, AST, BIL, CHE, CHOL, CREA, GGT, PROT: Decimal Number
4. Check duplicates using `Record_ID` and full-row duplicate checks.
5. Keep missing lab values as null. Do **not** replace missing lab values with zero.
6. Split `Category` at `=`:
   - Category Code
   - Category Label
7. Replace `m` with `Male` and `f` with `Female` in a new Sex Label field.
8. Create Disease Status:
   - Hepatitis, Fibrosis, Cirrhosis → Disease
   - Blood Donor and suspect Blood Donor → Non-disease
9. Create Age Group:
   - <30
   - 30–39
   - 40–49
   - 50–59
   - 60–69
   - 70+

## Recommended report pages

### Page 1 — Executive Overview

KPI cards:
- Total Records
- Blood Donor Records
- Disease Records
- Average Age
- Male %
- Female %
- Missing Lab Values

Visuals:
- Bar chart: Records by Clinical Category
- Doughnut chart: Sex Distribution
- Column chart: Disease Records by Age Group
- Table: Category, Records, Average Age, % of Total

Slicers:
- Category Label
- Sex Label
- Age Group
- Disease Status

### Page 2 — Laboratory Profile

Visuals:
- Clustered bar: Average AST by Category
- Clustered bar: Average GGT by Category
- Clustered bar: Average BIL by Category
- Clustered bar: Average ALB by Category
- Matrix: Category × Average Lab Values
- Scatter: AST vs GGT, legend by Category

### Page 3 — Disease vs Non-Disease

Visuals:
- Clustered columns: Disease vs Non-disease average AST, GGT, BIL
- Bar: Disease Rate by Sex
- Bar: Disease Records by Age Group
- Table: Disease Status, Avg ALB, Avg AST, Avg BIL, Avg GGT, Avg CREA
- Scatter: BIL vs AST with Category legend

### Page 4 — Data Quality

Visuals:
- KPI: Missing Values
- Bar: Missing Values by Laboratory Field
- Category imbalance chart
- Data-quality notes text box

## DAX measures

```DAX
Total Records =
COUNTROWS('HepatitisC')

Average Age =
AVERAGE('HepatitisC'[Age])

Male Records =
CALCULATE(
    [Total Records],
    'HepatitisC'[Sex Label] = "Male"
)

Female Records =
CALCULATE(
    [Total Records],
    'HepatitisC'[Sex Label] = "Female"
)

Male % =
DIVIDE([Male Records], [Total Records], 0)

Female % =
DIVIDE([Female Records], [Total Records], 0)

Disease Records =
CALCULATE(
    [Total Records],
    'HepatitisC'[Disease Status] = "Disease"
)

Non-Disease Records =
CALCULATE(
    [Total Records],
    'HepatitisC'[Disease Status] = "Non-disease"
)

Disease Record % =
DIVIDE([Disease Records], [Total Records], 0)

Average AST =
AVERAGE('HepatitisC'[AST])

Average GGT =
AVERAGE('HepatitisC'[GGT])

Average BIL =
AVERAGE('HepatitisC'[BIL])

Average ALB =
AVERAGE('HepatitisC'[ALB])

Average ALT =
AVERAGE('HepatitisC'[ALT])

Average CREA =
AVERAGE('HepatitisC'[CREA])

Average CHOL =
AVERAGE('HepatitisC'[CHOL])

Missing ALP =
CALCULATE(
    COUNTROWS('HepatitisC'),
    ISBLANK('HepatitisC'[ALP])
)

Missing CHOL =
CALCULATE(
    COUNTROWS('HepatitisC'),
    ISBLANK('HepatitisC'[CHOL])
)
```

## Calculated column: Disease Status

```DAX
Disease Status =
IF(
    'HepatitisC'[Category Label] IN {"Hepatitis", "Fibrosis", "Cirrhosis"},
    "Disease",
    "Non-disease"
)
```

## Calculated column: Sex Label

```DAX
Sex Label =
SWITCH(
    'HepatitisC'[Sex],
    "m", "Male",
    "f", "Female",
    'HepatitisC'[Sex]
)
```

## Calculated column: Age Group

```DAX
Age Group =
SWITCH(
    TRUE(),
    'HepatitisC'[Age] < 30, "<30",
    'HepatitisC'[Age] < 40, "30-39",
    'HepatitisC'[Age] < 50, "40-49",
    'HepatitisC'[Age] < 60, "50-59",
    'HepatitisC'[Age] < 70, "60-69",
    "70+"
)
```

## Portfolio questions the dashboard should answer

1. How are records distributed across the clinical categories?
2. Which laboratory markers differ most across Blood Donor, Hepatitis, Fibrosis and Cirrhosis categories?
3. How do AST, GGT and bilirubin behave across disease stages?
4. How do disease records vary by age and sex in this sample?
5. Where are missing values concentrated?
6. Which laboratory variables move together?

## Important interpretation note

This dataset can demonstrate analytical and visualization skills, but Power BI findings should be described as patterns or associations in the sample. Avoid statements such as “AST diagnoses cirrhosis” or “men are more likely to develop hepatitis” because this dataset alone cannot establish diagnostic validity, population risk, or causation.
