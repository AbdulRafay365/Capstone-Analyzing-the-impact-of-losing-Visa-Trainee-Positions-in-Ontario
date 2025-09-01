# Capstone: Analyzing the impact of losing Visa-Trainee Positions in Ontario
Explored healthcare analytics with real Ontario hospitals and stakeholders, building an analytical solution to assess the impact of gaining or losing visa trainees on patient care and system outcomes.

```mermaid
erDiagram
    DimDate {
        int date_key PK
        date full_date
        int day
        int month
        int year
        string day_name
        string month_name
        boolean is_weekend
    }

    DimRegion {
        int region_key PK
        string region_code
        string region_name
    }

    DimModule {
        int module_key PK
        string module_code
        string module_name
    }

    DimPriority {
        int priority_key PK
        string priority_level
        int target_first_response_hrs
        int target_resolution_hrs
    }

    DimProcessor {
        int processor_key PK
        string processor_name
        int region_key FK
    }

    FactSupportCases {
        int case_id
        int created_date_key FK
        int resolved_date_key FK
        int region_key FK
        int module_key FK
        int priority_key FK
        int processor_key FK
        int resolution_hrs
        int first_response_hrs
        int processor_changes
        boolean escalated_flag
        boolean reopen_flag
        boolean first_response_met_flag
        boolean sla_met_flag
        int csat_score
        int ces_score
    }

    DimDate ||--o{ FactSupportCases : created_date
    DimDate ||--o{ FactSupportCases : resolved_date
    DimRegion ||--o{ FactSupportCases : region
    DimModule ||--o{ FactSupportCases : module
    DimPriority ||--o{ FactSupportCases : priority
    DimProcessor ||--o{ FactSupportCases : processor
    DimRegion ||--o{ DimProcessor : region
```
