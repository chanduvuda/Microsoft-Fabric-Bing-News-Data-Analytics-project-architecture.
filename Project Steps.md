---

# **__STEP 1 — API Setup for News Data Source__**

## 📌 Overview

In the original design of this project, the **Azure Bing News API** was used to ingest news data into Microsoft Fabric.  
However, Microsoft retired Bing Search APIs in **August 2025**, so the ingestion step has been updated to use an alternative API provider.

For this project, we use **SearchAPI** as a replacement for Bing API.  
SearchAPI provides a compatible endpoint that allows us to fetch Bing News results using a REST API, which can be easily integrated with **Microsoft Fabric Data Factory Copy Activity**.

This step covers:

- Creating a SearchAPI account
- Generating API credentials
- Preparing the API endpoint for Fabric ingestion

---

## 🔄 Why SearchAPI Instead of Bing API?

- Bing Search API retired in August 2025
- Fabric Copy Data requires REST endpoint
- SearchAPI supports Bing News engine
- Works with JSON output
- Easy integration with Data Factory

This makes SearchAPI a suitable replacement for the original project design.

---

## 🌐 Create SearchAPI Account

1. Go to the official website:
**https://www.searchapi.io**

2. Click **Sign Up**
3. Create a free account
4. Verify your email
5. Log in to the dashboard

SearchAPI provides a free plan which is enough for this project.

---

## 🔑 Generate API Key

After logging in:

1. Open Dashboard
2. Navigate to **API Keys**
3. Copy your API key

You will use this key inside Microsoft Fabric Data Factory.

Example:
api_key = YOUR_API_KEY


---

## 🔗 API Endpoint Configuration

We will use the SearchAPI endpoint that supports Bing News engine.

### Base URL
https://www.searchapi.io/api/v1/search


### Required Parameters

| Parameter | Value |
|----------|--------|
| engine | bing_news |
| api_key | YOUR_API_KEY |

Example request format:

**https://www.searchapi.io/api/v1/search?engine=bing_news&api_key=YOUR_API_KEY**


This endpoint returns news data in JSON format, which can be used directly in Fabric.

---

## 📦 API Credentials Used in This Project

url: https://www.searchapi.io/api/v1/search
engine: bing_news
api_key: <your_api_key>


These credentials will be used in the next step when configuring **Data Ingestion in Microsoft Fabric**.

---

