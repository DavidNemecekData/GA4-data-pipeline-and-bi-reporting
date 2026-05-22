# Data Directory: Processed GA4 Analytics Datasets

This directory contains the final, transformed datasets responsible for powering the Power BI dashboard.
All datasets in this directory are 100% analysis-ready and formatted for direct, seamless ingestion into Power BI.

## Directory Contents
* `2023.csv`
* `2024.csv`
* `2025.csv`

---

## Dataset Specifications & Structure

Every CSV file in this directory has undergone rigorous transformation via the Python ETL pipeline (`2_data_processing.ipynb`) and adheres to the following data standards:

1. **Unified Schema:** Multi-property web analytics data merged into a single, cohesive tabular format.
2. **Database-Standard Naming:** All column headers are converted from API `camelCase` to clean, database-ready `snake_case`
3. **Optimized Data Types:** Strict type casting has been applied (e.g., primary `date` column as datetime, durations as floats) to eliminate data type errors during Power BI import.

---

**Data Anonymization Notice:** To ensure confidentiality and protect sensitive business assets, all data contained within these annual CSV files has been altered and randomized for portfolio demonstration purposes. The numbers, trends, and specific website identifiers do not reflect actual real-world web traffic.*