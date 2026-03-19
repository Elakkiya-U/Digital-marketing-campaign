# Digital Marketing Campaign - Conversion Prediction

Predicts whether a customer will convert based on digital marketing campaign data using four machine learning models.

---

## Problem Statement

Marketing teams invest budgets across multiple channels without knowing which customers are likely to convert. This project builds a classification model to identify high-probability converters, enabling smarter campaign targeting and spend optimisation.

---

## Dataset

- **Source:** Kaggle - Digital Marketing Campaign Dataset
- **Records:** 8,000 customers
- **Features:** 22 (age, income, ad spend, email engagement, loyalty points, campaign type, channel, and more)
- **Target:** `Conversion` - 1 (converted) or 0 (not converted)
- **Class distribution:** 87.6% converted · 12.4% not converted (imbalanced)

---

## Approach

1. Exploratory Data Analysis - conversion rates by channel, campaign type, and age
2. Data cleaning - removed null columns, converted currency strings to float, dropped redundant derived features
3. Class imbalance handling - applied `class_weight="balanced"` to all models
4. Encoding - Label Encoding for categorical features (Gender, CampaignChannel, CampaignType)
5. Outlier detection - Z-score analysis (outliers retained; tree models are robust to them)
6. Feature engineering - StandardScaler for Logistic Regression
7. Model training - four classifiers compared
8. Feature importance comparison - RF vs Gradient Boosting agreement analysis

---

## Model Results

| Model | Accuracy | F1 Score | ROC-AUC |
|-------|----------|----------|---------|
| Logistic Regression | 0.75 | 0.84 | 0.77 |
| Decision Tree | 0.78 | 0.92 | 0.67 |
| Random Forest | 0.89 | 0.89 | 0.81 |
| **Gradient Boosting** | **0.91** | **0.92** | **0.81** |

**Winner: Gradient Boosting** - 91% accuracy, 0.92 F1 Score, 0.81 ROC-AUC.

> **Why F1 Score matters here:** With 87.6% of customers already converted, a model predicting "always convert" would achieve 87.6% accuracy while being useless. F1 Score and ROC-AUC are the reliable metrics for imbalanced classification problems.

---

## Key Findings

- **Gradient Boosting outperforms Random Forest** because it builds trees sequentially - each tree corrects the previous one's errors. This makes it better at identifying the harder-to-classify non-converters.
- **Both models agree** that loyalty points, email opens, email clicks, and ad spend are the strongest conversion signals - confirmed through a feature importance agreement scatter plot.
- **Business recommendation:** Re-engage customers with high loyalty points and strong email interaction before investing in new customer acquisition.

---

## Visualisations Generated

| File | Description |
|------|-------------|
| `target_distribution.png` | Conversion count and rate breakdown |
| `conversion_by_channel.png` | Conversion rate by campaign channel |
| `conversion_by_type.png` | Conversion rate by campaign type |
| `age_distribution.png` | Age distribution by conversion outcome |
| `correlation_heatmap.png` | Feature correlation matrix |
| `model_comparison.png` | All 4 models across all metrics |
| `confusion_matrices.png` | Side-by-side confusion matrices |
| `roc_curves.png` | All 4 ROC curves on one chart |
| `feature_importance_comparison.png` | RF vs GB feature importance side-by-side |
| `rf_vs_gb_agreement.png` | Scatter plot of feature importance agreement |

---

## Tools & Libraries

![Python](https://img.shields.io/badge/Python-3.9-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?logo=pandas)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3-F7931E?logo=scikit-learn)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7-blue)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)

**Core libraries:** pandas · numpy · scikit-learn · matplotlib · seaborn · scipy

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/Elakkiya-U/Digital-marketing-campaign.git
cd Digital-marketing-campaign

# 2. Install dependencies
pip install pandas numpy scikit-learn matplotlib seaborn scipy openpyxl

# 3. Open the notebook
jupyter notebook Digital_Marketing_Campaign_Conversion.ipynb

# 4. Run all cells (Kernel → Restart & Run All)
```

> The dataset is included in the repository as `Digital_Marketing_Campaign_Dataset.xlsx`. No external downloads needed.

---

## Project Structure

```
Digital-marketing-campaign/
│
├── Digital_Marketing_Campaign_Conversion.ipynb   # Main notebook
├── Digital_Marketing_Campaign_Dataset.xlsx        # Dataset (Excel)
├── README.md                                      # This file
│
└── outputs/                                       # Generated after running notebook
    ├── target_distribution.png
    ├── conversion_by_channel.png
    ├── model_comparison.png
    ├── confusion_matrices.png
    ├── roc_curves.png
    ├── feature_importance_comparison.png
    └── rf_vs_gb_agreement.png
```

---

## Limitations & Future Work

- Dataset may be synthetic - `AdvertisingPlatform` and `AdvertisingTool` are masked
- Hyperparameter tuning with `GridSearchCV` could further improve Gradient Boosting performance
- SMOTE oversampling could be explored as an alternative to `class_weight="balanced"`
- Feature interactions (e.g. AdSpend × LoyaltyPoints) have not been explicitly engineered

---

## Author

**Elakkiya Ulaganathan**  
Customer Operations & CRM Professional | Data Science Certified  
[LinkedIn](https://www.linkedin.com/in/uelakkiya) · [GitHub](https://github.com/Elakkiya-U)

---

*This project was built as part of a Data Science and AI certification and connects directly to 6 years of real-world customer operations experience - where these exact metrics (conversion rate, campaign channel performance, customer engagement) were tracked manually.*
