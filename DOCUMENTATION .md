# 📄 Documentation — Zepto Sales Dashboard

This document covers the project aim, dataset description, cleaning process, the full set of analysis questions the project was built to answer, and the final results, outcomes, and insights.

---

## 🎯 Project Aim / Goal

Build a fully interactive, formula-and-slicer-driven **Excel sales dashboard** for Zepto that lets a non-technical stakeholder answer sales, customer, payment, and delivery questions by clicking slicers — with no manual filtering, VLOOKUPs, or external BI tool required. The dashboard needed to surface:

- Overall business health at a glance (KPI cards)
- Where revenue and volume come from (orders, customers, SKUs, cities, segments)
- How customers pay, and how that varies by customer type
- How reliably orders are delivered (cancelled / delivered / failed / returned)
- Trends over time (daily, monthly)

---

## 🗃️ Dataset Description

**Source file:** [`data/zepto_sales_raw_table.xlsx`](https://github.com/DRasool7013/Zepto-Sales-Dashboard/blob/main/zepto_sales_raw%20table.xlsx)

The raw dataset is a transaction-level table of Zepto sales orders, with one row per order line, including fields such as:

- Order ID, Order Date
- Customer ID, City
- Customer Segment (Bakery, Café, Cloud Kitchen, Household, Office, Tea Stall)
- Customer Type (Bulk, New, Returning)
- Product ID, Quantity, Price, Sales value
- Payment Method (Card, COD, GPay, NetBanking, PhonePe, UPI)
- Delivery Status (Cancelled, Delivered, Failed, Returned)

Loaded into a sheet and converted into a structured Excel **Table** (`Ctrl+T`) so every PivotTable and formula stays dynamic as rows are added.

---

## 🧹 Cleaning Process

Performed with **Power Query** and native Excel tools before any PivotTable was built:

1. Removed duplicate order rows.
2. Standardized text fields — City, Customer Segment, and Payment Method labels were inconsistently cased/spelled in the source export and were normalized (e.g. unifying Payment Method values down to Card / COD / GPay / NetBanking / PhonePe / UPI).
3. Handled blanks — rows with missing City were bucketed as `N/A` rather than dropped, so they remain visible and filterable rather than silently disappearing.
4. Validated numeric fields (Sales, Quantity, Price) for negative/zero anomalies before aggregating.
5. Loaded the cleaned table into the Excel Data Model so all PivotTables reference the same source, which is required for **Report Connections** (shared slicers) to work across every chart.

---

## 🧮 Analysis Questions

The project was scoped from a working list of business questions. The table below maps each question to how it was addressed in the dashboard.

| # | Question | Status / Visual |
|---|---|---|
| 1 | Top 10 orders by sales value | ✅ Top 10 Orders by Sales Value (horizontal bar) |
| 2 | Top 10 customers | 🔲 Future scope — same PivotTable pattern as Top 10 Orders, filtered on Customer ID |
| 3 | Top 10 SKUs | 🔲 Future scope — Value Filter → Top 10 on Product ID |
| 4 | Bottom 10 orders | 🔲 Future scope — Value Filter → Bottom 10 |
| 5 | Bottom 10 customers | 🔲 Future scope |
| 6 | Bottom 10 SKUs | 🔲 Future scope |
| 7 | Trend of sales over months | ✅ Monthly Price Trends captures the price angle; a parallel Sales-over-months line can reuse the same PivotTable with Sum of Sales |
| 8 | Trend of price over months | ✅ Monthly Price Trends (line chart) |
| 9 | Trend of quantity over months | 🔲 Future scope — same pattern, Sum of Quantity by month |
| 10 | Volume of sales over days | ✅ Daily Sales Performance (area chart) |
| 11 | Volume of quantity over days | 🔲 Future scope — same pattern as Daily Sales Performance, Sum of Quantity |
| 12 | Chart to display volume of sub-total over days | ✅ Covered by Daily Sales Performance |
| 13 | Compare sales over different customer segments | ✅ Sales by Customer Segment (column chart) |
| 14 | Compare sales over different cities | ✅ Sales by Customer Type Across Cities (clustered column) |
| 15 | Compare the payment method of sales | ✅ Order Contribution by Payment Method (pie chart) |
| 16 | Compare payment method of sales over customer type | 🔲 Future scope — clustered column, Payment Method × Customer Type |
| 17 | Show contribution of customer type to quantity | ✅ Quantity Contribution by Customer Type (pie chart) |
| 18 | Show contribution of payment method to orders (Order ID in Values as Count) | 🔲 Future scope — Payment Method PivotTable with Count of Order ID |
| 19 | Show contribution of customers by city | 🔲 Future scope — Count of Customer ID by City |
| 20 | Compare customer type by each city over sales | ✅ Sales by Customer Type Across Cities (clustered column) |
| 21 | Compare customer type by payment method | 🔲 Future scope |
| 22 | Compare customer segment by delivery status (orders received vs not received) | ✅ Orders by Customer Segment & Delivery Status (clustered column) |

**8 of the 22 planned questions are live on the current dashboard sheet** (all core KPI, trend, and segment/payment/delivery views). The remaining items are scoped as extensions using the same PivotTable → PivotChart → Slicer pattern documented in [`docs/SLICER_GUIDE.md`](docs/SLICER_GUIDE.md), so they can be added without restructuring the workbook.

---

## 📈 Final Result

A single-sheet, presentation-style **Dashboard** tab with:

- 6 KPI cards (Total Sales, Total Orders, Total Customers, Quantity, Total Products, Average Sales)
- 8 PivotCharts covering payment methods, customer segments, cities, customer types, delivery status, and time trends
- 4 slicers (Payment_Method, Delivery_Status, Customer_Segment, Customer_Type), each connected to every relevant PivotTable, so one click updates the entire dashboard simultaneously
- Gridlines/headings hidden and sheet optionally protected, so end users can only interact with the slicers — nothing can be accidentally overwritten

## 🔍 Outcomes & Insights

- **Total Sales of 563,284.8** across **1,499 orders** from **301 customers**, giving an average order value of **~376**.
- **4,494 units** sold across **201 unique SKUs**, indicating a broad, long-tail product mix rather than a few dominant items.
- Sales by city shows a concentration pattern across Bangalore, Delhi, and Mumbai, with Bulk/New/Returning customer types split differently by city — useful for city-level marketing or fulfillment decisions.
- Payment method mix (Card, COD, GPay, NetBanking, PhonePe, UPI) shows where digital-payment adoption is strongest, which can guide payment-partner negotiations or COD-reduction strategies.
- Order Contribution by Customer Segment & Delivery Status highlights which segments have disproportionate Cancelled/Failed/Returned rates — a direct input for operations and delivery-partner review.
- Daily Sales Performance and Monthly Price Trends together separate **volume-driven** revenue swings from **price-driven** ones, which is useful when diagnosing a revenue dip.

---

## 🔗 Related Files

- [`README.md`](README.md) — project overview, KPI table, dashboard components, slicer summary
- [`docs/SLICER_GUIDE.md`](docs/SLICER_GUIDE.md) — full step-by-step build guide for KPI cards and slicers
- [`dashboard/zepto_sales_Dashboard.xlsx`](https://github.com/DRasool7013/Zepto-Sales-Dashboard/blob/main/zepto_sales_Dashboard.xlsx)— final Excel dashboard file
- [`data/zepto_sales_raw_table.xlsx`](https://github.com/DRasool7013/Zepto-Sales-Dashboard/blob/main/zepto_sales_raw%20table.xlsx)— source dataset
