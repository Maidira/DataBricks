
# NYC Taxi Data Pipeline: Medallion Architecture

An end to  end Data Engineering pipeline built on **Databricks** using **PySpark** and **Delta Lake**. This project processes millions of records from the NYC Taxi & Limousine Commission dataset, transforming raw, messy CSV data into business-ready insights.

## Architecture Overview
This project follows the **Medallion Architecture**, which organizes data into three distinct layers to ensure quality and reliability:

1.  **Bronze (Raw):** Ingests raw compressed CSV files from DBFS. Includes custom schema definition to handle historical data variations.
2.  **Silver (Cleaned):** Data cleaning and transformation. Handles null values, filters out "junk" records (0 distance/fare), and performs feature engineering.
3.  **Gold (Business):** High level aggregations designed for BI reporting. Focuses on vendor performance, revenue trends, and average trip metrics.

---

## Tech Stack
*   **Language:** Python (PySpark)
*   **Processing Engine:** Apache Spark (Databricks Serverless)
*   **Storage:** Delta Lake (ACID Transactions, Schema Enforcement, Time Travel)


---

## Pipeline Visualization
The pipeline is orchestrated as a multi task job. Each stage depends on the successful completion of the previous layer, ensuring data integrity.


---

## Key Features & Logic
*   **Schema Enforcement:** Manually defined `StructType` schemas to prevent data corruption from evolving CSV headers.
*   **Data Quality Monitoring:** Programmatic NULL count checks across all columns using Spark list comprehensions.
*   **Performance Optimization:** Utilizes the **Delta** format for 10x-100x faster query performance compared to raw CSVs.


---

## Insights Produced
The final **Gold Table** provides instant answers to business questions such as:
*   Daily Revenue?
*   Dail trips count?
*   Payment Type Analysis?
*   Identification of "junk" data trends in raw source files.
