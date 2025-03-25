# Project Background
The University of Maryland has 20 Division 1 teams, encompassing over 550 student-athletes. To optimize their performance and health, coaches use monitoring tools like wearable Catapult vests to track workload, movement, and performance during practices and games.

This project aims to develop a performance analytics dashboard for 10+ teams on a centrified cloud-based platform using Microsoft Fabric, Microsoft’s latest data analytics and data engineering suite. The dashboard will integrate data from Catapult and provide coaches with real-time insights to better lead their team.

As an analyst, my primary role was to build Power BI dashboards and help implement ETL pipelines and Spark notebooks. Below consists a summary of data processes and the dashboards generated for the Football and Men's Soccer Team.

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

## Soccer Data Model
![image](https://github.com/user-attachments/assets/289cc0e0-2e20-41a5-99a1-fa5bdb6a21f9)
## Football Data Model
![image](https://github.com/user-attachments/assets/d4c6f7ac-796b-49d5-a553-399579ebc417)


# Football Visualizations
[Link to football]
## Coach's Report
The dashboard provides the following key insights for coaches:

**Player Load Metrics:** Displays overall player load per minute and rankings by position.

**Distance Analysis:** Highlights 30+ yard efforts and 70+ yard efforts across different positions and top-performing athletes.

**Speed Insights:** Lists the top 10 highest speeds recorded and an assessment of speed readiness (7-day window to reach 92% max speed).

**Explosive Efforts:** Provides an average count of high-intensity efforts.
![image](https://github.com/user-attachments/assets/1031618d-4beb-43b8-a576-1acae09cb16c)

## Report for by Postion Group
The following dashboards provide a overview of athlete performance metrics across different position groups . It highlights Distance, Player Load, Speed, breaking down each individual athlete. Additionally, Total Player Load and Explosive Efforts over time are also featured in a bar graph to offer insight on workload distribution accross different time periods. 

![Screenshot 2025-03-25 at 10 54 19 AM](https://github.com/user-attachments/assets/b1cdba40-2cee-4f09-ac6e-26b44e5599ab)
![Screenshot 2025-03-25 at 10 54 06 AM](https://github.com/user-attachments/assets/a23f0d13-d520-432f-a58d-f6211a376162)
![Screenshot 2025-03-25 at 10 53 52 AM](https://github.com/user-attachments/assets/e9b6795d-04ac-459a-af96-289acc51bae0)

# Men's Soccer Visualizations
## Data Considerations
## Individual Overview
The top portion of dashboard highlights distance, workload, and other performance indicators broken down by athletes with condtional formatting to quickly assess performance trends. The bottom portion of the dashboard includes a athlete and date slider that users can drag to observe the shifts in distance and workload metrics over time. 
![Individual Overview](https://github.com/user-attachments/assets/0162050f-1cf5-41a9-9087-d8bd1cc66e90)
## Individual Acute Chronic Workload Ratio
ACWR is a athlete’s short-term workload relative to their long-term workload to assess injury risk and training load management, the following calculations for the visual utilize both a traditonal calculation as well as a Weighted Moving Average that increaseses the influence more recent data points have. A slider is provided for coaches to observe how the ACWR of a certain performance indicator changes over time.
![ACWR](https://github.com/user-attachments/assets/292d2334-d225-411f-9bbf-bf2dfffa690c)
## Team Overview
The dashboard includes a range of filters that enable coaches to sort metrics by date, activity type such as match/practice name, team assignments based on player attributes such as injury status, and individual players. The dashboard provides an overview of athlete performance indicators and a table breaking down the key metrics by position. Additionaly, graphs are also shown for users to view team averages of the specified metric over time. 
![Team Overview](https://github.com/user-attachments/assets/bc8e880b-8861-4138-b94f-281167849787)
## Weekly Trends
View average load metrics week by week seperated by team and individual. Users are able to filter by season, team, and individual player.
![Weekly Trends](https://github.com/user-attachments/assets/a1a2a712-661b-4aba-b8ee-4b2eb224ccf1)
## Game Overview
View Peformance metrics of players by Game both in a table and graph. Users are able to filter by season, team, and individual player. 
![Game Overview](https://github.com/user-attachments/assets/ad8fb543-c999-4be8-8bee-d60e06eb8f6f)








