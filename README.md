# 📦 International Trade Data Pipeline (2017–2025)
### Python • SQL • Power BI • Data Cleaning • NLP • ETL Pipeline

This project is an end-to-end data pipeline designed to automate international trade data analysis for Siddharth Associates.  
It replaces manual Excel workflows with a scalable solution using Python, SQL, and Power BI.

---

## 🚀 **Project Overview**

The workflow automates:
- Parsing complex **Goods Description** text using Regex/NLP
- Data cleaning, handling missing values, standardizing unit fields
- Feature engineering (Grand Total, Landed Cost Per Unit, categories)
- SQL-based macro & micro analysis
- Interactive dashboards in Power BI

This project processes import/export data from **2017 to 2025 (sample provided)**.

---

## 🗂️ **Project Structure**

siddharth_trade_pipeline/
│
├─ data/
│ ├─ raw/ # Sample raw Excel/CSV data (from assignment)
│ └─ processed/ # Cleaned CSV after Python processing
│
├─ python/
│ ├─ parsing_code.py # Regex/NLP extraction from Goods Description
│ ├─ cleaning_code.py # Date parsing, missing values, unit cleanup
│ └─ feature_engineering.py # Grand Total, category logic, landed cost
│
├─ sql/
│ ├─ schema.sql # Database table creation
│ ├─ macro_trends.sql # Yearly growth, YoY %
│ ├─ pareto_hsn.sql # Top 25 HSN codes (Pareto analysis)
│ └─ supplier_analysis.sql # Supplier activity/churn analysis
│
├─ powerbi/
│ └─ trade_dashboard.pbix # Complete interactive Power BI dashboard
│
└─ README.md

markdown
Copy code

---

## 🧹 **1. Data Cleaning (Python)**

Key tasks:
- Convert shipment date → proper datetime  
- Extract Year, Month  
- Standardize units (`pcs`, `nos`, `pieces` → `PCS`)
- Handle missing values  
- Convert numeric columns to correct types  

Technologies:
- Python (Pandas, Regex, NumPy)

---

## 🔍 **2. Text Parsing (Python)**

The **Goods Description** field is unstructured and contains:
- Model name  
- Model number  
- Capacity (e.g., 500ML, 2.5L, 10 Inch)  
- Material type (Glass, Steel, Wooden, etc.)  
- Embedded quantity  
- USD price  

Regex extraction functions parse:
- `model_number`
- `capacity_spec`
- `material_type`
- `unit_price_usd_parsed`
- `embedded_quantity`

All extracted features are added as new columns.

---

## 🧮 **3. Feature Engineering**

Computed fields:
- **Grand Total INR**  
grand_total = total_value_inr + duty_paid_inr

markdown
Copy code
- **Landed Cost Per Unit**  
landed_cost = grand_total / quantity

yaml
Copy code
- **Category / Sub-category**  
Based on HSN + keywords in Goods Description.

---

## 🗄️ **4. SQL Analysis**

Loaded cleaned dataset into SQL (SQLite/PostgreSQL).

### Key SQL analyses:
- **Year-over-year growth** (Total Imports, Duty Paid, Grand Total)
- **Pareto Analysis** (Top 25 HSN codes)
- **Supplier Longevity** (Active vs Churned suppliers in 2025)
- **Model-level price comparison**
- **Capacity-wise volume analysis**

SQL scripts are included in `/sql/` folder.

---

## 📊 **5. Power BI Dashboard**

The Power BI report includes:

### 📈 **Macro Dashboard**
- Imports vs Duty Paid vs Grand Total (line chart)
- YoY Growth heatmap

### 🧩 **HSN → Model → Capacity Treemap**
Interactive drill-down from category to model level.

### 🧪 **Unit Economics Scatter Plot**
- X-axis: Capacity  
- Y-axis: Landed Cost Per Unit  
- Size: Quantity  
- Color: HSN or Model  

### 🧑‍🤝‍🧑 **Supplier Insights**
- Active suppliers in 2025
- Historical vs new suppliers

File: `powerbi/trade_dashboard.pbix`

---

## 🛠️ **How to Run the Project**

### ▶️ **1. Install Dependencies**
pip install -r requirements.txt

markdown
Copy code

### ▶️ **2. Run the Python Notebooks/Scripts**
- Load raw dataset
- Clean data
- Generate processed CSV

### ▶️ **3. Import Clean Data into SQL**
sqlite3 trade.db < sql/schema.sql

yaml
Copy code

### ▶️ **4. Open `trade_dashboard.pbix` in Power BI**
Connects to the processed data automatically.

---

## 📥 **Input Dataset**

The project uses the **Sample Data 2.xlsx** provided in the assignment (included in `/data/raw/`).

---

## 🧑‍💼 **Author**

**Gopichand Thammi Setty**  
Python Developer | Data Analysis | Power BI  
Email: tgc19992001@gmail.com

---

## ⭐ **Acknowledgment**

This project was created as part of the **Siddharth Associates - International Trade Analysis Assignment**.
