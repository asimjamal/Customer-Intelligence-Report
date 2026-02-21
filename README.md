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
 ┗ 📄 Data Folder                    ← Dataset Zip (download from Kaggle, not tracked in git)
```

---

## 🔬 Analysis Roadmap

| Phase | Status | Description |
|---|---|---|
| 1️⃣ Setup & Data Loading | ✅ Complete | Environment setup, loading CSV, first look at schema and data quality |
| 2️⃣ Data Cleaning | 🔄 In Progress | Handling nulls, cancellations, bad records, duplicates |
| 3️⃣ Revenue & Sales Analysis | ⏳ Upcoming | Monthly trends, top products, top markets |
| 4️⃣ RFM Segmentation | ⏳ Upcoming | Customer scoring, segment labeling (Champions, At-Risk, Lost, etc.) |
| 5️⃣ Cohort Analysis | ⏳ Upcoming | Retention heatmap by customer acquisition month |
| 6️⃣ Insights & Recommendations | ⏳ Upcoming | Business narrative and strategic recommendations |

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

## 💡 Key Insights

> _This section will be populated at the end of each phase as findings emerge._

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
