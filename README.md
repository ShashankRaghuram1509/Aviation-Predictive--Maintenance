# Aviation Engine Predictive Maintenance Analytics

## 📌 Project Overview
This project simulates an end-to-end predictive maintenance architecture for an aviation fleet. By analyzing turbofan engine sensor data over time, the dashboard predicts the Remaining Useful Life (RUL) of engines, flags anomalies, and quantifies the financial impact of proactive maintenance versus catastrophic in-flight failures.

## 🛠️ Tech Stack & Tools
* **Database & ETL:** SQL Server Management System (SSMS)
* **Data Modeling:** Star Schema design (Fact and Dimension views)
* **Business Intelligence:** Power BI
* **Analytics & AI:** Advanced DAX, Native Power BI Anomaly Detection, Key Influencers Machine Learning visual.

## ⚙️ Architecture & Execution
### 1. Data Engineering (SQL)
Raw transactional sensor data was ingested into SQL Server. To optimize for BI reporting, the data was transformed into a Star Schema using SQL Views:
* `vw_Dim_Engine`: Calculated the maximum lifecycle for each unique engine.
* `vw_Fact_EngineHealth`: Engineered the `RemainingUsefulLife` metric by calculating the delta between maximum lifecycles and current operational cycles.

### 2. Data Modeling & DAX (Power BI)
Imported the SQL views into Power BI with a 1-to-many relationship. Created dynamic DAX measures to track:
* Total active engines and average RUL.
* **Engines at Risk:** Filtered count of engines with critically low RUL.
* **Financial Impact:** Simulated cost avoidance by calculating `Risk Exposure` ($2M per unplanned failure) minus `Proactive Repair Cost` ($50k per planned maintenance).

### 3. Native AI Integration
* **Anomaly Detection:** Applied to the engine degradation curve to automatically flag mathematically unnatural spikes in sensor readings (e.g., sudden pressure drops).
* **Automated Root Cause (Key Influencers):** Utilized built-in AI to run regression analysis across all sensors, identifying which specific mechanical settings drive engine failure the fastest.

## 📊 Dashboard Preview
<img width="1098" height="613" alt="Screenshot 2026-04-01 175733" src="https://github.com/user-attachments/assets/57cdfaf2-a061-4f19-b726-c26b7f88de6e" />

