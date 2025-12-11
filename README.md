# customer-churn-analysis
End‑to‑end customer churn analysis using Python (EDA, visualization, and simple modeling).

# Customer Churn Analysis (Telco)

This project analyzes customer churn for a telecommunications company using the Telco Customer Churn dataset. The goal is to understand which types of customers are most likely to leave and to build a simple model that predicts churn. The work includes data cleaning, exploratory data analysis (EDA), and a baseline logistic regression model.

## Dataset

The dataset contains 7,043 customers with 21 columns, including:

- Customer details: customerID, gender, SeniorCitizen, Partner, Dependents  
- Services: phone service, multiple lines, internet service type, online security/backup, device protection, tech support, streaming services  
- Contract and billing: contract type, paperless billing, payment method, monthly charges, total charges  
- Target: `Churn` ("Yes" / "No")

The raw data is stored in `data/telco_churn.csv`.

## Tech stack

- Python, Jupyter Notebook  
- pandas, NumPy  
- Matplotlib, Seaborn  
- scikit-learn  
- Git, GitHub

## Data cleaning

- Loaded the CSV into a pandas DataFrame and inspected column types and missing values.  
- Converted columns to appropriate types and created a clean DataFrame (`df_clean`) for analysis.  
- Created useful derived features, such as tenure buckets, to compare churn across different customer groups.

## Exploratory data analysis (EDA) – key findings

- Around one quarter of customers churn ("Yes"), while about three quarters stay ("No"), so churn is a meaningful issue for this business.  
- Customers on month-to-month contracts cancel much more often than those on one-year or two-year contracts, making short-term contracts the riskiest group.  
- Newer customers (lower tenure buckets) churn more frequently, and long-term customers churn much less, so churn risk drops as customers stay longer.  
- Customers who churn tend to pay higher monthly charges than those who stay, so more expensive plans are at higher risk of churn.  
- Among internet types, Fiber optic customers churn the most, DSL customers churn less, and customers with no internet service churn the least.

## Model

A simple logistic regression model was trained to predict `Churn` using:

- Numeric features: `tenure`, `MonthlyCharges`  
- Categorical features: `Contract`, `InternetService` (one-hot encoded)

Results on the test set:

- About 77% overall accuracy  
- Strong performance on identifying customers who stay (churn = "No")  
- Identifies roughly half of the customers who churn (churn = "Yes"), which is reasonable for a first baseline model and reflects the patterns seen in the EDA

## Project structure

- `data/` – raw dataset (`telco_churn.csv`)  
- `notebooks/01_eda_telco_churn.ipynb` – full analysis and modeling notebook  
- `requirements.txt` – Python dependencies

## How to run

1. Clone the repository:

git clone https://github.com/<your-username>/customer-churn-analysis.git
cd customer-churn-analysis

2. Create and activate a virtual environment:
python3 -m venv .venv
source .venv/bin/activate

3. Install dependencies:
pip install -r requirements.txt

4. Launch Jupyter:
jupyter lab

text
Open `notebooks/01_eda_telco_churn.ipynb` and run all cells.

## Future improvements

- Try more advanced models (e.g., tree-based models) and compare performance.  
- Add feature importance or SHAP analysis to explain which features drive predictions.  
- Extend the project with SQL queries and/or a small dashboard for business users.