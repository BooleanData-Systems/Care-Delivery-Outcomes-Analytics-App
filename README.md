# Care Delivery & Outcomes Analytics

## Overview

The **Care Delivery & Outcomes Analytics** accelerator is a comprehensive hospital performance intelligence platform that enables healthcare operations teams to monitor, benchmark, and optimize care delivery across admissions, outcomes, utilization, and provider performance.

Built on Snowflake with Cortex AI, this accelerator provides real-time clinical KPIs, readmission analytics, capacity planning, and intelligent anomaly detection — all within your Snowflake environment.

## Key Features

- **Executive Overview** — Hospital-wide KPIs: admissions, CMI, LOS, mortality, recovery, readmission, bed occupancy, ICU utilization
- **Care Flow** — Patient journey tracking with episode sequencing, discharge disposition, and avoidable readmission detection
- **Length of Stay** — LOS trends, classification distribution, facility/diagnosis benchmarking
- **Readmission & Outcomes** — 30-day readmission rates, avoidable readmission analysis, facility comparison
- **Provider Performance** — Specialty-level metrics, provider rankings, patient load analysis
- **Capacity & Utilization** — Bed occupancy trends, ICU monitoring, department-level capacity planning
- **Clinical Intelligence** — Case mix analysis, chronic disease management, diagnosis-level mortality
- **Payer & Cohort** — Insurance mix analytics and custom cohort builder
- **AI Agent** — Natural language Q&A powered by Snowflake Cortex for care delivery insights

## Required Views

After installation, bind the following 13 views via the app's configuration page:

### `CARE_SUMMARY` — Aggregated Care Metrics
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| FACILITY_NAME | VARCHAR | Hospital/facility name | Metro General Hospital |
| YEAR | INTEGER | Calendar year | 2024 |
| QUARTER | INTEGER | Calendar quarter (1–4) | 2 |
| YEAR_MONTH | VARCHAR | Year-month period | 2024-04 |
| TOTAL_ADMISSIONS | INTEGER | Total patient admissions | 285 |
| AVG_LOS | NUMBER(5,2) | Average length of stay (days) | 6.42 |
| READMISSION_RATE | NUMBER(5,2) | 30-day readmission rate (%) | 14.8 |
| READMISSIONS | INTEGER | Total readmission count | 42 |
| AVOIDABLE_READMISSIONS | INTEGER | Avoidable readmission count | 12 |
| AVG_DISCHARGE_DELAY_HOURS | NUMBER(5,1) | Average discharge delay (hours) | 18.5 |

### `KPI_OVERVIEW` — Executive KPIs
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| FACILITY_NAME | VARCHAR | Hospital/facility name | Riverside Medical Center |
| YEAR | INTEGER | Calendar year | 2024 |
| YEAR_MONTH | VARCHAR | Year-month period | 2024-06 |
| TOTAL_ADMISSIONS | INTEGER | Monthly admissions | 342 |
| CASE_MIX_INDEX | NUMBER(4,2) | Case mix index (severity) | 1.85 |
| AVG_LOS | NUMBER(5,2) | Average length of stay (days) | 5.73 |
| KPI_READMISSION_RATE | NUMBER(5,2) | 30-day readmission rate (%) | 13.2 |
| KPI_AVOIDABLE_READMIT_RATE | NUMBER(5,2) | Avoidable readmission rate (%) | 28.5 |
| KPI_MORTALITY_RATE | NUMBER(4,2) | In-hospital mortality rate (%) | 2.1 |
| KPI_RECOVERY_RATE | NUMBER(5,2) | Patient recovery rate (%) | 89.4 |
| KPI_DISCHARGE_DELAY | NUMBER(5,1) | Average discharge delay (hours) | 14.2 |

### `OUTCOME_TRENDS` — Outcomes by Diagnosis Over Time
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| DIAGNOSIS_DESCRIPTION | VARCHAR | Diagnosis name | Congestive Heart Failure |
| YEAR | INTEGER | Calendar year | 2024 |
| YEAR_MONTH | VARCHAR | Year-month period | 2024-07 |
| AVG_LOS | NUMBER(5,2) | Average length of stay (days) | 8.24 |
| READMISSION_RATE | NUMBER(5,2) | 30-day readmission rate (%) | 18.6 |
| MORTALITY_RATE | NUMBER(4,2) | Mortality rate (%) | 3.2 |

