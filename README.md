# Project Background
The University of Maryland has 20 Division 1 teams, encompassing over 550 student-athletes. To optimize their performance and well-being, coaches use monitoring tools like Catapult vests to track workload, movement, and performance during practices and games.

As an analyst, my primary role was to build Power BI dashboards that provided coaches with key insights to enhance decision-making. Additionally, I helped implement ETL pipelines and Spark notebooks using Microsoft Fabric, Microsoft’s latest data analytics and engineering suite.

# Data Processing
The data process begins with data collection, which is transferred to Azure Blob Storage via a data pipeline and Catapult’s API. From there, all data processing takes place within Microsoft Fabric, following a medallion architecture.

Bronze Layer (Raw Data) – A Data Factory pipeline moves the raw, unstructured data from Blob Storage into an initial Lakehouse (Bronze) while continuously updating it with new data.

Silver Layer (Structured Data) – Apache Spark notebooks process, clean, and structure the data for reporting, storing it in a Lakehouse (Silver).

Gold Layer (Refined Data) – The final layer prepares the data for integration with other tools, ensuring it is fully optimized for analysis.

Finally, a SQL Analytics Endpoint is created to expose the refined data to a Semantic Model, which powers Power BI reports for visualization and in-depth analysis.
![image](https://github.com/user-attachments/assets/fd0b18b9-ce0f-485e-ba95-b1c9bf717dec)
