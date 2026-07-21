\# RFM Customer Segmentation Analysis



\## Overview

Analyzed 12 months of sales data (January–December 2025) to segment 

287 customers using RFM (Recency, Frequency, Monetary) methodology 

in Google BigQuery and visualized in Power BI.



\## Tools Used

| Tool | Purpose |

|---|---|

| Google BigQuery | Data storage, SQL analysis |

| Power BI | Dashboard \& Visualization |



\## Dataset

\- 12 monthly sales tables (sales202501 → sales202512)

\- Combined into one master table: `sales\_2025`

\- Fields: CustomerID, OrderID, OrderDate, ProductType, OrderValue



\## Process



\### Step 1 — Combine Monthly Tables

Combined all 12 monthly sales tables into one master table 

using UNION ALL in BigQuery.



\### Step 2 — Calculate RFM Metrics

Calculated for each customer:

\- \*\*Recency\*\* → Days since last order

\- \*\*Frequency\*\* → Total number of orders

\- \*\*Monetary\*\* → Total amount spent



\### Step 3 — Score Customers

Scored each customer from 1–10 using NTILE(10) window function

for each RFM dimension.



\### Step 4 — Segment Customers

Combined R + F + M scores into a total RFM score (max 30)

and assigned each customer to a segment.



\## SQL File

\- `rfm\_analysis.sql` — Contains all steps from combining 

&#x20; tables to final segmentation



\## Results



\### Total Customers Analyzed: 287



| Segment | Customers | Score Range |

|---|---|---|

| Engaged | 61 | 12–15 |

| Promising | 45 | 16–19 |

| Loyal VIPs | 41 | 24–27 |

| Potential Loyalists | 41 | 20–23 |

| At Risk | 38 | 4–7 |

| Requires Attention | 32 | 8–11 |

| Champions | 22 | 28–30 |

| Lost/Inactive | 7 | 0–3 |



\## Dashboard

!\[RFM Dashboard](dashboard.png)



\## Key Insights

\- \*\*Engaged\*\* is the largest segment (61 customers) — 

&#x20; these customers need nurturing to become Loyal VIPs

\- \*\*Champions\*\* (22 customers) are the most valuable — 

&#x20; high recency, frequency and monetary value

\- \*\*At Risk + Requires Attention\*\* = 70 customers — 

&#x20; need re-engagement campaigns

\- \*\*Lost/Inactive\*\* (7 customers) — 

&#x20; lowest priority, may need win-back offers



\## How to Reproduce

1\. Upload monthly CSV files to BigQuery

2\. Run `rfm\_analysis.sql` in BigQuery

3\. Connect BigQuery to Power BI

4\. Load `rfm\_segments\_final` table

5\. Build dashboard visuals



\## Author

Tejas Ratnakar Shetty

