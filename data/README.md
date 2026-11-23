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

## Source cycle

NHANES 2017–2018 (9,254 participants; respondent sequence numbers from 93703). Of these, 5,856 are adults aged 18 or over and are used in the analysis.

## Outcome definition

`CVD` is a composite, self-reported outcome taken from the NHANES 2017–2018 Medical Conditions questionnaire (`MCQ_J`). A participant is coded **CVD = 1** if they answered **"Yes"** to *any* of the following questions:

| NHANES item | Question: "Has a doctor or other health professional ever told you that you had…" |
|---|---|
| `MCQ160C` | coronary heart disease |
| `MCQ160E` | a heart attack (myocardial infarction) |
| `MCQ160F` | a stroke |

All other participants are coded **CVD = 0**, including those who answered "No", "Refused" (7) or "Don't know" (9), and those not asked the questions.

**Notes**
- Congestive heart failure (`MCQ160B`) and angina (`MCQ160D`) are **not** included in this definition.
- The outcome is **self-reported** physician diagnosis, so it is subject to recall and under-diagnosis bias.
- NHANES asks the `MCQ160` items only of participants aged **20 and over**. Participants aged 18–19 are therefore always coded CVD = 0. Very few people that age have CVD, so the effect on the results is negligible.
