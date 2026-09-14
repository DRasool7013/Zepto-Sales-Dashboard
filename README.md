# 📊 Zepto Sales Dashboard

An interactive **Excel sales analytics dashboard** for **Zepto**, built to track sales performance, customer behavior, order fulfillment, and payment trends using **PivotTables, PivotCharts, and Slicers** — a fully click-to-filter dashboard with no external tools or formulas required by the end user.

![Zepto Sales Dashboard](https://github.com/DRasool7013/Zepto-Sales-Dashboard/blob/main/Zepto%20Sales%20Dashboard.png)

---

## 📌 Overview

This dashboard gives a **360° view of sales operations** — from revenue and order volume to customer segmentation, payment behavior, and delivery performance — letting stakeholders filter and drill down interactively using slicers, all inside native Excel.

| | |
|---|---|
| **Tool used** | Microsoft Excel (PivotTables, PivotCharts, Slicers) |
| **Data source** | [`data/zepto_sales_raw_table.xlsx`](https://github.com/DRasool7013/Zepto-Sales-Dashboard/blob/main/zepto_sales_raw%20table.xlsx).  |
| **Final dashboard** | [`dashboard/zepto_sales_Dashboard.xlsx`](https://github.com/DRasool7013/Zepto-Sales-Dashboard/blob/main/zepto_sales_Dashboard.xlsx). |
| **Dashboard title** | "ZEPTO SALES DASHBOARD" |

---

## 🎯 Key Performance Indicators (KPIs)

| KPI | Value | Description |
|---|---|---|
| 💵 Total Sales | **563,284.8** | Sum of all sales revenue |
| 🛒 Total Orders | **1,499** | Count of all orders placed |
| 👥 Total Customers | **301** | Unique customers served |
| 📦 Quantity | **4,494** | Total units sold |
| 🏷️ Total Products | **201** | Unique SKUs sold |
| 📈 Average Sales | **376.0245** | Average sales value per order |

> These KPIs sit directly below the dashboard title as formula-driven summary cards (shape + cell reference), giving an at-a-glance snapshot before the user drills into any visual.

---

## 📊 Dashboard Components

| Visual | Chart Type | Insight |
|---|---|---|
| Order Contribution by Payment Method | Pie Chart | Share of orders by Card, COD, GPay, NetBanking, PhonePe, UPI |
| Sales by Customer Type Across Cities | Clustered Column | Bulk / New / Returning sales split by city (Bangalore, Delhi, Mumbai, N/A) |
| Daily Sales Performance | Area Chart | Day-wise sales trend across the month |
| Sales by Customer Segment | Column Chart | Bakery, Café, Cloud Kitchen, Household, Office, Tea Stall segments |
| Quantity Contribution by Customer Type | Pie Chart | Units sold by Bulk / New / Returning customers |
| Monthly Price Trends | Line Chart | Average price movement across months |
| Top 10 Orders by Sales Value | Horizontal Bar | Highest value orders ranked |
| Orders by Customer Segment & Delivery Status | Clustered Column | Cancelled / Delivered / Failed / Returned orders, split by customer segment |

For the full list of business questions this dashboard (and its extensions) was designed to answer, see [`DOCUMENTATION.md`](https://github.com/DRasool7013/Zepto-Sales-Dashboard/blob/main/DOCUMENTATION%20.md).

---

## 🎚️ Interactive Slicers

Four slicers are connected to every relevant PivotTable/PivotChart for synchronized, one-click filtering:

| Slicer | Filters By |
|---|---|
| **Payment_Method** | Card, COD, GPay, NetBanking, PhonePe, UPI |
| **Delivery_Status** | Cancelled, Delivered, Failed, Returned |
| **Customer_Segment** | Bakery, Café, Cloud Kitchen, Household, Office, Tea Stall |
| **Customer_Type** | Bulk, New, Returning |

Slicers are arranged along the right/left panel of the dashboard sheet, styled to match the theme, and set to a single-column layout for a clean vertical list.

### 🛠️ How to Add Slicers (Quick Steps)

1. **Build your PivotTables first** — select the raw data → `Insert` → `PivotTable` → new sheet. Create one PivotTable per chart (e.g. `PT_TopOrders`, `PT_PaymentMode`) so each visual can be wired up individually.
2. **Insert a Slicer** — click any cell inside a PivotTable → `PivotTable Analyze` (or `PivotTable Tools → Analyze`) → **Insert Slicer**.
3. **Choose fields** — tick `Payment_Method`, `Delivery_Status`, `Customer_Segment`, `Customer_Type` → **OK**.
4. **Connect one slicer to multiple PivotTables** — right-click the slicer → **Report Connections** → check every PivotTable that should respond → **OK**. This is what makes one slicer control every chart and KPI at once.
5. **Style the slicer** — select it → `Slicer` tab → pick a style from **Slicer Styles** to match the dashboard theme.
6. **Set columns** — `Slicer` → **Columns** → `1` for a vertical list layout.
7. **Move to the Dashboard sheet** — cut (`Ctrl+X`) the slicer and paste it onto the main `Dashboard` sheet near its related chart.
8. **Repeat** steps 2–7 for each remaining slicer.
9. **Test** — click a slicer button (e.g. "Delivered") and confirm every connected chart and KPI updates together.

📄 **Full step-by-step build guide (KPI cards + slicers, from scratch):** [`docs/SLICER_GUIDE.md`](docs/SLICER_GUIDE.md)

---

## 🧰 Tech Stack

- **Microsoft Excel** — PivotTables, PivotCharts, Slicers, GETPIVOTDATA
- **Power Query** — data cleaning (duplicate removal, blank handling, standardizing City/Category/Payment Method labels)
- **Design** — rounded-rectangle KPI cards, card-based layout, consistent color theme, gridlines/headings hidden for a presentation look

---

## 📁 Repository Structure

```
zepto-sales-dashboard/
│
├── assets/
│   └── dashboard-preview.png          # Screenshot of the final dashboard
│
├── data/
│   └── zepto_sales_raw_table.xlsx     # Raw/cleaned source dataset
│
├── dashboard/
│   └── zepto_sales_Dashboard.xlsx     # Final Excel dashboard file (KPIs + charts + slicers)
│
├── docs/
│   └── SLICER_GUIDE.md                # Full build guide: KPI cards & slicers, step-by-step
│
├── README.md                          # Project overview (this file)
├── DOCUMENTATION.md                   # Project aim, dataset, cleaning process, analysis, insights
└── LICENSE                            # License file
```

---

## 🚀 How to Use

1. Clone or download this repository.
2. Open `dashboard/zepto_sales_Dashboard.xlsx` in Microsoft Excel.
3. Use the **slicers** to filter by Payment Method, Delivery Status, Customer Segment, or Customer Type.
4. All KPI cards and charts update automatically based on your selection.
5. To rebuild the dashboard from scratch, follow [`docs/SLICER_GUIDE.md`](docs/SLICER_GUIDE.md).
6. For the analysis approach, cleaning steps, and insights, see [`DOCUMENTATION.md`](DOCUMENTATION.md).

---

## 👤 Author

**D. Alla Rasool**
📧 rasoolpinjari0@gmail.com
🔗 [LinkedIn](www.linkedin.com/in/drasool7663) • [Portfolio](#)


## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
