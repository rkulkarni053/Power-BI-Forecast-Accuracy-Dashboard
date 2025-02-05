# Power BI Forecast Accuracy Dashboard

## 📌 Overview
This project provides an interactive **Power BI dashboard** to analyze **forecast accuracy, net error, and inventory risks**. The dashboard helps in identifying forecasting trends, overstock/understock issues, and customer-specific forecasting accuracy.

## 🚀 Features
- 📊 **Forecast Accuracy Analysis** – Compare actual vs. forecasted data.
- 📉 **Net Error Trends** – Identify over-forecasting and under-forecasting.
- 🔍 **Customer & Segment Insights** – Drill down into granular performance metrics.
- 🕒 **Time-Based Filters** – Year, Quarter, and YTD/YTG selection.
- ⚠️ **Risk Classification** – Highlights **Out-of-Stock** and **Excess Inventory**.
- 📈 **Data Visualization** – Interactive graphs, tables, and KPIs for better decision-making.

## 📂 Data Model
The Power BI dashboard follows a **star schema** with the following key tables:

| Table Name | Description |
|------------|-------------|
| **fact_forecast_monthly** | Contains forecasted sales data at the monthly level. |
| **fact_actuals_estimates** | Stores actual sales and estimates. |
| **dim_customer** | Customer segmentation details. |
| **dim_product** | Product hierarchy, category, and segment mapping. |
| **dim_date** | Date dimension for time-based analysis. |
| **dim_market** | Market, region, and sub-zone details. |

### **Data Model Schema**
[image](https://github.com/user-attachments/assets/7bbc5800-b2d6-4830-9629-51550bb62049)


## 🔧 How to Use
1. **Download & Open** – Open `Forecast_Accuracy.pbix` in **Power BI Desktop**.
2. **Apply Filters** – Use dropdown filters for **region, market, and customer**.
3. **Analyze KPIs** – Review **forecast accuracy, net error, and risk factors**.
4. **Identify Risks** – Address **out-of-stock** and **excess inventory** situations.

## 📁 Repository Files
📂 **`Forecast_Accuracy.pbix`** → The Power BI dashboard file.  
📂 **`Data_Model_Schema.png`** → Diagram of the data model relationships.  
📂 **`Screenshots/`** → Images showing dashboard UI & insights.  
📂 **`SQL_Scripts/`** → SQL queries used for data extraction.  
📂 **`DAX_Formulas.md`** → Documentation of key DAX measures used in Power BI.  

## 🛠️ Key DAX Measures
Here are some of the main **DAX formulas** used in the report:

```DAX
Forecast Accuracy % = 
1 - ( ABS( SUM( 'fact_actuals_estimates'[Actual Sales] ) - SUM( 'fact_forecast_monthly'[Forecast Sales] ) ) 
      / SUM( 'fact_actuals_estimates'[Actual Sales] ) )