### `PROVIDER_PERFORMANCE` — Provider-Level Metrics
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| PROVIDER_NAME | VARCHAR | Provider/physician name | Dr. Sarah Chen |
| SPECIALTY | VARCHAR | Medical specialty | Cardiology |
| DEPARTMENT | VARCHAR | Department name | Cardiac Care |
| FACILITY_NAME | VARCHAR | Hospital/facility name | Metro General Hospital |
| YEAR | INTEGER | Calendar year | 2024 |
| PATIENT_LOAD | INTEGER | Annual patient count | 142 |
| AVG_LOS | NUMBER(5,2) | Average length of stay (days) | 5.8 |
| AVG_CMI | NUMBER(4,2) | Average case mix index | 1.92 |
| READMISSION_RATE | NUMBER(5,2) | 30-day readmission rate (%) | 11.4 |
| RECOVERY_RATE | NUMBER(5,2) | Patient recovery rate (%) | 91.3 |
| MORTALITY_COUNT | INTEGER | Mortality count | 3 |
| AVG_DISCHARGE_DELAY | NUMBER(5,1) | Average discharge delay (hours) | 12.5 |

### `UTILIZATION_TRENDS` — Bed Occupancy by Department
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| FACILITY_NAME | VARCHAR | Hospital/facility name | Summit Health System |
| DEPARTMENT | VARCHAR | Department name | General Medicine |
| YEAR | INTEGER | Calendar year | 2024 |
| YEAR_MONTH | VARCHAR | Year-month period | 2024-01 |
| KPI_BED_OCCUPANCY_RATE | NUMBER(5,2) | Bed occupancy rate (%) | 82.4 |

### `ICU_UTILIZATION` — ICU Occupancy Rates
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| FACILITY_NAME | VARCHAR | Hospital/facility name | Metro General Hospital |
| YEAR | INTEGER | Calendar year | 2024 |
| YEAR_MONTH | VARCHAR | Year-month period | 2024-03 |
| ICU_OCCUPANCY_RATE | NUMBER(5,1) | ICU bed occupancy rate (%) | 78.5 |

### `AI_INSIGHTS` — Anomaly Detection Results
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| FACILITY_NAME | VARCHAR | Hospital/facility name | Riverside Medical Center |
| YEAR_MONTH | VARCHAR | Year-month period | 2024-09 |
| ADMISSION_ANOMALY_DETAIL | VARCHAR | Admission volume anomaly | Spike detected: +28% above mean |
| READMISSION_ANOMALY_DETAIL | VARCHAR | Readmission rate anomaly | Elevated: 22.1% vs 15.6% benchmark |
| LOS_ANOMALY_DETAIL | VARCHAR | Length of stay anomaly | Extended: 9.2d vs 4.7d benchmark |

### `LOS_DISTRIBUTION` — Length of Stay Classification
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| FACILITY_NAME | VARCHAR | Hospital/facility name | Metro General Hospital |
| YEAR | INTEGER | Calendar year | 2024 |
| LOS_CLASSIFICATION | VARCHAR | LOS category | Short Stay (1-3d) |
| ADMISSION_COUNT | INTEGER | Admissions in this LOS band | 185 |

### `DIAGNOSIS_CASE_MIX` — Case Mix by Diagnosis
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| DIAGNOSIS_DESCRIPTION | VARCHAR | Diagnosis name | Acute Myocardial Infarction |
| DIAGNOSIS_CATEGORY | VARCHAR | Clinical category | Cardiovascular |
| ADMISSION_TYPE | VARCHAR | Admission type | Emergency |
| PRIORITY_LEVEL | VARCHAR | Clinical priority | Critical |
| FACILITY_NAME | VARCHAR | Hospital/facility name | Metro General Hospital |
| YEAR | INTEGER | Calendar year | 2024 |
| CASE_COUNT | INTEGER | Number of cases | 87 |
| AVG_CMI | NUMBER(4,2) | Average case mix index | 2.15 |
| MORTALITY_RATE | NUMBER(5,2) | Mortality rate (%) | 4.2 |
| READMISSION_RATE | NUMBER(5,2) | 30-day readmission rate (%) | 16.8 |

### `CHRONIC_DISEASE_ANALYSIS` — Chronic Condition Analytics
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| DIAGNOSIS_DESCRIPTION | VARCHAR | Chronic condition name | Congestive Heart Failure |
| FACILITY_NAME | VARCHAR | Hospital/facility name | Summit Health System |
| YEAR | INTEGER | Calendar year | 2024 |
| CASE_COUNT | INTEGER | Number of cases | 95 |
| AVG_LOS | NUMBER(5,2) | Average length of stay (days) | 9.8 |
| READMISSION_RATE | NUMBER(5,2) | 30-day readmission rate (%) | 24.3 |

