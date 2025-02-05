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

### **Dashboard Views**

** Open the images in a new tab for ease of access
[Sales View](https://github.com/user-attachments/assets/7ab4a2bf-d787-4161-a6d6-b26ccfab246b)

[Marketting View](https://github.com/user-attachments/assets/54908c2c-9031-463d-bec2-8fb588098dcc)

[Supply Chain View](https://github.com/user-attachments/assets/2a8392fc-3fa9-4273-9f4a-a7781214f669)

[Finance View](https://github.com/user-attachments/assets/c719e3d6-85c4-4d1c-aabf-f4fa277fa73b)

## 🔧 How to Use
1. **Download & Open** – Open `Forecast_Accuracy.pbix` in **Power BI Desktop**.
2. **Apply Filters** – Use dropdown filters for **region, market, and customer**.
3. **Analyze KPIs** – Review **forecast accuracy, net error, and risk factors**.
4. **Identify Risks** – Address **out-of-stock** and **excess inventory** situations.

## 📁 Repository Files
📂 **`Forecast_Accuracy.pbix`** → The Power BI dashboard is not shareable due to the filesize, however will be provided on demand.  
📂 **`Data_Model_Schema.png`** → Diagram of the data model relationships.  

## 🛠️ Key DAX Measures
Here are some of the main **DAX formulas** used in the report:

```DAX
Forecast Accuracy % = 
1 - ( ABS( SUM( 'fact_actuals_estimates'[Actual Sales] ) - SUM( 'fact_forecast_monthly'[Forecast Sales] ) ) 
      / SUM( 'fact_actuals_estimates'[Actual Sales] ) )
