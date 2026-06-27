# Customer Segmentation using RFM Analysis | Power BI

![Dashboard Overview](screenshots/overview.png)

## 📌 Project Overview

An end-to-end customer segmentation project built on the 
UCI Online Retail Dataset containing 541,909 transactions 
from December 2010 to December 2011. This project uses 
RFM (Recency, Frequency, Monetary) analysis to segment 
4,338 customers into 8 business groups using Power BI, 
Power Query, and DAX.

---

## 🎯 Business Problem

Retail businesses struggle to identify which customers 
to retain, reward, and re-engage. Without proper 
segmentation, marketing budgets are wasted on the wrong 
customers with the wrong message.

**Goal:** Segment customers based on their purchasing 
behaviour to enable targeted marketing strategies for 
each group.

---

## 📊 Dataset Information

| Detail | Info |
|---|---|
| Source | UCI Machine Learning Repository |
| Dataset | Online Retail Dataset |
| Time Period | Dec 2010 – Dec 2011 |
| Raw Rows | 541,909 transactions |
| Columns | 8 (InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country) |
| After Cleaning | ~397,000 rows |
| Unique Customers | 4,338 |

---

## 🧹 Data Cleaning Steps (Power Query)

| Step | Action | Rows Removed |
|---|---|---|
| Remove null CustomerID | Uncheck null in CustomerID filter | ~135,000 rows |
| Remove cancellations | InvoiceNo does not begin with C | ~8,905 rows |
| Remove returns | Quantity greater than 0 | ~10,624 rows |
| Remove zero price | UnitPrice greater than 0 | ~2,517 rows |
| Fix InvoiceDate type | Changed to Date/Time | — |
| Fix CustomerID type | Changed to Text | — |
| Add Revenue column | Quantity × UnitPrice | — |

---

## 🧮 RFM Methodology

### What is RFM?

| Dimension | Definition | Scoring Logic |
|---|---|---|
| Recency | Days since last purchase | Lower days = Higher score |
| Frequency | Number of unique orders | Higher orders = Higher score |
| Monetary | Total amount spent | Higher spend = Higher score |

### Scoring Scale (1–5)

**Recency Score:**
| Days Since Purchase | Score |
|---|---|
| 0 – 30 days | 5 |
| 31 – 60 days | 4 |
| 61 – 90 days | 3 |
| 91 – 180 days | 2 |
| 180+ days | 1 |

**Frequency Score:**
| Number of Orders | Score |
|---|---|
| 10+ orders | 5 |
| 6 – 9 orders | 4 |
| 4 – 5 orders | 3 |
| 2 – 3 orders | 2 |
| 1 order | 1 |

**Monetary Score:**
| Total Spend | Score |
|---|---|
| £5,000+ | 5 |
| £2,000 – £4,999 | 4 |
| £1,000 – £1,999 | 3 |
| £500 – £999 | 2 |
| Under £500 | 1 |

---

## 🏷️ Customer Segments

| Segment | Condition | Business Action |
|---|---|---|
| Champions | R≥4, F≥4, M≥4 | Reward with loyalty programs |
| Loyal Customers | R≥3, F≥3 | Upsell premium products |
| Potential Loyalists | R≥3, M≥3 | Offer membership programs |
| New Customers | R≥4, F≤2 | Onboarding email sequences |
| At Risk | R≤2, F≥3 | Win-back campaigns |
| Cant Lose Them | R=1, F≥4 | Aggressive re-engagement |
| Lost Customers | R≤2, F≤2 | High discount reactivation |
| Hibernating | Everything else | Low cost awareness campaigns |

---

## 💡 Key Insights
