# ⚡ Power System Load Type Classification
📌 Objective
The goal of this project is to build an effective machine learning model to classify power system load into three categories:
1. Light_Load
2. Medium_Load
3. Maximum_Load
Using historical data including electrical usage and power factor measurements, the objective is to create a robust, explainable model capable of making accurate predictions.

## 🧾 Dataset Overview
Feature	Description
| Column Name                 | Description                                           |
|-----------------------------|-------------------------------------------------------|
| Date_Time                   | Timestamp of measurement (1st of every month)         |
| Usage_kWh                   | Industry energy consumption (kWh)                     |
| Lagging_Current_Power_Factor| Reactive power (lagging) – kVarh                      |
| Leading_Current_Power_Factor| Reactive power (leading) – kVarh                      |
| CO2                         | CO2 emissions in ppm                                  |
| NSM                         | Number of seconds from midnight (time info)           |
| Load_Type                   | Target label: Light_Load / Medium_Load / Maximum_Load |

