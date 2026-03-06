# 🛒 Customer Intelligence Report — Online Retail II

> An end-to-end Exploratory Data Analysis project built to surface actionable marketing insights from real transactional data. Developed as part of my BI Analyst portfolio.

---

## 📌 Project Overview

This project performs a full customer analytics deep-dive on the **Online Retail II dataset** (UCI / Kaggle) — a real dataset from a UK-based online retailer covering transactions between **2009 and 2011**.

The analysis is framed as if presenting to a marketing leadership team, with each phase producing business-ready insights rather than just charts.

---

## 🎯 Objectives

- Practice and showcase **advanced EDA** skills in Python and SQL
- Build a **customer segmentation model** using RFM analysis
- Perform **cohort-based retention analysis**
- Tell a clear **data story** that a non-technical stakeholder can follow
- Produce clean, well-documented code suitable for a professional portfolio

---

## 📂 Dataset

| Field | Detail |
|---|---|
| **Source** | [Kaggle — Online Retail II UCI](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci) |
| **File** | `online_retail_II.csv` |
| **Period** | December 2009 — December 2011 |
| **Size** | ~1 million rows |
| **Columns** | Invoice, StockCode, Description, Quantity, InvoiceDate, Price, Customer ID, Country |

> ⚠️ The dataset file is not included in this repo due to size, although i have included the zip file in the data folder if you wish you download it from here or download it directly from Kaggle and place it in the root folder before running the notebook.

---

## 🗂️ Project Structure

```
📦 customer-intelligence-report
 ┣ 📓 customer_analytics_eda.ipynb   ← Main analysis notebook
 ┣ 📄 README.md                      ← You are here
 ┣ 🖼️ cohort_heatmap.png
 ┣ 🖼️ segment_matrix.png
 ┗ 📄 Data Folder                    ← Dataset Zip (download from Kaggle, not tracked in git)
```

---

## 🔬 Analysis Roadmap

### Core Notebook (Phases 1–6)

| Phase | Status | Description |
|---|---|---|
| 1️⃣ Setup & Data Loading | ✅ Complete | Environment setup, loading CSV, first look at schema and data quality |
| 2️⃣ Data Cleaning | ✅ Complete | Removed duplicates, cancellations, missing IDs, bad price/quantity records |
| 3️⃣ Revenue & Sales Analysis | ✅ Complete | Monthly trends, seasonality, top products, top markets, Pareto analysis |
| 4️⃣ RFM Segmentation | ✅ Complete | Customer scoring on Recency, Frequency, Monetary; 6 named segment labels |
| 5️⃣ Cohort Analysis | ✅ Complete | Retention heatmap, cohort curves, avg retention by month index |
| 6️⃣ Insights & Recommendations | ✅ Complete | Executive KPI summary, 4 business insights, segment action matrix |

### Advanced Notebook (Phases 7–10)

| Phase | Status | Description |
|---|---|---|
| 7️⃣ Churn Prediction Model | ✅ Complete | Random Forest classifier, ROC-AUC 0.804, ranked at-risk customer list |
| 8️⃣ Customer Lifetime Value | ✅ Complete | Historical CLV, predicted CLV, priority matrix, retention budget calculator |
| 9️⃣ Time-Between-Purchases | 🔄 In Progress | Purchase gap analysis, repurchase cycle detection, early churn signals |
| 🔟 Product Affinity Analysis | ⏳ Upcoming | Basket analysis, frequently bought together, cross-sell opportunities |

---
## 🧹 Data Cleaning Decisions

| Issue | Rows Affected | Decision |
|---|---|---|
| Duplicate rows | ~5,268 | Dropped — skew all aggregations |
| Cancelled invoices (prefix 'C') | ~22,950 | Removed from main df; saved in `df_cancelled` |
| Missing Customer ID | 243,007 (22.77%) | Dropped — required for all customer-level analysis |
| Zero/negative Price or Quantity | ~6,207 | Dropped — data entry errors, not real transactions |

---
## 💡 Key Insights

> **Phase 3 — Revenue & Sales**
> - Revenue grew consistently 2009–2011 with a sharp Q4 spike driven by pre-Christmas wholesale purchasing
> - **November** is the single highest revenue month; summer months (Jun–Aug) are a consistent trough
> - UK dominates revenue; top international markets are Netherlands, Ireland, Germany, and France
> - Classic **Pareto pattern** — a small % of customers generate the majority of revenue

> **Phase 4 — RFM Segmentation**
> - Champions are few but generate a disproportionate share of total revenue — the highest-ROI retention target
> - At Risk customers represent significant revenue about to be lost — immediate re-engagement needed
> - Potential Loyalists bought recently but infrequently — a key growth segment to convert
> - 6 named segments mapped to concrete marketing actions (reward, upsell, win-back, suppress)

