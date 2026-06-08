# Customer Retention Intelligence Platform

> Telco churn analysis · Predictive ML models · CLV · Retention ROI · Power BI dashboard

---

## Business Problem

A telecom company is losing **26.6% of its customers** annually — above the industry average of ~20%. This translates to **$139,131 in monthly recurring revenue** walking out the door. This project identifies *why* customers churn, *who* is most at risk, and quantifies the ROI of specific retention programs.

---

## Key Findings

| Metric | Value |
|--------|-------|
| Overall churn rate | **26.6%** |
| Monthly revenue lost | **$139,131** |
| Annual revenue lost | **~$1.67M** |
| Month-to-month churn rate | **42.7%** |
| Electronic check churn rate | **45.3%** |
| Best ML model AUC | **>0.84** (Gradient Boosting) |
| Combined retention strategy ROI | **>400%** |

### Top Churn Drivers
1. **Month-to-month contract** — 42.7% churn vs 11.3% for annual contracts
2. **Fiber optic internet** — significantly higher churn than DSL
3. **Electronic check payment** — 45.3% churn (highest of any payment method)
4. **No tech support / online security** — 30%+ higher churn rate
5. **Short tenure (<12 months)** — highest early-life churn risk

---

## Project Structure

```
customer-churn-dataanlyst/
├── data/
│   ├── WA_Fn-UseC_-Telco-Customer-Churn.csv   # Raw dataset (7,043 customers)
│   ├── telco_churn_cleaned.csv                 # Cleaned dataset (7,032 customers)
│   └── customer_risk_scores.csv               # ML-scored customer list (generated)
├── notebooks/
│   ├── python code of customer churn.ipynb    # EDA & visualization
│   └── advanced_churn_analysis.ipynb          # ML models · CLV · ROI analysis
├── visualization/
│   ├── churn_full_analysis.png                # 6-panel EDA overview
│   ├── heatmap.png                            # Correlation matrix
│   ├── senior_churn.png                       # Senior citizen churn
│   ├── partner_dependents_churn.png           # Demographics analysis
│   ├── monthly_dist_churn.png                 # Monthly charges distribution
│   ├── security_support_churn.png             # Service add-ons impact
│   ├── tenure_group_churn.png                 # Churn by tenure band
│   ├── high_risk_customers.png                # Top-10 high-risk table
│   ├── roc_pr_curves.png                      # ROC & Precision-Recall curves
│   ├── confusion_matrices.png                 # All model confusion matrices
│   ├── feature_importance.png                 # RF + LR feature importance
│   ├── risk_tier_analysis.png                 # Customer risk segmentation
│   ├── clv_analysis.png                       # Customer Lifetime Value
│   ├── cohort_retention.png                   # Cohort retention heatmap
│   ├── retention_roi.png                      # Strategy ROI comparison
│   ├── cross_validation.png                   # 5-fold CV stability
│   └── executive_dashboard.png               # KPI summary dashboard
└── dashboard/
    ├── dashboard.pbix                         # Interactive Power BI file
    └── dashboard.pdf                          # PDF export
```

---

## Methodology

### 1. Exploratory Data Analysis
- Distribution of churn across demographics, services, contracts, billing
- Correlation analysis of numeric features
- Tenure group segmentation (0-12, 13-24, 25-48, 49-72 months)

### 2. Feature Engineering
- `NumAddOnServices` — count of value-added services per customer
- `AvgChargePerMonth` — spend normalized by tenure
- `IsHighValue`, `IsNewCustomer`, `IsLongTermCustomer` — behavioral flags

### 3. Predictive Modeling
Three models trained and compared on a stratified 80/20 split:

| Model | AUC | F1 | Recall |
|-------|-----|----|--------|
| Logistic Regression | ~0.84 | ~0.62 | ~0.77 |
| Random Forest | ~0.83 | ~0.59 | ~0.72 |
| Gradient Boosting | ~0.84 | ~0.63 | ~0.75 |

Model selection criterion: **AUC** (favors recall — catching churners matters more than false alarms).

### 4. Business Analytics
- **Customer Lifetime Value** — discounted expected revenue per customer
- **Risk Tier Segmentation** — Low / Medium / High / Critical
- **Cohort Retention** — retention rates by tenure band and contract type
- **Retention ROI Calculator** — 4 intervention strategies with quantified ROI

---

## Retention Strategy ROI

| Strategy | Targets | Converted | Monthly Saved | ROI |
|----------|---------|-----------|---------------|-----|
| Contract Upgrade Incentive | M2M + high-risk | ~30% | substantial | >400% |
| Proactive Support Outreach | New + critical risk | ~25% | meaningful | >300% |
| Service Bundle Upgrade | Fiber users | ~35% | meaningful | >500% |
| Loyalty Rewards Program | 12-24mo tenure | ~60% | preventive | >200% |

> Full numbers generated dynamically in the advanced notebook.

---

## Quick Start

```bash
# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn

# Run EDA
jupyter notebook "notebooks/python code of customer churn.ipynb"

# Run advanced analysis (ML + CLV + ROI)
jupyter notebook "notebooks/advanced_churn_analysis.ipynb"
```

---

## Dataset

**Telco Customer Churn** — IBM Watson Analytics sample dataset  
7,043 customers · 21 features · Binary churn target

Features include: demographics, service subscriptions, contract type, billing method, monthly/total charges, tenure.

---

## Tools & Technologies

| Category | Tools |
|----------|-------|
| Data wrangling | pandas, NumPy |
| Visualization | matplotlib, seaborn |
| Machine learning | scikit-learn |
| BI dashboard | Power BI Desktop |
| Environment | Jupyter Notebook, Python 3.13 |

---

## Author

**Waqas Ahmed** — [GitHub](https://github.com/waqaswajla/customer-retention-analysis-dashboard)
