# Bing News Data Analytics using Microsoft Fabric  
### End-to-End Data Engineering, Data Science, and BI Pipeline  
**Author:** SAI CHANDAN VUDA  

---

## 📌 Project Overview

This project demonstrates an end-to-end modern data engineering and analytics pipeline built using **Microsoft Fabric** to collect, process, analyze, and visualize real-time news data from the **Azure Bing News API**. The solution is designed using the Lakehouse architecture where raw JSON data is ingested using Fabric Data Factory, stored in OneLake, transformed using Synapse Data Engineering, and enriched with sentiment analysis using Synapse Data Science. The processed data is stored as Delta tables inside the Fabric Lakehouse and is used for reporting through Power BI dashboards. Real-time monitoring is implemented using Data Activator to trigger alerts based on sentiment results. This project showcases how Microsoft Fabric can be used as a unified platform to integrate Data Engineering, Data Science, Business Intelligence, and real-time alerting in a single environment without external storage or services.

---

# **__IMPORTANT STEPS IN THE PROJECT__**

---

# **__1. Data Ingestion from Azure Bing API__**

- Data is collected from the **Azure Bing News API**.
- The API returns news data in **JSON format**.
- **Microsoft Fabric Data Factory** is used to ingest the data into the Fabric environment.
- A pipeline is created to pull current news data at scheduled intervals.
- The raw API response is copied directly into the Fabric workspace for further processing.

### Tools Used
- Azure Bing News API  
- Microsoft Fabric Data Factory  

---

# **__2. Storing Raw Data in OneLake (Lakehouse)__**

After ingestion:

- The raw JSON data is stored inside **Microsoft Fabric OneLake**.
- OneLake acts as the **centralized storage layer** of Microsoft Fabric.
- It provides a unified storage foundation for different Fabric experiences and workloads.
- Inside OneLake, multiple data systems can be created and managed such as:
  - **Lakehouse / Lake Database**
  - **Data Warehouse**
  - **Kusto Database**

For this project:

- A **Lakehouse** is used to store the raw JSON file.
- The raw file is placed in the **Files section** of the Lakehouse.
- This becomes the **RAW data layer** of the project.

### Why OneLake?
- Centralized and unified storage
- Easy collaboration across teams
- Native integration with Microsoft Fabric services
- No need for separate external storage configuration

---

# **__3. Data Transformation using Synapse Data Engineering__**

Raw JSON data is not directly suitable for analytics or reporting.

To solve this:

- **Synapse Data Engineering** is used to read and process the raw JSON data.
- A **Spark Notebook** is used to define a predefined schema and transform the semi-structured JSON into a structured format.
- The cleaned and structured output is stored as **Delta Tables** inside the Lakehouse.

### Transformation Steps
- Read raw JSON from OneLake
- Apply predefined schema
- Parse and flatten JSON fields
- Convert data into structured table format
- Store the output as Delta tables

### Tools Used
- Synapse Data Engineering
- Spark Notebook
- PySpark
- Microsoft Fabric Lakehouse

### Why Delta Tables?
- Better performance for analytics
- ACID transaction support
- Supports incremental loading
- Optimized for downstream reporting and analytics

---

# **__4. Incremental Load Implementation__**

To improve efficiency, **incremental load** logic is implemented in the pipeline.

Instead of processing the complete dataset every time:

- Only newly ingested news records are identified
- Only new data is transformed and appended
- Existing processed data is preserved

### Benefits
- Faster execution
- Reduced processing cost
- Better scalability
- Efficient handling of frequently updating news data

At this stage, the project has:

- Cleaned data
- Structured schema
- Delta tables in Lakehouse
- A collaborative data layer accessible to different users such as:
  - Data Engineers
  - Data Scientists
  - Data Analysts

This makes the Lakehouse a strong collaboration point across multiple personas in the data platform.

---

# **__5. Sentiment Analysis using Synapse Data Science__**

After the data engineering stage, the cleaned data is enriched with AI-driven insights using **Sentiment Analysis**.

### Objective
Determine the sentiment of each news article using the **description** text field.

