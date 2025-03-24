# Project Background
The University of Maryland has 20 Division 1 teams which encompasses over 550 student athletes. To maximize the performance and health of athletes, coaches use monitoring tools such as Catapult Vests that track athlete workload, movement, and performance during practice and games. 

As an analyst my primary role was to build Power BI dashbaords that provided coaches the insights needed to elevate decision making. Additionaly, I also helped implement ETL pipelines and Spark notebooks utilizing Microsoft’s new data analytics/data engineering suite called Microsoft Fabric.

# Data Processing
The data process starts with the data collected being transferred into a Azure Blob Storage using a data pipeline and Catapult's API. Afterwards, the rest of data processes are done within Microsoft's Fabric platform where the data follows a medallion architecture. First, a pipeline from the Data Factory is used to transport data from blob into a initial unstructured Lake House called "Bronze", as well as update the Lakehouse with any new data. Second, notebooks using Apache Spark transform and structure of data for reporting while storing it in a Lakehouse labeled "Silver". Finally, a third gold layer was to prepare the data for 

. Finally, A SQL Analytics Endpoint is created, exposing the data to a Semantic Model, which was then used by a Power BI report for visualization and analysis.
![image](https://github.com/user-attachments/assets/fd0b18b9-ce0f-485e-ba95-b1c9bf717dec)
