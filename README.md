# 🛒 Carrefour Sales & Performance Analysis Dashboard

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

## 📌 Overview
An interactive and comprehensive Power BI dashboard designed to analyze and visualize sales performance, customer behavior, and product metrics for **Carrefour**. 

The dashboard provides actionable business insights through time-series forecasting, geographical distribution analysis, product performance tracking, and dynamic DAX-driven KPIs.

---

## 📊 Key Metrics & Highlights
* **Total Revenue:** $90.58M
* **Total Cost:** $63.96M
* **Total Profit:** $26.63M
* **Total Quantity Sold:** 149K units
* **Average Order Value (AOV):** $1.83K
* **Average Profit Per Product:** $332.85K
* **Top Country by Revenue:** Saudi Arabia ($23.7M)
* **Top Region by Profit:** MENA
* **Top Product Category:** Electronics
* **Top Sub-Category:** Laptops
* **Top Product:** MacBook Pro ($3.92M Profit)

---

## 📑 Dashboard Pages & Navigation

The Power BI report features a custom Navigation Landing Page with 3 main interactive analytical reports:

### 1. 📈 Time Series Analysis
Focuses on tracking business performance over time (2023–2025).
* **Monthly Revenue & Profit Trends:** Line charts comparing revenue, costs, and profits across months.
* **Running Totals (YTD):** Evaluates cumulative metrics (`Running_Rev_Year`, `Running_Profit_Year`, `Running_Cost_Year`, `Running_Quantity_Year`).
* **KPI Cards:** Instant high-level summary of Total Revenue, Total Cost, Total Profit, and Total Quantity.

### 2. 👥 Customers Analysis
Analyzes customer distribution, profitability, and geographic spread.
* **Geographic Insights:** Revenue by Country (Saudi Arabia, USA, Germany, Egypt) and Profit by State (Makkah, Illinois, Berlin, Riyadh, etc.).
* **Top Performers:** KPI metrics identifying top customers (e.g., David Smith as `Top1_Customer`).
* **Customer Table:** Tabular analysis of customer-level Revenue, Cost, Quantity, and their relative percentage contributions (`%Customer_Revenue`, `%Customer_Profit`).

### 3. 📦 Product Analysis
Breaks down sales performance by products, categories, and sub-categories.
* **Revenue vs. Quantity:** Combo chart showing Total Revenue and Quantity across sub-categories (Laptops, Washing Machines, Refrigerators, etc.).
* **Top Products Ranking:** Horizontal bar chart highlighting top-grossing products (MacBook Pro, Samsung Refrigerator, Toshiba Washing, etc.).
* **Product Detail Matrix:** Detailed view showing Profit, Revenue, Cost, and share percentages (`%_Products_Revenue`, `%_Products_Profit`, `%_Products_Cost`).

---

## 🧮 DAX Formulas & Calculations
The project utilizes advanced DAX (Data Analysis Expressions) measures to compute dynamic metrics, time-intelligence calculations, and rank top performers:

### 1. Key Performance Indicators (KPIs) & Averages
* `TotalCost = SUM(Sales[Cost])`
* `TotalRevenue = SUM(Sales[Revenue])`
* `TotalProfit = [TotalRevenue] - [TotalCost]`
* `Profit_Margin = DIVIDE([TotalProfit], [TotalRevenue], 0)`
* `Avg_Order_Value = DIVIDE([TotalRevenue], [TotalOrders], 0)`
* `Avg_Profit_Per_Product = DIVIDE([TotalProfit], [TotalProducts], 0)`
* `Avg_Cost_Per_Customers = DIVIDE([TotalCost], [TotalCustomers], 0)`

### 2. Time Intelligence & Running Totals
* `LY_Revenue = CALCULATE([TotalRevenue], SAMEPERIODLASTYEAR('Date'[Date]))`
* `LY_Profit = CALCULATE([TotalProfit], SAMEPERIODLASTYEAR('Date'[Date]))`
* `LY_Cost = CALCULATE([TotalCost], SAMEPERIODLASTYEAR('Date'[Date]))`
* `LY_Quantity = CALCULATE([TotalQuantity], SAMEPERIODLASTYEAR('Date'[Date]))`
* `Running_Rev_Year = CALCULATE([TotalRevenue], DATESYTD('Date'[Date]))`
* `Running_Profit_Year = CALCULATE([TotalProfit], DATESYTD('Date'[Date]))`

### 3. Top Performers Identification (Dynamic Ranking)
* `Top1_Products_Revenue = CALCULATE(SELECTEDVALUE(Product[ProductName]), TOPN(1, ALL(Product), [TotalRevenue], DESC))`
* `Top1_category_Revenue = CALCULATE(SELECTEDVALUE(Category[CategoryName]), TOPN(1, ALL(Category), [TotalRevenue], DESC))`
* `Top1_SubCategory_Revenue = CALCULATE(SELECTEDVALUE(SubCategory[SubCategoryName]), TOPN(1, ALL(SubCategory), [TotalRevenue], DESC))`
* `Top1_Customer_Rev = CALCULATE(SELECTEDVALUE(Customer[Name]), TOPN(1, ALL(Customer), [TotalRevenue], DESC))`
* `Top1_Region_Profit = CALCULATE(SELECTEDVALUE(Location[Region]), TOPN(1, ALL(Location), [TotalProfit], DESC))`
* `Top1_State_Profit = CALCULATE(SELECTEDVALUE(Location[State]), TOPN(1, ALL(Location), [TotalProfit], DESC))`

### 4. Percentage Share Measures
* `%_Products_Revenue = DIVIDE([TotalRevenue], CALCULATE([TotalRevenue], ALL(Product)), 0)`
* `%_Products_Profit = DIVIDE([TotalProfit], CALCULATE([TotalProfit], ALL(Product)), 0)`
* `%Customer_Revenue = DIVIDE([TotalRevenue], CALCULATE([TotalRevenue], ALL(Customer)), 0)`

---

## 🛠️ Tools & Features Used
* **Power BI Desktop:** Dashboard design, reporting, and visualization.
* **DAX (Data Analysis Expressions):** Data modeling, measures, time-intelligence, and ranking calculations.
* **Custom UI/UX Design:** Dark-themed dashboard with custom side navigation, icons, and filter buttons.
* **Page Navigator & Buttons:** Seamless switching between main pages and reset filter actions.
* **Interactive Slicers:** Date/Year, Month, Region, Country, City, and Product hierarchy slicers.

---

## 📂 Repository Structure
```text
├── Data/                      # Raw or processed dataset files (CSV/Excel)
├── Reports/                   # Power BI Template (.pbit) or Screenshots
├── Carrefour_Analysis.pbix    # Main Power BI Project File
└── README.md                  # Project Documentation
