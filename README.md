# MarginWatch — Discount-Driven Profitability Dashboard

A Superstore sales and profitability analysis project uncovering **why discounting is silently destroying profit** — built end-to-end using SQL, Excel, and Power BI.

---

## 📌 Problem Statement

A retail Superstore's raw order data (9,994 orders, 22 columns) was analyzed to answer a core business question: *where is the company actually making and losing money, and why?* The analysis moves beyond surface-level revenue reporting to uncover root causes behind unprofitable orders, states, and seasons.

## 🛠️ Tools & Skills Used

- **SQL (SQLite via Python)** — primary analysis engine; used `GROUP BY`, `HAVING`, `CASE WHEN`, `CTEs`, and window functions (`SUM() OVER`, `ROW_NUMBER()`)
- **Excel** — PivotTables, `IFS()`, calculated fields — cross-validated all SQL findings
- **Power BI** — DAX measures, a custom Date table, discount-band segmentation, state-level map, and built-in ETS forecasting
- **Python (Pandas)** — initial data loading and inspection

## 🧹 Data Preparation

The dataset was self-cleaned prior to analysis: null values handled, duplicates removed, and data errors corrected. A `Revenue` column (Sales × Quantity) was derived to separate per-unit price from total order value.

## 🔎 Key Insights

1. **Discount is the #1 driver of unprofitability.** Orders with 30%+ discount lost ₹1,25,007 net across 1,166 orders (avg -₹107/order), while 0% discount orders averaged +₹66.90/order.
2. **Region-level profitability hides state-level losses.** All 4 regions are profitable in aggregate, but Texas (-₹25,729) and Ohio (-₹16,971) are significant loss-makers at the state level — both driven by the same 30%+ discount pattern.
3. **Furniture (Tables, Bookcases) and Office Supplies (Supplies) are net loss-making sub-categories**, despite meaningful revenue.
4. **Festive season (Nov–Dec) revenue grows year-over-year, but profit margin stays flat** (~2–3%), suggesting margin isn't scaling with the discount-driven volume push.
5. **Home Office is the most margin-efficient segment** (2.80% margin, lowest avg. discount), while Consumer drives the most absolute profit through volume.
6. **Profit is not concentrated in a few customers.** Unlike the typical 80/20 rule, ~793 of the customer base is needed to reach 80% of total profit — a healthily diversified customer base.

*(Full breakdown with tables and recommendations in [`Superstore_Insights_Summary.md`](./Superstore_Insights_Summary.md).)*

## 📊 Dashboard

**MarginWatch** is a 3-page interactive Power BI dashboard:
**Page 1 — Executive Overview:** KPI cards, profit by sub-category, segment split, top customers, interactive slicers
![Page 1 - Executive Overview]("E:\ScreenShots\Page1.png")

**Page 2 — Regional & Discount Deep-Dive:** State-level profit map with discount-band breakdown
![Page 2 - Regional Deep-Dive]("E:\ScreenShots\Page2.png")

**Page 3 — Forecast:** Revenue and Profit trend with built-in Power BI (ETS) forecasting and confidence intervals
![Page 3 - Forecast]("E:\ScreenShots\Page3.png")




## 📁 Repository Structure

```
MarginWatch/
├── data/
│   └── Sample - cleaned Superstore.xlsx
├── notebooks/
│   └── superstore_analysis.ipynb      # SQL + Pandas analysis
├── excel/
│   └── Sample - cleaned Superstore.xlsx       # PivotTable-based analysis
├── powerbi/
│   └── MarginWatch.pbix
├── ScreenShots/
│   └── (dashboard page images)
├── Superstore_Insights_Summary.md
└── README.md
```

## ▶️ How to Reproduce

1. Clone the repo and open `notebooks/superstore_analysis.ipynb`
2. Run cells sequentially — loads the cleaned CSV into a Pandas DataFrame and SQLite database
3. Run the SQL queries to reproduce each business question's analysis
4. Open `powerbi/MarginWatch.pbix` in Power BI Desktop to explore the interactive dashboard

## 👤 Author

**Rohan Choudhary**
B.Tech CSE (Data Science & Analytics), JECRC University, Jaipur
[GitHub](https://github.com/Rohans515) • [LinkedIn](https://linkedin.com/in/rohan-choudhary-80422a250)
