# Customer Attrition Modeling and Business Strategy

**Author:** Shloke Binani

## Project Overview
This project explores the Telco Customer Churn dataset to understand churn behavior and build an analytical model to predict customer retention. It involves data cleaning, interactive dashboarding, and machine learning classification using the Random Forest algorithm to help businesses achieve a sustainable competitive advantage.

## Tools and Technologies
* **SQL Server:** Data cleaning and preprocessing
* **Power BI:** Interactive dashboards and presentations
* **Python (Jupyter Notebook):** Machine learning (Random Forest), feature analysis, and evaluation
* **Libraries:** pandas, matplotlib, seaborn, scikit-learn

## Dataset and Methodology
To identify drivers of customer attrition and help the business achieve a sustainable competitive advantage, I managed a complete analytical pipeline from data preparation to predictive modeling. I executed data cleaning protocols using SQL to ensure zero defect analysis by formatting account variables and handling missing values. To structure the communication of insights logically, I developed an interactive Power BI dashboard which revealed that fiber optic users experienced a peak 42 percent churn rate. Finally, I generated hypotheses and programmed a Random Forest analytical model in Python that predicted customer departure with an 80 percent accuracy, successfully translating raw data into meaningful insights for targeted retention campaigns.

## Model Evaluation

| Metric | Class 0 (Retained) | Class 1 (Churned) |
| :--- | :--- | :--- |
| Precision | 83% | 67% |
| Recall | 92% | 46% |
| F1 Score | 87% | 55% |

**Overall Accuracy:** 80%

## Key Insights from Research Questions
1. Churned customers stay for an average of 18 months, while retained customers stay around 38 months, indicating longer tenured customers are less likely to churn.
2. Fiber optic users show the highest churn rate at approximately 42 percent, while DSL users churn moderately at 20 percent and customers without internet service churn the least at 6 percent.
3. Month to month contract users churn the most at 45 percent, whereas one year contract users drop to 12 percent and two year contract users are more loyal at 2 percent, proving long term contracts reduce churn.
4. Retained customers have significantly higher Lifetime Value (LTV) than churned ones, indicating that churned users generate less revenue over time.
5. Internet Service and Contract Type had the strongest influence on LTV, while Gender had a negligible impact.

## Business Insights and Recommendations
Based on the analysis of churn behavior, tenure, contract types, and LTV, here are key insights and actions the business can take to reduce customer churn:

**1. Encourage Long Term Contracts**
* **Insight:** Customers on month to month plans have the highest churn (45%), while two year contracts have the lowest (2%).
* **Recommendation:** Offer loyalty rewards, discounts, or perks to encourage longer contract commitments.

**2. Improve Experience for Fiber Optic Users**
* **Insight:** Fiber optic users show the highest churn (42%) among all internet service types.
* **Recommendation:** Investigate pricing or service quality concerns and offer customized plans or customer support.

**3. Strengthen Early Customer Engagement**
* **Insight:** Churned customers typically leave within the first 18 months.
* **Recommendation:** Focus on onboarding, regular engagement, and first year incentives to retain new customers.

**4. Boost Lifetime Value Through Segmentation**
* **Insight:** Contract type and Internet Service significantly affect LTV, while features like gender have little impact.
* **Recommendation:** Use segmentation and upselling strategies to improve LTV among low value customers.

**5. Offer Proactive Technical Support**
* **Insight:** Better service support is linked to higher tenure and retention.
* **Recommendation:** Introduce tech support plans and flag high risk accounts for proactive outreach.

**6. Leverage Machine Learning for Early Churn Prediction**
* **Insight:** The Random Forest model predicts churn with 80% accuracy.
* **Recommendation:** Use the model to trigger retention campaigns before customers decide to leave.