### Process
- Cleaned data is loaded from the **Lakehouse Delta tables**
- A **Synapse Data Science notebook** is used for processing
- A **pretrained text analytics model** is applied to classify sentiment
- Each news record is labeled as:
  - **Positive**
  - **Negative**
  - **Neutral**

### Steps Performed
- Read cleaned news data from Delta tables
- Use Python / PySpark notebook for processing
- Apply pretrained text analysis model
- Generate a new column called `sentiment`
- Store the sentiment-enriched output back into the Lakehouse as a Delta table

### Tools Used
- Synapse Data Science
- Python
- PySpark
- Pretrained Text Analytics Model
- Microsoft Fabric OneLake integration

### Benefits
- Adds AI-based insights to news analytics
- No need to build a custom ML model from scratch
- Fully integrated inside Microsoft Fabric
- Final output is optimized for reporting and alerting

This step strengthens the project by combining **Data Engineering + Data Science** in a single Fabric architecture.

---

# **__6. Power BI Dashboard for Analytics__**

The sentiment-enriched Delta table stored in the Lakehouse is used as the **final reporting dataset**.

This stage represents the **Data Analyst layer** of the project.

### Reporting Layer
- **Power BI** inside Microsoft Fabric is connected directly to the Lakehouse Delta table
- No external database or storage connection is required
- The dashboard is created to monitor the latest news data and sentiment patterns in an interactive format

### Dashboard Visuals
- Sentiment distribution (**Positive / Negative / Neutral**)
- News count by category
- Latest news list
- Source-wise news analysis
- Date-wise news trend
- Sentiment trends over time

### Benefits
- Interactive dashboarding
- Unified analytics experience
- Direct connection to OneLake Delta tables
- Easy exploration of final curated data

This dashboard acts as a **daily news monitoring and analytics solution** built completely on top of Microsoft Fabric.

---

# **__7. Real-Time Alerts using Data Activator__**

To add real-time monitoring capability, the project uses **Data Activator**, a built-in tool in Microsoft Fabric.

### Integration Flow
- Power BI semantic model is connected to **Data Activator**
- Rules are configured based on sentiment metrics and report data
- Alerts are triggered when specific business conditions are met

### Example Alert Rule
- Trigger an alert when:
  - `sentiment = Negative`

### Notification Channels
- Microsoft Teams
- Email notifications (optional)

For this project:

- Alerts are delivered to a **Microsoft Teams channel** for real-time news monitoring.

### Use Case
This helps stakeholders react quickly whenever negative news articles are detected in the latest incoming data.

---

# **__8. Complete Microsoft Fabric Architecture__**

This project demonstrates a complete end-to-end Microsoft Fabric solution including:

- **Data Ingestion** → Azure Bing News API  
- **Data Engineering** → Data Factory + Synapse Data Engineering  
- **Storage Layer** → OneLake Lakehouse  
- **Transformation Layer** → Spark / PySpark Notebooks  
- **Incremental Processing** → Efficient data pipeline logic  
- **Data Science** → Sentiment Analysis using Synapse Data Science  
- **Analytics Layer** → Power BI Dashboard  
- **Real-Time Monitoring** → Data Activator  
- **Collaboration Layer** → Shared OneLake data access  

This showcases how **Microsoft Fabric** can serve as a **single unified platform** for Data Engineering, Data Science, Analytics, and Alerting.
---

## 🚀 Key Features

- End-to-end Microsoft Fabric pipeline
- Real-time news ingestion
- Raw to curated data transformation
- Lakehouse architecture using OneLake
- Delta table implementation
- Incremental data loading
- Sentiment analysis using pretrained text analytics model
- Power BI reporting inside Fabric
- Real-time alerts through Data Activator
- Unified collaboration across data roles

---

## 🧠 Use Case

This project can be used for:

- Real-time news monitoring
- Sentiment-based analytics
- Media trend analysis
- Data engineering portfolio demonstration
- Microsoft Fabric hands-on learning
- End-to-end modern data platform design

---

## 👨‍💻 Author

**SAI CHANDAN VUDA**  
Data Engineer | Azure | Microsoft Fabric | PySpark | Power BI | Python
