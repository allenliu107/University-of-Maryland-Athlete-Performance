# Project Background
The University of Maryland has 20 Division 1 teams, encompassing over 550 student-athletes. To optimize their performance and health, coaches use monitoring tools like Catapult vests to track workload, movement, and performance during practices and games.

This project aimed to develop a performance analytics dashboard for over 10 team on a centrified cloud-based platform using Microsoft Fabric, Microsoft’s latest data analytics and data engineering suite. The dashboard will integrate data from Catapult and provide coaches with real-time insights to better lead their team.

As an analyst, my primary role was to build Power BI dashboards and help implement ETL pipelines and Spark notebooks using Microsoft Fabric. Below consists a summary of data processes and the dashboards generated for the Football and Men's Soccer Team.

# Data Processing and Warehouse Architecture
A data pipeline first initiates the transfer of data from the Catapult system to Azure Blob Storage via Catapult’s API.

Once ingested, all data processing occur within Microsoft Fabric and follow the medallion architecture framework to ensure structured and efficient data management.

Bronze Layer (Raw Data) – A Data Factory pipeline transfers raw, unstructured data from Blob Storage into an initial OneLake file storage. An Apache Spark Notebook then processes and writes this data into a Delta Table while a additional Spark Notebook is used to update the tables with new data and at the same time preserving the raw structure.

Silver Layer (Structured Data) – Apache Spark Notebooks are used to clean, structure, and validate the data before storing it in the Lakehouse (Silver) for reporting and analysis.

Gold Layer (Refined Data) – The final layer prepares the data for integration with other tools. *Wasn't Required for the scope of the project

Finally, a SQL Analytics Endpoint is created to expose the data to a Semantic Model, which is read Power BI reports for visualization and in-depth analysis.
![image](https://github.com/user-attachments/assets/fd0b18b9-ce0f-485e-ba95-b1c9bf717dec)

# Data Model
A galaxy Schema with two fact tables (Sport)_Catapult_Periods_Summary and (Sport)_Catapult_Activity_Summary, were chosen to enable accurate data across different levels of granularity. (Sport)_Catapult_Periods_Summary stored aggregated performance data for predefined periods such as warmup or first quarter, while (Sport)_Catapult_Activity_Summary tracked activity-based metrics, meaning each record were tied to a specific movement rather than a broad period, allowing both time-series and comparative analysis. Shared dimension tables, such as Athletes, Date, and Activity Details, allowed for efficient filtering and comparison across multiple datasets, ensuring that queries remain optimized for efficency. 

**Soccer:**
![image](https://github.com/user-attachments/assets/289cc0e0-2e20-41a5-99a1-fa5bdb6a21f9)
**Football:**
![image](https://github.com/user-attachments/assets/d4c6f7ac-796b-49d5-a553-399579ebc417)


# Football
[Link to football]
## Data Overview/Dax Formulas



# Men's Soccer/Dax Formulas
[Link to Soccer]
## Data Overview

# Visualization Preview
https://github.com/user-attachments/assets/f8c326dc-f09c-4178-a1b3-0f3dd805a7f0







