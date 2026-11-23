# Data

The prepared dataset `NHANES_FINAL_DATASET.csv` is **not included** in this repository. Place it in this folder before running the notebook.

NHANES is publicly available from the U.S. CDC / National Center for Health Statistics: <https://www.cdc.gov/nchs/nhanes/>

## Expected columns

| Column | Type | Notes |
|---|---|---|
| `Participant_ID` | ID | NHANES respondent sequence number (excluded from modelling) |
| `CVD` | 0/1 | **Target**: 1 = cardiovascular disease, 0 = none (no missing values) |
| `Age` | numeric | Years; the analysis keeps participants aged 18 and over |
| `Gender` | coded | Treated as categorical |
| `Race_Ethnicity` | coded | Treated as categorical |
| `Education_Level` | coded | Treated as categorical |
| `Diabetes_Status` | coded | Treated as categorical |
| `Smoking_Status` | coded | Treated as categorical |
| `BMI` | numeric | kg/m² |
| `Average_Systolic_BP` | numeric | mmHg |
| `Average_Diastolic_BP` | numeric | mmHg |
| `Total_Cholesterol` | numeric | mg/dL |
| `HDL_Cholesterol` | numeric | mg/dL |
| `HbA1c` | numeric | % |

Other numeric columns are used as predictors automatically. Columns with more than 50% missing values in the training set are dropped.

## Outcome definition

<!-- TODO: describe how CVD was derived, e.g. which NHANES cycles and which MCQ questionnaire items
     (coronary heart disease, angina, heart attack, stroke, congestive heart failure) were combined. -->
