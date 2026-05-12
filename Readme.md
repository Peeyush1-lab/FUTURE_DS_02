# Telco Customer Churn Analysis
### Customer Retention Analytics — Data Science & Analytics Internship (2026)

> **Can we predict which customers will leave — and understand why before they do?**

This project performs an end-to-end churn and retention analysis on the Telco Customer Churn dataset. The goal is to move beyond surface-level charts and deliver insights that could genuinely inform a retention strategy for a subscription business.

## Problem Statement

Customer churn is one of the most costly problems for any subscription-based business. Acquiring a new customer costs 5–7x more than retaining an existing one. In this project, I explore:

- **Who is churning?** — demographic and behavioural patterns of customers who leave
- **Why are they churning?** — which product features and contract types drive attrition
- **When do they churn?** — tenure-based survival and cohort retention curves
- **What can be done?** — data-backed recommendations to reduce churn

## Dataset

**Source:** [Telco Customer Churn — Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

| Property | Details |
|---|---|
| Records | 7,043 customers |
| Features | 21 columns (demographics, services, billing, churn status) |
| Target | `Churn` — Yes / No |

**Key columns used:**
`tenure`, `MonthlyCharges`, `TotalCharges`, `Contract`, `InternetService`, `PaymentMethod`, `TechSupport`, `OnlineSecurity`, `Churn`

## Project Structure

```
FUTURE_DS_02
├── dataset/
|   ├──raw/
│   |   └── telco_customer_churn.csv   # raw dataset (not tracked in git)
│   └──cleaned/
|       └──telco_churn_clean.csv       # cleaned dataset(after running the 01_data_cleaning.ipynb)
├── notebooks/
│   ├── 01_data_cleaning.ipynb                  # loading, cleaning, encoding
│   ├── 02_exploratory_analysis.ipynb           # churn patterns and distributions
│   ├── 03_cohort_retention_analysis.ipynb      # cohort heatmap, CLV estimates
│   └── 04_churn_insights_report.ipynb          # executive summary & recommendations
│
├── reports/
│   └── figures/                                # saved charts referenced in this README
├── dashboard.pbix                              # dashboard for telco customer churn analysis
├── requirements.txt
└── README.md
```

## Methodology

### 1. Data Cleaning
- Converted `TotalCharges` from object to float (whitespace issue on 11 rows)
- Encoded `Churn` as binary (Yes = 1, No = 0)
- Verified no duplicate CustomerIDs
- Bucketed `tenure` into cohort groups: 0–12, 13–24, 25–36, 37–48, 49–60, 61–72 months

### 2. Exploratory Analysis
Analysed churn distribution across:
- Contract type (month-to-month vs one-year vs two-year)
- Internet service type (Fiber optic vs DSL vs None)
- Add-on services (TechSupport, OnlineSecurity)
- Payment method
- Monthly charges distribution

### 3. Cohort & Retention Analysis
- Grouped customers by tenure cohort (as a proxy for signup period)
- Calculated retention rate per cohort
- Estimated Customer Lifetime Value (CLV) per segment: `CLV = avg(MonthlyCharges) × avg(tenure)` per group
- Visualised as a heatmap showing churn concentration across cohorts

### 4. Business Insights Report
Summarised the five highest-impact findings with supporting evidence, and provided three prioritised retention recommendations written for a non-technical audience.



## Key Findings

1. **Month-to-month contracts have a ~42% churn rate** vs only 11% for one-year and 3% for two-year contracts. Contract type is the single strongest predictor of churn.

2. **Fiber optic users churn at nearly double the rate of DSL users** — suggesting a gap between pricing expectations and perceived service quality.

3. **Customers without OnlineSecurity or TechSupport churn at ~2x the rate** of those with these add-ons, even when controlling for contract type.

4. **The first 12 months are critical** — over 50% of churned customers leave within their first year. Retention effort is most cost-effective in this window.

5. **Electronic check payers have the highest churn rate** among payment methods (~45%), pointing to a segment of lower-commitment customers.

## Recommendations

| Priority | Recommendation | Target Segment |
|---|---|---|
| High | Offer an incentive to switch from month-to-month to annual contracts at the 3-month mark | New customers, month-to-month |
| Medium | Bundle OnlineSecurity and TechSupport at a discounted rate for first-year customers | Customers without add-ons |
| Medium | Investigate Fiber optic satisfaction — consider a feedback loop or SLA-based discount | Fiber optic subscribers |

## Tools & Libraries

| Tool | Purpose |
|---|---|
| Python 3.11 | Core language |
| pandas | Data loading, cleaning, manipulation |
| matplotlib / seaborn | Visualisation |
| plotly | Interactive charts |
| Jupyter Notebook | Analysis environment |

## How to Run

```bash
# 1. Clone the repo
git clone https://github.com/Peeyush1-lab/telco-churn-analysis.git
cd telco-churn-analysis

# 2. Install dependencies
pip install -r requirements.txt

# 3. Add the dataset
# Dataset is downloaded from this link https://www.kaggle.com/datasets/blastchar/telco-customer-churn


# 4. Run notebooks in order
jupyter notebook
# Open notebooks/ and run 01 → 02 → 03 → 04
```

## What I Learned

Working through this project reinforced a few things that go beyond technical skills:

- Business framing matters more than chart quantity. A single well-interpreted insight is worth more than ten unlabelled plots.
- Data cleaning is where the real work is. The TotalCharges whitespace issue is a good example of real-world messiness.
- Cohort thinking changes how you read data. Aggregate churn rates hide the fact that most risk sits in the first year.

## About

This project was completed as part of the **Future Interns — Data Science & Analytics Internship (2026), Task 2**.

Connect on [LinkedIn](https://www.linkedin.com/in/peeyush-tiwari) | More projects on [GitHub](https://github.com/Peeyush1-lab)