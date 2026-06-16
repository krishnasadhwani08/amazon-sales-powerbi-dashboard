# Amazon Sales Analytics Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=flat&logo=microsoft&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)

An interactive Power BI dashboard built on Amazon sales data covering 1,28,975 orders across 69 states, transforming raw transactional records into actionable business intelligence.

---

## Dashboard Preview

### Sales Performance Overview
*Screenshot — dashboard-overview.png*

### Regional Sales Analysis
*Screenshot — sales-analysis.png*

### Promotion Impact Analysis
*Screenshot — promotion-analysis.png*

---

## Key Performance Indicators

| Metric | Value |
|---|---|
| Total Revenue | ₹7.86 Crore |
| Average Order Value | ₹648.57 |
| Total Orders | 1,28,975 |
| Cancellation Rate | 14.21% |
| States Covered | 69 |

---

## Key Insights

**Regional Performance**
- Maharashtra is the top-performing state, contributing **16.97% (₹1.33 Cr)** of total revenue
- Karnataka (₹1.05 Cr) and Telangana (₹69.2 L) follow as the next strongest markets
- The top 3 states together account for over **38%** of total revenue

**Product Performance**
- *Sets* are the highest revenue category at **₹3.92 Cr**, driven by a high AOV of ₹833
- *Kurtas* lead in units sold (45,045) but at a lower AOV of ₹456
- The ₹600–800 price range generates the highest revenue across all categories

**Promotion Effectiveness**
- Promoted products account for **68.19% of total revenue (₹5.36 Cr)**
- Promoted AOV (₹674) is **12.4% higher** than non-promoted AOV (₹600)
- Promotions drive both volume and higher spend per order

**Fulfillment & Cancellations**
- Amazon fulfills **69.55%** of orders with a cancellation rate of **12.79%**
- Merchant-fulfilled orders have a significantly higher cancellation rate of **17.47%**
- April was the peak revenue month; sales show a declining trend through June

**B2B vs B2C**
- Business is **99.32% B2C** — B2B orders represent only 0.68% of volume
- B2B AOV (₹701) is slightly higher than B2C (₹648)

---

## Data Preparation

- Removed redundant and unnamed columns
- Handled null and missing values across Amount, Qty, and status fields
- Standardized categorical fields (ship-state, Category, Status)
- Created a `Promotion_Type` column derived from promotion-ids
- Built a `Cancelled` flag from order status for cancellation analysis
- Created a `Promoted` binary flag from promotion-ids
- Prepared date fields for month-level time intelligence in DAX

---

## DAX Measures

```dax
Total Revenue = SUM('Sales'[Amount])

Average Order Value = AVERAGE('Sales'[Amount])

Cancellation Rate = 
DIVIDE(
    COUNTROWS(FILTER('Sales', 'Sales'[Status] = "Cancelled")),
    COUNTROWS('Sales')
) * 100

Promoted Revenue = 
CALCULATE(SUM('Sales'[Amount]), 'Sales'[Promoted] = 1)
```

---

## Tools & Technologies

- **Power BI Desktop** — Dashboard development and visualization
- **DAX** — KPI and measure calculations
- **Microsoft Excel** — Initial data exploration and cleaning
- **Power Query** — Data transformation pipeline

---

## Project Structure

```
amazon-sales-powerbi-dashboard/
│
├── Dashboard.pbix
├── README.md
├── Screenshots/
│   ├── dashboard-overview.png
│   ├── sales-analysis.png
│   └── promotion-analysis.png
│
└── Dataset/
    └── Amazon_Sale_Report.csv
```

---

## Future Enhancements

- Customer segmentation by purchase frequency and value
- Predictive sales forecasting using time-series models
- State-level heatmap for geographic visualization
- Cancellation root-cause analysis by product and fulfillment type
- Automated report refresh and scheduling

---

## Author

**Krishna Sadhwani**
B.Tech CSE (AI & ML)

Data Analyst | Power BI Developer | Machine Learning

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/krishna-sadhwani-109366330)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black)](https://github.com/krishnasadhwani08)
