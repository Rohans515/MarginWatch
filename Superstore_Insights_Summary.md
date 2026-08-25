# Superstore Sales & Profitability Analysis — Insights Summary

**Dataset:** Superstore Orders (9,994 rows, 22 columns) — self-cleaned (nulls, duplicates, and errors handled), with a self-derived `Revenue` column (Sales × Quantity) added to distinguish per-unit price from total order value.

**Tools used:** SQL (SQLite via Python) for primary analysis, Excel (PivotTables + formulas) for cross-validation, Power BI for visualization and forecasting.

---

## 1. Overall Business Snapshot
- Total Revenue, Total Profit, and overall Profit Margin % calculated as headline KPIs for the dashboard.

## 2. Category & Sub-Category Performance
- Full revenue and profit breakdown by Category and Sub-Category.
- Highlighted where high revenue does not translate to high profit.

## 3. Loss-Making Sub-Categories
Three sub-categories are net loss-making despite meaningful revenue:

| Sub-Category | Total Revenue | Total Profit | Margin % |
|---|---|---|---|
| Tables | ₹11,44,514 | -₹17,725 | -1.55% |
| Bookcases | ₹5,97,826 | -₹3,472 | -0.58% |
| Supplies | ₹2,01,236 | -₹1,189 | -0.59% |

## 4. Discount vs Profit — Core Insight #1
Discount level has a direct, systematic relationship with profitability across the entire dataset:

| Discount Band | Orders | Total Profit | Avg Profit/Order |
|---|---|---|---|
| 0% | 4,798 | ₹3,20,988 | ₹66.90 |
| 1–10% | 94 | ₹9,029 | ₹96.06 |
| 11–20% | 3,709 | ₹91,756 | ₹24.74 |
| 21–30% | 227 | -₹10,369 | -₹45.68 |
| 30%+ | 1,166 | -₹1,25,007 | -₹107.21 |

**Root-cause example — Supplies sub-category:** at 0% discount, Supplies orders average +₹14.69 profit; at 20% discount, they average -₹39.83 (driven heavily by low-margin products like electric letter openers).

**Recommendation:** Cap discounts at 20% or restrict deeper discounts to high-margin categories only.

## 5. Region & State Profitability — Core Insight #2
All 4 regions are profitable at the aggregate level (West highest, Central lowest), which **masks a state-level problem**. Drilling down reveals 10 loss-making states, led by:

| State | Total Profit |
|---|---|
| Texas | -₹25,729 |
| Ohio | -₹16,971 |
| Pennsylvania | -₹15,560 |
| Illinois | -₹12,608 |

Cross-validated against Insight #1: both Texas and Ohio are profitable at 11–20% discount but swing sharply negative at 30%+ discount (Texas: +₹8,226 → -₹29,223), confirming the same discount-driven loss pattern at the state level.

**Recommendation:** Aggregate regional reporting can hide problem areas — state-level (or product-level) drill-down should be a standard part of profitability review, not an exception.

## 6. Time Trend — Core Insight #3
- 2016–2017 show stronger overall sales than 2014–2015.
- Nov–Dec (festive season) revenue grows year-over-year, but profit margin stays flat (roughly 2–3%) rather than scaling with revenue — consistent with increased discounting during the festive push.

**Recommendation:** Review festive-season discount policy specifically; volume growth is not converting into proportional profit growth.

## 7. Customer Segment Performance
| Segment | Orders | Total Profit | Margin % | Avg Discount |
|---|---|---|---|---|
| Consumer | 5,191 | ₹1,34,119 | 2.30% | 0.158 |
| Corporate | 3,020 | ₹91,979 | 2.62% | 0.158 |
| Home Office | 1,783 | ₹60,299 | 2.80% | 0.147 |

Consumer drives the most absolute profit (volume-led), but Home Office is the most margin-efficient segment, aided by a lower average discount.

## 8. Customer Concentration (Pareto Check)
Classic 80/20 expectations do **not** hold here — approximately 793 customers (nearly the entire customer base) are needed to reach 80% of total profit. Profit is broadly distributed rather than concentrated in a small set of "whale" accounts, indicating a diversified customer base with no single point of revenue risk.

---

## Overall Narrative
The single biggest lever on profitability in this business is **discounting policy**, not category, region, or customer mix. Discounts above 20% are consistently value-destructive across products (Supplies), states (Texas, Ohio), and seasons (Nov–Dec), while the customer base itself is healthily diversified with no concentration risk.