> **Phase 5 — Cohort Retention**
> - Month 1 retention averages 22.5% — 1 in 4 customers returns the following month
> - Gradual decline to ~15% through Month 10 with no single churn cliff — healthy pattern
> - Month 11-12 uptick (15% to 18.2%) reveals annual wholesale repurchase behaviour
> - Biggest lever: a 30-day post-first-purchase re-engagement sequence targeting Month 1
>
> **Phase 6 — Business Recommendations**
> - Launch summer campaigns (Jun–Aug) to smooth the seasonal revenue trough
> - Immediate win-back campaign for 192 At Risk customers — over £400K in at-risk revenue
> - Build a Loyal customer retention programme — losing one Loyal customer = losing 13x a Lost one
> - Automate re-engagement triggers at the 10-month mark to capture annual repurchase cycle
>
> **Phase 7 — Churn Prediction**
> - ROC-AUC of 0.804 — model genuinely learns behavioural churn patterns
> - **Tenure** is the single strongest predictor — loyalty is built over time, not just transactions
> - **UniqueProducts** is 2nd — customers who buy across more categories are harder to churn
> - £4.2M sits in the Medium Risk tier — the most cost-effective retention target
>
> **Phase 8 — Customer Lifetime Value**
> - 324 customers sit in the Urgent quadrant (High CLV + High Churn Risk)
> - £780K historical revenue at stake in Urgent quadrant alone
> - Suggested retention budget of £219K covers the entire Urgent segment at 15% of predicted CLV
> - Protect segment (2,615 customers) holds 89.1% of all revenue — the entire business runs on this group
> - 2 Loyal customers appear in the Urgent quadrant — most alarming signal, active but showing churn behaviour
> - Top Urgent customer (ID 12346) has £77K historical CLV — warrants personal outreach, not just email
> - Lost/Inactive dominates the Urgent list — high-value customers who left but have strong predicted CLV to recover

---

## 🤖 Model Summary — Churn Prediction (Phase 7)

| Item | Detail |
|---|---|
| **Algorithm** | Random Forest Classifier |
| **Features** | Frequency, Monetary, AvgOrderValue, AvgDaysBetween, StdDaysBetween, UniqueProducts, Tenure |
| **Churn Definition** | No purchase within 60 days of reference date (Dec 10, 2011) |
| **Test ROC-AUC** | 0.804 |
| **Top Churn Predictor** | Tenure (0.290) — long-tenure customers are significantly less likely to churn |
| **High Risk Customers** | 2,413 customers — £1.4M revenue at stake |
| **Medium Risk Customers** | 2,149 customers — £4.2M revenue at stake |

> **Key finding:** Customers with `Tenure = 0` and `Frequency = 1` (one-time buyers with no loyalty history) dominate the High Risk tier. The biggest churn lever is converting first-time buyers into repeat purchasers.

---

## 💰 CLV Summary (Phase 8)

| Item | Detail |
|---|---|
| **Historical CLV** | Total revenue per customer to date |
| **Predicted CLV** | AvgOrderValue × Purchase Frequency Rate × Personal Lifespan |
| **Urgent Quadrant** | 324 customers — High CLV + High Churn Risk |
| **Revenue at Stake** | £780,499 in the Urgent quadrant alone |
| **Suggested Retention Budget** | £219,879 (@ 15% of predicted CLV per customer) |

---
## 🛠️ Tools & Libraries

| Tool | Purpose |
|---|---|
| `Python 3.9+` | Core language |
| `pandas` | Data manipulation and SQL-style analysis |
| `numpy` | Numerical operations |
| `matplotlib` | Base visualizations |
| `seaborn` | Statistical plots and heatmaps |
| `sqlite3` | In-notebook SQL queries |
| `Jupyter Notebook` | Interactive development environment |

---

## 📊 Project Previews

### Cohort Retention Heatmap
<img width="973" height="650" alt="image" src="https://github.com/user-attachments/assets/dc70e84d-a60f-4e5f-934f-69dc8ab8d97c" />

### Customer Segment Strategy Matrix
<img width="973" height="612" alt="image" src="https://github.com/user-attachments/assets/f0e0c304-bdbc-4873-855e-ac2562d9ba7d" />

```
---

## ▶️ How to Run

```bash
# 1. Clone the repo
git clone https://github.com/your-username/customer-intelligence-report.git
cd customer-intelligence-report

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn notebook

# 3. Download the dataset from Kaggle and place it in the root folder
#    → online_retail_II.csv

# 4. Launch Jupyter
jupyter notebook customer_analytics_eda.ipynb
```

---

## 👤 Author

**Asim Jamal**  
Python · SQL · Data Storytelling  
[LinkedIn](https://www.linkedin.com/in/asimjamal/)

---

## 📄 License

This project is open source under the [MIT License](LICENSE).  
The dataset belongs to its original authors via UCI Machine Learning Repository.
