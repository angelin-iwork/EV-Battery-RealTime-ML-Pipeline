# EV-Battery-RealTime-ML-Pipeline
End to End EV Battery Telemetry
# EV Battery Real-Time Energy & Machine Learning Pipeline

## 🏗️ Project Architecture
markdown

1.**Bronze Layer:** Simulated real-time Smart BMS telemetry data
2.**Silver Layer:** filtered hardware anomalies like Overheating(>45°C).
3.**Gold Layer:** Saved clean enriched data into Delia Lake Tables.
4.**Analytifcs Layer:** Ran Spark SQL quertes for fleet risk management.
5.**AI Layer:** Trained a Random Forest Classifier using PySpark MLlib.

```mermaid
graph TD
    A[Smart BMS Sensors] -->|Voltage, SoC, Temp, kW| B(PySpark Data Ingestion)
    B --> C[(Bronze Layer: Raw Data)]
    C -->|Data Cleaning & Filtering| D[(Silver Layer: Enriched Alerts)]
    D -->|Optimized Storage Write| E[(Gold Layer: Delta Lake Table)]
    E -->|Spark SQL Queries| F[Fleet Risk Management BI]
    E -->|PySpark MLlib Training| G[Random Forest Classifier Model]
    G -->|98.63% Accuracy Prediction| H[Predictive Overheat Alerts]



## Tech Stack
* Azure Databricks
* PySpark & Spark SQL
* Delta Lake
* PySpark MLlib (Random Forest)
