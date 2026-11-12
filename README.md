# Customer Attrition Modeling and Retention Strategy

**Author:** Shloke Binani | Academic project

![Power BI dashboard](images/dashboard.png)

## Overview
This project analyzes the public [Telco Customer Churn dataset](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) (7,043 customers, 21 features) to find out who churns and why, tests whether the patterns are statistically real, and trains a Random Forest model to flag at-risk customers. Findings are summarized in a Power BI dashboard and turned into retention recommendations.

**Headline results**
- 26.5% of customers churned (1,869 of 7,043).
- Month-to-month customers churn at 43%, against 3% on two-year contracts.
- The Random Forest reaches 0.83 ROC AUC and 80% accuracy on a held-out 20% test set. Predicting "no churn" for everyone scores 73.5%, so accuracy alone is a weak measure here.
- The top 20% of customers by risk score contain about 50% of all churners (2.5x lift).

## Tools
Python (pandas, scikit-learn, SciPy, matplotlib, seaborn), Power BI

## Repository contents
| File | Purpose |
| :--- | :--- |
| `CUSTOMER ATTRITION _final.ipynb` | Analysis, hypothesis tests, model, scenario analysis |
| `Customer-Churn_Telco_Clean.csv` | Cleaned dataset used by the notebook and dashboard |
| `churn_dashboard.pbix` | Power BI dashboard (screenshot above) |
| `requirements.txt` | Python dependencies |

## Key findings
| Segment | Churn rate |
| :--- | :--- |
| Month-to-month contract | 43% |
| One-year contract | 11% |
| Two-year contract | 3% |
| Fiber optic internet | 42% |
| DSL internet | 19% |
| No internet service | 7% |
| Electronic check payment | 45% |
| Other payment methods | 15% to 19% |
| Senior citizens | 42% |
| Non-senior customers | 24% |
| Gender (female / male) | 26.9% / 26.2% |

- Churned customers stayed 18 months on average; retained customers stayed 38.
- Lifetime value (monthly charge x tenure) averages USD 1,532 for churned customers and USD 2,550 for retained customers.
- Internet service and contract type vary LTV the most. Gender has no measurable effect.

## Hypothesis tests (alpha = 0.05)
Null hypothesis: churn is independent of the variable. Chi-square tests of independence, with Cramer's V as effect size.

| Variable | p-value | Cramer's V | Decision |
| :--- | :--- | :--- | :--- |
| Contract | < 0.001 | 0.41 | Reject H0 |
| Internet service | < 0.001 | 0.32 | Reject H0 |
| Payment method | < 0.001 | 0.30 | Reject H0 |
| Senior citizen | < 0.001 | 0.15 | Reject H0 |
| Gender | 0.49 | 0.01 | Fail to reject H0 |

Welch t-tests: churned customers have significantly lower tenure (18.0 vs 37.6 months, p < 0.001) and higher monthly charges (USD 74.44 vs USD 61.27, p < 0.001).

## Model evaluation
Random Forest (100 trees), 80/20 train-test split, `random_state=42`.

| Metric | Retained | Churned |
| :--- | :--- | :--- |
| Precision | 0.82 | 0.67 |
| Recall | 0.92 | 0.46 |
| F1 | 0.87 | 0.54 |

- Accuracy: 79.6% (baseline 73.5%). ROC AUC: 0.833 (5-fold cross-validated AUC: 0.82).
- Top 10% of risk scores: 76% churned (2.9x lift). Top 20%: 66% churned, capturing 50% of all churners.
- The model finds fewer than half of churners at the default 0.5 threshold, so it is better used to rank customers by risk than to make yes/no calls.

## Scenario analysis
These scenarios rest on stated assumptions and are observational, not causal estimates.

1. **Contract migration.** If 10% / 20% / 30% of month-to-month customers moved to one-year contracts and then churned like current one-year customers, about 122 / 244 / 365 fewer customers would churn, protecting roughly USD 97K / USD 194K / USD 291K of annual revenue.
2. **Targeted outreach.** Contacting the top 20% of risk scores on the test set reaches 185 actual churners. If an offer saves 10% / 20% / 30% of them, that keeps 18 / 37 / 56 customers, about USD 17K / USD 35K / USD 52K of annual revenue.

## Recommendations
1. **Encourage longer contracts.** Month-to-month churn is 43% against 3% for two-year plans, so offer discounts or perks for committing.
2. **Investigate fiber optic.** It has the highest churn (42%); review pricing and service quality for this segment.
3. **Focus on the first 18 months.** Churned customers leave after 18 months on average, so strengthen onboarding and first-year incentives.
4. **Review electronic check customers.** They churn at 45%; nudging them to automatic payment is worth testing.
5. **Prioritize outreach by risk score.** Use the model to rank customers and contact the highest-risk 20% first.
6. **Offer technical support plans** and flag high-risk accounts for proactive contact.

## Limitations
- Single train-test split with no hyperparameter tuning; churner recall is 46% at the default threshold.
- LTV is a simple proxy (monthly charge x tenure), not a forecast of future revenue.
- The scenario estimates assume customers who switch contracts behave like existing customers on those contracts.
- The dataset is a public benchmark, not a live business, so no recommendation was tested in practice.

## How to run
```
pip install -r requirements.txt
jupyter notebook "CUSTOMER ATTRITION _final.ipynb"
```
