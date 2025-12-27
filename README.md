# Customer Churn Analysis & Prediction – StreamWorks Media

## 📊 Project Overview
This project analyzes customer churn at **StreamWorks Media**, a UK-based streaming platform competing with services such as Netflix and Amazon Prime. The goal is to understand why customers leave, identify at-risk subscribers early, and uncover behaviors that impact revenue and engagement.

The analysis combines **data cleaning, exploratory data analysis, statistical testing, feature engineering, machine learning models, and business insights** to support customer retention and sustainable growth.

---

## 🎯 Business Objectives
1. **Understand churn patterns** – identify who is leaving and potential reasons.
2. **Predict churn probability** – flag at-risk customers for early intervention.
3. **Explore revenue-impacting behaviors** – such as viewing habits, subscription type, device usage, and tenure.

---

## 📂 Dataset Description
- **Records:** 1,500 subscribers (1,495 after cleaning)
- **Features:** Demographics, subscription details, monthly fees, viewing hours, device usage, complaints, promotions, referrals, and churn status
- **Target Variable:** `is_churned`

---

## 🧹 Data Cleaning & Preparation
Key steps included:
- Standardized column names for consistency
- Handled missing values:
  - Numerical features imputed using median values
  - Categorical features filled with the most frequent category
  - Monthly fees imputed using median values within subscription types
- Removed rows with missing churn labels
- Converted date columns to datetime format
- Removed non-predictive identifiers (`user_id`)

### Feature Creation
- `tenure_days`: Days between signup and last activity
- `is_loyal`: Tenure greater than 180 days
- `watch_per_fee_ratio`: Engagement relative to subscription cost
- `heavy_mobile_user`: >70% viewing on mobile
- `promo_low_watch`: Low watch time users who received promotions

Final dataset: **28 features**, ready for modeling.

---

## 🛠 Feature Engineering
- Age grouped into meaningful categories
- One-hot encoding applied to categorical variables
- Interaction features created to capture complex behavior patterns

---

## 📈 Exploratory Analysis & Key Findings
### Statistical Tests
- **Gender:** No significant relationship with churn (p = 0.36)
- **Promotions:** Slightly lower churn for promoted users (not statistically significant)
- **Referrals:** No meaningful effect on churn
- **Watch Time:** No significant difference between churned and retained users

### Behavioral Insights
- Churn is weakly influenced by demographics
- Engagement metrics (tenure, plan type) provide stronger behavioral signals
- Promotions show potential as a retention lever despite weak statistical evidence

---

## 🤖 Machine Learning Models

### 1. Logistic Regression – Churn Prediction
- **Accuracy:** 76.7% (misleading due to class imbalance)
- **ROC-AUC:** 0.486 (worse than random)
- Failed to correctly identify churners
- Indicates need for class balancing or advanced models (e.g., tree-based methods)

**Top Influencing Features:**
- Country (India)
- Monthly fee
- Gender (Other)
- Customer tenure (`is_loyal`)

---

### 2. Linear Regression – Watch Time Prediction
- **R²:** 0.89
- **RMSE:** 7.23
- **MAE:** 5.81

When grouped into low vs. high watch time:
- **Accuracy:** 98%
- Excellent precision and recall

**Top Predictors of Engagement:**
- Premium subscription
- Monthly fee
- Watch-per-fee ratio
- Country (UK, USA, Germany)
- Heavy mobile usage

---

## ⏱ Time Series Analysis
- Churn rates are generally stable across signup cohorts
- Temporary spike observed mid-2024, likely event-driven
- Indicates consistent onboarding but rising churn among existing users

---

## 💡 Business Recommendations
1. **Prioritize high-risk segments**
   - UK customers, Standard plan users, female subscribers
   - Low-watch, mobile-heavy users

2. **Targeted promotions**
   - Focus on low-engagement, high-risk users
   - Avoid blanket discounting

3. **Encourage Premium adoption**
   - Free trials, discounts, and bundles
   - Premium users show higher engagement and lower churn

4. **Improve customer support**
   - Faster complaint resolution to reduce churn risk

---

## ⚠️ Limitations
- Class imbalance affects churn prediction performance
- Missing and imputed fee data may introduce bias
- Results should be interpreted with caution

---

## 📁 Repository Contents
- `Churn Prediction for StreamWorks Media.ipynb` – Full analysis, modeling, and visualizations
- Data preprocessing, feature engineering, statistical tests, ML models, and charts

---

## 🧰 Tools & Technologies
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebook

---

## 📌 Conclusion
This project demonstrates how data-driven analysis can identify churn risks and guide retention strategies. While churn prediction remains challenging due to data imbalance, engagement modeling reveals clear drivers of customer value. Targeted promotions, premium adoption, and improved customer support offer actionable paths to reducing churn and increasing lifetime value.
