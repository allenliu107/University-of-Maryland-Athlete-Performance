# Project Background
An interactive Power BI dashboard used by University of Maryland soccer coaches to track athlete workload, movement, and overall performance.

The University of Maryland has 20 Division 1 teams which encompasses over 550 student athletes. To maximize the competitivenes of teams, coaches use monitoring tools in order to help enhance athlete performance and health. Every practice and game soccer players wear Catapult Vests which uitlize a small GPS and a inertial measurement device to collect data on player movement. As an analyst I was tasked to build tools and visualisations that provide coaches the insights needed to elevate their teams.

# Data Processing
A data pipeline using the Catapult API transfers and stores the data into Azure Blob Storage. Afterwards all data is transported into Microsoft’s Fabric service, a all-in-one cloud data analytics platform that combines Microsofts's existing technologies such as OneLake, Azure Data Factory, and Power BI Reporting.

First, a pipeline from the Data Factory was used to copy new blob data into a Lake House. Second, notebooks using Apache Spark were used to transform the structure of data for reporting as well as update existing data. Finally, A SQL Analytics Endpoint was created, exposing the data to a Semantic Model, which was then used by a Power BI report for visualization and analysis.
