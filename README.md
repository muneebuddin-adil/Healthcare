# Healthcare Data Pipeline Project

## Project Overview
This project focuses on building a data pipeline using Azure services to automate the ingestion, transformation, and analysis of a healthcare dataset. The dataset contains 55,500 rows with 15 columns, including patient demographics, medical conditions, hospital admission details, and billing information. The goal is to clean and transform the data, extract insights, and create visualizations using Power BI.

## Dataset
The dataset was sourced from Kaggle and includes the following columns:
- `Name`, `Age`, `Gender`, `Blood Type`, `Medical Condition`
- `Date of Admission`, `Doctor`, `Hospital`, `Insurance Provider`
- `Billing Amount`, `Room Number`, `Admission Type`, `Discharge Date`
- `Medication`, `Test Results`

## Data Pipeline Architecture
1. **Data Ingestion**: 
   - Data was ingested from GitHub to **Azure Data Lake Storage (ADLS)** using **Azure Data Factory (ADF)** and stored in a "raw" container.
   
2. **Data Storage**: 
   - The raw data was linked to **Azure Databricks** for processing using key-based authentication.

3. **Data Cleaning & Transformation (PySpark)**: 
   - Cleaned data by standardizing text formats, removing duplicates, handling missing values, and renaming columns for consistency.
   - Added a unique `ID` column and standardized patient names using the `initcap` function.
   - The transformed data was stored in a "cleaned" container, then further transformed and stored in the "transformed" container in **Parquet format**.

4. **Analytics (Azure Synapse Analytics)**:
   - Created an external table in **Azure Synapse Analytics** from the transformed data.
   - Performed SQL queries to analyze:
     - Number of patients by medical condition
     - Total billing by insurance provider
     - Patient distribution by gender for each medical condition
     - Total billing by medical condition

5. **Visualization (Power BI)**:
   - Connected Synapse Analytics to **Power BI** to create visualizations such as:
     - Clustered bar and column charts for patient counts and billing
     - Line charts for trends over time
     - Pie charts to show distributions by insurance provider
     - Interactive slicers for dynamic filtering

## Key Benefits
- **Automated Data Processing**: Streamlined data ingestion, cleaning, and transformation processes with minimal manual intervention.
- **Improved Data Quality**: Data cleaning steps ensured consistency, accuracy, and readiness for analysis.
- **Efficient Storage and Performance**: Parquet format optimized storage and query performance in ADLS and Synapse Analytics.
- **Actionable Insights**: SQL queries enabled analysis of patient demographics, billing trends, and medical conditions, providing valuable insights for decision-making.
- **Scalability**: Azure services allow the pipeline to scale efficiently for larger datasets.

## Conclusion
This project demonstrates how cloud-based technologies can improve healthcare data processing and analysis, leading to enhanced decision-making, cost savings, and better patient outcomes.

## Future Improvements
- **Advanced Data Cleaning**: Outlier detection and missing value imputation.
- **Data Enrichment**: Adding more detailed demographic or geographical data.
- **Enhanced Visualizations**: Adding more interactivity and filters in Power BI.
