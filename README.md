## Customer Churn Analysis
A Python-based analysis of subscription customer data to understand churn behavior, calculate key business KPIs, and identify the factors most associated with customers leaving.
##Overview
Subscription businesses lose revenue every time a customer cancels. This project cleans and merges raw customer, subscription, and support data into a single analysis-ready dataset, then answers a set of core business questions:
What is the overall churn rate and retention rate?
How much monthly revenue is at risk from churned customers?
Which plan types and states have the highest churn?
Does support escalation correlate with churn?
Can customers be segmented into low / medium / high churn-risk tiers?
## Dataset
Raw data is provided as a single Excel workbook with three sheets:
Sheet	Description
`db_customer`	Customer demographics (name, gender, DOB, location)
`db_subscription`	Subscription details (plan type, contract type, start/cancellation/renewal dates, monthly charges, churn score)
`db_support`	Support ticket history (complaint date, escalation flag)
## Approach
Data Cleaning — standardized inconsistent category labels (e.g. gender values), fixed data types (dates), handled missing values (country filled via state lookup), and dropped irrelevant columns.
Feature Engineering — derived `churn_flag` from cancellation date, `tenure_days` (active or churned), a per-customer `complain_count`, and a `churn_risk` tier (low/med/high) based on `churn_score`.
Merging — combined all three tables into a single customer-level dataset (support records deduplicated to one row per customer before merging).
KPI Calculation — churn rate, retention rate, ARPU, revenue at risk, escalation rate, average complaints per customer, and the correlation between escalations and churn.
Visualization — churn trend over time, churn rate by plan/state, correlation heatmaps, pairplots, and multi-dimensional comparisons (Matplotlib + Seaborn).
Pivot Tables — plan-level summaries of churn rate, revenue, and customer count.
## Key Business Metrics Calculated
Overall Churn Rate & Retention Rate
Average Revenue Per User (ARPU)
Revenue at Risk (from churned customers)
Average Customer Tenure
Support Escalation Rate & its correlation with churn
Churn Risk Segmentation (Low / Medium / High)
## Tools & Libraries
Python: Pandas, NumPy
Visualization: Matplotlib, Seaborn
Environment: Jupyter Notebook
## Project Structure
```
customer-churn-analysis/
│
├── customer_churn_analysis.ipynb   # Main analysis notebook (documented, section-by-section)
├── customer_churn_data_raw.xlsx    # Raw input data (3 sheets)
├── exported_customer_churn_data.csv # Cleaned, merged output dataset
└── README.md
```
## How to Run
Clone the repository
```bash
   git clone https://github.com/<your-username>/customer-churn-analysis.git
   cd customer-churn-analysis
   ```
Install dependencies
```bash
   pip install pandas numpy matplotlib seaborn openpyxl jupyter
   ```
Launch the notebook
```bash
   jupyter notebook customer_churn_analysis.ipynb
   ```
## Key Takeaways
Churn rate and revenue-at-risk together give a fast health check of the subscriber base.
Churn varies meaningfully by plan type and state, pointing to where retention efforts should be focused first.
Support escalations show a measurable correlation with churn — proactive support quality directly affects retention.
Segmenting customers into churn-risk tiers (via `churn_score`) enables targeted, prioritized retention campaigns instead of one-size-fits-all outreach.
