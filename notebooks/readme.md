# 🐍 Python ETL Pipeline: GA4 Data Extraction & Processing

This directory contains the Python Jupyter Notebooks responsible for the **Extract, Transform, and Load (ETL)** phases of the Multi-Property GA4 Analytics project. 

The pipeline extracts raw data from the Google Analytics 4 Data API, handles complex JSON responses, performs feature engineering, and exports a clean, analysis-ready CSV file for Power BI ingestion.

## 📂 Directory Contents
* `1_data_download.ipynb`: Extraction script interacting with the GA4 API.
* `2_data_processing.ipynb`: Transformation script utilizing Pandas and NumPy.
* `requirements.txt`: Python dependencies required to run the notebooks.

---

## 📓 Notebook 1: GA4 Data Extraction for Multiple Websites

**Goal:**
This notebook automates the process of fetching key performance metrics from the Google Analytics 4 (GA4) Data API for a list of specified websites.

**Process:**
1. **Authentication:** Securely connects to the Google Analytics API using a service account.
2. **Configuration:** Loads a list of website property IDs from an external JSON file.
3. **Data Fetching:** Iterates through each website ID, sending a request to the API for a predefined set of dimensions and metrics within a specified date range.
4. **Output:** For each website, the raw data is processed from the API response object into a clean list of dictionaries and saved as a separate JSON file in a designated output directory.

**Final Output:** A collection of JSON files, each named after its corresponding website, containing the raw analytics data.

---

## 📓 Notebook 2: Data Processing and Preparation for Power BI

**Goal:**
The purpose of this notebook is to process the raw JSON files downloaded from the Google Analytics API. The script transforms the raw data into a single, clean, and analysis-ready dataset suitable for visualization in Power BI.

**Process:**
The notebook performs the following key steps in the Transform and Load stages of an ETL process:

1. **Load Data:** Iterates through all JSON files.
2. **Initial Transformation:** For each file, the script:
   * Creates a pandas DataFrame.
   * Renames columns (converting from API `camelCase` to database-standard `snake_case`).
   * Converts all columns to their appropriate data types (e.g., casting time durations to floats).
3. **Feature Engineering:**
   * Creates a primary `date` column (datetime type) from the original `year` and `month` columns.
   * Calculates two new key performance indicators (KPIs) using safe array division to handle zero-denominators:
     * `engagement_rate`: To measure the quality of user sessions.
     * `new_users_ratio`: To measure audience growth.
4. **Data Aggregation:**
   * Extracts the source website name from each filename using Regular Expressions and adds it as a `website` column.
   * Combines all the individual DataFrames into a single DataFrame.
5. **Final Output:**
   * Saves the master dataset as a CSV file.