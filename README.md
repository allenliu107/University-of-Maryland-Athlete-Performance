# Project Background
The University of Maryland has 20 Division 1 teams, encompassing over 550 student-athletes. To optimize their performance and health, coaches use monitoring tools like Catapult vests to track workload, movement, and performance during practices and games.

As an analyst, my primary role was to build Power BI dashboards that provided coaches key insights to enhance decision-making as well as help implement ETL pipelines and Spark notebooks using Microsoft Fabric, Microsoft’s latest data analytics and data engineering suite.

# Project Scope

# Data Processing and Warehouse Architecture
A data pipeline first initiates the transfer of data from the Catapult system to Azure Blob Storage via Catapult’s API.

Once ingested, all data processing occur within Microsoft Fabric and follow the medallion architecture framework to ensure structured and efficient data management.

Bronze Layer (Raw Data) – A Data Factory pipeline transfers raw, unstructured data from Blob Storage into an initial OneLake file storage. An Apache Spark Notebook then processes and writes this data into a Delta Table while a additional Spark Notebook is used to update the tables with new data while preserving the raw structure.

Silver Layer (Structured Data) – Apache Spark Notebooks are used to clean, structure, and validate the data before storing it in the Lakehouse (Silver) for reporting and analysis.

Gold Layer (Refined Data) – The final layer prepares the data for integration with other tools. *Wasn't Required for the scope of the project

Finally, a SQL Analytics Endpoint is created to expose the data to a Semantic Model, which is read Power BI reports for visualization and in-depth analysis.
![image](https://github.com/user-attachments/assets/fd0b18b9-ce0f-485e-ba95-b1c9bf717dec)

# Data Model
A galaxy Schema with two fact tables MSC_Catapult_Periods_Summary and MSC_Catapult_Activity_Summary, were chosen to enable accurate data across different levels of granularity. MSC_Catapult_Periods_Summary stored aggregated performance data for predefined periods such as warmup or first quarter, while MSC_Catapult_Activity_Summary tracked activity-based metrics, meaning each record were tied to a specific movement rather than a broad period, allowing both time-series and comparative analysis. Shared dimension tables, such as Athletes, Date, and Activity Details, allow for efficient filtering and comparison across multiple datasets, ensuring that queries remain optimized for efficency. 
![image](https://github.com/user-attachments/assets/289cc0e0-2e20-41a5-99a1-fa5bdb6a21f9)