### `PAYER_ANALYSIS` — Insurance/Payer Mix Analytics
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| INSURANCE_TYPE | VARCHAR | Insurance/payer type | Medicare |
| FACILITY_NAME | VARCHAR | Hospital/facility name | Metro General Hospital |
| YEAR | INTEGER | Calendar year | 2024 |
| ADMISSION_COUNT | INTEGER | Admissions for this payer | 215 |
| AVG_LOS | NUMBER(5,2) | Average length of stay (days) | 7.2 |
| READMISSION_RATE | NUMBER(5,2) | 30-day readmission rate (%) | 16.1 |

### `CARE_FLOW` — Patient Journey & Episode Data
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| EPISODE_ID | VARCHAR | Unique episode identifier | EP-000142 |
| PATIENT_ID | VARCHAR | Patient identifier | PAT-00085 |
| FACILITY_NAME | VARCHAR | Hospital/facility name | Metro General Hospital |
| DIAGNOSIS_DESCRIPTION | VARCHAR | Primary diagnosis | Pneumonia |
| ADMISSION_TYPE | VARCHAR | Admission type | Emergency |
| YEAR | INTEGER | Calendar year | 2024 |
| YEAR_MONTH | VARCHAR | Year-month period | 2024-04 |
| DISCHARGE_STATUS | VARCHAR | Discharge status | Recovered |
| DISCHARGE_DISPOSITION | VARCHAR | Discharge destination | Home |
| LENGTH_OF_STAY_DAYS | INTEGER | Length of stay (days) | 6 |
| ENCOUNTER_SEQ | INTEGER | Episode sequence number | 1 |
| IS_INDEX_ADMISSION | BOOLEAN | Whether this is an index admission | TRUE |
| IS_30_DAY_READMISSION | BOOLEAN | Whether readmitted within 30 days | FALSE |
| IS_AVOIDABLE_READMISSION | BOOLEAN | Whether readmission was avoidable | FALSE |

### `COHORT_BASE` — Patient-Level Cohort Data
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| PATIENT_ID | VARCHAR | Patient identifier | PAT-00142 |
| FACILITY_NAME | VARCHAR | Hospital/facility name | Valley Community Hospital |
| DIAGNOSIS_CATEGORY | VARCHAR | Clinical category | Cardiovascular |
| INSURANCE_TYPE | VARCHAR | Insurance/payer type | Medicare |
| IS_CHRONIC | BOOLEAN | Whether patient has chronic condition | TRUE |
| PRIORITY_LEVEL | VARCHAR | Clinical priority | High |
| ADMISSION_COUNT | INTEGER | Total admission count | 3 |
| AVG_LOS | NUMBER(4,1) | Average length of stay (days) | 7.2 |
| AVG_CMI | NUMBER(4,2) | Average case mix index | 1.85 |
| READMISSIONS | INTEGER | Readmission count | 1 |
| AVOIDABLE_READMISSIONS | INTEGER | Avoidable readmission count | 0 |

## Installation Steps

1. **Install the app** from the Marketplace listing
2. **Grant privileges** — Grant the `SNOWFLAKE.CORTEX_USER` database role to the app for AI Agent (optional)
3. **Bind your views** — Navigate to the app configuration page and map each of the 13 required views to your existing data
4. **Launch the dashboard** — Open the Streamlit app from the installed application

## Clinical Benchmarks

The app includes built-in benchmarks:
- **AHRQ LOS Benchmark:** 4.7 days
- **CMS Readmission Benchmark:** 15.6%
- **National Mortality Avg:** 2.3%
- **CMS Bed Occupancy Benchmark:** 75%
- **ICU Target:** 70–80%

## Architecture

```
Application Package
├── manifest.yml          — App metadata, version, references
├── scripts/
│   └── setup.sql         — Creates schemas, views, Streamlit app
├── streamlit/
│   ├── streamlit_app.py  — Main dashboard application
│   └── environment.yml   — Python dependencies
└── readme.md             — This file
```

## Cortex AI (Optional)

The AI Agent tab uses Snowflake Cortex (mistral-large2, llama3.1-70b) for natural language analysis. This feature works automatically in regions where Cortex is available. If Cortex is not available in your region, all other tabs function normally.

## Support

For issues or feature requests, contact the provider through the Marketplace listing page.
