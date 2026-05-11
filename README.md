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

| Reference | Description |
|-----------|-------------|
| `CARE_SUMMARY` | Aggregated care metrics by facility, year, month |
| `KPI_OVERVIEW` | Executive KPIs — admissions, CMI, LOS, readmission, mortality |
| `OUTCOME_TRENDS` | Outcome metrics by diagnosis over time |
| `PROVIDER_PERFORMANCE` | Provider-level metrics and patient load |
| `UTILIZATION_TRENDS` | Bed occupancy and utilization by department |
| `ICU_UTILIZATION` | ICU-specific occupancy rates |
| `AI_INSIGHTS` | Anomaly detection results by facility and month |
| `LOS_DISTRIBUTION` | Length of stay classification distribution |
| `DIAGNOSIS_CASE_MIX` | Case mix by diagnosis category |
| `CHRONIC_DISEASE_ANALYSIS` | Chronic condition analytics |
| `PAYER_ANALYSIS` | Insurance/payer mix analytics |
| `CARE_FLOW` | Patient journey and episode data |
| `COHORT_BASE` | Patient-level cohort data |

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
