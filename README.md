# Trial-to-Paid Conversion Analysis — RavenStack SaaS Dataset

> Analyzing user behavior data to identify what drives trial users to convert to paid subscriptions.

## 📌 Project Overview

This project analyzes a synthetic multi-table SaaS dataset (RavenStack) to uncover patterns that influence trial-to-paid conversion. The goal is to derive actionable product recommendations that can improve conversion rates, reduce churn, and optimize user onboarding.

**Dataset Credit:** River @ Rivalytics — [Kaggle Dataset](https://www.kaggle.com/datasets/rivalytics/saas-subscription-and-churn-analytics-dataset)

## 🎯 Business Questions Answered

- Which plan tier and referral channel has the highest conversion rate?
- Which features do converted users engage with most?
- Does feature breadth (exploring more features) drive conversion?
- Why are users churning — and what can be done about it?
- Does support quality impact retention?
- How has churn trended over time?

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Python | Data cleaning, EDA, analysis |
| Pandas | Data manipulation and merging |
| SQLite (via sqlite3) | SQL-based multi-table analysis |
| Matplotlib & Seaborn | Data visualization |
| Tableau Public | Interactive dashboard |
| Google Colab | Development environment |

---

## 📁 Dataset Structure

5 interconnected tables:

```
accounts (500 rows)
│
├── subscriptions (5,000 rows)
│   └── feature_usage (25,000 rows)
│
├── support_tickets (2,000 rows)
└── churn_events (600 rows)
```

| Table | Key Columns |
|---|---|
| accounts | account_id, plan_tier, referral_source, is_trial, churn_flag |
| subscriptions | subscription_id, mrr_amount, upgrade_flag, billing_frequency |
| feature_usage | feature_name, usage_count, usage_duration_secs |
| support_tickets | resolution_time_hours, satisfaction_score, escalation_flag |
| churn_events | reason_code, refund_amount_usd, is_reactivation |

---

## 📊 Key Findings

### 1. Feature Breadth Drives Conversion
Converted users explored significantly more unique features than churned users during their trial period. Users who engaged with a broader range of features were more likely to convert to paid plans.

**Recommendation:** Add feature discovery prompts during onboarding to guide trial users to explore at least 5+ features in week 1.

### 2. Features Gap is the #1 Churn Reason
19% of churned accounts cited missing features as their reason for leaving — the highest of any churn reason.

**Recommendation:** Conduct a feature gap analysis by surveying churned users to identify the most requested missing features and prioritize them in the product roadmap.

### 3. Budget & Pricing Drive ~32% of Churn
Combined, budget (17.33%) and pricing (15.17%) account for nearly a third of all churn. Notably, budget-churned users had the highest reactivation rate (12 users came back).

**Recommendation:** Introduce a plan pause option or a discounted recovery offer for budget-constrained users before they fully churn.

### 4. Support Quality Did Not Drive Churn
Retained and churned users had nearly identical support satisfaction scores (3.98 vs 4.01) and resolution times (~35.9 hrs each). Support is not the root cause of churn in this dataset.

### 5. Partner Channel Converts Best
Among all referral sources, the partner channel delivered the highest quality users with the best conversion rate.

**Recommendation:** Increase investment in partner acquisition channels and referral programs.

---

## 📈 Tableau Dashboard

👉 **[View Interactive Dashboard](https://public.tableau.com/app/profile/harshitha.thangella/viz/RavenStackTrial-to-PaidConversionAnalysis/Dashboard1?publish=yes)** 

The dashboard includes:
- Conversion Funnel (Total → Trial → Churned → Converted)
- Churn Reasons Breakdown
- Feature Usage: Converted vs Churned Users
- Monthly Churn Trend

---

## 🗂️ Project Structure

```
trial-to-paid-analysis/
│
├── data/
│   ├── ravenstack_accounts.csv
│   ├── ravenstack_subscriptions.csv
│   ├── ravenstack_feature_usage.csv
│   ├── ravenstack_support_tickets.csv
│   └── ravenstack_churn_events.csv
│
├── charts/
│   ├── account_overview.png
│   ├── signup_trend.png
│   ├── conversion_funnel.png
│   ├── conversion_by_segment.png
│   ├── feature_usage_comparison.png
│   ├── feature_diversity.png
│   ├── churn_analysis.png
│   └── monthly_churn.png
│
├── Trial_to_Paid_Conversion_Analysis.ipynb
└── README.md
```

---

## 🚀 How to Run

1. Clone this repository
```bash
git clone https://github.com/harshithathangella/trial-to-paid-analysis.git
```

2. Open the notebook in Google Colab or Jupyter

3. Upload the 5 CSV files from the `data/` folder

4. Run all cells top to bottom

---

## 💡 SQL Queries Used

- Conversion rate by plan tier and referral source
- Top features used by converted vs churned users
- Revenue breakdown by plan tier and billing frequency
- Churn reason analysis with refund and reactivation data
- Support ticket impact on retention

---

## 👩‍💻 Author

**Thangella Harshitha**  
[GitHub](https://github.com/harshithathangella) · [LinkedIn](https://www.linkedin.com/in/thangella-harshitha-654668262/)

> Dataset credit: River @ Rivalytics — used for educational and portfolio purposes under MIT-like license.
