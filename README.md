# EV-Battery-RealTime-ML-Pipeline
End to End EV Battery Telemetry
# EV Battery Real-Time Energy & Machine Learning Pipeline

## Project Architecture
1. **Bronze Layer:** Simulated real-time Smart BMS telemetry data for 1,000 EVs using PySpark.
2. **Silver Layer:** Filtered hardware anomalies like Overheating (>45°C) and Low Battery (<20%).
3. **Gold Layer:** Saved clean enriched data into Delta Lake Tables.
4. **Analytics Layer:** Ran Spark SQL queries for fleet risk management metrics.
5. **AI Layer:** Trained a **Random Forest Classifier** using PySpark MLlib to predict battery overheat risks.

## 🏗️ Project Architecture

```mermaid
graph TD
    %% Define Styles
    classDef bronze fill:#cd7f32,stroke:#333,stroke-width:2px,color:#fff;
    classDef silver fill:#c0c0c0,stroke:#333,stroke-width:2px,color:#000;
    classDef gold fill:#ffd700,stroke:#333,stroke-width:2px,color:#000;
    classDef ml fill:#8673a1,stroke:#333,stroke-width:2px,color:#fff;

    %% 1. Fleet Telemetry Ingestion
    subgraph IoT_Telemetry [1000 EV Fleet Telemetry]
        A[Smart BMS Sensors] -->|Voltage, SoC, Temp, kW| B(PySpark Ingestion)
    end

    %% 2. Medallion Architecture Steps
    subgraph Medallion_Architecture [Databricks Lakehouse Pipeline]
        B -->|Raw Ingest| C[(Bronze Layer: Raw Data)]:::bronze
        C -->|Cleaning & Filtering| D[(Silver Layer: Alerts)]:::silver
        D -->|Optimized Write| E[(Gold Layer: Delta Table)]:::gold
    end

    %% 3. Output Consumption
    subgraph Value_Realization [Analytics & AI Layer]
        E -->|Spark SQL| F[Fleet Risk Management BI]
        E -->|PySpark MLlib| G[Random Forest Classifier Model]:::ml
        G -->|98.63% Accuracy| H[Predictive Overheat Alerts]
    end

## Tech Stack
* Azure Databricks
* PySpark & Spark SQL
* Delta Lake
* PySpark MLlib (Random Forest)
