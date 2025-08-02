# ⚡ Power System Load Type Classification
## 📌 Objective
The goal of this project is to build an effective machine learning model to classify power system load into three categories:
1. Light_Load
2. Medium_Load
3. Maximum_Load   
Using historical data including electrical usage and power factor measurements, the objective is to create a robust, explainable model capable of making accurate predictions.

## 🧾 Dataset Overview
<b>Feature	Description</b>
| <b>Column Name                 | Description                                       </b>    |
|-----------------------------|-------------------------------------------------------|
| Date_Time                   | Timestamp of measurement (1st of every month)         |
| Usage_kWh                   | Industry energy consumption (kWh)                     |
| Lagging_Current_Power_Factor| Reactive power (lagging) – kVarh                      |
| Leading_Current_Power_Factor| Reactive power (leading) – kVarh                      |
| CO2                         | CO2 emissions in ppm                                  |
| NSM                         | Number of seconds from midnight (time info)           |
| Load_Type                   | Target label: Light_Load / Medium_Load / Maximum_Load |

## 🧹 1. Data Preprocessing
✅ Actions Performed:

a. Parsed Date_Time column and sorted chronologically.  
b. Handled missing values:  
&nbsp;&nbsp;&nbsp;&nbsp;i. Forward-fill for `Lagging_Current_Power_Factor` and `Leading_Current_Power_Factor`  
&nbsp;&nbsp;&nbsp;&nbsp;ii. Median fill for `Usage_kWh`, `NSM`, `CO2`  
c. Removed duplicates and rows with constant values.  
d. Applied outlier filtering using Z-score.  
e. Label encoded the Load_Type column for modeling.  

## 📊 2. Exploratory Data Analysis (EDA)
🔍 Correlation Matrix:

a. Strong correlation observed between Usage_kWh and Load_Type  
b. CO2 and NSM also show relevant patterns.  

<img width="1098" height="745" alt="Screenshot 2025-08-02 205257" src="https://github.com/user-attachments/assets/12cf214c-51c7-406a-9dbc-ff1bee2e7206" />


## 🛠️ 3. Feature Engineering
a. Converted Date_Time to extract month-based features (optional).  
b. Scaled features using StandardScaler.  
c. All features kept numerical for clean integration with all models.  

## 🔀 4. Dataset Splitting
a. Stratified splitting to maintain class distribution.  
  &nbsp;&nbsp;&nbsp;&nbsp;i. 60% Training  
  &nbsp;&nbsp;&nbsp;&nbsp;ii. 20% Validation  
  &nbsp;&nbsp;&nbsp;&nbsp;iii. 20% Test  
Ensures fair evaluation and robust model performance tracking.

## 🤖 5. Model Training & Performance Evaluation
Models Compared:  
a. RandomForestClassifier 🌲  
b. LogisticRegression 🧠  
c. XGBoostClassifier 🚀  



<b>✅ Validation Set Performance:</b>  

<img width="531" height="772" alt="Screenshot 2025-08-02 205235" src="https://github.com/user-attachments/assets/8692ba2c-8f0b-4e13-8965-d16e45823b93" />



<b>✅ Confusion Matrix (for "XGBoost" Model):</b>  

<img width="835" height="617" alt="Screenshot 2025-08-02 205400" src="https://github.com/user-attachments/assets/2c6b06c8-bac1-4dfb-9bc1-6841b61554bc" />



## 📉 6. Feature Importance
a. Feature importances obtained from RandomForest and XGBoost.  
b. Usage_kWh dominates in impact.  
c. Secondary factors: CO2, Lagging_Current_Power_Factor  

<img width="1376" height="734" alt="Screenshot 2025-08-02 205351" src="https://github.com/user-attachments/assets/5798ce5e-07e8-450f-ae02-91f0e75bbea1" />


## 🧠 7. Explainability with SHAP
<b>SHAP Summary:</b>  
a. SHAP (SHapley Additive exPlanations) used for interpreting XGBoost.  
b. Each feature’s impact on predictions shown clearly.  

<img width="1112" height="672" alt="Screenshot 2025-08-02 205437" src="https://github.com/user-attachments/assets/9aa361c5-8c14-4707-a32b-2f8254b03fe6" />


## ✅ 8. Final Test Set Evaluation
Final model performance (XGBoost) remained strong on unseen test data. Metrics matched validation results, confirming stability.


