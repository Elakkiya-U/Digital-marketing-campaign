# Digital Marketing Campaign Conversion Prediction

A machine learning project to predict whether a customer will convert based on digital marketing campaign data.

---

## 🧠 Problem Statement

The objective is to build a predictive model using customer and campaign interaction data to identify which customers are most likely to convert. This helps marketing teams better target their efforts and improve campaign ROI.

---

## 📂 Dataset

**Source**: [Digital_Marketing_Campaign_Dataset](https://github.com/Elakkiya-U/Digital-marketing-campaign/blob/main/Digital_Marketing_Campaign_Dataset.csv)

---

## 📊 Dataset Description

### 🎯 Demographic Information
- `CustomerID`: Unique identifier for each customer
- `Age`: Age of the customer
- `Gender`: Male or Female
- `Income`: Annual income (USD)

### 📣 Marketing Variables
- `CampaignChannel`: Email, Social Media, SEO, PPC, Referral
- `CampaignType`: Awareness, Consideration, Conversion, Retention
- `AdSpend`: Campaign spend (USD)
- `ClickThroughRate`: Percentage of clicks per impression
- `ConversionRate`: Clicks that result in conversion

### ⚙️ Engagement Metrics
- `WebsiteVisits`: Number of visits
- `PagesPerVisit`: Avg pages per session
- `TimeOnSite`: Avg time per visit (minutes)
- `SocialShares`, `EmailOpens`, `EmailClicks`: Engagement levels

### 📦 Purchase History
- `PreviousPurchases`: Count of past purchases
- `LoyaltyPoints`: Points earned

### 🏁 Target Variable
- `Conversion`: 1 = Converted, 0 = Not Converted

---

## 🔄 Project Workflow

1. **Data Preprocessing** (nulls, encoding, outliers)
2. **Exploratory Data Analysis (EDA)** (visuals, insights)
3. **Feature Engineering**
4. **Model Training** (Logistic Regression, Random Forest, Gradient Boosting,and Decision tree)
5. **Model Evaluation** (Accuracy, ROC-AUC, Confusion Matrix)

---

## 🛠 Tech Stack

- Python, Pandas, NumPy, Scikit-Learn
- Matplotlib, Seaborn
- VS Code / Jupyter
- Power BI Dashboard

---

## 📈 Model Evaluation Summary

Four classification models were trained and compared using:
- Accuracy, Precision, Recall, F1 Score
- ROC-AUC Score
- Confusion Matrix
- Classification Report

> Given the **class imbalance** (many more converters than non-converters), the focus was on recall and F1-score for both classes — especially for the minority class (non-converters).

---

## 🔍 Key Observations

- **Accuracy alone was misleading** — many models predicted converters well but ignored non-converters.
- Logistic Regression and Random Forest had **high recall for Class 1** but very low recall for Class 0.
- **Gradient Boosting** delivered the best balance:
            Accuracy : 92%
            Precision (1) : 0.92
            Recall (1) : 0.99
            Recall (0) : 0.40 (best among all)
            F1 Score (0) : 0.55
            ROC-AUC : 0.84

---

## 🧾 Final Conclusion

**Gradient Boosting** was the most effective model, providing the most balanced performance across both customer segments. With its superior ability to detect both likely and unlikely converters, it is the best choice for deployment in this marketing campaign context.

It supports more efficient campaign targeting, increased ROI, and better customer segmentation strategy.

---

